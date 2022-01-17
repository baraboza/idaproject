<template>
  <div class="wrap">
    <p class="title">
      Добавление товара
    </p>
    <form class="form">
      <div
        v-for="(field, key) in fields"
        :key="key"
        class="form-row"
      >
        <label
          :for="'product-' + key"
          :class="{
            'is-required': field.required
          }"
        >
          {{ field.label }}
        </label>

        <input
          v-if="field.element === 'input'"
          :id="'product-' + key"
          v-model="field.value"
          :class="{
            'has-error': field.error
          }"
          type="text"
          :placeholder="field.placeholder"
          @keydown="field.onKeyDown && field.onKeyDown($event)"
          @input="field.onInput && field.onInput(field)"
          @blur="validation(field)"
        >

        <textarea
          v-else-if="field.element === 'textarea'"
          :id="'product-' + key"
          v-model="field.value"
          :placeholder="field.placeholder"
        />

        <span
          v-if="field.error"
          class="error"
        >
          {{ field.errorText }}
        </span>
      </div>

      <button
        type="submit"
        class="button-submit"
        :disabled="disabledSubmit"
      >
        Добавить товар
      </button>
    </form>
  </div>
</template>

<script>
export default {
  data () {
    return {
      fields: {
        title: {
          label: 'Наименование товара',
          placeholder: 'Введите наименование товара',
          element: 'input',
          value: '',
          required: true,
          error: false,
          errorText: ''
        },
        description: {
          label: 'Описание товара',
          placeholder: 'Введите описание товара',
          element: 'textarea',
          value: '',
          required: false,
          error: false,
          errorText: ''
        },
        image: {
          label: 'Ссылка на изображение товара',
          placeholder: 'Введите ссылку',
          element: 'input',
          value: '',
          required: true,
          error: false,
          errorText: ''
        },
        price: {
          label: 'Цена товара',
          placeholder: 'Введите цену',
          element: 'input',
          value: '',
          required: true,
          error: false,
          errorText: '',
          onKeyDown: (e) => {
            const key = e.key
            const cond = (
              (key >= '0' && key <= '9') ||
              key === 'ArrowLeft' || key === 'ArrowRight' ||
              key === 'Delete' || key === 'Backspace'
            )

            if (!cond) {
              e.preventDefault()
            }
          },
          onInput: (field) => {
            console.log(field.value)
            field.value = field.value
              .replaceAll(' ', '')
              .replace(/(\d)(?=(\d\d\d)+([^\d]|$))/g, '$1 ')
          }
        }
      }
    }
  },

  computed: {
    disabledSubmit () {
      return Object.values(this.fields)
        .some(field => field.error || (field.required && !field.value))
    }
  },

  methods: {
    validation (field) {
      if (!field.required) {
        return
      }

      if (field.value === '') {
        field.error = true
        field.errorText = 'Поле является обязательным'
      } else {
        field.error = false
        field.errorText = ''
      }
    }
  }
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
      transition: border-color 0.3s;

      &:focus {
        border-color: rgba(0, 0, 0, 0.1);
        outline: none;
      }

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
  transition-property: background, box-shadow;
  transition-duration: 0.3s;

  &:hover,
  &:focus {
    background: #7b9d76;
    outline: none;
  }

  &:active {
    box-shadow: none;
  }

  &:disabled {
    background: #EEEEEE;
    color: #B4B4B4;
    box-shadow: none;
    pointer-events: none;
  }
}

@media (max-width: 600px) {
  .title {
    font-size: 24px;
    line-height: 32px;
  }

  .form {
    padding: 16px;
  }

  .button-submit {
    margin-top: 20px;
  }
}
</style>
