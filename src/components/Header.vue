<template>
  <header>

    <div class="title">
      {{ title }}
    </div>

    <div class="hd-con">
      <div class="user-con">
        <div class="userimg">
          <img src="../assets/planner_user01.png" alt="">
        </div>
        <p class="username">
          user01
        </p>
      </div>

      <Button v-show="homePage"
        @btn-click="$emit('toggle-add-plan')"
        :text="showAddPlan ? 'Close' : 'Add Plan'"
        :color="showAddPlan ? '#ff625a' : '#ffbc00'"
      />
    </div>

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
.hd-con {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 20px 0;
}

.title {
  font-size: x-large;
  font-weight: bold;
}

.userimg {
  width: 120px;
  height: 120px;
  /* margin-bottom: 20px; */
  /*background-color: #7f7f7f;*/
}

.userimg :deep(img) {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.username {
  font-size: 15px;
  padding: 10px 0;
}

</style>