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
        <ul class="list grid-row">
          <li
            v-for="(item, index) in items"
            :key="index"
            class="item grid-col"
          >
            <ProductItem
              :data="item"
            />
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      items: [
        {
          title: 'Наименование товара',
          description: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
          image: '/images/product.jpg',
          price: '10 000'
        }
      ]
    }
  },

  methods: {
    addItem (product) {
      this.items.push(product)
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
