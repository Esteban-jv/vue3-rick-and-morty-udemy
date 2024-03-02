<template>
  <div class="search">
    <input
        type="text"
        placeholder="Search by name"
        v-model="name"
        @keyup="filter()"
    >
  </div>
</template>

<script>
import { ref } from "vue";
import { useStore } from "vuex";
export default {
  name: "FilterByName",
  setup () {
    const store = useStore()
    const name = ref()

    const filter = () => {
      store.dispatch('filterByName', name.value)
    }
//a comment
    return {
      name,
      filter
    }
  }
}
</script>

<style scoped>
  .search {
    width: 400px;
    margin: 3rem auto 0;
    input {
      height: 53px;
      width: 400px;
      border: none;
      border-radius: 10px;
      padding: 0 0.5rem;
    }
  }
</style>