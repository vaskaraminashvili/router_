<template>
  <div>
    <ul>
      <li v-for="li in list" :key="li.name">
        {{ li.name }}
        <router-link :to="'/teams/' + li.id">View Members</router-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      list: [
        {
          id: 't1',
          name: 'test',
          firstna: 'kargi ra '
        },
        {
          id: 't2',
          name: 'test',
          firstna: 'kargi ra '
        },
        {
          id: 't3',
          name: 'test',
          firstna: 'kargi ra '
        }
      ]
    };
  },
  computed: {
    teamMembersLink() {
      return '/teams/' + 't1';
    }
  }
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
