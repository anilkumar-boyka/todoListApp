<template>
 <div>
     <h1 class="time">{{time()}}</h1>
     <h1>Keep Your Todo List Items Here</h1>
     {{show}}

<div class="box">
    
    
        <form class="item" @submit.prevent="add">

    <!-- <input class="text"v-model="newItem" required  placeholder="Add Item "> -->
    <button  class="add" type="submit.prevent">+</button><br>
  </form>
  <div>
  <ul>
      <li>
          
          
          <button class="remove"v-on:click="remove(input)"><i class="fas fa-trash-alt fa-2x"></i></button>
      </li>
  </ul>
  </div>
</div>
 </div>
</template>

<script>

export default {
    name:'Todo',
    data()
    {   return{
           newItem:'',
           inputs:[],
           
               
        }     
            
    },           
           
     methods:{
         time:function(){
             var d = (new Date()).toString().split(' ').splice(1,3).join(' ');
             return d;
         },
        add:function()
        {
            // this.inputs.push({
            //     title:this.newItem,
            //     done:false
            // });
               this.newItem='';
           
                alert("i am clicked..");
                
                 var playersRef = firebase.database().ref("todoItems/");

                    // playersRef.push({
                    //    [] data1:{
                    //       number: 1,
                    //       age: 30
                    //    },
                    //    data2:{
                    //     number:2,
                    //     age:40
                    //    },
                    //    data2:{
                    //     number:3,
                    //     age:50
                    //    },
                    //});
                     // Get a reference to the database service
                       // var ref = new Firebase('https://tutorialsfirebase.firebaseio.com');
                       var playersRef = firebase.database().ref("todoItems/");

                        var playersRef = firebase.database().ref().child("todoItems");
                        playersRef.push ({
                           name: "amit",
                           number: 1,
                           age: 30
                        });

                        playersRef.push ({
                           name: "Anil",
                           number: 2,
                           age: 20
                        });


                          var playersRef = firebase.database().ref("todoItems/");

                          playersRef.orderByChild("name").on("child_added", function(data) {
                             // console.log(data.val().name);
                             // console.log(data.val().number);
                          });

                          
                                                                        
        },


                  show:function()
                     {
                      console.log("showwww..");
                      var playersRef = firebase.database().ref("todoItems/");

                          playersRef.orderByChild("name").on("child_added", function(data) {
                             console.log("show"+data.val().name);
                             console.log(data.val().number);
                             return(data.val().name[0]);
                          });

                          

                   },
                       

                    
         











          


          

            








            

            

       

        remove:function(input)
        { console.log("single op is:"+input);
          const inputIndex=this.inputs.indexOf(input);
          this.inputs.splice(inputIndex,1);

        }
    }


}
    

</script>
<style scoped>

.done{
    text-decoration: line-through;
}

.item{
    min-height: 30px;
    align-items: center;
    border-bottom: 1px solid #f1f1f1;
    display: flex;
    font-family: 'Oxygen', sans-serif;
}

::placeholder
{
    color:grey;
    opacity: 1;
}
 .text{
     text-align: center;
     height: 60px;
     top:10px;
     font-size:30px;
     width:360px;
     border:none;
     outline: none;
     box-shadow:inset 0 -3px 0 0 #A683E3;
 }

 .box{
     max-width: 500px;
     margin:50px auto;
     background-color: white;
     border-radius: 5px;
     box-shadow:7px 17px 35px -5px rgba(0,0,0,0.3);
 } 
 .add{
     min-height: 50px;
     width:50px;
     border-radius: 50px;
     border-color: transparent;
     background-color: #A683E3;
     color:white;
     font-size:30px;
     padding-bottom: 6px;
     border-width:0;
     margin-left: 12px;

 }

 .showitem{
     margin-right:10px ;
     padding:20px 30px 10px 20px;
     font-size:20px;
     font-weight: 1100;
     color:#00204a;
     width:275px;
     font-family: 'Oxygen', sans-serif;
     font-size: x-large;
 }

 input[type="checkbox"]
 {
     margin: 20px;
 }

h1{
color:#A683E3;
text-align: center;
padding:30px;
opacity:0.9;
}
 .remove{
     margin-left: 350px;
     position: absolute;
     border:none;
     background-color:transparent;
     opacity:0.5;
      }

      .time{
          color:grey;
          text-align: left;
           opacity:0.6;
          
         
      }
</style>