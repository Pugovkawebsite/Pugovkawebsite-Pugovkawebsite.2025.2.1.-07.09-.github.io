<template>
  <div id="input-main__content">
  <form action="#" @submit.prevent>
    <div class="form-main">

    <div class="input-main__wrap__big">

    <h3 class="input-main__title">Contact details</h3>
    <h4 class="input-main__title__small">Lorem ipsum dolor sit amet consectetur adipisc.</h4>
      <div class="input-main__wrap__small">  
        <div class="input-main"> 
            <label class="input-main__label" for="name">Name</label>
            <input class="input-real" name="name" :value="input.name" @change="input.name=$event.target.value"  placeholder="Name">
            <img class="input-main__img" src="../img/Name.svg">
        </div>
        <div class="input-main"> 
            <label class="input-main__label" for="email">Email </label>
            <input class="input-real" name="email" :value="input.email" @change="input.email=$event.target.value" type="email" placeholder="Email">
            <img class="input-main__img" src="../img/Email.svg">
        </div>
        
        <div class="input-main"> 
            <label class="input-main__label" for="number">Phone Number</label>
            <input class="input-real" name="number" :value="input.number" @change="input.number=$event.target.value" type="tel" placeholder="Number">
            <img class="input-main__img" src="../img/Phone.svg">
        </div>
        
        <div class="input-main"> 
            <label class="input-main__label" for="company">Company</label>
            <input class="input-real" placeholder="Company name" name="company" :value="input.company" @change="input.company=$event.target.value" type="text" >
            <img class="input-main__img" src="../img/Company.svg">
        </div>
        </div>
    </div>
    </div>
    
    <button-component @click="saveInput">"button"</button-component>
  </form>
  
  
  </div>

  
</template>


<script>

import ButtonComponent from './ButtonComponent.vue';
    export default {
        components: {
            ButtonComponent
        },
        data() {
            return {
                input: {
                    name: " ",
                    email: " ",
                    number: " ",
                    company: " "
                }
            }
        },
        methods: {
            saveInput() {
                this.input.id = Date.now();
                this.$emit('save', this.input);
                console.log(this.input);
                this.input = {
                    name: " ",
                    email: " ",
                    number: " ",
                    company: " "
                }
                const input = document.getElementById("input-main__content");
                input.style.display = "none";
            }
        }
    }


</script>



<style scoped>
.form-main {
    border: 1px solid #D9DBE9;
    border-radius: 34px;
    width: 698px;
    height: 606px;
    box-shadow: 0 5px 16px 0 rgba(8, 15, 52, 0.06);
    background: white;
    padding: 32px 50px 80px 50px;
    margin-bottom: 31.61px;
}
.input-real {
    border: 1px solid #D9DBE9;
    border-radius: 46px;
    width: 284px;
    height: 66px;
    box-shadow: 0 2px 6px 0 rgba(19, 18, 66, 0.07);
    background: white;
    padding-left: 20.72px;
    
    
}
input::placeholder {
    font-weight: 400;
    font-size: 18px;
    color: red;
}
.input-main__label {
    font-weight: 500;
    font-size: 18px;
    color: #170F49;
}
.input-main {
    width: 284px;
    height: 105px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    position: relative;
}
.input-main__img {
    position: absolute;
    width: 23px;
    height: 29px;
    bottom: 20.09px;
    right: 22.25px;
}
.input-main__wrap__big {
    width: 596px;
    height: 362px;
}
.input-main__title {
    font-weight: 700;
    font-size: 34px;
    color: #170F49;
    margin-bottom: 7.5px;
}
.input-main__title__small {
    font-weight: 400;
    font-size: 18px;
    color: #6F6C90;
    margin-bottom: 39px;
}
.input-main__wrap__small {
    width: 596px;
    height: 250px;
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    
}
form {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: end;
}
</style>
