<template>
  <div class="container py-5">
    <h1>餐廳描述頁</h1>
    <!-- 餐廳資訊頁 RestaurantDetail -->
    <RestaurantDetail :initial-restaurant="restaurant" />
    <hr />
    <!-- 餐廳評論 RestaurantComments -->
    <RestaurantComments
      :restaurant-comments="restaurantComments"
      @after-delete-comment="afterDeleteComment"
    />
    <!-- 新增評論 CreateComment -->
    <CreateComment
      :restaurant-id="restaurant.id"
      @after-create-comment="afterCreateComment"
    />
  </div>
</template>

<script>
import RestaurantDetail from "../components/RestaurantDetail.vue";
import RestaurantComments from "../components/RestaurantComments.vue";
import CreateComment from "../components/CreateComment.vue";
const dummyData = {
  restaurant: {
    id: 1,
    name: "Myrtie Lubowitz",
    tel: "430.055.6819 x78875",
    address: "6965 Alba Flats",
    opening_hours: "08:00",
    description:
      "Eaque accusamus veritatis minima numquam voluptas delectus quam impedit provident.\nQuae perferendis mollitia eos molestiae rem inventore beatae illo cumque.",
    image:
      "https://loremflickr.com/320/240/restaurant,food/?random=82.87613490975679",
    viewCounts: 1,
    createdAt: "2022-02-04T16:57:33.000Z",
    updatedAt: "2022-02-05T08:46:09.060Z",
    CategoryId: 1,
    Category: {
      id: 1,
      name: "中式料理",
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
    },
    FavoritedUsers: [],
    LikedUsers: [],
    Comments: [
      {
        id: 51,
        text: "Cumque eligendi doloremque iure deleniti quaerat minima vitae quaerat occaecati.",
        UserId: 2,
        RestaurantId: 1,
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
        User: {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$I6fbQRqwMUWq/5O5OVzuE.oSQrxwv0nBAV7skX1huZX3HiKuSAI/m",
          isAdmin: false,
          image: null,
          createdAt: "2022-02-04T16:57:33.000Z",
          updatedAt: "2022-02-04T16:57:33.000Z",
        },
      },
      {
        id: 1,
        text: "Dolorem sit quod fugit.",
        UserId: 3,
        RestaurantId: 1,
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
        User: {
          id: 3,
          name: "user2",
          email: "user2@example.com",
          password:
            "$2a$10$Gr4nxbzXZ4lhqblC79jLveOaCUUF2F.pnOYWkY1fvwnNIvYGm2Hiy",
          isAdmin: false,
          image: null,
          createdAt: "2022-02-04T16:57:33.000Z",
          updatedAt: "2022-02-04T16:57:33.000Z",
        },
      },
      {
        id: 101,
        text: "Est velit possimus molestias cumque molestiae praesentium ipsa.",
        UserId: 3,
        RestaurantId: 1,
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
        User: {
          id: 3,
          name: "user2",
          email: "user2@example.com",
          password:
            "$2a$10$Gr4nxbzXZ4lhqblC79jLveOaCUUF2F.pnOYWkY1fvwnNIvYGm2Hiy",
          isAdmin: false,
          image: null,
          createdAt: "2022-02-04T16:57:33.000Z",
          updatedAt: "2022-02-04T16:57:33.000Z",
        },
      },
    ],
  },
  isFavorited: false,
  isLiked: false,
};

const dummyUser = {
  currentUser: {
    id: 1,
    name: "管理者",
    email: "root@example.com",
    image: "https://i.pravatar.cc/300",
    isAdmin: true,
  },
  isAuthenticated: true,
};

export default {
  components: {
    RestaurantDetail,
    RestaurantComments,
    CreateComment,
  },
  data() {
    return {
      restaurant: {
        id: -1,
        name: "",
        categoryName: "",
        image: "",
        openingHours: "",
        tel: "",
        address: "",
        description: "",
        isFavorited: false,
        isLiked: false,
      },
      restaurantComments: [],
      currentUser: dummyUser.currentUser,
    };
  },
  created() {
    const { id } = this.$route.params;
    this.fetchRestaurant(id);
  },
  methods: {
    fetchRestaurant(restaurantId) {
      console.log("fetchRestaurant id: ", restaurantId);
      const { restaurant, isFavorited, isLiked } = dummyData;
      const {
        id,
        name,
        tel,
        image,
        address,
        opening_hours: openingHours,
        description,
        Category,
        Comments,
      } = restaurant;

      this.restaurant = {
        id,
        name,
        categoryName: Category ? Category.name : "未定義",
        image,
        tel,
        address,
        openingHours,
        description,
        isFavorited,
        isLiked,
      };
      this.restaurantComments = Comments;
    },
    afterDeleteComment(commentId) {
      // 以 filter 保留未被選擇的 comment.id
      this.restaurantComments = this.restaurantComments.filter(
        (comment) => comment.id !== commentId
      );
    },
    afterCreateComment(payload) {
      const { commentId, restaurantId, text } = payload;
      this.restaurantComments.push({
        id: commentId,
        RestaurantId: restaurantId,
        User: {
          id: this.currentUser.id,
          name: this.currentUser.name,
        },
        text,
        createdAt: new Date(),
      });
    },
  },
};
</script>
