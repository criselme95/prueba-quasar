<template>
  <div class="q-pa-md" style="max-width: 400px">

    <q-form
      @submit="onSubmit"
      @reset="onReset"
     
      class="q-gutter-md"
    >
      <q-input
        filled
        v-model="name"
        label="ingresar un nombre *"
        hint="Name"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'por favor ingrese un nombre']"
      />
      <q-input
        filled
        v-model="apellido"
        label="ingresar un apellido *"
        hint="Apellido"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'por favor ingrese un apellido']"
      />

      <q-input
        filled
        type="number"
        v-model="Telefono"
        label="celular *"
        lazy-rules
        :rules="[
          val => val !== null && val !== '' || 'por favor ingrese un numero de telefono',
          
        ]"
      />
      <q-input
        filled
        type="number"
        v-model="cc"
        label="cc *"
        lazy-rules
        :rules="[
          val => val !== null && val !== '' || 'por favor ingrese numero de cedula',
      
        ]"
      />

      <q-toggle v-model="accept" label="acepta los terminos y condiciones" />

      <div>
        <q-btn label="Guardar" type="submit" color="primary"/>
        <q-btn label="Borrar" type="reset" color="primary" flat class="q-ml-sm" />
      </div>
    </q-form>

  </div>
</template>

<script>
import { useQuasar } from 'quasar'
import { ref } from 'vue'

export default {
  setup () {
    const $q = useQuasar()

    const name = ref(null)
    const apellido = ref(null)
    const Telefono = ref(null)
    const cc = ref(null)
    const accept = ref(false)

    return {
      name,
      apellido,
      Telefono,
      cc,
      accept,

      onSubmit () {
        if (accept.value !== true) {
          $q.notify({
            color: 'red-5',
            textColor: 'white',
            icon: 'warning',
            message: 'You need to accept the license and terms first'
          })
          
        }
        else {
          $q.notify({
            color: 'green-4',
            textColor: 'white',
            icon: 'cloud_done',
            message: 'Submitted'
          })
        }
      },
      onReset () {
        name.value = null
        apellido.value = null
        Telefono.value = null
        cc.value = null
        accept.value = false
      }

     
    }
  }
}
</script>
