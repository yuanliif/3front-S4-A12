<template>
  <div class="container py-5">
    <NavTabs />
    <!-- 餐廳類別標籤 RestaurantsNavPills -->
    <RestaurantsNavPills :categories="categories" />

    <div class="row">
      <!-- 餐廳卡片 RestaurantCard-->
      <RestaurantCard
        v-for="restaurant in restaurants"
        :key="restaurant.id"
        :initial-restaurant="restaurant"
      />
    </div>

    <!-- 分頁標籤 RestaurantPagination -->
    <RestaurantPagination
      v-if="totalPage.length > 1"
      :category-id="categoryId"
      :current-page="currentPage"
      :total-page="totalPage"
      :previous-page="previousPage"
      :next-page="nextPage"
    />
  </div>
</template>

<script>
import NavTabs from "../components/NavTabs.vue";
import RestaurantCard from "../components/RestaurantCard.vue";
import RestaurantsNavPills from "../components/RestaurantsNavPills.vue";
import RestaurantPagination from "../components/RestaurantPagination.vue";

const dummyData = {
  restaurants: [
    {
      id: 1,
      name: "Myrtie Lubowitz",
      tel: "430.055.6819 x78875",
      address: "6965 Alba Flats",
      opening_hours: "08:00",
      description: "Eaque accusamus veritatis minima numquam voluptas ",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=82.87613490975679",
      viewCounts: 0,
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 2,
      name: "Valentine Kub",
      tel: "516.843.7944",
      address: "676 Leif Flats",
      opening_hours: "08:00",
      description: "Molestiae ut numquam ipsa dolores quia temporibus.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=72.1759010868031",
      viewCounts: 0,
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 3,
      name: "Marlen Mohr",
      tel: "959.653.4673 x952",
      address: "9958 Halie Crossing",
      opening_hours: "08:00",
      description: "Est eveniet vero sit aliquam labore sed vitae. Con",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=98.22923112194066",
      viewCounts: 0,
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 4,
      name: "Ocie Koelpin",
      tel: "(684) 577-7777 x66283",
      address: "38849 Polly Brook",
      opening_hours: "08:00",
      description: "Et molestiae aliquam.\nDolores magnam eligendi repe",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=99.41929436382728",
      viewCounts: 0,
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 5,
      name: "Opal Block",
      tel: "(736) 038-9734",
      address: "47649 Goldner Shore",
      opening_hours: "08:00",
      description: "minus qui et",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=9.497006780990947",
      viewCounts: 0,
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 6,
      name: "Jacinto Mohr",
      tel: "1-232-943-0194 x6026",
      address: "01454 Braun Island",
      opening_hours: "08:00",
      description: "vel nihil nulla",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=38.73021641147902",
      viewCounts: 0,
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 7,
      name: "Zita Doyle",
      tel: "190.631.8080 x46774",
      address: "3798 Jace Causeway",
      opening_hours: "08:00",
      description: "Saepe quia ut voluptate ut reiciendis consequuntur",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=85.02534210822192",
      viewCounts: 0,
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 8,
      name: "Miss Jarrod Gibson",
      tel: "658.558.9648",
      address: "2035 Jaclyn Lodge",
      opening_hours: "08:00",
      description: "Provident quia suscipit et inventore vel rerum.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=40.20983401937299",
      viewCounts: 0,
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 9,
      name: "Lamont Schmidt",
      tel: "723.297.3914 x44643",
      address: "9092 Daniel Forge",
      opening_hours: "08:00",
      description: "iusto",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=60.22588169190182",
      viewCounts: 0,
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 10,
      name: "Tabitha Beer",
      tel: "1-711-936-7855",
      address: "06054 Kris Run",
      opening_hours: "08:00",
      description: "Culpa illum ut non possimus consequatur dolore. Cu",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=88.02446584572414",
      viewCounts: 0,
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
  ],
  categories: [
    {
      id: 1,
      name: "中式料理",
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
    },
    {
      id: 2,
      name: "日本料理",
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
    },
    {
      id: 3,
      name: "義大利料理",
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
    },
    {
      id: 4,
      name: "墨西哥料理",
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
    },
    {
      id: 5,
      name: "素食料理",
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
    },
    {
      id: 6,
      name: "美式料理",
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
    },
    {
      id: 7,
      name: "複合式料理",
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
    },
  ],
  categoryId: "",
  page: 1,
  totalPage: [1, 2, 3, 4, 5],
  prev: 1,
  next: 2,
};

export default {
  components: {
    NavTabs,
    RestaurantCard,
    RestaurantsNavPills,
    RestaurantPagination,
  },
  data() {
    return {
      restaurants: [],
      categories: [],
      categoryId: -1,
      currentPage: -1,
      totalPage: [],
      previousPage: -1,
      nextPage: -1,
    };
  },
  methods: {
    fetchRestaurants() {
      const {
        restaurants,
        categories,
        categoryId,
        page: currentPage,
        totalPage,
        prev: previousPage,
        next: nextPage,
      } = dummyData;
      this.restaurants = restaurants;
      this.categories = categories;
      this.categoryId = categoryId;
      this.currentPage = currentPage;
      this.totalPage = totalPage;
      this.previousPage = previousPage;
      this.nextPage = nextPage;
    },
  },
  created() {
    this.fetchRestaurants();
  },
};
</script>
