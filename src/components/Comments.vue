
<template>
<div class="container">
  <h1>Comentários</h1>
  <hr/>
  <FormToDo v-on:addToDo="addComment"/>
  <div class="list-group">
    <p v-if="comments.length <= 0">Sem comentários</p>
    <div class="list-group-item" v-for="(comment,index) in allComments" v-bind:key="index" >
      <span class="comment__author">Autor: <strong>{{comment.name}}</strong></span>
      <p>{{comment.message}}</p>
      <div>
        <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)" >
          Excluir
        </a>
      </div>
    </div>
  </div>
  <hr>
</div>

</template>



<script>
import FormToDo from './FormToDo';
  export default {
    components:{
      FormToDo,
    },
    data:function() {
      return {
        comments:[

        ],

      };
    },
    methods: {
      addComment(comment) {
        this.comments.push(comment);
      },
      removeComment(index) {
        this.comments.splice(index, 1);
      }

    },
    computed:{
      allComments() {
        return this.comments.map((comment) => (
          {
          ...comment,
          name: comment.name.trim() === '' ? 'Anônimo' : comment.name
          }
        ))
      }
    },
    watch:{
      comments(){

      }
    }
  }
</script>

