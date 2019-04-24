<template>
    <div class="clearAllContainer">
        <span class="clearAllBtn" @click="clearTodo">Clear All</span>
    </div>
</template>

<script>
export default {
    methods: {
        clearTodo(){
            this.$emit('removeAll');
        }
    }
}
</script>

<style>

.clearAllContainer { width: 8.5rem; height: 50px; line-height: 50px; margin: 0 auto; border-radius: 5px; background: #fff; }
.clearAllBtn { display: block; margin: 0.5rem 0; color: #e20303; cursor: pointer; }

</style>

