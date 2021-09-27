<template>
  <div id="app">
    <div class="box container-fluid overflow-auto">
      <div class="titles">
        <h5 class="card-title">{{ msg }}</h5>
        <a title="Alle Länder" class="countryLink" href="#">Alle</a>
        <h6 class="sub-title text-muted">Lorem Ipsum Länder, Regionen, Orte</h6>
      </div>

      <div class="cardparent d-inline-flex flex-row flex-nowrap">
        <div
          v-for="(item, i) in offers"
          :key="i"
          class="card"
          style="width: 18rem"
        >
          <div class="card-body">
            <img class="card-images" :src="item.image" :alt="'Das Bild zeigt ' +item.text" />
            <div class="card-text">
              <a :href="item.link" class="destination">{{ item.text }}</a>
              <div class="price">
                <p v-if="item.price != 0">ab €{{ item.price }}</p>
                <p v-else>kein Preis vorhanden</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import OfferData from "./assets/data.json";
export default {
  name: "app",
  data() {
    return {
      msg: "Länder, Regionen, Orte",
      offers: OfferData,
    };
  },
};
</script>

<style>
@media only screen and (max-width: 600px) {
  .box {
    max-width: 100% !important;
  }
}


.box {
  max-width: 350px;
  position: relative;
}

.countryLink{
  position: absolute;
  right: 0;
  top: 0;
}

.sub-title {
  padding-left: 5px;
}

.titles {
  position: -webkit-sticky;
  position: sticky;
  left: 0;
}

.titles > h5,
.destination {
  color: #16828f;
  font-weight: bold;
}

.price {
  color: #a11a79;
}

.card-title {
  padding-left: 5px;
  margin: 0;
}

.card-text {
  padding-top: 5px;
  padding-left: 12px;
  padding-right: 12px;
  display: flex;
  justify-content: space-between;
}

.cardparent:after{
  content: "";
  position: sticky;
  right:-20px;
  width: 60px;
  height:240px;
  background: linear-gradient(to right, transparent, white);
  pointer-events: none;
}

.card-images {
  width: 100%;
  border-radius: 5% 5% 0% 0%;
}

.card-body {
  padding: 0;
}

.card {
  background: white;
  min-width: 300px;
  margin: 5px;
  border-radius: 5%;
  box-shadow: -2px 2px #d9e15f;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

a {
  color: #16828F;
}
</style>
