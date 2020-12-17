<script>
export default {
  name: "PeopleList",
  props: {
    /**
     * { name: string, email: string }
     */
    people: {
      type: Array,
      default: () => []
    }
  }
};
</script>

<template>
  <div class="names-list">
    <ul>
      <li v-for="{ name, email } in people" :key="email">
        {{ name }}
      </li>
    </ul>
  </div>
</template>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
