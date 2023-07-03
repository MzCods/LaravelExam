<template>
  <div class="center">
    <vs-table striped class="report-table">
      <template #thead>
        <vs-tr>
          <vs-th>Event ID</vs-th>
          <vs-th>Nom</vs-th>
          <vs-th>Date</vs-th>
          <vs-th>Type de billet</vs-th>
          <vs-th>Nom du client</vs-th>
          <vs-th>Email</vs-th>
          <vs-th>Nbre de billets</vs-th>
          <vs-th>Coût</vs-th>
        </vs-tr>
      </template>
      <template #tbody>
        <vs-tr :key="i" v-for="(tr, i) in report_data" :data="tr">
          <vs-td>#{{ tr.event_id }}</vs-td>
          <vs-td>{{ tr.e_name }}</vs-td>
          <vs-td>{{ tr.e_date }}</vs-td>
          <vs-td>{{ tr.t_type }}</vs-td>
          <vs-td>{{ tr.c_name }}</vs-td>
          <vs-td>{{ tr.c_email }}</vs-td>
          <vs-td>{{ tr.no_of_tickets }}</vs-td>
          <vs-td>{{ tr.cost }}$</vs-td>
        </vs-tr>
      </template>
    </vs-table>
  </div>
</template>

<script>
import axios from '../vuexios';

export default {
  data() {
    return {
      report_data: [],
    };
  },
  mounted() {
    axios
      .get('/getbookingdetails')
      .then(response => {
        this.report_data = response.data;
      })
      .catch(error => console.log(error.message));
  },
  name: 'BookingReport',
};
</script>

<style scoped>
.report-table {
  height: 500px !important;
  overflow: auto;
}
</style>
