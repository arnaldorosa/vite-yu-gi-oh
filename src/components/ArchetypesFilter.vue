<template>
    <select
      name="archetype"
      id="archetype"
      v-model="state.selectedArchetype"
      @change="$emit('filter')"
    >
      <option value="">All</option>
      <option
        :value="archetype.archetype_name"
        v-for="archetype in state.archetypes"
      >
        {{ archetype.archetype_name }}
      </option>
    </select>
  </template>
  <script>
  import { state } from "./store.js";
  export default {
    name: "ArchetypesFilter",
    emits: ["filter"],
    data() {
      return {
        state,
      };
    },
    created() {
      this.state.getArchetypesList(
        "https://db.ygoprodeck.com/api/v7/archetypes.php"
      );
    },
  };
  </script>
  
  <style scoped></style>