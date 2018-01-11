<template>
  <div>
    <div>
      Name: <input type="text" v-model="nameCustomer" placeholder="Type">

    </div>
    <table align="center">
      <tr>
        <th>Name</th>
      </tr>
      <tr v-for="d in data" :key="d.id">
        {{d.name}}
      </tr>
    </table>
  </div>
</template>
<script>
  import axios from 'axios'
  export default {
    name: 'customer-list',
    data () {
      return {
        nameCustomer: '',
        addressCust: '',
        data: null
      }
    },
    methods: {
      getUsers () {
        const URL = '/api/customers'
        axios.get(URL)
          .then(response => {
            this.data = response.data
            alert(JSON.stringify(this.data))
          })
          .catch(error => {
            alert(error)
          })
      }
    },
    mounted () {
      this.getUsers()
    }
  }
</script>
<style>
</style>
