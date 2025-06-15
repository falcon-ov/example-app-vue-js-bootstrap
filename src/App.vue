<template>
  <h1>{{ info }}</h1>
  <p>{{ someInfo }}</p>

  <button type="button" @click="userData('Some new')">Отправить</button>
</template>

<script>
export default {
  data() {
    return {
      info: "title!",
      someInfo: "Description"
    }
  },
  methods: {
    userData(word = "new text") {
      this.someInfo = word;
    }
  }
}
</script>

<style scoped></style>
