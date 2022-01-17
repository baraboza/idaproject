<template>
  <div class="container grid-container">
    <div class="grid-row">
      <div class="col-form grid-col">
        <ProductAdd />
      </div>
      <div class="col-list grid-col">
        <div class="sort">
          <SelectComponent />
        </div>
        <ul class="list grid-row">
          <li class="item grid-col">
            <ProductItem />
          </li>
          <li class="item grid-col">
            <ProductItem />
          </li>
          <li class="item grid-col">
            <ProductItem />
          </li>
          <li class="item grid-col">
            <ProductItem />
          </li>
          <li class="item grid-col">
            <ProductItem />
          </li>
          <li class="item grid-col">
            <ProductItem />
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {

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
</style>
