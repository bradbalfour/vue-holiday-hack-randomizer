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
        class="flip-list-item"
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
  font-weight: bold;
  font-size: 40px;
}

/* Transition Handling */
/* https://vuejs.org/v2/guide/transitions.html#List-Transitions */

.flip-list-move {
  transition: all 1s;
}

.flip-list-item {
  transition: all 1s;
}
.flip-list-enter, .flip-list-leave-to
/* .list-complete-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: translateY(30px);
}
</style>
