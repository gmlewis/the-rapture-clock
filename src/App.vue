<template>
  <div class="paragraphs">
    <h1>Jesus (Yeshua משיח — Messiah) Saves!</h1>
    <p>Have you given your life to Jesus?</p>
    <p>&nbsp;</p>
    <p>Jesus Christ loves you so much that He died for you (and for me)
      on the cross for our sins and rose again on the third day and
      reigns at the right hand of the Father forever more!</p>
    <p>&nbsp;</p>
    <p><sup>9</sup>That if you confess with your mouth, “Jesus is Lord,” and
      believe in your heart that God raised him from the dead, you will be saved.
      <br>
      <sup>10</sup>For it is with your heart that you believe and are justified,
      and it is with your mouth that you confess and are saved.
      <br>
      <sup>11</sup>As the Scripture says, “Anyone who trusts in him will never be put to shame.”
      <br>
      — <a href="https://goodnewsuk.com/bible-helps/romans-109-11">Romans 10:9-11</a>
    </p>

    <p>&nbsp;</p>
    <p>It is now {{ currentTime.toLocaleTimeString() }} on {{ currentTime.toLocaleDateString() }} (local time).</p>
  </div>
</template>

<script setup>
import { onBeforeUnmount, onMounted, ref } from 'vue'

const currentTime = ref(new Date())
const updateCurrentTime = () => currentTime.value = new Date()

let updateTimeInterval = null
onMounted(() => {
  updateTimeInterval = setInterval(updateCurrentTime, 1000)
})
onBeforeUnmount(() => {
  clearInterval(updateTimeInterval)
})
</script>

<style lang="scss" scoped>
.paragraphs {
  display: flex;
  flex-direction: column;
  justify-items: center;
  align-items: center;

  &>p {
    max-width: 45rem;
  }
}
</style>
