<template>  
  <div class="game-area">
    <h1 class="title">Kedi <span>Nerede</span>?</h1>
    <h4 class="description">
      Açık kartlardan birini seçtikten sonra kapalı olan karta tıklayınız.
    </h4>
    <div class="container">
      <transition-group name="rotate-all" appear class="card-container">
        <app-card
          :key="card.id"
          :class="{ shadow: selectedCard == card.id }"
          @click.native="selectedCard = card.id"
          v-for="card in cards"
          :card="card"
        >
        </app-card>
      </transition-group>
    </div>
    <div class="container">
      <transition name="rotate" mode="out-in">
        <component
          @click.native="showCard(answer)"
          :card="answer"
          :is="activeCard"
        >
        </component>
      </transition>
    </div>
  </div>
</template>
<script>
import Card from "./Card";
import DefaultCard from "./DefaultCard";
export default {
  components: {
    appCard: Card,
    appDefaultCard: DefaultCard,
  },
  data() {
    return {
      selectedCard: null,
      answer: {},
      activeCard: "app-default-card",
      cards: [
        { id: 1, component: "app-card", image: "/src/assets/card-1.jpg" },
        { id: 2, component: "app-card", image: "/src/assets/card-2.jpg" },
        { id: 3, component: "app-card", image: "/src/assets/card-3.jpg" },
        { id: 4, component: "app-card", image: "/src/assets/card-4.jpg" },
        { id: 5, component: "app-card", image: "/src/assets/card-5.jpg" },
      ],
    };
  },
  created() {
    let answer = Math.ceil(Math.random() * this.cards.length);
    this.answer = this.cards[answer - 1]; // Cevap kartın algoritması
  },
  methods: {
    showCard(answer) {
      if(this.selectedCard == null){
        alert("İlk Olarak Bir Kart Seçiniz!");
      }else{
        this.activeCard = answer.component;
        setTimeout(() => {
          if(answer.id == this.selectedCard){
            this.$emit("activeComponentEvent", "app-celebrate");
          }else{
            this.$emit("activeComponentEvent", "app-failure");
          }
        }, 1000);        
      }
    },
  },
};
</script>
<style scoped>
.title {
  text-align: center;
  font-family: sans-serif;
  color: rosybrown;
}
.title span {
  color: mediumpurple;
}
.description {
  color: gray;
  text-align: center;
}
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 15px;
  margin-top: 35px;
}
.card-container {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 15px;
}
.shadow {
  box-shadow: 0px 5px 48px #30969f !important;
  transition: box-shadow 0.5s;
}
.rotate-all-enter-active {
  animation: rotate-all ease-in-out 2s forwards;
}
@keyframes rotate-all {
  from {
    transform: rotateY(0);
  }
  to {
    transform: rotateY(1080deg);
  }
}
.rotate-enter-active {
  animation: rotate-in .5s ease-in-out forwards;
}
.rotate-leave-active {
  animation: rotate-out .5s ease-in-out forwards;
}
@keyframes rotate-in {
  from {
    transform: rotateY(90deg);
  }
  to {
    transform: rotateY(0deg);
  }
}
@keyframes rotate-out {
  from {
    transform: rotateY(0deg);
  }
  to {
    transform: rotateY(90deg);
  }
}
</style>
