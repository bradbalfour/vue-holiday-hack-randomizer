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
      contestants: samplePeople,
      winners: [],
      highlightWinner: false
    };
  },
  methods: {
    randomize() {
      // tracking the interval when running
      // need to track so we can clear it later
      let shuffleInterval;

      // TODO - allow this to vary between 2 & 5
      const numberOfShuffles = 2;

      let currentShuffle = 0;

      const shuffleCallback = () => {
        if (currentShuffle < numberOfShuffles) {
          this.contestants = shuffle(this.contestants);
          currentShuffle++;
        } else {
          clearInterval(shuffleInterval);
          this.highlightWinner = true;
          setTimeout(() => {
            this.highlightWinner = false;
            this.moveWinner();
          }, 3000);
        }
      };

      const startInterval = () => {
        this.contestants = shuffle(this.contestants);
        shuffleInterval = setInterval(shuffleCallback, 1000);
      };

      startInterval();
    },
    moveWinner() {
      this.winners.push(this.contestants.shift());
    }
  }
};
</script>

<template>
  <div class="home">
    <h2>Contestants</h2>
    <PeopleList :people="contestants" :highlightWinner="highlightWinner" />
    <button @click="randomize">Randomize! 🤪</button>
    <h2>Winners</h2>
    <PeopleList :people="winners" />
    <!-- <PeopleList v-bind="{ people }" /> -->
  </div>
</template>
