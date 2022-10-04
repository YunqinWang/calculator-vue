<script>
  export default {
    data() {
      return {
        value: 33.333333333,
        max: 50
      }
    }
  }
</script>
<template>
  <div class="col-10">
    <b-container class="text-center">
      <b-row class="mb-2 fs-4" >
        <b-col md="4" class="fw-bold">Movie Scene</b-col>
        <b-col md="8" class="fw-bold">Scene Status</b-col>
      </b-row>

      <b-row class="mb-2 fs-6 d-flex align-items-center">
        <b-col md="4">Standoff</b-col>
        <b-col md="8"><b-progress variant="primary" :value="80" show-value/></b-col>
      </b-row>

      <b-row class="mb-2 fs-6 d-flex align-items-center">
        <b-col md="4">Bank Robbery</b-col>
        <b-col md="8"><b-progress variant="success" :value="100" show-value/></b-col>
      </b-row>

      <b-row class="mb-2 fs-6 d-flex align-items-center">
        <b-col md="4">Car Chase</b-col>
        <b-col md="8"><b-progress variant="warning" :value="25" show-value/></b-col>
      </b-row>

      <b-row class="mb-2 fs-6 d-flex align-items-center">
        <b-col md="4">Jail</b-col>
        <b-col md="8"><b-progress variant="danger" :value="50" show-value/></b-col>
      </b-row>
    </b-container>
  </div>
</template>
