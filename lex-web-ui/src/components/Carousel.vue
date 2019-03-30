<template>
    <div class="slides">
        <div v-bind:style="{width: innerWidth + 'px'}" class="slides-inner" style="display:-webkit-inline-box">  
            <div v-for="card in cardData" v-bind:key="card">
                <div class="card" v-on:click="cardClicked">
                    <img v-bind:src="card.image" alt="">
                    <div class="text">
                        <h3>{{ card.name }}</h3>
                        <p>{{ card.location }}</p>
                        <a v-bind:href="'tel:' + card.href">{{card.href}}</a>
                        <p><b>Meal time:</b> {{card.time}}</p>
                        <p><b>Who it serves:</b> {{card.serves}}</p>
                    </div>
                    <button class="directions" v-on:click="goToDirections">
                        <p class="button"><b>See directions</b></p>
                    </button>
                </div>
            </div>
        </div>
        <!-- <div class="navigation">
            <span v-on:click="goToPrev">Prev</span>
            <span class="nav-number" v-for="slide in slides" v-bind:key="slide"> {{slides.length}}</span>
            <span v-on:click="goToNext">Next</span>
        </div> -->
    </div>
</template>

<script>

export default {
  data() {
    return {
      cardData: [
        {
          name: 'Sistering - Drop-In Centre',
          location: '962 Bloor St W, Toronto',
          href: '123-456-7899',
          time: '9:30-12:30am',
          serves: 'Everyone',
          image: 'static/img/flowers.jpeg',
        },
      ],
      innerWidth: 0,
      singleWidth: 0,
    };
  },
  computed: {
    freeMeal() {
      return this.$store.state.lex.message;
    },
  },
  methods: {
    goToPrev() {
      console.log('prev');
    },
    goToNext() {
      console.log('next');
    },
    cardClicked() {
      console.log('card clicked');
    },
    goToDirections() {
      console.log('directions');
    },
  },
};
</script>

<style scoped>

img {
    max-width: 100%;
    display: block;
    border-radius: 9px 9px 0 0;
}

.card {
    position: relative;
    margin-bottom: 10px;
    margin-top: 15px;
    box-shadow: 4px 4px 6px grey;
    display: inline-block;
    border-radius: 10px;
    background-color: white;
    width: 295px;
    margin-left: 10px;
}

.card:hover {
    box-shadow: 4px 4px 16px 0 grey;
    cursor: pointer;
}

p {
    margin-bottom: 0px;
}

.text {
    padding: 4px 7px;
    color: black;
}

.button {
    color: red;
}

.directions {
    border-top: 1px solid gray;
    padding: 10px;
    text-align: center;
    width: 100%;
}

.directions:active {
  background-color: #f2f2f2;
  border-radius: 0 0 10px 10px;
}

button:focus {
    outline: 0;
}

</style>