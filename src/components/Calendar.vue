<template>
  <link
    href="https://fonts.googleapis.com/css2?family=Roboto:wght@100;300;400;800&display=swap"
    rel="stylesheet"
  />
  <h1 class="calendar-title">Calendar</h1>
  <div class="title-num">
    <div class="current-date">
      <p class="current-month">{{ currentMonthName }}</p>
      <p class="current-year"> {{ currentYear }}</p>
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
        v-for="num in daysInMonth()"
        :key="num"
        :class="currentDateClass(num)"
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
      currentDate: new Date().getUTCDate(),
      currentMonth: new Date().getMonth(),
      currentYear: new Date().getFullYear(),
      days: ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"],
    };
  },
  methods: {
    daysInMonth() {
      return new Date(this.currentYear, this.currentMonth + 1, 0).getDate();
    },
    startDay() {
      return new Date(this.currentYear, this.currentMonth, 1).getDay();
    },
    next() {
      if (this.currentMonth === 11) {
        this.currentMonth = 0;
        this.currentYear++;
      } else {
        this.currentMonth++;
      }
    },
    previous() {
      if (this.currentMonth === 0) {
        this.currentMonth = 11;
        this.currentYear--;
      } else {
        this.currentMonth--;
      }
    },
    currentDateClass(num) {
      const calenderhDate = new Date(
        this.currentYear,
        this.currentMonth,
        num
      ).toDateString();
      const currentFullDate = new Date().toDateString();
      return calenderhDate === currentFullDate ? "current-day" : "";
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
