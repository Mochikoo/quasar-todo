<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
       

        <q-toolbar-title>
         Mochikoo Form Validation..
        </q-toolbar-title>

        <div>Mochikoo{{ $q.version }}</div>
      </q-toolbar>
    </q-header>
    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>



  <div class="q-pa-md" style="max-width: 500px">

    <q-form @submit="onSubmit"
            @reset="onReset"
            class="q-gutter-md">
      <q-input filled
               v-model="name"
               label="Your name "
             
               lazy-rules
               :rules="[ val => val && val.length > 0 || 'Please type something']" />

      <q-input filled
               type="number"
               v-model="age"
               label="Your age "
               lazy-rules
               :rules="[
               val=>
        val !== null && val !== '' || 'Please type your age',
        val => val > 100 && val < 500 || 'Please type a real age'
        ]"
        />

        

        <div>
          <q-btn label="Submit" type="submit" color="primary" />
          <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" />
        </div>
    </q-form>

  </div>
</template>

<script>
  import { useQuasar } from 'quasar'
  import { ref } from 'vue'
  export default {
    setup() {
      const $q = useQuasar()
      const name = ref(null)
      const age = ref(null)
      const accept = ref(false)
      return {
        name,
        age,
        accept,
        onSubmit() {
          if (accept.value !== true) {
            $q.notify({
              color: 'black-2',
              textColor: 'red',
              icon: 'warning',
              message: 'You need to accept the license and terms first'
            })
          }
          else {
            $q.notify({
              color: 'green-4',
              textColor: 'black',
              icon: 'cloud_done',
              message: 'Submitted'
            })
          }
        },
        onReset() {
          name.value = null
          age.value = null
          accept.value = false
        }
      }
    }
  }
</script>
