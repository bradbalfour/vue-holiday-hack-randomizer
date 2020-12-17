<script>
import shuffle from "lodash/shuffle";
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
  },
  {
    name: "Tracey Holinka",
    email: "hello1@email.com"
  },
  {
    name: "Brad Balfour", // I totally know how to spell Brad's last name without looking it up
    email: "hello2@anotheremail.com"
  },
  {
    name: "Bryan Strong",
    email: "hi3@something.com"
  },
  {
    name: "Tracey Holinka",
    email: "hello4@email.com"
  },
  {
    name: "Brad Balfour", // I totally know how to spell Brad's last name without looking it up
    email: "hello5@anotheremail.com"
  },
  {
    name: "Bryan Strong",
    email: "hi6@something.com"
  }
];

export default {
  name: "Home",
  components: {
    PeopleList
  },
  data() {
    return { people: samplePeople };
  },
  methods: {
    randomize() {
      console.log("randomize it!");
      // tracking the interval when running
      // need to track so we can clear it later
      let shuffleInterval;

      const numberOfShuffles = 4;
      let currentShuffle = 0;

      const shuffleCallback = () => {
        console.log("shuffling", currentShuffle);
        if (currentShuffle < numberOfShuffles) {
          this.people = shuffle(this.people);
          currentShuffle++;
        } else {
          clearInterval(shuffleInterval);
        }
      };

      const startInterval = () => {
        shuffleInterval = setInterval(shuffleCallback, 1000);
      };

      startInterval();
    }
  }
};
</script>

<template>
  <div class="home">
    <PeopleList :people="people" />
    <button @click="randomize">Randomize! 🤪</button>
    <!-- <PeopleList v-bind="{ people }" /> -->
  </div>
</template>
