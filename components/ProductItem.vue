<template>
  <div class="box">
    <div class="img-box">
      <img src="/images/product.jpg" alt="Наименование товара">
    </div>
    <div class="content">
      <p class="title">Наименование товара</p>
      <p class="description">Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк</p>
      <p class="price">10 000 руб.</p>
    </div>
    <button type="button" class="button-delete">
      <img src="/images/delete.svg" alt="">
    </button>
  </div>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
@use "sass:math";

.box {
  background: #FFFEFB;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  display: flex;
  flex-direction: column;
  height: 100%;
  position: relative;

  &:hover {

    .button-delete {
      opacity: 1;
      pointer-events: auto;
    }
  }
}

.img-box {
  position: relative;
  overflow: hidden;
  border-radius: 4px 4px 0px 0px;

  &::before {
    content: '';
    display: block;
    padding-top: math.div(100% * 200, 332);
  }

  img {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}

.content {
  padding: 16px 16px 24px;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
}

.title {
  font-weight: 600;
  font-size: 20px;
  line-height: 25px;
}

.description {
  line-height: 20px;
  margin-top: 16px;
  margin-bottom: auto;
}

.price {
  margin-top: 32px;
  font-weight: 600;
  font-size: 24px;
  line-height: 30px;
}

.button-delete {
  position: absolute;
  top: -8px;
  right: -8px;
  background: #FF8484;
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 32px;
  height: 32px;
  border: none;
  opacity: 0;
  pointer-events: none;
  transition-property: opacity, transform, box-shadow;
  transition-duration: 0.3s;

  &:focus {
    opacity: 1;
    pointer-events: auto;
    outline: none;
  }

  &:focus,
  &:hover {
    transform: scale(1.1);
  }

  &:active {
    box-shadow: none;
  }
}

@media (max-width: 600px) {
  .content {
    padding-bottom: 20px;
  }

  .title {
    font-size: 18px;
    line-height: 22px;
  }

  .description {
    margin-top: 12px;
    font-size: 14px;
    line-height: 18px;
  }

  .price {
    margin-top: 16px;
    font-size: 22px;
    line-height: 26px;
  }

  .button-delete {
    opacity: 1;
    pointer-events: auto;
    top: 8px;
    right: 8px;
  }
}
</style>
