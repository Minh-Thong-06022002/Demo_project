<template>
  <base-dialog v-if="inputIsvalid" title="Invalid Input" @close="confirmError">
    <template #default>
      <p>Unfortunetely, at least one input value is invalid</p>
      <p>Please check all input and make sure you enter at least a few characters into each input field.</p>
    </template>
    <template #actions>
      <base-button @click="confirmError">Okay</base-button>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <labe for="title">Title</labe>
        <input type="text" id="title" name="title" ref="titleInput"/>
      </div>
      <div class="form-control">
        <labe for="description">Description</labe>
        <textarea id="description" name="description" rows="3" ref="desInput"/>
      </div>
      <div class="form-control">
        <labe for="link">Link</labe>
        <input id="link" name="link" type="url" ref="urlInput"/>
      </div>
      <div class="form-control">
        <base-button type="submit">Add Resource</base-button>
      </div>
    </form>
  </base-card>
</template>
<script>
export default{
    inject: ['addResource'],
    data() {
      return {
        inputIsvalid: false,
      }
    },
    methods: {
        submitData() {
            const enteredTitle = this.$refs.titleInput.value;
            const enteredDes = this.$refs.desInput.value;
            const enteredLink = this.$refs.urlInput.value;
            if(enteredTitle.trim() === '' || enteredDes.trim() === '' || enteredLink.trim() === '') {
              this.inputIsvalid = true;
              return;
            }
            this.addResource(enteredTitle, enteredDes, enteredLink);
        },
        confirmError() {
          this.inputIsvalid = false;
        }
    },
}

</script>
<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
