<template>
  <header id="navbar" class="site-header">
    <div class="grid container">
      <div class="grid_column nav-brand" col="s6,l2">
        <nuxt-link to="/">
          <img src="~assets/img/aces-logo.png" class="site-logo" alt="" />
          <span> ACES </span>
        </nuxt-link>
      </div>

      <div class="grid_column main-nav" col="s3,l8">
        <headerMainNav :is-active="navActive" @toggle="navToggler" />
        <img
          src="~assets/img/menu-bar.svg"
          class="toggler"
          alt=""
          @click="navToggler"
        />
      </div>

      <div class="grid_column second-nav" col="s3,l2">
        <ul class="second-nav">
          <li class="second-nav-item">
            <img src="~assets/img/icon-instagram.svg" alt="" />
          </li>
        </ul>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'HeaderComp',
  data() {
    return {
      navActive: false,
      sideNav: [
        {
          title: 'Getting Started',
          url: '/documentation'
        },
        {
          title: 'Typography',
          url: '/documentation/typography'
        }
      ]
    }
  },
  methods: {
    navToggler() {
      this.navActive = !this.navActive
    }
  }
}
</script>
<style lang="scss" scoped>
.site-header {
  display: flex;
  position: fixed;
  z-index: 5;

  top: 0;
  left: 0;
  width: 100%;
  height: 70px;

  background-color: #fff;
  color: #151515;
  box-shadow: 0 5px 5px rgba($color: #000000, $alpha: 0.1);

  flex-direction: row;
  align-items: center;

  @media #{$md} {
    height: 80px;
  }
}

.nav-brand {
  display: flex;
  align-items: center;
  justify-content: center;

  font-size: 1.25em;
  font-family: Poppins-medium, sans-serif;

  .site-logo {
    width: 100%;
    max-width: 30px;
    margin-right: 0.5em;
  }

  span {
    letter-spacing: 2px;
    color: #151515;
  }

  @media #{$large} {
    justify-content: flex-start;
    align-items: center;
  }
}

.toggler {
  cursor: pointer;

  @media #{$large} {
    display: none;
  }
}

.nav {
  display: flex;
  align-items: center;
}

.main-nav {
  display: flex;
  justify-content: flex-end;

  img {
    max-width: 1.5em;
  }
}

.second-nav {
  @extend .nav;

  padding: 0;
  margin: 0;

  display: flex;
  flex-direction: row;
  align-items: center;
  order: -1;

  gap: 1em;

  &-item {
    padding: 0;
    margin: 0;

    display: flex;
    align-items: center;

    img {
      max-width: 1.5em;
    }
  }

  @media #{$large} {
    order: 0;

    justify-content: flex-end;
  }
}
</style>
