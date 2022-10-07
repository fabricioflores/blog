<template>
  <div class="cv divide-y-4 divide-green-400 space-y-4">
    <div class="cv__header">
      <div class="cv__header__left">
        <img
          src="https://avatars.githubusercontent.com/u/3495122?v=4"
          class="rounded-full w-36 h-36"
          alt=""
        >
        <h2 class="cv__title">
          Fabricio Flores | Software Developer
        </h2>
      </div>
      <div class="cv__header__right">
        <p>Loja, Ecuador</p>
        <p><a href="mailto:fabrifloresg@gmail.com">fabrifloresg@gmail.com</a></p>
        <p><a href="https://github.com/fabricioflores" target="_blank">github.com/fabricioflores</a></p>
      </div>
    </div>
    <div class="cv__skills">
      <h3 class="cv__skills-left">
        Skills
      </h3>
      <div class="cv__skills-right cv__skills__entry">
        <p>
          Languages: JavaScript, TypeScript, HTML, CSS, SCSS. A bit of Ruby.
        </p>
        <p>
          Frameworks and libraries: Angular, AngularJS, Vue, React, NodeJS, Express, Ruby on Rails.
        </p>
        <p>
          Cloud Technologies: AWS (S3, EC2, LightSail), CircleCI, TravisCI, GitHub Actions, Jenkins.
        </p>
        <p>
          Databases: PostgreSQL, MongoDB, MySQL. A bit of ElasticSearch.
        </p>
        <p>
          Tools: Git, GitHub, NPM, ESLint, Jest. A bit of RSpec.
        </p>
      </div>
    </div>
    <div class="cv__experience">
      <h3 class="cv__experience-left">
        Work Experience
      </h3>
      <div class="cv__experience-right">
        <ExperienceEntry
          v-for="experienceEntry in experience"
          :key="experienceEntry.title"
          :entry="experienceEntry"
        />
      </div>
    </div>
    <div class="cv__education">
      <h3 class="cv__education-left">
        Education
      </h3>
      <div class="cv__education-right">
        <div class="cv__education__entry">
          <div class="cv__education__entry-title">
            Universidad Politécnica de Madrid
          </div>
          <div>Master's degree on Web Engineering</div>
        </div>
        <div class="cv__education__entry">
          <div class="cv__education__entry-title">
            Universidad Nacional de Loja
          </div>
          <div>Bachelor's degree on Computer Science</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Context } from '@nuxt/types'
export default {
  name: 'CV',
  async asyncData ({ $content, error }: Context) {
    try {
      const experience = await $content('cv')
        .only(['title', 'dates', 'activities'])
        .sortBy('path', 'desc')
        .fetch()

      return {
        experience
      }
    } catch (e) {
      error({ statusCode: 404, message: 'Not found' })
    }
  },
  head: {
    title: 'Fabricio Flores | CV'
  }
}
</script>

<style lang="scss">
.cv {
  display: flex;
  flex-direction: column;
  width: 100%;

  &__header {
    display: flex;
    justify-content: space-between;

  @include for-phone-and-tablet {
    flex-direction: column;
    align-items: center;
  }

    &__left, &__right {
      display: flex;
      align-items: center;
      justify-content: center;
    }

    &__right {
      flex-direction: column;
      justify-content: center;
      align-items: flex-end;

      @include for-phone-and-tablet {
        margin-top: 1rem;
        align-items: center;
        flex: 1;
      }
    }
  }

  &__title {
    font-size: 2rem;
    font-weight: bold;
    margin: 0 1rem;
  }

  &__experience,
  &__skills,
  &__education {
    display: flex;

    @include for-phone-and-tablet {
      flex-direction: column;
    }

    &-left {
      flex: 0.3;
      font-size: 1.8rem;
      font-weight: bold;
      margin-top: 1rem;
    }

    &-right {
      flex: 1;
    }

    &__entry {
      @include box();

      &-title {
        font-size: 1.5rem;
        font-weight: bold;
        margin: 0;
      }

    }

  }

  ul, ol {
    margin: 1rem 2rem;
  }

  ul {
    @apply list-disc;
  }

  ol {
    @apply list-decimal;
  }
}
</style>
