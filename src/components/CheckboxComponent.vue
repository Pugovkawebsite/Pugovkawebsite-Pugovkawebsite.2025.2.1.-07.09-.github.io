<template>
  <div>
    <form @submit.prevent>
        <div class="checkbox-elem" v-for="checkbox in checkboxes">
            <input type="checkbox" class="checkbox" :id="checkbox.id" :value="checkbox.id" v-model="selectedUsers" :checked="checkbox.checked">
            <label class="checkbox-elem__label" :for="checkbox.id">{{checkbox.label}}</label>
            <img class="checkbox-elem__img" :src="checkbox.src">
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
                checkboxes: [
                    {id:'development', label: 'Development', checked: false, src: "src/img/checkbox/development.svg"},
                    {id:'design', label: 'Web Design', checked: false, src: "src/img/checkbox/design.svg"},
                    {id:'marketing', label: 'Marketing', checked: false, src: "src/img/checkbox/marketing.svg"},
                    {id:'other', label: 'Other', checked: false, src: "src/img/checkbox/other.svg"}
                ],
                selectedUsers: [
                    
                ]
            }
        },
        methods: {
           saveInput() {
                console.log(this.selectedUsers);
                this.$emit('save', this.selectedUsers);
                checkboxes: [
                    {id:'development', label: 'Development', checked: false},
                    {id:'design', label: 'Web Design', checked: false},
                    {id:'marketing', label: 'Marketing', checked: false},
                    {id:'other', label: 'Other', checked: false}
                ]
           }
           
        },    
        
    }


</script>



<style scoped>
.checkbox-elem {
    width: 284px;
    height: 114px;
    position: relative;
}
.checkbox-elem__new {
    border: 1px solid #D9DBE9;
    border-radius: 16px;
    width: 284px;
    height: 114px;
    position: absolute;
    top: 0px;
    left: 0px;
}
.checkbox-elem__label {
    font-weight: 500;
    font-size: 18px;
    color: #170F49;
    position: absolute;
    top: 47px;
    left: 105px;
}
.checkbox {
    appearance: none;
    position: relative;
    border: 1px solid #EFF0F7;
    border-radius: 16px;
    width: 284px;
    height: 114px;
    position: relative;
}
.checkbox:checked {
    border: 2px solid #4A3AFF;
    box-shadow: 0 4px 10px 0 rgba(31, 37, 89, 0.07), 0 2px 11px 0 rgba(69, 65, 164, 0.06);
}
.checkbox-elem__img {
    position: absolute;
    top: 24px;
    left: 26px;
}
</style>
