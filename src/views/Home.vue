<template>
  <div class="home">
    <PeopleList :people="people" />
    <!-- <PeopleList v-bind="{ people }" /> -->
  </div>
</template>

<script>
// @ is an alias to /src
import PeopleList from "@/components/PeopleList.vue";

const samplePeople = [
  {
    name: "Tracey Holinka",
    email: "hello@email.com"
  },
  {
    name: "Brad Balfour", // I totally know how to spell Brad's last name without looking it up
    email: "hello@anotheremail.com"
  },
  {
    name: "Bryan Strong",
    email: "hi@something.com"
  }
];

export default {
  name: "Home",
  components: {
    PeopleList
  },
  data() {
    return { people: samplePeople };
  }
};
</script>
