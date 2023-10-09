<template>
  <div class="nav-menu" :class="{ 'nav-down-box-shadow': isScrolled }">
    <div class="logo">
      <a href="/">
        <img src="../assets/img/logo-white.png" alt="logo" width="110" />
      </a>
    </div>

    <!-- Move the hamburger menu here -->
    <div class="hamburger-menu" @click="showMenu">
      <img src="../assets/img/hamburger.svg" alt="hamburger" width="60" />
    </div>

    <div class="nav-content" :class="this.showMobileMenu ? 'open-menu' : 'closed-menu'">
      <ul class="nav-items">
        <li @click="setActiveNavItem"><a href="#" class="active">Home</a></li>
        <li @click="setActiveNavItem"><a href="#about_us">Über uns</a></li>
        <li @click="setActiveNavItem"><a href="#our_project">Projekt</a></li>
      </ul>
    </div>
  </div>
</template>
  
<style lang="scss" scoped>
.nav-menu {
  display: flex;
  justify-content: center;
  background-color: var(--color-background);
  color: var(--color-white);
  height: 120px;
  width: 100%;
  top: 0;
  left: 0;
  position: fixed;
  z-index: 2;
}

.nav-content {
  display: flex;
  justify-content: space-between;
  padding: 10px 30px;
  align-items: center;
}

div.logo {
  margin-right: 50px;
}

.nav-items {
  font-size: 1.2rem;
  font-family: 'Lato-Black', sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  list-style: none;
  margin: 0;
  padding: 0;
  margin-left: 50px;

  li {
    padding: 0 15px;
  }

  a {
    color: var(--color-white);
    text-decoration: none;

    &.active {
      border-bottom: 2px solid var(--color-text);
    }

    &:hover {
      border-bottom: 2px solid var(--color-text);
    }
  }
}

.hamburger-menu {
  display: none;
  cursor: pointer;
}

.nav-down-box-shadow {
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.4);
}

@media screen and (max-width: 768px) {
  .nav-menu {
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    margin: 0;
  }

  div.logo {
    margin: 10px 0px 0px 30px;
  }


  .hamburger-menu {
    display: block;
    margin: 0 30px;
  }

  .nav-content {
    background-color: var(--color-background);
    width: 100%;
    position: absolute;
    top: 120px;
    left: 0;
    z-index: 1;
    transition: all 0.5s ease-in-out;
    box-shadow: 0px 10px 10px rgba(0, 0, 0, 0.2);
    height: 100vh;
  }

  .closed-menu {
    display: none;

  }

  .open-menu {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: var(--color-background);
  }

  .nav-items {
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin: 0;
    padding: 0;
    margin-top: 50px;

    li {
      padding: 18px 0;
    }
  }


}
</style>
  
<script>
export default {
  data() {
    return {
      showMobileMenu: false,
      isScrolled: false,// Add a flag to track if the page is scrolled
      clickedNavItem: false
    };
  },
  methods: {
    showMenu() {
      this.showMobileMenu = !this.showMobileMenu;
    },
    hideMenu() {
      this.showMobileMenu = false;
    },
    setActiveNavItem(event) {
      this.clickedNavItem = true;

      const navItems = document.querySelectorAll('.nav-items a');
      navItems.forEach((item) => {
        item.classList.remove('active');
      });

      event.target.classList.add('active');

      // Hide the mobile menu when an item is clicked (in mobile view)
      if (this.showMobileMenu) {
        this.hideMenu();
      }

      // Set the flag to false after 1 second
      setTimeout(() => {
        this.clickedNavItem = false;
      }, 1000);
    },

    handleScroll() {
      this.isScrolled = window.scrollY > 10;

      if (!this.clickedNavItem) {
        this.addActiveClassOnScroll();
      }
    },

    addActiveClassOnScroll() {
      const navItems = document.querySelectorAll('.nav-items a');
      const sections = document.querySelectorAll('section');
      const scrollPosition = window.scrollY || document.documentElement.scrollTop || document.body.scrollTop || 0;

      sections.forEach((section, index) => {
        if (scrollPosition >= section.offsetTop - 100) {
          navItems.forEach((item) => {
            item.classList.remove('active');
          });

          navItems[index].classList.add('active');
        }
      });
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
  }
};
</script>