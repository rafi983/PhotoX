<template>
  <div>
    <header :style="headerStyle">
      <nav class="navbar navbar-expand-lg fixed-top nav-menu" :class="{ 'custom-navbar': isCompactNav }">
        <a href="#" class="navbar-brand text-light text-uppercase">
          <span class="h2 font-weight-bold">photo</span><span class="h1">X</span>
        </a>
        <button class="navbar-toggler nav-button" type="button" @click="toggleMenu" :class="{ change: mobileMenuOpen }">
          <div class="bg-light line1"></div>
          <div class="bg-light line2"></div>
          <div class="bg-light line3"></div>
        </button>
        <div
          class="mobile-collapse justify-content-end text-uppercase font-weight-bold"
          :class="{ show: mobileMenuOpen }"
        >
          <ul class="navbar-nav">
            <li v-for="item in navItems" :key="item.label" class="nav-item" @click="mobileMenuOpen = false">
              <a
                :href="item.href"
                class="nav-link m-2 menu-item"
                :class="{ 'nav-active': item.label === 'Home' }"
              >
                {{ item.label }}
              </a>
            </li>
          </ul>
        </div>
      </nav>

      <div class="text-light text-md-right text-center banner">
        <h1 class="display-4 banner-heading">
          Welcome to <span class="text-uppercase">photo</span><span class="display-3">X</span>
        </h1>
        <p class="lead banner-par">Lorem ipsum dolor sit amet consectetur adipisicing.</p>
      </div>
    </header>

    <section id="mission" class="p-5 mission">
      <div class="container-fluid">
        <div class="row text-white text-center">
          <div class="col m-4">
            <h1 class="display-4 mb-4">Our Mission</h1>
            <div class="underline mb-4"></div>
            <p class="lead">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium inventore, sint quisquam fugiat
              pariatur culpa officia. Eveniet omnis quia tempora.
            </p>
          </div>
        </div>

        <div class="row my-5">
          <div v-for="item in missionCards" :key="item.title" class="col-md-4 text-center">
            <i :class="item.icon" class="fa-5x text-danger mb-4"></i>
            <h1 class="text-white mb-3">{{ item.title }}</h1>
            <p class="text-muted">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Ea hic perferendis dolor vitae sed, quae
              officiis exercitationem quaerat? Fugit excepturi exercitationem inventore, repellendus architecto illum!
            </p>
          </div>
        </div>
      </div>

      <div class="container">
        <div class="row align-items-center">
          <div class="col-lg-5 text-center">
            <img :src="asset('camera.png')" width="350" class="img-fluid camera-img" :class="{ fromLeft: missionVisible }">
          </div>
          <div class="col-lg-7 text-white text-lg-right text-center mission-text" :class="{ fromRight: missionVisible }">
            <h1>We know what we do</h1>
            <p class="lead">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Eveniet tempora itaque obcaecati voluptas?
              Perferendis voluptate accusantium eum sit deleniti harum, assumenda vitae! Cupiditate eos iusto ab
              rerum, voluptatum minima sed?
            </p>
          </div>
        </div>
      </div>
    </section>

    <section id="collection" class="bg-secondary py-4">
      <div class="container-fluid">
        <div class="row text-white text-center">
          <div class="col m-4">
            <h1 class="display-4 mb-4">Collection</h1>
            <div class="underline mb-4"></div>
            <p class="lead">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium inventore, sint quisquam fugiat
              pariatur culpa officia. Eveniet omnis quia tempora.
            </p>
          </div>
        </div>

        <div class="row">
          <div v-for="item in collection" :key="item.title" class="col-lg-4 col-sm-6 my-5">
            <div class="card border-0 card-shadow">
              <img :src="asset(item.image)" class="card-img" :alt="item.title">
              <div class="card-img-overlay">
                <h5 class="text-white text-uppercase font-weight-bold p-2 heading">{{ item.title }}</h5>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="gallery" class="py-5">
      <div class="container-fluid">
        <div class="row text-muted text-center">
          <div class="col m-4">
            <h1 class="display-4 mb-4">Gallery</h1>
            <div class="underline-dark mb-4"></div>
            <p class="lead">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium inventore, sint quisquam fugiat
              pariatur culpa officia. Eveniet omnis quia tempora.
            </p>
          </div>
        </div>

        <ul class="list-inline text-center text-uppercase font-weight-bold my-4">
          <li
            v-for="filter in filters"
            :key="filter"
            class="list-inline-item gallery-list-item"
            :class="{ 'active-item': selectedFilter === filter }"
            @click="selectedFilter = filter"
          >
            {{ filter }}
            <span v-if="filter !== 'pro'" class="mx-md-5 mx-3 text-muted">/</span>
          </li>
        </ul>

        <div class="container-fluid">
          <div class="d-flex flex-wrap justify-content-center">
            <div v-for="item in visibleGallery" :key="item.image" class="filter px-1 py-1">
              <img :src="asset(item.image)" width="300" :alt="item.type + ' sample'">
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="customers" class="p-5 customers">
      <div class="container-fluid">
        <div class="row text-white text-center">
          <div class="col m-4">
            <h1 class="display-4 mb-4">Happy Customers</h1>
            <div class="underline mb-4"></div>
            <p class="lead">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium inventore, sint quisquam fugiat
              pariatur culpa officia. Eveniet omnis quia tempora.
            </p>
          </div>
        </div>

        <div class="row">
          <div class="col-md-6 mx-auto">
            <div class="text-center">
              <img :src="asset(activeCustomer.image)" class="img-fluid rounded-circle m-5" width="150" :alt="activeCustomer.name">
              <blockquote class="blockquote text-white">
                <p class="mb-5">{{ activeCustomer.quote }}</p>
              </blockquote>
              <h5 class="text-light text-uppercase font-weight-bold mb-3">{{ activeCustomer.name }}</h5>
              <ul class="list-inline mb-5">
                <li v-for="star in 5" :key="star" class="list-inline-item">
                  <i class="fas fa-star text-warning"></i>
                </li>
              </ul>
              <div>
                <button
                  v-for="(customer, index) in customers"
                  :key="customer.name"
                  class="customer-dot"
                  :class="{ active: index === activeCustomerIndex }"
                  @click="activeCustomerIndex = index"
                  :aria-label="`Show review ${index + 1}`"
                ></button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="pricing" class="bg-light text-center p-5">
      <div class="container-fluid">
        <div class="row text-muted text-center">
          <div class="col m-4">
            <h1 class="display-4 mb-4">Join Us</h1>
            <div class="underline-dark mb-4"></div>
            <p class="lead">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium inventore, sint quisquam fugiat
              pariatur culpa officia. Eveniet omnis quia tempora.
            </p>
          </div>
        </div>

        <div class="row align-items-center">
          <div
            v-for="(plan, index) in pricingPlans"
            :key="plan.title"
            class="col-lg-4"
          >
            <div
              class="card text-light py-4 my-4 mx-auto pricing-card"
              :class="[plan.cardClass, pricingAnimation(index)]"
              :style="pricingCardStyle()"
            >
              <div class="card-body">
                <h5 class="text-uppercase font-weight-bold mb-5">{{ plan.title }}</h5>
                <h1 class="display-4"><i class="fas fa-dollar-sign"></i> {{ plan.price }}</h1>
                <ul class="list-unstyled">
                  <li v-for="feature in plan.features" :key="feature" class="font-weight-bold py-3 card-list-item">{{ feature }}</li>
                </ul>
                <a href="#" class="btn p-2 text-uppercase font-weight-bold price-card-button text-light">sign-up!</a>
              </div>
            </div>
          </div>
        </div>

        <div class="my-5">
          <h2 class="text-muted mb-4">Thanks for being with us!</h2>
          <i class="fas fa-coffee fa-3x"></i>
        </div>
      </div>
    </section>

    <section id="contact" class="contact p-5" :style="contactStyle">
      <div class="container-fluid">
        <div class="row">
          <div class="col-lg-5 pb-4">
            <h3 class="display-4 mb-5 text-white">Get In Touch</h3>
            <form class="contact-form" @submit.prevent>
              <div class="form-group py-4">
                <input id="name" type="text" class="form-control my-2 p-2 input" placeholder="Name">
                <label for="name" class="label">Name</label>
              </div>
              <div class="form-group py-4">
                <input id="email" type="email" class="form-control my-2 p-2 input" placeholder="Email Address">
                <label for="email" class="label">Email Address</label>
              </div>
              <div class="form-group py-4 my-4">
                <input id="check" type="checkbox" checked>
                <label for="check" class="text-white">Send Announcements</label>
              </div>
              <button type="submit" class="btn btn-block p-2 font-weight-bold text-uppercase submit-button">
                Subscribe
              </button>
            </form>
          </div>
        </div>
      </div>
    </section>

    <footer class="bg-dark px-5">
      <div class="container-fluid">
        <div class="row text-light py-4">
          <div class="col-lg-4 col-sm-6">
            <h5 class="pb-3">About Us</h5>
            <p class="small">
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ipsam nobis dicta molestiae id laboriosam
              natus repudiandae, ducimus illum veritatis perspiciatis possimus, at facere debitis accusantium?
            </p>
          </div>

          <div class="col-lg-2 col-sm-6">
            <h5 class="pb-3">Visit Us</h5>
            <ul class="list-unstyled">
              <li v-for="item in navItems" :key="`footer-${item.label}`">
                <a :href="item.href" class="footer-link">{{ item.label }}</a>
              </li>
            </ul>
          </div>

          <div class="col-lg-2 col-sm-6">
            <h5 class="pb-3">Need Help?</h5>
            <ul class="list-unstyled">
              <li><a href="#" class="footer-link text-uppercase">Customer Service</a></li>
              <li><a href="#" class="footer-link text-uppercase">Online Chat</a></li>
              <li><a href="#" class="footer-link text-uppercase">Support</a></li>
              <li><a href="#" class="text-info">photox@email.com</a></li>
            </ul>
          </div>

          <div class="col-lg-4 col-sm-6">
            <h5 class="pb-3">Stay Connected</h5>
            <p class="small">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Itaque accusamus dolores iste praesentium
              assumenda est quia accusantium corrupti ipsam inventore.
            </p>
            <form class="mb-3" @submit.prevent>
              <div class="input-group">
                <input type="text" class="form-control" placeholder="Email Address">
                <div class="input-group-append">
                  <button type="button" class="btn bg-danger text-white text-uppercase font-weight-bold">Sign Up</button>
                </div>
              </div>
            </form>
            <ul class="list-inline">
              <li class="list-inline-item"><i class="fab fa-facebook-square fa-2x text-primary"></i></li>
              <li class="list-inline-item"><i class="fab fa-google-plus fa-2x text-danger"></i></li>
              <li class="list-inline-item"><i class="fab fa-instagram fa-2x text-danger"></i></li>
              <li class="list-inline-item"><i class="fab fa-twitter fa-2x text-info"></i></li>
              <li class="list-inline-item"><i class="fab fa-youtube fa-2x text-danger"></i></li>
            </ul>
          </div>
        </div>

        <div class="row">
          <div class="col text-center text-light border-top pt-3">
            <p>&copy; 2018 Copyright, All Rights Reserved</p>
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      mobileMenuOpen: false,
      isCompactNav: false,
      missionVisible: false,
      pricingVisible: false,
      selectedFilter: 'all',
      activeCustomerIndex: 0,
      navItems: [
        { label: 'Home', href: '#' },
        { label: 'Mission', href: '#mission' },
        { label: 'Collection', href: '#collection' },
        { label: 'Gallery', href: '#gallery' },
        { label: 'Customers', href: '#customers' },
        { label: 'Pricing', href: '#pricing' },
        { label: 'Contact', href: '#contact' }
      ],
      filters: ['all', 'new', 'free', 'pro'],
      missionCards: [
        { title: 'Creativity', icon: 'fas fa-cogs' },
        { title: 'Quality', icon: 'far fa-thumbs-up' },
        { title: 'Experience', icon: 'far fa-handshake' }
      ],
      collection: [
        { title: 'Nature Photography', image: 'nature.jpeg' },
        { title: 'Wedding Photography', image: 'wedding.jpeg' },
        { title: 'Party Photography', image: 'party.jpeg' },
        { title: 'Business Photography', image: 'business.jpeg' },
        { title: 'Fashion Photography', image: 'fashion.jpeg' },
        { title: 'Family Photography', image: 'family.jpeg' }
      ],
      gallery: [
        { type: 'new', image: 'img1.jpeg' },
        { type: 'free', image: 'img2.jpeg' },
        { type: 'pro', image: 'img3.jpeg' },
        { type: 'new', image: 'img4.jpeg' },
        { type: 'pro', image: 'img5.jpeg' },
        { type: 'free', image: 'img6.jpeg' },
        { type: 'pro', image: 'img7.jpeg' },
        { type: 'free', image: 'img8.jpeg' },
        { type: 'new', image: 'img9.jpeg' },
        { type: 'pro', image: 'img10.jpeg' },
        { type: 'free', image: 'img11.jpeg' },
        { type: 'pro', image: 'img12.jpeg' },
        { type: 'new', image: 'img13.jpeg' },
        { type: 'free', image: 'img14.jpeg' },
        { type: 'new', image: 'img15.jpeg' },
        { type: 'pro', image: 'img16.jpeg' }
      ],
      customers: [
        {
          name: 'Monica',
          image: 'customer1.jpeg',
          quote: 'Lorem, ipsum dolor sit amet consectetur adipisicing elit. Eum earum fuga natus veritatis minima voluptatibus? Quae consequuntur beatae repudiandae aut!'
        },
        {
          name: 'Johnathan',
          image: 'customer2.jpeg',
          quote: 'Lorem, ipsum dolor sit amet consectetur adipisicing elit. Eum earum fuga natus veritatis minima voluptatibus? Quae consequuntur beatae repudiandae aut!'
        },
        {
          name: 'Helen',
          image: 'customer3.jpeg',
          quote: 'Lorem, ipsum dolor sit amet consectetur adipisicing elit. Eum earum fuga natus veritatis minima voluptatibus? Quae consequuntur beatae repudiandae aut!'
        }
      ],
      pricingPlans: [
        {
          title: 'Monthly Membership',
          price: 19,
          cardClass: 'card-1',
          features: ['Photoshop', 'After Effects', 'Graphic Design', 'Video Montage']
        },
        {
          title: 'Unlimited Access',
          price: 499,
          cardClass: 'card-2',
          features: ['Photoshop', 'After Effects', 'Graphic Design', 'Video Montage', 'Clip Making']
        },
        {
          title: 'Annual Membership',
          price: 199,
          cardClass: 'card-3',
          features: ['Photoshop', 'After Effects', 'Graphic Design', 'Video Montage']
        }
      ]
    }
  },
  computed: {
    visibleGallery() {
      if (this.selectedFilter === 'all') {
        return this.gallery
      }
      return this.gallery.filter((item) => item.type === this.selectedFilter)
    },
    activeCustomer() {
      return this.customers[this.activeCustomerIndex]
    },
    headerStyle() {
      return {
        backgroundImage: `linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.5)), url('${this.asset('header-img.jpeg')}')`,
        backgroundRepeat: 'no-repeat',
        backgroundPosition: 'center center',
        backgroundSize: 'cover'
      }
    },
    contactStyle() {
      return {
        backgroundImage: `linear-gradient(105deg, rgba(21, 31, 32, 1) 0%, rgba(21, 31, 32, 0.95) 50%, transparent 50%), url('${this.asset('form-img.jpeg')}')`,
        backgroundRepeat: 'no-repeat',
        backgroundPosition: 'center center',
        backgroundSize: 'cover'
      }
    }
  },
  mounted() {
    window.addEventListener('scroll', this.onScroll)
    this.onScroll()
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.onScroll)
  },
  methods: {
    asset(name) {
      return `${process.env.BASE_URL}images/${name}`
    },
    pricingCardStyle() {
      return {
        backgroundImage: `linear-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.5)), url('${this.asset('pricing-card-bg.jpeg')}')`,
        backgroundRepeat: 'no-repeat',
        backgroundPosition: 'center center',
        backgroundSize: 'cover'
      }
    },
    toggleMenu() {
      this.mobileMenuOpen = !this.mobileMenuOpen
    },
    onScroll() {
      const position = window.scrollY
      this.isCompactNav = position >= 200
      this.missionVisible = position >= 650
      this.pricingVisible = position >= 2600
    },
    pricingAnimation(index) {
      if (!this.pricingVisible) {
        return ''
      }
      if (index === 0) {
        return 'moveFromLeft'
      }
      if (index === 1) {
        return 'moveFromBottom'
      }
      return 'moveFromRight'
    }
  }
}
</script>

<style scoped>
:global(body) {
  font-family: 'Montserrat', sans-serif;
}

header {
  height: 100vh;
  background: linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.5)),
    url('/images/header-img.jpeg') no-repeat center center / cover;
}

.nav-menu {
  background: linear-gradient(rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0.5));
  padding: 30px;
  transition: all 0.7s;
}

.mobile-collapse {
  display: flex;
}

.menu-item {
  font-size: 13px;
  letter-spacing: 1px;
  color: #eee;
  transition: color 0.5s;
}

.menu-item:hover {
  color: #70aed2;
}

.nav-active {
  color: #70aed2;
}

.line1,
.line2,
.line3 {
  width: 23px;
  height: 3px;
  margin: 5px;
  transition: all 0.4s;
}

.change .line1 {
  transform: rotate(-45deg) translate(-5px, 6px);
}

.change .line2 {
  opacity: 0;
}

.change .line3 {
  transform: rotate(45deg) translate(-5px, -6px);
}

.custom-navbar {
  padding: 5px 30px;
  background: linear-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.7));
}

.banner {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 80%;
}

.banner-heading {
  animation-name: anim;
  animation-duration: 2s;
}

.banner-par {
  animation-name: anim;
  animation-duration: 2s;
  animation-delay: 0.5s;
  animation-fill-mode: backwards;
}

@keyframes anim {
  0% {
    transform: translateX(-100px);
    opacity: 0;
  }
  100% {
    transform: translateX(0);
    opacity: 1;
  }
}

.mission {
  background: #151f20;
}

.underline {
  width: 150px;
  border: 3px solid #eee;
  margin: auto;
}

.fromLeft {
  animation-name: fromLeft;
  animation-duration: 3s;
}

.fromRight {
  animation-name: fromRight;
  animation-duration: 3s;
}

@keyframes fromLeft {
  0% {
    transform: translateX(-120px);
    opacity: 0;
  }
  100% {
    transform: translateX(0);
    opacity: 1;
  }
}

@keyframes fromRight {
  0% {
    transform: translateX(30px);
    opacity: 0;
  }
  100% {
    transform: translateX(0);
    opacity: 1;
  }
}

.card-shadow {
  box-shadow: 5px 8px 20px #444;
}

.heading {
  position: absolute;
  top: 70%;
  right: 0;
  font-size: 14px;
  letter-spacing: 1px;
  background: #222;
  width: 70%;
  cursor: pointer;
  opacity: 0.7;
  transition: all 0.5s;
}

.heading:hover {
  opacity: 1;
}

.underline-dark {
  width: 150px;
  border: 3px solid #888;
  margin: auto;
}

.gallery-list-item {
  color: #777;
  cursor: pointer;
  user-select: none;
}

.active-item {
  color: #70aed2;
}

.customers {
  background: #151f20;
}

.customer-dot {
  width: 12px;
  height: 12px;
  margin: 0 4px;
  border-radius: 50%;
  border: none;
  background: #6c757d;
}

.customer-dot.active {
  background: #fff;
}

.pricing-card,
.card-1,
.card-2,
.card-3 {
  background: linear-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.5));
  box-shadow: 7px 18px 50px #555;
  max-width: 400px;
}

.card-list-item {
  border-bottom: 1px groove #eee;
  width: 55%;
  margin: auto;
}

.price-card-button {
  background: #f5593d;
  width: 130px;
  border-radius: 25px;
  box-shadow: 5px 8px 18px #000;
  transition: all 0.2s;
}

.price-card-button:hover {
  background: #f9793d;
  transform: translateY(-2px);
}

.moveFromLeft {
  animation-name: moveFromLeft;
  animation-duration: 2s;
}

.moveFromRight {
  animation-name: moveFromRight;
  animation-duration: 2s;
}

.moveFromBottom {
  animation-name: moveFromBottom;
  animation-duration: 2s;
}

@keyframes moveFromLeft {
  0% {
    transform: translateX(-100px);
    opacity: 0;
  }
  100% {
    transform: translateX(0);
    opacity: 1;
  }
}

@keyframes moveFromRight {
  0% {
    transform: translateX(100px);
    opacity: 0;
  }
  100% {
    transform: translateX(0);
    opacity: 1;
  }
}

@keyframes moveFromBottom {
  0% {
    transform: translateY(100px);
    opacity: 0;
  }
  100% {
    transform: translateY(0);
    opacity: 1;
  }
}

.contact {
  background: linear-gradient(105deg, rgba(21, 31, 32, 1) 0%, rgba(21, 31, 32, 0.95) 50%, transparent 50%),
    url('/images/form-img.jpeg') no-repeat center center / cover;
}

.input {
  background: transparent;
  border-color: transparent;
  border-bottom: 2px solid #ccc;
  border-radius: 0;
  transition: all 0.8s;
  color: #fff;
}

.input:focus {
  background: transparent;
  border-color: transparent;
  box-shadow: none;
  color: #fff;
  border-bottom: 2px solid #f5593d;
}

.submit-button {
  background: #f5593d;
  color: #eee;
  transition: all 0.3s;
}

.submit-button:hover {
  background: #f9793d;
  transform: translateY(-3px);
}

.label {
  color: #777;
  display: block;
  margin-top: -70px;
  margin-left: 4px;
  font-size: 13px;
  transition: all 0.3s;
}

.input:placeholder-shown + .label {
  transform: translate(20px, 20px);
  opacity: 0;
  visibility: hidden;
}

.footer-link {
  color: #eee;
  font-size: 13px;
  transition: all 0.3s;
}

.footer-link:hover {
  color: #70aed2;
  text-decoration: none;
}

@media (max-width: 992px) {
  .mobile-collapse {
    display: none;
    width: 100%;
  }

  .mobile-collapse.show {
    display: block;
  }

  .contact {
    background: linear-gradient(rgba(21, 31, 32, 1), rgba(21, 31, 32, 0.95));
  }

  .contact-form {
    width: 80%;
    margin: auto;
  }
}
</style>
