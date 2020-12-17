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
    },
    highlightWinner: {
      type: Boolean,
      default: false
    }
  }
};
</script>

<template>
  <div class="people-list">
    <transition-group name="flip-list" tag="ul">
      <li
        v-for="({ name, email }, index) in people"
        :key="email"
        :class="{ 'highlighted-winner': highlightWinner && index === 0 }"
      >
        {{ name }}
      </li>
    </transition-group>
  </div>
</template>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.people-list li {
  list-style: none;
  transition: all 1s;
}
.highlighted-winner {
  font-size: 40px;
}
.flip-list-move {
  transition: transform 1s;
}
</style>
