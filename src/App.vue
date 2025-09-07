<template>
  <div>
  <input-component @save="saveInformation"></input-component>
  </div>
<div>
  <checkbox-component @save="saveInformation" ></checkbox-component>
  </div>
<div>
  <radio-component @save="saveInformation"></radio-component>
  </div>
  <div>
     <div>
    <div class="red active"></div>
    <div class="pink active__no"></div>
    <div class="orange active__no"></div>
    <div class="blue active__no"></div>
    </div>
    <button id="button__previous" class="active__no" @click="clickPrevious"> Previous step</button>
    <button id="button" @click="clickNext"> Next</button>
    
  </div>
  
</template>


<script>
import InputComponent from './components/InputComponent.vue';
import CheckboxComponent from './components/CheckboxComponent.vue';
import RadioComponent from './components/RadioComponent.vue';

export default {
  components: {
   InputComponent,
   CheckboxComponent,
   RadioComponent
  },
  data() {
    return {
      user: {

      }
    }
  },
  methods: {
    saveInformation(information) {
      const user = Object.assign(information);
      console.log(user);
    },
    clickNext(e) {
      let children = e.target.parentNode.firstChild.children;
      let parent = e.target.parentNode.firstChild;
      
      console.log(children);
      console.log(parent);
      for (let element of children) {
        if (element.classList.contains("active")) {
       console.log(children.item(element));
       let index = Array.prototype.indexOf.call(children, element);
       
          document.getElementById("button__previous").classList.remove('active__no');
          
       
       if ((index+2) < children.length) {
       console.log(index);
       console.log(children.length);
       
       console.log(children.item(index + 1));
       children.item(index).classList.remove('active');
       children.item(index).classList.add('active__no');

       children.item(index+1).classList.remove('active__no');
      children.item(index+1).classList.add('active'); break;
       } else if ((index+2) == children.length) {
        children.item(index).classList.remove('active');
       children.item(index).classList.add('active__no');

       children.item(index+1).classList.remove('active__no');
      children.item(index+1).classList.add('active');

        document.getElementById("button").classList.add('active__no'); break;
       }
       
        else {
        children.item(index).classList.remove('active');
       children.item(index).classList.add('active__no');

       children.item(index+1).classList.remove('active__no');
      children.item(index+1).classList.add('active'); break;
      
       }
       } 
}


      
    },
    clickPrevious(e) {
      let children = e.target.parentNode.firstChild.children;
      let parent = e.target.parentNode.firstChild;
      
     
      for (let element of children) {
        if (element.classList.contains("active")) {
       console.log(children.item(element));
       let index = Array.prototype.indexOf.call(children, element); //индекс активного элемента//
       document.getElementById("button").classList.remove('active__no');
       if (index == 1) {
       
       children.item(index).classList.remove('active');
       children.item(index).classList.add('active__no');

       children.item(index-1).classList.remove('active__no');
      children.item(index-1).classList.add('active');

       document.getElementById("button__previous").classList.add('active__no'); break;
       } else {
        children.item(index).classList.remove('active');
       children.item(index).classList.add('active__no');

       children.item(index-1).classList.remove('active__no');
      children.item(index-1).classList.add('active');

       
       }
       
       
       } 
}
    }
  }
}


</script>



<style scoped>
.red {
  width: 104px;
  height: 114px;
  background-color: red;
}
.pink {
  width: 104px;
  height: 114px;
  background-color: pink;
}
.orange {
  width: 104px;
  height: 114px;
  background-color: orange;
}
.blue {
  width: 104px;
  height: 114px;
  background-color: blue;
}
.active {
  display: block;
}
.active__no {
  display: none;
}
#button {
  width: 204px;
  height: 214px;
  border: 3px solid green;
}
#button__previous {
  width: 204px;
  height: 214px;
  border: 3px solid red;
}
</style>
