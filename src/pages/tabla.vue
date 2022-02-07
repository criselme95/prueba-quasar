<template>

  
  <div class="q-pa-md">
    <q-table
      title="Personal"
      :rows="rows"
      :columns="columns"
      row-key="name"
    />
  </div>
 
</template>

<script>
  import axios from 'axios';

const columns = [
  {
    name: 'name',
    required: true,
    label: 'Nombre',
    align: 'left',
    field: row => row.name,
    format: val => `${val}`,
    sortable: true
  },
  { name: 'Apellido', align: 'center', label: 'Apellido', field: 'Apellido', sortable: true },
  { name: 'Correo', label: 'Correo', field: 'Correo', sortable: true },
  { name: 'Telefono', label: 'Telefono', field: 'Telefono' },
]

const rows = [];

export default {
  
  setup () {
    return {
    columns,
     rows,
      
    }

  },
 mounted () {
  //  then.getPost() 
      axios.get('https://jsonplaceholder.typicode.com/users')
      .then(function (response) {
        response.data.forEach(element => {
          rows.push({name: element.name, Apellido: element.username, Correo: element.email, Telefono: element.phone});
        });
      })
      .catch(function(error) {
        console.log(error.message);
      });
  
  },


} 
   
</script>