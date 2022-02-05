<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">美食達人</h1>
    <hr />
    <div class="row text-center">
      <div class="col-3" v-for="user in users" :key="user.id">
        <a href="#">
          <img
            src="http://via.placeholder.com/300x300?text=No+Image"
            width="140px"
            height="140px"
          />
        </a>
        <h2>{{ user.name }}</h2>
        <span class="badge badge-secondary"
          >追蹤人數： {{ user.FollowerCount }}</span
        >
        <p class="mt-3">
          <button
            type="button"
            class="btn btn-danger"
            v-if="user.isFollowed"
            @click.prevent.stop="user.isFollowed = !user.isFollowed"
          >
            取消追蹤
          </button>
          <button
            type="button"
            class="btn btn-primary"
            v-else
            @click.prevent.stop="user.isFollowed = !user.isFollowed"
          >
            追蹤
          </button>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from "../components/NavTabs.vue";

const dummyData = {
  users: [
    {
      id: 1,
      name: "root",
      email: "root@example.com",
      password: "$2a$10$s1olshBeCvWg5xnERHAiXexc8EdNbCTagSEt/zo0bQJo0E8XRMGiO",
      isAdmin: true,
      image: null,
      createdAt: "2022-01-31T16:12:30.000Z",
      updatedAt: "2022-01-31T16:12:30.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false,
    },
    {
      id: 2,
      name: "user1",
      email: "user1@example.com",
      password: "$2a$10$RRxUcI5vsPTo7h/NcyZcjepEQJiFX2kNJL3x3FUA//sdoncBPJClK",
      isAdmin: false,
      image: null,
      createdAt: "2022-01-31T16:12:30.000Z",
      updatedAt: "2022-01-31T16:12:30.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false,
    },
    {
      id: 3,
      name: "user2",
      email: "user2@example.com",
      password: "$2a$10$tM/EyX.WQp4Bp0O3GKZNh.2o1LrIgP/F6HxFZXYrHA82pqWwOqRee",
      isAdmin: false,
      image: null,
      createdAt: "2022-01-31T16:12:30.000Z",
      updatedAt: "2022-01-31T16:12:30.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false,
    },
  ],
};

export default {
  components: {
    NavTabs,
  },
  data() {
    return {
      users: [],
    };
  },
  methods: {
    fetchUsers() {
      const { users } = dummyData;
      this.users = users;
    },
  },
  created() {
    this.fetchUsers();
  },
};
</script>
