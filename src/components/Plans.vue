<template>
  <div :key="plan.id" v-for="plan in plans">
    <Plan 
      @toggle-reminder="$emit('toggle-reminder', plan.id)"
      @delete-plan="$emit('delete-plan', plan.id)"
      :plan="plan"
    />
  </div>  
</template>

<script>
import Plan from './Plan'

export default {
  name: 'Plans',
  props: {
    plans: Array,
  },
  components: {
    Plan,
  },
  emits: ['delete-plan', 'toggle-reminder'],
}
</script>