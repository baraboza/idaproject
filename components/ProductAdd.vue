<template>
  <div class="wrap">
    <p class="title">
      Добавление товара
    </p>
    <form class="form">
      <div class="form-row">
        <label for="product-title" class="is-required">Наименование товара</label>
        <input id="product-title" type="text" placeholder="Введите наименование товара">
      </div>

      <div class="form-row">
        <label for="product-description">Описание товара</label>
        <textarea id="product-description" placeholder="Введите описание товара" />
      </div>

      <div class="form-row">
        <label for="product-title" class="is-required">Ссылка на изображение товара</label>
        <input id="product-title" type="text" placeholder="Введите ссылку" class="has-error">
        <span class="error">Поле является обязательным</span>
      </div>

      <div class="form-row">
        <label for="product-title" class="is-required">Цена товара</label>
        <input id="product-title" type="text" placeholder="Введите цену">
      </div>

      <button type="submit" class="button-submit" disabled>
        Добавить товар
      </button>
    </form>
  </div>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
.title {
  font-weight: 600;
  font-size: 28px;
  line-height: 35px;
}

.form {
  margin-top: 16px;
  background: #FFFEFB;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  padding: 24px;

  &-row {
    margin-top: 16px;
    position: relative;
    display: flex;
    flex-direction: column;

    &:first-child {
      margin-top: 0;
    }

    label {
      align-self: flex-start;
      font-size: 10px;
      line-height: 13px;
      letter-spacing: -0.02em;
      color: #49485E;

      &.is-required {
        position: relative;

        &::after {
          content: '';
          position: absolute;
          top: 0;
          left: 100%;
          width: 4px;
          height: 4px;
          border-radius: 50%;
          background: #FF8484;
        }
      }
    }

    input, textarea {
      width: 100%;
      margin-top: 4px;
      background: #FFFEFB;
      box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
      border-radius: 4px;
      border: 1px solid #FFFEFB;
      font-size: 12px;
      line-height: 15px;
      padding: 9px 15px 10px;

      &.has-error {
        border-color: #FF8484;
      }

      &::placeholder {
        color: #B4B4B4;
      }
    }

    textarea {
      resize: none;
      height: 108px;
    }

    .error {
      position: absolute;
      top: 100%;
      left: 0;
    }
  }
}

.error {
  margin-top: 4px;
  font-size: 8px;
  line-height: 10px;
  letter-spacing: -0.02em;
  color: #FF8484;
}

.button-submit {
  margin-top: 24px;
  background: #7BAE73;
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
  font-family: 'Inter', sans-serif;
  font-weight: 600;
  font-size: 12px;
  line-height: 15px;
  color: #fff;
  padding: 10px 16px 11px;
  border: none;
  width: 100%;

  &:disabled {
    background: #EEEEEE;
    color: #B4B4B4;
    box-shadow: none;
    cursor: default;
  }
}
</style>
