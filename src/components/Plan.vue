<template>
  <div @dblclick="$emit('toggle-reminder', plan.id)"
  :class="[plan.reminder ? 'reminder' : '', 'plan']"
  >
    <h3>
      {{ plan.text }}
      <i @click="$emit('delete-plan' ,plan.id)" class="fas fa-times"></i>
    </h3>
    <p>{{ plan.day }}</p>
  </div>
</template>

<script>
export default {
  name: 'Plan',
  props: {
    plan: Object,
  },
}
</script>

<style scope>
.fas {
  color: #ff625a;
}

.plan {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}

.plan.reminder {
  border-left: 5px solid #ffbc00;
}

.plan h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

</style>