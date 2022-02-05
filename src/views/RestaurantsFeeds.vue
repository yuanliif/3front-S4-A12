<template>
  <div class="container py-5">
    <NavTabs />

    <h1 class="mt-5">最新動態</h1>
    <hr />
    <div class="row">
      <div class="col-md-6">
        <h3>最新餐廳</h3>
        <!-- 最新餐廳 NewestRestaurants -->
        <NewestRestaurants :restaurants="restaurants" />
      </div>
      <div class="col-md-6">
        <!-- 最新評論 NewestComments-->
        <h3>最新評論</h3>
        <NewestComments :comments="comments"/>
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from "../components/NavTabs.vue";
import NewestRestaurants from "../components/NewestRestaurants.vue";
import NewestComments from "../components/NewestComments.vue";

const dummyData = {
  restaurants: [
    {
      id: 1,
      name: "Myrtie Lubowitz",
      tel: "430.055.6819 x78875",
      address: "6965 Alba Flats",
      opening_hours: "08:00",
      description:
        "Eaque accusamus veritatis minima numquam voluptas delectus quam impedit provident.\nQuae perferendis mollitia eos molestiae rem inventore beatae illo cumque.",
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
    },
    {
      id: 2,
      name: "Valentine Kub",
      tel: "516.843.7944",
      address: "676 Leif Flats",
      opening_hours: "08:00",
      description:
        "Molestiae ut numquam ipsa dolores quia temporibus. Molestiae ad fuga sed veniam sint aut quam. Harum autem ducimus quam. Est animi recusandae qui similique molestiae labore praesentium totam sunt.",
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
    },
    {
      id: 3,
      name: "Marlen Mohr",
      tel: "959.653.4673 x952",
      address: "9958 Halie Crossing",
      opening_hours: "08:00",
      description:
        "Est eveniet vero sit aliquam labore sed vitae. Consectetur quia optio. Id repellendus ipsum architecto voluptatem ut voluptas distinctio maiores aut. In aperiam vel natus natus reiciendis quas.\n \rCupiditate aut sint eius non dolores. Quos iste dolores sed aperiam hic animi nihil eaque ipsam. Quidem aut rem.\n \rAut officiis magnam voluptate. Expedita expedita nihil. Blanditiis modi magni ipsam laboriosam minus sint. Inventore voluptates quibusdam sunt voluptatem porro aut totam illum. Sed animi similique voluptatibus quasi.",
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
    },
    {
      id: 4,
      name: "Ocie Koelpin",
      tel: "(684) 577-7777 x66283",
      address: "38849 Polly Brook",
      opening_hours: "08:00",
      description:
        "Et molestiae aliquam.\nDolores magnam eligendi repellendus repudiandae molestias.\nIllo sed qui eaque.\nBeatae et et architecto.\nMagnam unde illo voluptatem.",
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
    },
    {
      id: 7,
      name: "Zita Doyle",
      tel: "190.631.8080 x46774",
      address: "3798 Jace Causeway",
      opening_hours: "08:00",
      description: "Saepe quia ut voluptate ut reiciendis consequuntur natus.",
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
    },
    {
      id: 10,
      name: "Tabitha Beer",
      tel: "1-711-936-7855",
      address: "06054 Kris Run",
      opening_hours: "08:00",
      description:
        "Culpa illum ut non possimus consequatur dolore. Culpa et earum id. Odio beatae omnis id labore eaque saepe ratione qui. Excepturi qui illo sed illum. Sit error aperiam labore doloremque voluptas dolor nemo. Doloremque magni unde quisquam consequatur autem.\n \rEa sit enim. Incidunt dolorem dolores tempore maxime pariatur architecto. Non tempore et fugiat provident non dignissimos sed omnis. Veritatis dignissimos quaerat eos. Aut molestias ut ad dolorem sunt debitis architecto. Quaerat cum velit omnis odit.\n \rDolor esse aliquam voluptas et. Qui dolor corporis qui facere assumenda. Eius officia nobis quaerat hic reprehenderit quia. Aut nihil provident quia inventore eaque assumenda laborum sint alias. Eaque officia omnis aliquam ut. Ut minima libero reprehenderit rerum consequatur.",
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
    },
  ],
  comments: [
    {
      id: 4,
      text: "Numquam unde assumenda non.",
      UserId: 1,
      RestaurantId: 4,
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
      User: {
        id: 1,
        name: "root",
        email: "root@example.com",
        password:
          "$2a$10$O99CfqTqMDUP3COoxN3aAeqb6ZDq4sCFf.UtSZ6ovJn01gK2/3VhO",
        isAdmin: true,
        image: null,
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
      },
      Restaurant: {
        id: 4,
        name: "Ocie Koelpin",
        tel: "(684) 577-7777 x66283",
        address: "38849 Polly Brook",
        opening_hours: "08:00",
        description:
          "Et molestiae aliquam.\nDolores magnam eligendi repellendus repudiandae molestias.\nIllo sed qui eaque.\nBeatae et et architecto.\nMagnam unde illo voluptatem.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=99.41929436382728",
        viewCounts: 0,
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
        CategoryId: 2,
      },
    },
    {
      id: 26,
      text: "Maxime repellendus culpa qui placeat sed numquam recusandae dolorum.",
      UserId: 1,
      RestaurantId: 26,
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
      User: {
        id: 1,
        name: "root",
        email: "root@example.com",
        password:
          "$2a$10$O99CfqTqMDUP3COoxN3aAeqb6ZDq4sCFf.UtSZ6ovJn01gK2/3VhO",
        isAdmin: true,
        image: null,
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
      },
      Restaurant: {
        id: 26,
        name: "Talia Hoeger",
        tel: "145-513-2987 x74593",
        address: "97834 Lind Springs",
        opening_hours: "08:00",
        description:
          "Tempore sed voluptatem repellat at eos.\nMagni est cumque sequi nihil.\nLaboriosam officiis autem consequatur molestias repudiandae nihil cupiditate.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=10.848597324699917",
        viewCounts: 0,
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
        CategoryId: 3,
      },
    },
    {
      id: 54,
      text: "Quos doloribus dolores quo.",
      UserId: 1,
      RestaurantId: 4,
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
      User: {
        id: 1,
        name: "root",
        email: "root@example.com",
        password:
          "$2a$10$O99CfqTqMDUP3COoxN3aAeqb6ZDq4sCFf.UtSZ6ovJn01gK2/3VhO",
        isAdmin: true,
        image: null,
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
      },
      Restaurant: {
        id: 4,
        name: "Ocie Koelpin",
        tel: "(684) 577-7777 x66283",
        address: "38849 Polly Brook",
        opening_hours: "08:00",
        description:
          "Et molestiae aliquam.\nDolores magnam eligendi repellendus repudiandae molestias.\nIllo sed qui eaque.\nBeatae et et architecto.\nMagnam unde illo voluptatem.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=99.41929436382728",
        viewCounts: 0,
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
        CategoryId: 2,
      },
    },
    {
      id: 66,
      text: "Cum natus aut beatae aut qui eos est.",
      UserId: 1,
      RestaurantId: 16,
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
      User: {
        id: 1,
        name: "root",
        email: "root@example.com",
        password:
          "$2a$10$O99CfqTqMDUP3COoxN3aAeqb6ZDq4sCFf.UtSZ6ovJn01gK2/3VhO",
        isAdmin: true,
        image: null,
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
      },
      Restaurant: {
        id: 16,
        name: "Rickie Schuster Sr.",
        tel: "282-721-1121 x078",
        address: "887 Nienow Parks",
        opening_hours: "08:00",
        description:
          "Et perferendis et ut rerum veritatis sit. Vel recusandae nisi cum numquam quas sed culpa suscipit cumque.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=41.059612461284686",
        viewCounts: 0,
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
        CategoryId: 2,
      },
    },
    {
      id: 98,
      text: "Beatae similique ut at est cupiditate animi fugiat in.",
      UserId: 1,
      RestaurantId: 48,
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
      User: {
        id: 1,
        name: "root",
        email: "root@example.com",
        password:
          "$2a$10$O99CfqTqMDUP3COoxN3aAeqb6ZDq4sCFf.UtSZ6ovJn01gK2/3VhO",
        isAdmin: true,
        image: null,
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
      },
      Restaurant: {
        id: 48,
        name: "Sandra Macejkovic",
        tel: "1-866-065-3107",
        address: "7390 Natalie Crescent",
        opening_hours: "08:00",
        description:
          "Est aspernatur culpa quas officiis tempore inventore quibusdam autem. Aperiam voluptas praesentium officia sint. Enim non labore voluptatem exercitationem molestias sit consequatur ducimus. Inventore eveniet ipsam debitis voluptas sed blanditiis. Voluptatem commodi officiis doloremque animi. Harum sed distinctio recusandae in totam.\n \rUt atque non quibusdam rerum. Tenetur labore nostrum inventore maxime voluptas harum amet quas. Nobis assumenda aut.\n \rMagni fugiat distinctio consequatur dolorem. Quaerat facilis quo voluptatem temporibus est temporibus. Necessitatibus autem et pariatur adipisci ut. Exercitationem qui qui ut fuga sapiente accusantium. Quia deleniti optio sapiente. Aut culpa ut incidunt perferendis sit.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=90.24544339458056",
        viewCounts: 0,
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
        CategoryId: 2,
      },
    },
    {
      id: 118,
      text: "Incidunt quasi molestiae ipsa.",
      UserId: 1,
      RestaurantId: 18,
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
      User: {
        id: 1,
        name: "root",
        email: "root@example.com",
        password:
          "$2a$10$O99CfqTqMDUP3COoxN3aAeqb6ZDq4sCFf.UtSZ6ovJn01gK2/3VhO",
        isAdmin: true,
        image: null,
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
      },
      Restaurant: {
        id: 18,
        name: "Rosalinda Anderson",
        tel: "1-453-082-7259 x557",
        address: "724 Runolfsson Rapid",
        opening_hours: "08:00",
        description:
          "Architecto eum et. Ipsam saepe voluptatem dolorem qui qui enim sed. Quia quis magni doloremque veniam ut. Rerum et unde.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=56.67295380522539",
        viewCounts: 0,
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
        CategoryId: 3,
      },
    },
    {
      id: 150,
      text: "Repellendus expedita fugiat maiores sit temporibus aut suscipit eligendi.",
      UserId: 1,
      RestaurantId: 50,
      createdAt: "2022-02-04T16:57:33.000Z",
      updatedAt: "2022-02-04T16:57:33.000Z",
      User: {
        id: 1,
        name: "root",
        email: "root@example.com",
        password:
          "$2a$10$O99CfqTqMDUP3COoxN3aAeqb6ZDq4sCFf.UtSZ6ovJn01gK2/3VhO",
        isAdmin: true,
        image: null,
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
      },
      Restaurant: {
        id: 50,
        name: "Perry Osinski",
        tel: "392-685-0130 x877",
        address: "475 Seamus Pike",
        opening_hours: "08:00",
        description:
          "Dolore incidunt dignissimos velit iure voluptate est.\nMaiores tempore voluptatem doloremque corporis quia ipsum voluptates doloribus.\nEnim sed aut et laboriosam numquam.\nVero est vero ut earum nisi dolorum.\nMinima voluptatem vel et cumque et.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=46.75926016799927",
        viewCounts: 0,
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
        CategoryId: 3,
      },
    },
    {
      id: 24,
      text: "Quod distinctio rerum adipisci.",
      UserId: 2,
      RestaurantId: 24,
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
      Restaurant: {
        id: 24,
        name: "Dr. Jeanie Halvorson",
        tel: "1-524-675-2552",
        address: "1305 Mona Garden",
        opening_hours: "08:00",
        description:
          "Labore aut cum dolore vero error cupiditate repellat. Architecto totam ullam. Consequatur nisi omnis. Voluptatem dolor et aut quia eius ea. Consequatur maiores facere debitis occaecati odit est qui amet. Omnis dolor sed animi ut.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=95.39491048201675",
        viewCounts: 0,
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
        CategoryId: 4,
      },
    },
    {
      id: 43,
      text: "Minima nulla deleniti et id.",
      UserId: 2,
      RestaurantId: 43,
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
      Restaurant: {
        id: 43,
        name: "Cicero Nicolas",
        tel: "(572) 024-1434",
        address: "7587 Bode Track",
        opening_hours: "08:00",
        description:
          "Est sint maiores numquam quia. Quia recusandae quibusdam corrupti omnis eos. Molestias dignissimos veniam reiciendis ut similique ut incidunt et id. Quia id consequatur. Omnis praesentium a voluptas dolores illo sint omnis repudiandae.\n \rVoluptatem in qui ullam consequatur dolore eligendi. Neque iure ea omnis at deleniti aliquid. Voluptatem ut doloribus sapiente dignissimos commodi voluptatum.\n \rRepudiandae commodi quo quo quasi id ut tempore velit aliquam. Et sint et porro quaerat aperiam ut sequi rerum veritatis. Dolorem repellendus neque qui repudiandae architecto nihil dolor.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=65.18908705610139",
        viewCounts: 0,
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
        CategoryId: 3,
      },
    },
    {
      id: 57,
      text: "Et quisquam doloremque.",
      UserId: 2,
      RestaurantId: 7,
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
      Restaurant: {
        id: 7,
        name: "Zita Doyle",
        tel: "190.631.8080 x46774",
        address: "3798 Jace Causeway",
        opening_hours: "08:00",
        description:
          "Saepe quia ut voluptate ut reiciendis consequuntur natus.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=85.02534210822192",
        viewCounts: 0,
        createdAt: "2022-02-04T16:57:33.000Z",
        updatedAt: "2022-02-04T16:57:33.000Z",
        CategoryId: 5,
      },
    },
  ],
};

export default {
  components: {
    NavTabs,
    NewestRestaurants,
    NewestComments,
  },
  data() {
    return {
      restaurants: [],
      comments: [],
    };
  },
  methods: {
    fetchFeeds() {
      const { restaurants, comments } = dummyData;
      this.restaurants = restaurants;
      this.comments = comments.filter(comment => comment.Restaurant && comment.text);
    },
  },
  created() {
    this.fetchFeeds()
  }
};
</script>
