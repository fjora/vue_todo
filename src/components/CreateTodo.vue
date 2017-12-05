<template>
  <div class="ui basic content center aligned segment">
      <div class="ui centered card">
          <div class="content">
              <div class="ui form">
                  <div class="field">
                      <label>Title</label>
                      <input v-model="titleText" type="text">
                  </div>
                  <div class="field">
                      <label>Project</label>
                      <textarea v-model="projectText"></textarea>
                  </div>
                  <div class="ui two button attached buttons">
                      <button class="ui basic blue button" v-on:click="sendForm()">
                          Create
                      </button>
                  </div>
              </div>
          </div>
      </div>              
  </div>
</template>

<script>
export default {
  data() {
      return {
          titleText: '',
          projectText: '',
      };
  },
  methods: {
      sendForm(){
          console.log(this.titleText.length)
          console.log(this.titleText.length > 0 && this.projectText.length > 0)
          if(this.titleText.length > 0 && this.projectText.length > 0){
            const title = this.titleText;
            const project = this.projectText;
            this.$emit('create-todo', {
                title,
                project,
                done: false,
            });
            this.titleText = '';
            this.projectText = '';
          }
      }
  }
}
</script>

