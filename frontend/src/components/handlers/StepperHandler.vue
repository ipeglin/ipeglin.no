<script setup lang="ts">
import type { NumberedStepInterface, TimelineStepInterface } from "@/assets/interfaces/StepInterface";
import Timeline from "../organisms/Timeline.vue";
import Stepper from '../organisms/Stepper.vue';

interface Props {
  title: string,
  content: NumberedStepInterface[] | TimelineStepInterface[],
}

const props = defineProps<Props>();

const isNumberedStepper = (content: NumberedStepInterface[] | TimelineStepInterface[]): boolean => {
  return (content as NumberedStepInterface[])[0].active !== undefined;
}

</script>

<template>
  <div class="stepper">
    <h1 class="stepper-title">{{ title }}</h1>
    <Stepper v-if="isNumberedStepper(content)" :content="content" />
    <Timeline v-else :content="content" />
  </div>
</template>

<style scoped lang="scss">
  .stepper {
    display: flex;
    flex-direction: column;
    margin-top: 20px;
    width: 95%;

    .stepper-title {
      align-self: center;
      text-decoration: underline;
      text-underline-offset: 5px;
      text-decoration-color: $color-accent;
      text-decoration-thickness: 2px;
    }
  }
</style>