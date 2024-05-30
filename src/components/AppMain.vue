<template>
    <main>
      <ArchetypesFilter @filter="filterResults"></ArchetypesFilter>
      <div>
        {{ state.cards.length }}
      </div>
  
      <CardsList :cards="state.cards"></CardsList>
    </main>
  </template>
  
  <script>
  import { state } from "./store";
  import ArchetypesFilter from "./ArchetypesFilter.vue";
  import CardsList from "./CardsList.vue";
  export default {
    name: "AppMain",
    components: { ArchetypesFilter, CardsList },
    data() {
      return {
        state,
      };
    },
    methods: {
      filterResults() {
        console.log("filter all cards");
        let url;
        console.log(url);
        if (state.selectedArchetype === "") {
          url = state.api_url;
        } else {
          url = `${state.api_url}&archetype=${state.selectedArchetype}`;
        }
        state.fetchData(url);
      },
    },
    mounted() {
      state.fetchData(state.api_url);
    },
  };
  </script>
  
  <style scoped></style>