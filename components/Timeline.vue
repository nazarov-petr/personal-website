<template>
  <div class="">
    <h2 class="title is-2 has-text-centered" data-aos="fade-right">
      {{ title }}
    </h2>
    <div class="line__container" data-aos="fade-up">
      <div
        v-for="(element, index) in elements"
        :key="index"
        class="line__element "
      >
        <div class="line__dot" />
        <div class="line__right">
          <h5 class="line__title">
            <template v-if="!element.link">
              {{ element.title }}
            </template>
            <a
              v-if="element.link"
              :href="element.link"
              target="_blank"
              class="UI-external-link"
            >
              {{ element.title }}
              <font-awesome-icon
                class="UI-external-link__icon"
                size="sm"
                :icon="['fas', 'external-link-alt']"
              />
            </a>
          </h5>
          <h6 class="line__subtitle">{{ element.subtitle }}</h6>
          <p class="line__date">{{ element.date }}</p>
          <ul v-if="element.tasks" class="line__tasks">
            <li
              v-for="(task, taskIndex) in element.tasks"
              :key="taskIndex"
              class="line__tasks_element"
            >
              <b>-</b> {{ task }}
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: 'Timeline',
  props: {
    title: {
      type: String,
      required: true
    },
    elements: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      //
    }
  }
}
</script>
<style lang="scss" scoped>
@import '~/assets/styles/main';
.line {
  &__container {
    border-left: 2px solid #ccd1d9;
    margin-left: 16px;
    // padding-top: 32px;
    padding-bottom: 16px;
  }
  &__element {
    padding-top: 16px;
    padding-bottom: 16px;
    padding-left: 32px;
    position: relative;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: flex-start;
  }
  &right {
    display: block;
  }
  &__dot {
    width: 16px;
    height: 16px;
    position: absolute;
    background-color: $white;
    left: -9px;
    border: 5px solid $primary;
    border-radius: 50%;
  }
  &__title {
    font-size: 1.3rem;
    font-weight: 700;
    text-transform: uppercase;
    color: $secondary;
  }
  &__subtitle {
    font-size: 1rem;
    color: $secondary;
  }
  &__tasks {
    &_element {
      font-size: 1rem;
      color: $secondary;
      margin-top: 0;
      margin-bottom: 0;
    }
  }
  &__date {
    font-size: 1rem;
    color: $secondary;
  }
}
.line__subtitle,
.line__date,
.line__title,
.line__dot,
.line__tasks {
  transition-property: all;
  transition-timing-function: ease;
  transition-duration: 0.4s;
}
@media (min-width: $tablet) {
  .line__element:hover {
    .line__subtitle,
    .line__date,
    .line__title,
    .line__tasks {
      transform: scale(1.05);
      padding-left: 10px;
    }
    .line__tasks {
      padding-left: 30px;
    }
    .line__dot {
      transform: scale(1.2);
    }
  }
}
</style>
