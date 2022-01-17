<template>
  <div class="container grid-container">
    <div class="grid-row">
      <div class="col-form grid-col">
        <ProductAdd
          @submit="addItem"
        />
      </div>
      <div class="col-list grid-col">
        <div class="sort">
          <SelectComponent />
        </div>

        <transition-group
          name="item"
          tag="ul"
          class="list grid-row"
        >
          <li
            v-for="(item, index) in items"
            :key="item.title"
            class="item grid-col"
          >
            <ProductItem
              :index="index"
              :data="item"
              @remove="removeItem"
            />
          </li>
        </transition-group>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      items: []
    }
  },

  mounted () {
    if (localStorage.getItem('productList')) {
      try {
        this.items = JSON.parse(localStorage.getItem('productList'))
      } catch (e) {
        localStorage.removeItem('productList')
      }
    }
  },

  methods: {
    addItem (product) {
      this.items.push(product)
      this.saveItems()
    },

    removeItem (index) {
      this.items.splice(index, 1)
      this.saveItems()
    },

    saveItems () {
      const parsed = JSON.stringify(this.items)
      localStorage.setItem('productList', parsed)
    }
  }
}
</script>

<style lang="scss" scoped>
@use "sass:math";

.container {
  margin-top: 32px;
  margin-bottom: 32px;
}

.col {
  &-form {
    width: 25%;
  }

  &-list {
    width: 75%;
  }
}

.sort {
  display: flex;
  justify-content: flex-end;
}

.item {
  margin-top: 16px;
  width: math.div(100%, 3);

  &-enter-active,
  &-leave-active {
    transition-property: opacity, transform;
    transition-duration: .5s;
  }

  &-enter,
  &-leave-to {
    opacity: 0;
    transform: translateY(30px);
  }
}

@media (max-width: 1200px) {
  .col {
    &-form {
      width: math.div(100% * 6, 16);
    }

    &-list {
      width: math.div(100% * 10, 16);
    }
  }

  .item {
    width: 50%;
  }
}

@media (max-width: 900px) {
  .container {
    margin-top: 24px;
    margin-bottom: 24px;
  }

  .col {
    &-form,
    &-list {
      width: 100%;
    }

    &-list {
      margin-top: 32px;
    }
  }
}

@media (max-width: 600px) {
  .item {
    width: 100%;
  }
}
</style>
