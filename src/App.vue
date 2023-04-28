<template>
  <div class="paragraphs">
    <h1>Jesus (Yeshua משיח — Messiah) Saves!</h1>
    <p>Have you given your life to Jesus?</p>
    <p>&nbsp;</p>
    <p>Jesus Christ loves you so much that He died for you (and for me)
      on the cross for our sins and rose again on the third day and
      reigns at the right hand of God the Father forever more!</p>
    <p>&nbsp;</p>
    <p><sup>9</sup>That if you confess with your mouth, “Jesus is Lord,” and
      believe in your heart that God raised him from the dead, you will be saved.
      <br>
      <sup>10</sup>For it is with your heart that you believe and are justified,
      and it is with your mouth that you confess and are saved.
      <br>
      <sup>11</sup>As the Scripture says, “Anyone who trusts in him will never be put to shame.”
      — <a href="https://goodnewsuk.com/bible-helps/romans-109-11">Romans 10:9-11</a>
    </p>

    <p>&nbsp;</p>
    <p>It is now {{ currentTime.toLocaleTimeString() }} on {{ currentTime.toLocaleDateString() }} (local time).</p>
    <p>&nbsp;</p>
    <p>The first fruits rapture is at: {{ firstFruitsRapture.toLocaleTimeString() }} on {{
      firstFruitsRapture.toLocaleDateString() }} (local time)
      which {{ timeDiffToNow(firstFruitsRapture) }}</p>
    <p>&nbsp;</p>
    <p>The main harvest rapture is at: {{ mainHarvestRapture.toLocaleTimeString() }} on {{
      mainHarvestRapture.toLocaleDateString() }} (local time)
      which {{ timeDiffToNow(mainHarvestRapture) }}</p>
    <p>&nbsp;</p>
    <p>The second coming of Jesus is at: {{ secondComing.toLocaleTimeString() }} on {{
      secondComing.toLocaleDateString() }} (local time).
      which {{ timeDiffToNow(secondComing) }}</p>

    <p>&nbsp;</p>
    <h1 v-if="beforeFirstFruits">It's not too late! Pray to Jesus now!</h1>
    <h1 v-if="greatTribulation">Please do not be deceived by the lawless one and
      do not take his mark upon you. Pray to Jesus now!</h1>
    <h1 v-if="wrathOfGod">Be prepared for the coming of the King of kings and Lord of lords for His millennium reign!</h1>
    <h1 v-if="millenniumReign">Hallelujah! Jesus Christ reigns forever more!</h1>

    <p>&nbsp;</p>
    <p><sup>10</sup>that at the name of Jesus every knee should bow, of those in
      heaven, and of those on earth, and of those under the earth,
      <br>
      <sup>11</sup>and that every tongue should confess that Jesus Christ is Lord,
      to the glory of God the Father.
      — <a href="https://www.biblegateway.com/passage/?search=Philippians%202%3A10-11&version=NKJV">Philippians
        2:10-11</a>
    </p>

    <p>&nbsp;</p>
    <p>For more information, please visit: <a href="https://rapturepuzzle.com">rapturepuzzle.com</a></p>
  </div>
</template>

<script setup>
import { computed, onBeforeUnmount, onMounted, ref } from 'vue'

const firstFruitsRapture = new Date('May 28, 2023 15:00:00+3')  // "9th hour" = 3pm
const mainHarvestRapture = new Date('October 14, 2023 15:00:00+3')
const secondComing = new Date('December 22, 2023 15:00:00+3')

const currentTime = ref(new Date())
const updateCurrentTime = () => currentTime.value = new Date()
const beforeFirstFruits = computed(() => currentTime.value < firstFruitsRapture)
const greatTribulation = computed(() => currentTime.value >= firstFruitsRapture && currentTime.value < mainHarvestRapture)
const wrathOfGod = computed(() => currentTime.value >= mainHarvestRapture && currentTime.value < secondComing)
const millenniumReign = computed(() => currentTime.value >= secondComing)

const timeDiffToNow = (until) => {
  const delta = Math.round(Math.abs(until - currentTime.value) / 1000)
  const days = Math.floor(delta / (3600 * 24))
  const hours = Math.floor((delta - (3600 * 24 * days)) / 3600)
  const minutes = Math.floor((delta - (3600 * 24 * days) - (3600 * hours)) / 60)
  const seconds = Math.floor(delta - (3600 * 24 * days) - (3600 * hours) - (60 * minutes))
  const diff = `${days} days, ${hours} hours, ${minutes} minutes, ${seconds} seconds`
  if (currentTime.value < until) {
    return `is ${diff} from now.`
  }
  return `was ${diff} ago.`
}

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
