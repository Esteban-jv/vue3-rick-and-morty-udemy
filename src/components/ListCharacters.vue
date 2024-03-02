<template>
  <section>
    <div class="characters">
      <div class="characters__item" v-for="character in characters" :key="character.id">
        <CardCharacter :character="character" />
      </div>
    </div>
  </section>
</template>

<script>
import { useStore } from 'vuex'
import { onMounted, computed } from "vue";
import CardCharacter from "@/components/CardCharacter";
export default {
  name: "ListCharacters",
  components: {
    CardCharacter
  },
  setup() {
    const store = useStore();
    const characters = computed(() => {
      return store.state.charactersFilters
    })
    onMounted(() => {
      store.dispatch('getCharacters')
    })

    return {
      characters
    }
  }
}
</script>

<style>
  .characters {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 3rem;
    margin: 3rem;
  }

</style>