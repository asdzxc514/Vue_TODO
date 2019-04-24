<template>
    <section>
        <transition-group name="list" tag="ul">
            <li v-for="(todoItem, index) in propsdata" :key="todoItem" class="shadow">
                <i class="checkBtn fas fa-check" aria-hidden="true"></i>
                <div class="todo_txt">{{ todoItem }}</div>
                <span type="button" @click="removeTodo(todoItem, index)" class="removeBtn">
                    <i class="far fa-trash-alt" aria-hidden="true"></i>
                </span>
            </li>
        </transition-group>
    </section>
</template>

<script>
export default {
    props: ['propsdata'],
    methods: {
        removeTodo(todoItem, index){
            this.$emit('removeTodo', todoItem, index);
        }
    }
}
</script>

<style>

ul { max-width: 400px; padding-left: 0; margin: 20px auto; text-align: left; list-style-type: none; }
li { position: relative; height: auto; min-height: 50px; line-height: 1.4; vertical-align: middle; margin: 0.5rem 0; padding: 0.9rem 0.9rem; overflow: hidden; word-break: break-all; border-radius: 5px; background: #fff;  }
li > * { float: left; }
.checkBtn { display: block; width: 4%; margin-right: 15px; height: 100%; color: #62acde}
.todo_txt { width: 83%; }
.removeBtn { float: right; width: 4%; height: 100%; color: #de4343; }
.removeBtn i { cursor: pointer; }

.list-enter-active, .list-leave-active { transition: all .7s; }
.list-enter, .list-leave-to { transform: translateY(-20px); opacity:0; }
</style>

