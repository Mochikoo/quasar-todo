<template>
  <q-pages>
    <div class="q-pa-nd">
      <div style="max-width: 300px">
        <q-form @submit="submitForm">
          <div>
            <g-input label="Your Name" v-model="formData.textInput" />
          </div>
          <div class="q-pt-md">
            <q-btn type="submit" label="Submit" />
          </div>
        </q-form>
      </div>
      
    </div>
  </q-pages>
</template>

<script>
  import { defineComponent } from 'vue';

  export default defineComponent(option {
    name: 'PageIndex',
    data() {
      return {
        textinput: null
      }
    }
  },
    methods: {
      submitForm() {
        alert('Your name is: ' + this.formData.textInput);
      }
  })
</script>
