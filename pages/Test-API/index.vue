<template>
  <div>
    <v-autocomplete
      v-model="value"
      :items="items"
      dense
      filled
      label="Search US States"
    ></v-autocomplete>
    <v-btn @click="searchbtn">Summit</v-btn>
    <br /><br />
    <div>
      <v-card class="mx-auto">
        <v-card-title></v-card-title>
        <v-card-text>active : </v-card-text>
        <v-card-text>cases :</v-card-text>
        <v-card-text>casesPerOneMillion :</v-card-text>
        <v-card-text>deaths :</v-card-text>
        <v-card-text>deathsPerOneMillion :</v-card-text>
        <v-card-text>population :</v-card-text>
        <v-card-text>recovered :</v-card-text>
        <v-card-text>tests :</v-card-text>
        <v-card-text>testsPerOneMillion :</v-card-text>
        <v-card-text>todayDeaths :</v-card-text>
        <v-card-text>todayCases :</v-card-text>
        <v-card-text>testsPerOneMillion :</v-card-text>
        <v-card-text>updated :</v-card-text>
      </v-card>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data: () => ({
    items: ['Texas', 'New York', 'Ohio', 'Florida'],
    value: 'Texas',
    results: []
  }),
  methods: {
    searchbtn() {
      const url = `https://disease.sh/v3/covid-19/states/${this.value}`
      axios.get(url).then((res) => {
        console.log(res.data)
        this.results = res.data.results
      })
    },
  },
}
</script>

<style>
</style>