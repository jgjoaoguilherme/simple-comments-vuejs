<template>
  <div class="form-todo form-group">
    <p>
      <input type="text" name="author" placeholder="nome" class="form-control" v-model="name">
    </p>
    <p>
      <textarea placeholder="comentário" name="message" class="form-control" v-model="message"></textarea>
    </p>
    <button v-on:click="addComment" type="submit" class="btn btn-primary">Comentar</button>
  </div>
</template>


<script>
  export default{
      data(){
        return{
          comments: [],
          name: '',
          message: ''
        }
      },
      methods:
      {
        addComment()
        {
          if(this.name.trim() === '' || this.message.trim() === '')
          {
            alert('insira todas as informações');
            return;
          }

          // passando evento
          this.$emit('add-todo', {
            name: this.name,
            message: this.message
          })

          this.name = '';
          this.message = '';
        },
        removeComment(index)
        {
          this.comments.splice(index, 1)
        }
      }
    }
</script>
