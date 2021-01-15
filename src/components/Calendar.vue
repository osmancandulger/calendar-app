<template>
  <h1 class="calendar-title">Calendar</h1>
  <div class="title-num">
    <div class="current-date">
    <p>{{ currentMonth }}</p>
        <p>{{ currentYear }}</p>
        </div>

    <section class="days">
      <p class="days-text" v-for="day in days" :key="day">
        {{ day }}
      </p>
    </section>

    <section class="days-num-section">
      <p class="days-num" v-for="num in 30" :key="num">
        {{ num }}
      </p>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentMonth: new Date().toLocaleString("default", {
        month: "long",
      }),
      currentYear: new Date().getFullYear(),
      days: ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"],
    };
  },
};
</script>

<style lang="scss"></style>
