<template>
  <div>
    <div v-for="record in records" :key="record.id">
      <b-container class="bv-example-row py-4 py-md-6">
        <b-row>
          <b-col v-if="record.Order % 2 == 1" lg="6" sm="12" class="col align-self-center">
            <h3 class="val1 text-left">{{record.Value1}}</h3>
            <p class="val2">{{record.Value2}}</p>
          </b-col>
          <b-col lg="6" sm="12">
            <div class="img-container">
              <img loading="lazy" v-bind:src="record.Help[0].url" />
            </div>
          </b-col>
          <b-col v-if="record.Order % 2 == 0" lg="6" sm="12" class="col align-self-center">
            <h3 class="val1 text-left">{{record.Value1}}</h3>
            <p class="val2">{{record.Value2}}</p>
          </b-col>
        </b-row>
      </b-container>

      <br />
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "VueAirTable",
  props: ["base", "baseId"],
  data: function() {
    return {
      apiUrl: "https://api.airtable.com/v0/",
      apiKey: "key4FVrOBZr6jJZ5z", // Read-Only Profile
      records: []
    };
  },
  mounted: function() {
    if (!this.base || !this.baseId) {
      alert(
        "Please specify `base` and `baseId` attributes for <vue-airtable> component."
      );
    }
    this.getData();
  },
  methods: {
    // Getting data from API
    getData() {
      axios
        .get(this.apiUrl + this.baseId + "/" + this.base, {
          headers: { Authorization: "Bearer " + this.apiKey }
        })
        .then(response => {
          for (let key in response.data.records) {
            if (response.data.records[key].fields.Help != null) {
              // Adding data to records Array
              this.records.push(response.data.records[key].fields);
            }
          }
        })
        .catch(e => console.log(e));
    }
  }
};
</script>


<style>
.img-container {
  padding: 2rem;
}

.img-container img {
  border-radius: 12px;
  box-shadow: 0 2px 48px 0 rgba(176, 192, 237, 0.42);
}

img {
  max-width: 100%;
  height: auto;
  vertical-align: middle;
  border-style: none;
}

.val1 {
  font-size: 2.1rem;
  font-weight: 800;
  font-family: Montserrat, sans-serif;
  letter-spacing: 0;
  color: #323d47;
}

.col {
  flex-wrap: wrap !important;
  margin-right: -15px;
  margin-left: -15px;
}

.val2 {
  margin-top: 0;
  margin-bottom: 1rem;
  font-weight: 300;
  font-size: 1.2rem;
  display: block;
  margin-block-start: 1em;
  margin-block-end: 1em;
  margin-inline-start: 0px;
  margin-inline-end: 0px;
  text-align: left !important;
  font-family: OpenSans, sans-serif;
  line-height: 1.9;
}
</style>