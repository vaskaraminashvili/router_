<template>
  <button type="button" @click="confirmData">Confirm</button>
  <button type="button" @click="saveChanges">Save changes</button>
  <ul>
    <user-item
      v-for="user in users"
      :key="user.id"
      :name="user.fullName"
      :role="user.role"
    ></user-item>
  </ul>
</template>

<script>
import UserItem from './UserItem.vue';

export default {
  components: {
    UserItem
  },
  data() {
    return {
      savedChanges: false
    };
  },
  methods: {
    saveChanges() {
      this.savedChanges = true;
    },
    confirmData() {
      // do something
      this.$router.push('/teams');
    }
  },
  beforeRouteEnter(to, from, next) {
    console.log('users list log');
    console.log(to, from);
    next();
  },
  beforeRouteLeave(_, _2, next) {
    if (this.savedChanges) {
      next();
    } else {
      const userWantsToleave = confirm('ares you sure? ');
      next(userWantsToleave);
    }
  },
  unmounted() {
    console.log('unmounted');
  },
  inject: ['users']
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 2rem auto;
  max-width: 20rem;
  padding: 0;
}
</style>
