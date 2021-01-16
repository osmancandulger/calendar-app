<template>
  <h1 class="calendar-title">Calendar</h1>
  <div class="title-num">
    <div class="current-date">
      <p>{{ currentMonthName }}</p>
      <p>{{ currentYear }}</p>
    </div>

    <section class="days">
      <p class="days-text" v-for="day in days" :key="day">
        {{ day }}
      </p>
    </section>

    <section class="days-num-section">
      <p class="days-num" v-for="num in startDay()" :key="num"></p>

      <p
        class="days-num"
        v-for="num in daysInMonth(currentYear, currentMonth)"
        :key="num"
      >
        {{ num }}
      </p>
    </section>
    <section class="navigator">
      <button class="nav-button" @click="previous">Previous</button>
      <button class="nav-button" @click="next">Next</button>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentMonth: new Date().getMonth(),

      currentYear: new Date().getFullYear(),
      days: ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"],
    };
  },
  methods: {
    daysInMonth(year, month) {
      return new Date(year, month + 1, 0).getDate();
    },
    startDay() {
      return new Date(this.currentYear, this.currentMonth, 1).getDay();
    },
    next() {
      this.currentMonth++;
    },
    previous() {
      this.currentMonth--;
    },
  },
  computed: {
    currentMonthName() {
      return new Date(this.currentYear, this.currentMonth).toLocaleString(
        "default",
        {
          month: "long",
        }
      );
    },
  },
};
</script>

<style lang="scss"></style>
