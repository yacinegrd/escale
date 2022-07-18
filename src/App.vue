<script setup>
import Logo from "./components/icons/logo.vue";
import Insta from "./components/icons/insta.vue";
import PetitDej from "./components/PetitDej.vue";
import Boisson from "./components/Boisson.vue";
import Pizza from "./components/Pizza.vue";
import Sandwich from "./components/Sandwich.vue";
import TH from "./components/TH.vue";
import Patesserie from "./components/Patesserie.vue";
</script>

<template>
  <header><Logo /></header>
  <main v-if="!show" class="language">
    <ul>
      <li v-on:click="setLanguage($event.target)">Français</li>
      <li v-on:click="setLanguage($event.target)">العربية</li>
    </ul>
  </main>
  <main v-else :class="language === 'ar' ? 'ar' : ''">
    <ul class="categories">
      <li
        unselectable="on"
        v-for="categorie in categories"
        v-on:click="change(categorie, $event.target)"
        :class="categorie.active ? 'active' : ''"
      >
        {{ language === "fr" ? categorie.fr : categorie.ar }}
      </li>
    </ul>
    <section class="menu">
      <keep-alive>
        <PetitDej
          v-if="displayed === 'Petit Déjeuner' || displayed === 'فطور الصباح'"
          :lang="language"
        />
      </keep-alive>
      <keep-alive>
        <Boisson
          v-if="displayed === 'Boissons' || displayed === 'مشروبات'"
          :lang="language"
        />
      </keep-alive>
      <keep-alive>
        <Patesserie
          v-if="displayed === 'Patesserie' || displayed === 'حلويات'"
          :lang="language"
        />
      </keep-alive>
      <keep-alive>
        <Pizza
          v-if="displayed === 'Pizza' || displayed === 'بيتزا'"
          :lang="language"
        />
      </keep-alive>
      <keep-alive>
        <TH
          v-if="
            displayed === 'Hamburger & Tacos' || displayed === 'برغر و تاكوس'
          "
          :lang="language"
        />
      </keep-alive>
      <keep-alive>
        <Sandwich
          v-if="displayed === 'Sandwich' || displayed === 'ساندويتش'"
          :lang="language"
        />
      </keep-alive>
    </section>
  </main>
  <footer v-if="language === 'fr'">
    <Logo />
    <div style="text-align: center">
      <span style="display: block">USTO, à côté de l’hôtel Liberté. Oran.</span>
      <a
        class="itinéraire"
        href="https://www.google.com/maps/place/L%E2%80%99%C3%89SCALE/@35.6982966,-0.5962938,17z/data=!4m5!3m4!1s0xd7e6321cf3831e5:0x29e1ee307fac3e3d!8m2!3d35.6982965!4d-0.5949922?hl=FR"
        >voir l'itinéraire
      </a>
    </div>
    <div class="overture">
      <h6>Horaire d’ouverture :</h6>
      <span>Samedi à jeudi : 7:30 - 22:00 </span>
    </div>
    <div class="insta">
      <h6>Abonnez vous :</h6>
      <Insta />
    </div>
  </footer>
  <footer v-else>
    <Logo />
    <div style="text-align: center">
      <span style="display: block">إيسطو بجوار فندق ليبرتي وهران</span>
      <a
        class="itinéraire"
        href="https://www.google.com/maps/place/L%E2%80%99%C3%89SCALE/@35.6982966,-0.5962938,17z/data=!4m5!3m4!1s0xd7e6321cf3831e5:0x29e1ee307fac3e3d!8m2!3d35.6982965!4d-0.5949922?hl=FR"
        >انظر الطريق
      </a>
    </div>
    <div class="overture">
      <h6>: أوقات العمل</h6>
      <span>7:30 - 22:00 : من السبت إلى الخميس</span>
    </div>
    <div class="insta">
      <h6>: تابعنا</h6>
      <Insta />
    </div>
  </footer>
</template>

<script>
export default {
  name: "app",

  data() {
    return {
      show: false,
      isActive: false,
      language: "fr",
      displayed: "Petit Déjeuner",
      categories: [
        { fr: "Petit Déjeuner", ar: "فطور الصباح", active: true },
        { fr: "Boissons", ar: "مشروبات", active: false },
        { fr: "Patesserie", ar: "حلويات", active: false },
        { fr: "Pizza", ar: "بيتزا", active: false },
        { fr: "Hamburger & Tacos", ar: "برغر و تاكوس", active: false },
        { fr: "Sandwich", ar: "ساندويتش", active: false },
      ],
    };
  },
  methods: {
    change(categorie, target) {
      if (this.language === "fr") {
        this.displayed = categorie.fr;
        this.categories.forEach((cat) => {
          if (cat.fr === target.innerText) cat.active = true;
          else cat.active = false;
        });
      } else if (this.language === "ar") {
        this.displayed = categorie.ar;
        this.categories.forEach((cat) => {
          if (cat.ar === target.innerText) cat.active = true;
          else cat.active = false;
        });
      }
    },
    setLanguage(target) {
      if (target.innerText === "Français") this.language = "fr";
      else this.language = "ar";
      this.show = true;
    },
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Lora:ital,wght@0,500;0,600;1,400&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Cairo&display=swap");
body {
  max-width: 500px;
  margin: 0 auto;
  background-color: #fafafa;
  font-family: "Inter", "Cairo", -apple-system, BlinkMacSystemFont, "Segoe UI",
    Roboto, Oxygen, Ubuntu, Cantarell, "Fira Sans", "Droid Sans",
    "Helvetica Neue", sans-serif;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  #app {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
  }
}
header {
  display: flex;
  justify-content: center;
  background-color: #0a7e8b;
  padding: 15px;
}

.language {
  flex-grow: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 70vh;
  ul {
    padding: 0;
    list-style: none;
    li {
      background-color: white;
      padding: 8px 45px;
      font-size: 14px;
      font-weight: 500;
      border-radius: 100px;
      white-space: nowrap;
      box-shadow: 1px 1px 5px rgba(0, 0, 0, 0.25);
      color: #a0a0a0;
      text-align: center;
      &:last-of-type {
        margin-top: 20px;
      }
      &:active {
        color: #fff081;
        background-color: #0a7e8b;
      }
    }
  }
}
.itinéraire {
  color: #fafafa;
  font-weight: bold;
  letter-spacing: 0.7px;
  text-transform: capitalize;
}
main {
  .categories {
    list-style: none;
    display: flex;
    gap: 10px;
    padding: 3px 20px;
    overflow-x: auto;
    li {
      background-color: white;
      padding: 8px 20px;
      font-size: 14px;
      font-weight: 500;
      border-radius: 100px;
      white-space: nowrap;
      box-shadow: 1px 1px 5px rgba(0, 0, 0, 0.25);
      color: #a0a0a0;
      box-sizing: border-box;
      text-align: center;
    }
    .active {
      color: #fff081;
      background-color: #0a7e8b;
    }
    -ms-overflow-style: none; /* IE and Edge */
    scrollbar-width: none; /* Firefox */
    /* Hide scrollbar for Chrome, Safari and Opera */
    &::-webkit-scrollbar {
      display: none;
    }
  }
}
.ar {
  direction: rtl;
  .pizza {
    img {
      margin-left: 15px;
      margin-right: 0px;
    }
    .info {
      .np {
        .price {
          padding-left: 15px;
          padding-right: 0px;
        }
      }
    }
  }
}
footer {
  margin-top: auto;
  background-color: #0a7e8b;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px 0;
  gap: 20px;
  span {
    color: white;
  }
  h6 {
    color: #fafafa;
    margin: 0 0 7px 0;
    font-size: 18px;
  }
  .overture {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .insta {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}
</style>
