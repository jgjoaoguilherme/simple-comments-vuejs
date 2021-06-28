<template>
  <div class="container">
    <h1>Comentários</h1>
    <FormTodo v-on:add-todo="addComment"></FormTodo>
    <div class="list-group-item" v-for="(comment, index) in comments" v-bind:key="index">
      <span class="comment_author"><strong>Author: </strong>{{ comment.name }}</span>
      <p>{{ comment.message}}</p>
      <div>
        <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)">Exlcuir</a>
      </div>
    </div>
  </div>
</template>



<script>
  import FormTodo from './FormTodo';

  export default{
      components:{
        FormTodo
      },
      data(){
        return{
          comments: []
        }
      },
      methods:
      {
        addComment(comment){
          this.comments.push(comment)
        },
        removeComment(index)
        {
          this.comments.splice(index, 1)
        }
      },
      watch:{
        comments(val)
        {
          console.log("aqui: ", val)
        }
      }
  }
</script>
