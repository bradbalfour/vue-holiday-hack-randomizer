<script>
import shuffle from "lodash/shuffle";
// @ is an alias to /src
import PeopleList from "@/components/PeopleList.vue";

const samplePeople = [
  {
    name: "1 - Tracey Holinka",
    email: "hello@email.com"
  },
  {
    name: "2 - Brad Balfour", // I totally know how to spell Brad's last name without looking it up
    email: "hello@anotheremail.com"
  },
  {
    name: "3 - Bryan Strong",
    email: "hi@something.com"
  },
  {
    name: "4 - Tracey Holinka",
    email: "hello1@email.com"
  },
  {
    name: "5 - Brad Balfour", // I totally know how to spell Brad's last name without looking it up
    email: "hello2@anotheremail.com"
  },
  {
    name: "6 - Bryan Strong",
    email: "hi3@something.com"
  },
  {
    name: "7 - Tracey Holinka",
    email: "hello4@email.com"
  },
  {
    name: "8 - Brad Balfour", // I totally know how to spell Brad's last name without looking it up
    email: "hello5@anotheremail.com"
  },
  {
    name: "9 - Bryan Strong",
    email: "hi6@something.com"
  }
];

export default {
  name: "Home",
  components: {
    PeopleList
  },
  data() {
    return {
      people: samplePeople,
      highlightWinner: false
    };
  },
  methods: {
    randomize() {
      // tracking the interval when running
      // need to track so we can clear it later
      let shuffleInterval;

      const numberOfShuffles = 4;
      let currentShuffle = 0;

      const shuffleCallback = () => {
        if (currentShuffle < numberOfShuffles) {
          this.people = shuffle(this.people);
          currentShuffle++;
        } else {
          clearInterval(shuffleInterval);
          this.highlightWinner = true;
        }
      };

      const startInterval = () => {
        this.people = shuffle(this.people);
        shuffleInterval = setInterval(shuffleCallback, 1000);
      };

      startInterval();
    }
  }
};
</script>

<template>
  <div class="home">
    <PeopleList :people="people" :highlightWinner="highlightWinner" />
    <button @click="randomize">Randomize! 🤪</button>
    <!-- <PeopleList v-bind="{ people }" /> -->
  </div>
</template>
