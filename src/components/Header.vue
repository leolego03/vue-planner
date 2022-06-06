<template>
  <header>
    <div class="title">
      {{ title }}
      <p>Planner</p>
    </div>

    <Button v-show="homePage"
      @btn-click="$emit('toggle-add-plan')"
      :text="showAddPlan ? 'Close' : 'Add Plan'"
      :color="showAddPlan ? '#ff625a' : '#ffbc00'"
    />
  </header>
</template>

<script>
import Button from './Button'

export default {
  name: 'Header',
  props: {
    title: String,
    showAddPlan: Boolean
  },
  components: {
    Button,
  },
  computed: {
    homePage() {
      if(this.$route.path === '/') {
        return true
      } else {
        return false
      }
    }
  }
}
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
.title {
  font-size: x-large;
  font-weight: bold;
}
p {
  font-weight: normal;
}
</style>