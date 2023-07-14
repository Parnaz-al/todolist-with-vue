<template>
  <div class="all">
  <h2>What's up, 
    <input v-if="showname" class="section1" type="text" v-model="name" placeholder="Name here" @keyup.enter="showname=false"> 
    <span v-if="!showname">{{name}}</span>
  </h2>
  <p class="section2">CREATE A TODO</p>
  <p class="section3">What's on your todo listt?</p>
  <input class="section4" v-model="work" type="text" placeholder="e.g. make a video">
  <p class="section3" >Pick a category</p>
  <div class="section6">
    <div class="inner">
      <input type="checkbox" class="business" v-model="check"  >
      <p>Business</p>
      

    </div>
    <div class="inner">
      <input type="checkbox" class="personal" v-model="check2"  >
      <p>Personal</p>

    </div>
    
   
    
  </div>
  <button @click="addtodo" class="addtodo">Add todo</button>
  <div v-for="done in todo" :key="done" >
    <Tododetail :done="done" :check="check"  @dele="dele"  :class="{ pink : done.gitcheck==true }" />

  </div>

</div>


</template>

<script>

import {ref} from 'vue'
import Tododetail from './components/Tododetail.vue'




export default {
  components:{Tododetail},
  
  setup() {
    let name= ref('')
    let check =ref(false)
    let check2=ref(false)
    let showname=ref(true)
    let work=ref(null)
    let todo=ref([])
    console.log(check,todo)
    let counter=ref(-1)
    let checks=ref([])



    const addtodo=()=>{
      todo.value.push({
        check:check.value,
        work:work.value,
        check2:!check.value

        
      })
    
    }
    const dele=(a)=>{
      todo.value = todo.value.filter((item) => {return item != a});
    
    }

    return{name,showname, check,todo,check2,work,addtodo,counter,dele,checks}
    
    
  }


  


}
</script>

<style>

.all{
  width:500px;
  margin: auto;
  background-color: rgb(224, 224, 224);
  padding:20px;
  
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}
.section1 {

  background-color: rgb(224, 224, 224);
  border: none;
  font-size:20px;
  outline: none;
  width:60px;
  
}
.section2{
  text-align: left;
  font-size:13px;
  color:gray;

 

}
.section3{
  text-align: left;
  font-size:12px;
  color:gray;
  margin:7px;


}
 p{
  margin:3px;
 }
 h2{
  text-align: left;
 }
.section4{
  width:495px;
  margin-top: 10px;
  height: 40px;
  border:none;
  border-radius:5px;
  padding:10px;
  font-size: 20px;
  box-sizing: border-box;
}

.section6{
  display:flex;
  flex-direction:row;
  justify-content:space-around;
  
}
.section6 .inner{
  background-color: white ;
  width: 244px;
  padding: 5px;
  border-radius:5px;
  height:80px;
  box-sizing: border-box;
  padding-top: 15px;
}
.addtodo{
margin-top:15px;
width: 495px;
padding: 5px;
border: none;
background-color:aqua;
border-radius:5px;
color: white;
font-size: 17px;
}
.business{
  accent-color:rgb(207, 19, 50);

}
.pink{
  accent-color:rgb(207, 19, 50);

}
</style>