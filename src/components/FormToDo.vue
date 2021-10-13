<template>
  <div class="form-todo form-group">
    <p>
      <input type="text" name="author" id="" placeholder="nome" v-model="name" class="form-control">
    </p>
    <p>
      <textarea name="message" class="form-control" v-model="message" placeholder="comentário"></textarea>
    </p>
    <button type="submit" class="btn btn-primary" v-on:click="addComment">
      Comentar
    </button>
  </div>
</template>

<script>
export default {
  data:function() {
      return {
        name:'',
        message:'',
      };
    },
   methods: {
      addComment() {
        if (this.message.trim() === ''){
          return;
        }

        this.$emit('addToDo',{
          name:this.name,
          message:this.message,
        });
        this.name = '';
        this.message ='';
      },
    },
}
</script>
