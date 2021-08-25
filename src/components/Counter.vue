<template>
  <h2> {{ customTitle }} </h2>
  <p> {{ counter }}<sup>2</sup> = {{ squareCounter }} </p>
  <div>
    <button @click="increase">+1</button>
    <button @click="decrease">-1</button>
  </div>
</template>

<script>

export default {
  name: "Counter",
  props: {
    title: {
      type: String,
      default: 'Counter'
    },
    start: {
      type: Number,
      default: 10,
      validator(value) {
        return value > 0;
      }
    }
  },
  data() {
    return {
      counter: this.start
    }
  },
  methods: {
    getSquareValue() {
      return this.counter * this.counter;
    },
    increase() {
      this.counter++;
    },
    decrease() {
      this.counter--;
    }
  },
  computed: {
    squareCounter() {
      return this.counter * this.counter;
    },
    customTitle() {
      return this.title || 'Counter';
    }
  }
}
</script>

<style>
  button {
    background-color: #64bb87;
    border: 1px solid white;
    border-radius: 5px;
    color: white;
    cursor: pointer;
    margin: 0 5px;
    padding: 5px 15px;
    transition: 0.3s ease-in-out;
  }

  button:hover {
    background-color: #5aa67b;
    transition: 0.3s ease-in-out;
  }
</style>
