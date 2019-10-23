<template>
  <div class="container mt-2">
    <h1 class="mb-3">Ask a Question</h1>
    <form @submit.prevent="onSubmit">
      <textarea 
        v-model="question_body"
        class="form-control"
        placeholder="What do you want to ask?"
        rows="3">
      </textarea>
      <br>
      <button
        type="submit"
        class="btn btn-success">
        Publish
      </button>
    </form>
    <p v-if="error" class="muted mt-2">{{ error }}</p>
  </div>
</template>

<script>
export default {
  name: "QuestionEditor",
  data() {
    return {
      question_body: null,
      error: null
    }
  },
  methods: {
    onSubmit() {
      if (!this.question_body){
        this.error = "You can't send empty question!";
      } else if (this.question_body.length > 240) {
        this.error = "Ensure this field has no more 240 characters!";
      } else {
        let endpoint = "/api/questions/";
        let method = "POST"

      }
    }
  },
  created() {
    document.title = "Editor - QuestionTime"
  }
}
</script>

<style>

</style>