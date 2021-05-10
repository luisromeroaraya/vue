<template>
  <div id="home" class="home">
    <h1>{{ restaurantName }}</h1>
    <p class="description">
      Bienvenue dans notre café {{ restaurantName }}! Nous sommes réputés pour
      notre pain et nos merveilleuses pâtisseries. Faites vous plaisir dès le
      matin ou avec un goûter réconfortant. Mais attention, vous verrez qu'il
      est difficile de s'arrêter.
    </p>

    <section class="menu">
      <h2>Menu</h2>
      <MenuItem 
        v-for="item in simpleMenu" 
        :key="item.name"
        :name="item.name"
        :image="item.image"
        :quantity="item.quantity"
        :inStock="item.inStock"
        :addToShoppingCart="addToShoppingCart"
        />
    </section>

    <aside class="shopping-cart">
      <h2>Panier d'achat : {{ shoppingCart }} articles</h2>
    </aside>
    <footer class="footer">
      <p>{{ copyright }}</p>
    </footer>
  </div>
</template>

<script>
import MenuItem from "@/components/MenuItem.vue";

export default {
  name: "Home",
  components: {
    MenuItem,
  },
  data() {
    return {
      restaurantName: "La belle vue",
      shoppingCart: 0,
      simpleMenu: [
        {
          name: "Croissant",
          image: {
            source: "./images/croissant.jpg",
            alt: "Un croissant",
          },
          inStock: true,
          quantity: 0,
        },
        {
          name: "Baguette de pain",
          image: {
            source: "./images/french-baguette.jpeg",
            alt: "Quatre baguettes de pain",
          },
          inStock: true,
          quantity: 0,
        },
        {
          name: "Éclair",
          image: {
            source: "./images/eclair.jpg",
            alt: "Éclair au chocolat",
          },
          inStock: false,
          quantity: 0,
        },
      ],
    };
  },
  computed: {
    copyright() {
      const currentYear = new Date().getFullYear();

      return `Copyright ${this.restaurantName} ${currentYear}`;
    },
  },
  methods: {
    addToShoppingCart(amount) {
      this.shoppingCart += amount;
    },
  },
};
</script>
