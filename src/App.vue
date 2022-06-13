<template>
  <v-app>
    <v-card>
    <v-container fluid>
      <v-row
        align="center"
      >
        <v-col cols="12">
          <v-autocomplete
            v-model="values"
            :items="items"
            outlined
            dense

            label="Search"
          ></v-autocomplete>
        </v-col>

      </v-row>
    </v-container>
  </v-card>
  </v-app>
</template>

<script>
export default {
  name: 'App',
  issues:[],
  data: () => ({
          items: ["asd","asdw"],
      values: ['foo', 'bar'],
      value: null,
  }),
    created() {
    this.getIssues();
  },
  methods: {
    filterIssues() {
      console.log(this.issues);
    },
    getIssues() {
     return fetch('https://api.github.com/repos/facebook/react/issues')
        .then((resp) => resp.json())
        .then(async (json_data) => (this.items = json_data.map((issue)=>{return issue.title})));
    },
  },
};
</script>
