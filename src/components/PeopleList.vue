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
    <transition-group name="flip-list" tag="ul">
      <li v-for="{ name, email } in people" :key="email">
        {{ name }}
      </li>
    </transition-group>
  </div>
</template>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.flip-list-move {
  transition: transform 1s;
}
</style>
