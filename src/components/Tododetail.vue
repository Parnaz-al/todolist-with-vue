<template>
  
    <div class="singletodo">
        <div>
            <input  type="radio" >
            <span>{{done.work}} </span>
        </div>
        <div>
            <button class="btn" @click="del">DELETE</button>
        </div>
         
    </div>    
    </template>
    
    <script>
    export default {
    props:['done' ,'check','counter'],
    emits: ['del'],
    setup(props,{emit}){
        const del=()=>{
    
          emit('dele',props.done)
    
        }
        return{del}
    }
    }
    
    
    </script>
    
    <style scoped>
    .pink {
        accent-color:rgb(207, 19, 50);
    }
    .blue{
      accent-color:blue;
      appearance: none;
      -webkit-appearance: none;
      border-radius: 50%;
      background: #e8e8e8;
      border: 3px solid #FFF;
    
      /* The outline will be the outer circle */
      outline: 1px solid #999;}
    
    .singletodo{
        width:485px;
        margin-top:10px;
        padding:10px;
        background-color: white;
        text-align: left;
        border-radius:5px;
        display: flex;
        justify-content:space-between;
        flex-direction: row;
        
    
      }
      span{
        padding-left:5px ;
        font-size: 17px;
    
    
      }
      .btn{
        border: none;
        background-color: crimson;
        border-radius: 7px;
        padding: 5px;
        font-size: 13px;
        color: white;
      }
    
    </style>