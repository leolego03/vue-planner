<template>
  <AddPlan v-show="showAddPlan" 
  @add-plan="addPlan" />
  <Plans
    @toggle-reminder="toggleReminder"
    @delete-plan="deletePlan"
    :plans="plans"
  />
</template>

<script>
import Plans from '../components/Plans'
import AddPlan from '../components/AddPlan'
export default {
  name: 'Home',
  props: {
    showAddPlan: Boolean,
  },
  components: {
    Plans,
    AddPlan
  },
  data() {
    return {
      plans: [],
    }
  },
  methods: {
    async addPlan(plan) {
      const res = await fetch('api/plans', {
        method: 'POST',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify(plan),
      })

      const data = await res.json()

      this.plans = [...this.plans, data]
    },
    async deletePlan(id) {
      if(confirm('Are you sure?')) {
        const res = await fetch(`api/plans/${id}`, {
          method: 'DELETE'
        })

        res.status === 200 ? (
          this.plans = this.plans.filter((plan) => plan.id !== id)
        ) : alert('Error deleting plan')
      }
    },
    async toggleReminder(id) {
      const planToToggle = await this.fetchPlan(id)
      const updPlan = {...planToToggle, reminder: !planToToggle.reminder}

      const res = await fetch(`api/plans/${id}`, {
        method: 'PUT',
        headers: {
          'Content-type': 'application/json'
        },
        body: JSON.stringify(updPlan)
      })

      const data = await res.json()

      this.plans = this.plans.map((plan) => plan.id === id ? { ...plan, reminder: data.reminder } : plan)
    },
    async fetchPlans() {
      const res = await fetch('api/plans')

      const data = await res.json()

      return data
    },
    async fetchPlan(id) {
      const res = await fetch(`api/plans/${id}`)

      const data = await res.json()

      return data
    },
  },
  async created() {
    this.plans = await this.fetchPlans()
  },
}
</script>