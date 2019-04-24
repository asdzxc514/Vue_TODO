<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo" placeholder="Type what you have to do">
        <span class="addContainer" v-on:click="addTodo">
            <i class="addBtn fas fa-plus" aria-hidden="true"></i>
        </span>

        <modal v-if="showModal" @close="showModal = false">
            <i slot="header" class="closeModalBtn fas fa-times" aria-hidden="true" @click="showModal = false"></i>
            <h3 slot="header">경고</h3>    
            <span slot="body">할 일을 입력하세요.</span>
        </modal>

    </div>
</template>

<script>
import Modal from './common/Modal.vue'

export default {
    data() {
        return { 
            newTodoItem: '',
            showModal: false
        }
    },
    methods: {
        addTodo() {
            if(this.newTodoItem !== ""){
                var value = this.newTodoItem && this.newTodoItem.trim();
                this.$emit('addTodo', value);
                this.clearInput();
            } else{
                this.showModal = !this.showModal;
            }
        },
        clearInput(){
            this.newTodoItem = '';
        }        
    },
    components: {
        Modal: Modal
    }
}
</script>

<style>

input:focus { outline: none; }
.inputBox { max-width: 400px; height: 50px; line-height: 50px; margin: 0 auto; border-radius: 5px; background: #fff; }
.inputBox input { width: calc(100% - 3rem); height: 45px; padding: 0 0.9rem; font-size: 0.9rem; border-style: none; }
.addContainer { float: right; display: block; width: 3rem; border-radius: 0 5px 5px 0; background: linear-gradient(to right, #6378fb, #8763fb); cursor: pointer; }
.addBtn { vertical-align: middle; color: #fff; }

.modal-container { position: relative; }
.closeModalBtn { position: absolute; right: 5%; padding: 5px; cursor: pointer; }

</style>

