<template>
    

<div>

<h1>Customer List</h1><br>
  <b-table striped hover
  :items="Customers"
  :fields="fields"
  :per-page="pageSize"
  :current-page="pageIndex"></b-table>
   <b-pagination  align="center"  size="lg" :total-rows="Customers.lenght" v-model="pageIndex" :per-page="pageSize">
    </b-pagination>

</div>



</template>
<script>
import axios from 'axios'
export default {
  name: 'customers',
    data(){
return{
    
  fields: [
        {
          key: 'postal_code',
          sortable: true,
         variant: 'warning'
        },
        {
          key: 'address',
          sortable: false,
         variant: 'primary'
        },
        {
          key: 'phone',
          
          sortable: true,
          variant: 'danger'
        }
           ],
message : "final",
Customers : [],
pageSize:10,
pageIndex: 1

}

  },


  mounted(){

var instance = this

axios
.get('https://final-examtip.herokuapp.com/api/customers')
.then(function(response){
console.log(response.data)
instance.Customers = response.data.data



})



  }
}
</script>
