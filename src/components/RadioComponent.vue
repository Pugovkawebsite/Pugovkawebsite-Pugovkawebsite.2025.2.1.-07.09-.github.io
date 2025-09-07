<template>
  <div>
    <form name="myForm" @submit.prevent>
    
        <input type="radio" name="budget" value="$5.000 - $10.000" v-model="budget.budget"><span>$5.000 - $10.000</span>
        <input type="radio" name="budget" value="$10.000 - $20.000" v-model="budget.budget"><span>$10.000 - $20.000</span>
        <input type="radio" name="budget" value="$20.000 - $50.000" v-model="budget.budget"><span>$20.000 - $50.000</span>
        <input type="radio" name="budget" value="$50.000 +" v-model="budget.budget"><span>$50.000 +</span>

      
        
        <button-component @click="chooseRadio">"button"</button-component>
        <span>Выбрано: {{ budget.budget }}</span>
        
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
                budget: {
                    budget: ''
                }
            }
        },
        methods: {
           chooseRadio() {
                this.$emit('save', this.budget);
                console.log(this.budget);
                
            }
           
        },    
        
    }


</script>



<style scoped>

</style>
