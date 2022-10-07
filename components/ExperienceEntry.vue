<template>
  <div class="cv-experience-entry">
    <div class="cv-experience-entry-title" v-html="entry.title" />
    <div class="cv-experience-entry-date">
      {{ entry.dates }}
    </div>
    <div v-if="isComplexEntry">
      <ul v-for="activity in entry.activities" :key="activity.title">
        <li>{{ activity.title }}</li>
        <ul>
          <li v-for="innerActivity in activity.activities" :key="innerActivity.title">
            {{ innerActivity }}
          </li>
        </ul>
      </ul>
    </div>
    <div v-else>
      <ul>
        <li v-for="activity in entry.activities" :key="activity.title">
          {{ activity }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>

export default {
  name: 'ExperienceEntry',
  props: {
    entry: {
      type: Object,
      required: true
    }
  },
  computed: {
    isComplexEntry () {
      return typeof this.entry.activities[0] !== 'string'
    }
  }
}

</script>

<style lang="scss">
.cv-experience-entry {
  @include box();

  &-title {
    font-size: 1.5rem;
    font-weight: bold;
    margin: 0;
  }

  &-date {
    font-size: 1rem;
    font-weight: bold;
    margin: 0;
  }

}
</style>
