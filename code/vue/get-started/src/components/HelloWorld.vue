<template>
  <div class="hello">
    <div class="d-flex">
      <h1>{{ msg }}</h1>
      <div class="cart-item">
        <img src="../assets/cart.png" alt="cart" />
        <span class="count">{{ count }}</span>
      </div>
    </div>
    <div class="wrapper">
      <div class="row">
        <div class="column" v-for="product in products" :key="product.id">
          <div class="card">
            <div class="card-body">
              <div class="card-image">
                <img :alt="product.value" :src="product.image" />
                <figcaption>
                  <button class="cart-button" @click="addToCart">
                    Add to Cart
                  </button>
                </figcaption>
              </div>
              <h3 class="card-title">{{ product.value }}</h3>
              <p class="card-price">{{ product.price }}</p>

              <fieldset>
                <img class="star-item" src="../assets/star.svg" />
                <img class="star-item" src="../assets/star.svg" />
                <img class="star-item" src="../assets/star.svg" />
                <img class="star-item" src="../assets/star.svg" />
                <img class="star-item faded" src="../assets/star.svg" />
              </fieldset>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "HelloWorld",
    props: {
      msg: String,
    },
    data() {
      return {
        count: 0,
        products: [
          {
            value: "Ultrafine Merino T-Shirt (Black)",
            price: "$80.00",
            id: 1,
            image: require("../assets/shirt-1.jpg"),
          },
          {
            value: "Ultrafine Merino T-Shirt (Grey)",
            price: "$80.00",
            id: 2,
            image: require("../assets/shirt-2.jpg"),
          },
          {
            value: "Ultrafine Merino T-Shirt (Orange)",
            price: "$80.00",
            id: 3,
            image: require("../assets/shirt-3.jpg"),
          },
        ],
      };
    },

    methods: {
      addToCart() {
        this.count++;
      },
    },
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
  $primary: #2052a8;
  h1 {
    margin: 0;
  }
  h3 {
    margin: 40px 0 0;
  }
  .d-flex {
    display: flex;
    justify-content: center;
    align-content: center;
    margin-bottom: 20px;
  }
  a {
    color: #42b983;
  }

  .cart-item {
    position: relative;
    width: 40px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin-inline-start: 0.67em;

    img {
      width: 30px;
    }

    .count {
      background-color: $primary;
      width: 20px;
      height: 20px;
      position: absolute;
      top: -1px;
      right: -3px;
      border-radius: 50%;
      text-align: center;
      line-height: 21px;
      color: #fff;
      font-size: 12px;
      font-weight: 700;
      text-align: center;
    }
  }

  body {
    margin: 0;
    padding: 0;
    background-color: white;
    font-family: "Roboto", sans-serif;
  }

  .wrapper {
    width: auto;
    max-width: 1000px;
    padding: 0 15px;
    margin: 0 auto;
  }

  h1 {
    text-align: center;
  }

  h3 {
    margin-bottom: 0rem;
  }

  .card-price {
    margin-top: 0.5rem;
  }

  .row {
    display: flex;
    flex-wrap: wrap;
    margin-right: -15px;
    margin-left: -15px;
  }

  .column {
    padding: 0.75rem 15px;
    flex-basis: 0;
    flex-grow: 1;
    max-width: 100%;
  }

  .card {
    border-radius: 10px;
    box-shadow: 0 4px 20px 1px rgba(0, 0, 0, 0.06),
      0 1px 4px rgba(0, 0, 0, 0.08);
    border: 0;
    text-align: center;
    &-body {
      flex: 1 1 auto;
      padding: 1.25rem;
    }

    &-image {
      position: relative;
      figcaption {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        transition: transform 0.35s;
        transition: background-color 0.35s;
        display: flex;
        align-items: center;
        justify-content: center;

        button {
          opacity: 0;
          transition: opacity 0.35s, transform 0.35s;
          transform: scale(0);
          background-image: linear-gradient(
            to bottom,
            #5c95c5 0%,
            #2052a8 100%
          );
          color: white;
          border: 0;
          font-size: 1rem;
          padding: 0.75rem 2.2rem;
          border-radius: 5px;
        }
      }
      &:hover {
        figcaption {
          background-color: rgba(255, 255, 255, 0.65);

          button {
            opacity: 1;
            transform: scale(1);
          }
        }
      }
    }
  }

  img {
    max-width: 100%;
    height: auto;
  }

  fieldset {
    border: 0;
    border-radius: 1px;
    padding: 0em 1.5em 0.9em;
  }

  .star-item {
    width: 15px;
    margin: 1px;

    &.faded {
      opacity: 0.2;
    }
  }
</style>
