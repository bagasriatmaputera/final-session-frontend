<template>

  <!-- navbar -->
  <nav class="navbar bg-dark navbar-expand-lg bg-body-tertiary fixed-top" data-bs-theme="dark">
    <div class="container-fluid">
      <a class="navbar-brand" href="#"><img src="/src/assets/Brp logo.png" alt="" height="24"> Brp Market</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mx-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="#carouselExampleCaptions">Home</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#our">Our</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#search">Search</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#product">Product</a>
          </li>
        </ul>
        <!-- side bar cart di navbar-->
        <div class="sidebar-cart">
          <!-- Toggle Button di kanan atas -->
          <button class="btn btn-outline-success" @click="toggleSidebar">
            <i class="bi bi-bag"></i>
          </button>
          <!-- Sidebar -->
          <div class="sidebar bg-dark text-white p-3" :class="{ active: sidebarOpen }">
            <h4>Cart <i class="bi bi-bag"></i></h4>
            <hr />
            <h3>List Orders</h3>
            <div class="item">
              <div class="row">
                <div v-for="(order, i) in orders" :key="i" class="item-box  mb-2">
                  <div class="text-price-item d-flex justify-content-between">
                    <span>{{ order.name }} <br> ukuran:
                      {{ order.ukuran }}
                    </span>
                    <span>{{ `Rp.${order.price}` }}</span>
                  </div>
                  <div class="btn qty">
                    <button class="btn btn-sm btn-outline-warning" @click="decreaseQty(order)">-</button>
                    x{{ order.qty }}
                    <button class="btn btn-sm btn-outline-success" @click="increaseQty(order)">+</button>
                    <button class="btn btn-sm btn-outline-danger ms-2" @click="deleteOrders(order)">Hapus</button>
                  </div>
                </div>
              </div>
            </div>
            <hr>
            <div class="mt-3">
              <strong>Total: Rp.{{ total }}</strong>
            </div>
            <hr>
            <div class="col-12 btn-payment">
              <button class="btn btn-success w-100" @click="bayar()">Payment</button>
            </div>
          </div>
          <!-- klik luar untuk tutup -->
          <div v-if="sidebarOpen" class="overlay" @click="toggleSidebar"></div>
        </div>
      </div>
    </div>
  </nav>



  <!-- carusel-top -->
  <div id="carouselExampleCaptions" class="carousel slide carousel-style">
    <div class="carousel-indicators">
      <button type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide-to="0" class="active"
        aria-current="true" aria-label="Slide 1"></button>
      <button type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide-to="1"
        aria-label="Slide 2"></button>
      <button type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide-to="2"
        aria-label="Slide 3"></button>
    </div>
    <div class="carousel-inner">
      <div class="carousel-item active">
        <img :src="this.carouselProduct[1]" class="d-block w-100" alt="..." />
        <div class="carousel-caption d-none d-md-block">
          <h5>Selamat Datang di Toko Kami!</h5>
          <p>Temukan produk terbaik dengan penawaran menarik setiap hari.</p>
        </div>
      </div>
      <div class="carousel-item">
        <img :src="this.carouselProduct[2]" class="d-block w-100" alt="..." />
        <div class="carousel-caption d-none d-md-block">
          <h5>Promo Spesial Bulan Ini!</h5>
          <p>Dapatkan diskon hingga 50% untuk produk pilihan. Jangan lewatkan kesempatan ini!</p>
        </div>
      </div>
      <div class="carousel-item">
        <img :src="this.carouselProduct[0]" class="d-block w-100" alt="..." />
        <div class="carousel-caption d-none d-md-block">
          <h5>Promo Spesial Bulan Ini!</h5>
          <p>Dapatkan diskon hingga 50% untuk produk pilihan. Jangan lewatkan kesempatan ini!</p>
        </div>
      </div>
    </div>
    <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide="prev">
      <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Previous</span>
    </button>
    <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide="next">
      <span class="carousel-control-next-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Next</span>
    </button>
  </div>

  <!-- Out Team -->

  <div class="container mt-3">
    <div class="row text-white">
      <div class="col-12 col-md-4 mb-2">
        <img width="360px" src="/src/assets/Brp logo.png" alt="">
      </div>
      <div class="col-12 col-md-8 d-flex flex-column justify-content-center">
        <h1 id="our">Our Commitment</h1>
        <p>Kami menghadirkan beragam produk pilihan yang sudah dikurasi khusus untuk Anda. Mulai dari kebutuhan harian
          hingga produk favorit yang sedang tren, semuanya tersedia dalam satu tempat. Setiap item yang kami tawarkan
          telah melalui proses seleksi agar tetap mengutamakan kualitas dan kepuasan pelanggan.</p>
        <p>Tidak hanya itu, setiap harinya kami memberikan penawaran menarik dan diskon spesial untuk Anda yang ingin
          berbelanja lebih hemat. Dengan harga bersaing dan produk yang selalu up to date, kami pastikan Anda
          mendapatkan pengalaman belanja yang menyenangkan dan memuaskan.</p>
        <p>Jadi, tunggu apa lagi? Jelajahi koleksi kami dan temukan produk favoritmu hari ini juga. Belanja jadi lebih
          mudah, praktis, dan pastinya penuh kejutan seru setiap hari hanya di toko kami!</p>
      </div>
    </div>
  </div>

  <!-- content -->
  <div class="container-fluid col-11 d-flex justify-content-center mt-3">
    <div id="search" class="row">
      <!-- Search -->
      <div class="search col-12">
        <h3 class="text-center text-white">Explore Product</h3>
        <input type="text" class="form-control mb-2" v-model="keyword" placeholder="Cari" :input="searchItem()" />
      </div>
      <div class="col-12 col-sm-6 col-md-3 mb-3" v-for="(item, index) in filterItem" :key="index">
        <div class="card card-bg">
          <a href="#" data-bs-toggle="modal" data-bs-target="#exampleModal" @click="detailBtn(item, item.id)"><img
              class="card-img-top" :src="item.photo" alt="Card image cap" /></a>
          <div id="product" class="card-body">
            <h5 class="card-title text-center">{{ item.name }}</h5>
            <p class="card-text text-center">{{ `Rp.${item.price}` }}</p>
            <button class="btn btn-bg-card col-12 mt-2" @click="addToCart(item.id, index, item); toggleSidebar">
              Add to cart
            </button>
          </div>
        </div>
      </div>
    </div>

    <!-- Modal Product Detail -->
    <!-- Modal -->
    <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog modal-dialog modal-dialog-centered">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">
              {{ detailProduct.name }}
            </h5>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
          </div>
          <div class="modal-body d-flex justify-content-center">
            <img :src="detailProduct.photo" alt="" style="height: 200px" />
            <div class="Tipe">
              <div v-for="(child, index) in childPhoto" :key="index" class="col-md-6 mb-2">
                <img :src="child" alt="image" style="height: 100px">
              </div>
            </div>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">
              Close
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- footer -->
  <footer class="bg-dark text-white pt-4 pb-2">
    <div class="container">
      <div class="row">
        <!-- Tentang Kami -->
        <div class="col-md-4 mb-3">
          <h5>Tentang Kami</h5>
          <p>Toko kami menyediakan berbagai macam produk terbaik dengan harga terjangkau. Kepuasan Anda adalah prioritas
            kami.</p>
        </div>

        <!-- Kontak -->
        <div class="col-md-4 mb-3">
          <h5>Kontak</h5>
          <ul class="list-unstyled">
            <li><i class="bi bi-envelope"></i> email@brpmail.com</li>
            <li><i class="bi bi-phone"></i> +62 812-3456-7890</li>
            <li><i class="bi bi-geo-alt"></i> Jl. Contoh No. 123, Jakarta</li>
          </ul>
        </div>

        <!-- Ikuti Kami -->
        <div class="col-md-4 mb-3">
          <h5>Ikuti Kami</h5>
          <a href="#" class="text-white me-2"><i class="bi bi-facebook"></i></a>
          <a href="#" class="text-white me-2"><i class="bi bi-instagram"></i></a>
          <a href="#" class="text-white me-2"><i class="bi bi-twitter"></i></a>
        </div>
      </div>

      <hr class="border-light" />
      <p class="text-center mb-0">&copy; 2025 Brp Market. All rights reserved.</p>
    </div>
  </footer>
</template>
<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import axios from "axios";
export default {
  data() {
    return {
      sidebarOpen: false,
      products: [],
      galery: [],
      keyword: "",
      filterItem: [],
      // ukurans: [
      //   { value: "s", name: "S" },
      //   { value: "m", name: "M" },
      //   { value: "l", name: "L" },
      //   { value: "xl", name: "XL" },
      // ],
      // ukuran: {},
      detailProduct: '',
      productId: "",
      orders: [],
      carouselProduct: [],
      photoVarian: [],
      childItems: [],
      childPhoto: [],
      total: 0

    };
  },
  mounted() {
    this.getProduct();
  },
  methods: {
    bayar() {
      alert('Yeay')
    },
    toggleSidebar() {
      this.sidebarOpen = !this.sidebarOpen;
    },
    getProduct() {
      axios
        .get("https://sistemtoko.com/public/demo/product", {
          params: {
            page: 1,
            sorting: "Latest",
            categories: "all",
            search_name: "none",
          },
        })
        .then((response) => {
          // console.log(response)
          this.products = response.data.aaData;
          this.carouselProduct = this.products.map((item) => item.photo).slice(5, 8)
          //ambil childs di products
          this.childItems = this.products.map(item => item.childs).flat()
        })
        .catch(function (error) {
          console.log(error);
          alert('error network may use better network')
        });
    },
    addToCart(id, item) {
      //memfilter item menyesuaikan id (ini bentuk array)

      let items = this.filterItem.filter((item) => item.id == id)[0];
      //mengambil object (sekarang sudah jadi Object)
      let orderItem = Object.assign({}, items);
      orderItem.originalPrice = Number(parseInt(items.price.toString().replace(/\./g, ''))) // key originalPrice dibuat untuk logika perhitungan ytang dikalikan qty


      //untuk mendapatkan qty, melakukan map data indexOfArray
      let arrayIndex = this.orders.map(e => e.id).indexOf(orderItem.id)
      // console.log(arrayIndex)

      if (arrayIndex != -1) {//jika index bukan -1 maka qty akan ditambah 
        // disini ditambahkan qty lansung melalui code berikut
        this.orders[arrayIndex].qty++
        //untuk price akan di kali dengan qty
        this.orders[arrayIndex].price = this.orders[arrayIndex].originalPrice * this.orders[arrayIndex].qty
      } else {//jika -1 maka push ke array oders
        //memasukan qty kedalam object yang ada di variabel orderItem
        orderItem.qty = 1
        this.orders.push(orderItem)
      }

      let orderPrice = this.orders.map(e => Number(String(e.price).replace(/[.,]/g, match => match === ',' ? '.' : '')))
      // console.log(orderPrice)
      let priceTotal = 0

      orderPrice.forEach(order => {
        priceTotal += order
      })
      this.total = priceTotal

      // sidebarOpen when clik add to cart
      this.sidebarOpen = !this.sidebarOpen;



    },
    searchItem() {
      this.filterItem = this.products.filter((item) =>
        item.name.toLowerCase().includes(this.keyword.toLowerCase())
      );
    },
    detailBtn(item, id) {
      // console.log(item.id)
      this.productId = item.id;
      this.photoVarian = this.products.filter((v) => v.id === item.id).map((v) => v.photos)
      this.childPhoto = this.childItems.filter((o) => o.name === item.name).map((v) => v.photo)
      this.detailProduct = item;
    },
    decreaseQty(item) {
      // dapat array [0]
      let arrayIndex = this.orders.map(e => e.id).indexOf(item.id)
      // console.log(arrayIndex);

      // console.log(this.orders[arrayIndex].qty);
      if (this.orders[arrayIndex].qty > 1) {
        this.orders[arrayIndex].qty--
        this.orders[arrayIndex].price = this.orders[arrayIndex].originalPrice * this.orders[arrayIndex].qty
      } else {
        this.orders.splice(arrayIndex, 1)
      }

      let orderPrice = this.orders.map(e => e.price)
      let priceTotal = 0

      orderPrice.forEach(order => {
        priceTotal += order
      })

      this.total = priceTotal
    },
    increaseQty(item) {
      let arrayIndex = this.orders.map(e => e.id).indexOf(item.id)

      this.orders[arrayIndex].qty++
      this.orders[arrayIndex].price = this.orders[arrayIndex].originalPrice * this.orders[arrayIndex].qty

      let orderPrice = this.orders.map(e => e.price)
      let priceTotal = 0

      orderPrice.forEach(order => {
        priceTotal += order
      })

      this.total = priceTotal
    },
    deleteOrders(item) {
      let arrayIndex = this.orders.map((i) => i.id).indexOf(item.id)
      this.orders.splice(arrayIndex, 1)

      let orderPrice = this.orders.map(e => e.price)
      let priceTotal = 0

      orderPrice.forEach(order => {
        priceTotal += order
      })

      this.total = priceTotal
    },

  },
};
</script>
<style>
* {
  font-family: "Poppins", sans-serif;
  font-weight: 100;
  font-style: normal;
}

header {
  height: 80vh;
}

.sidebar {
  position: fixed;
  top: 0;
  right: -350px;
  width: 350px;
  height: 100vh;
  background-color: #343a40;
  transition: right 0.3s ease-in-out;
  z-index: 1050;
}

.sidebar.active {
  right: 0;
}

.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 1049;
}

.carousel-style {
  padding-top: 50px;
  display: flex;
  justify-content: center
}

.carousel-style img {
  height: 600px;
  object-fit: cover;
  object-position: center;
}

.card-bg {
  background-color: #EEEEEE;
}

.btn-bg-card {
  background-color: #343a40;
  color: white;
}
</style>
