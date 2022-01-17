<template>
  <div class="wrap">
    <input type="hidden" value="">
    <button type="button" class="button is-default">
      <span>По умолчанию</span>
      <svg width="8" height="6" viewBox="0 0 8 6" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M7.48532 1.24264L4.24268 4.48528L1.00003 1.24264" stroke="#B4B4B4"/>
      </svg>
    </button>
    <ul class="list has-aling-right">
      <li class="item" tabindex="0">По возрастанию цены</li>
      <li class="item" tabindex="0">По убыванию цены</li>
      <li class="item" tabindex="0">По наименованию</li>
    </ul>
  </div>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
.wrap {
  position: relative;
  font-size: 12px;
  line-height: 15px;
}
.button {
  display: inline-flex;
  align-items: center;
  background: #FFFEFB;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  border: 1px solid #FFFEFB;
  padding: 9px 15px 10px;
  cursor: pointer;
  transition-property: border-color, box-shadow;
  transition-duration: 0.3s;

  &:hover,
  &:focus {
    border-color: rgba(0, 0, 0, 0.1);
    outline: none;
  }

  &:active {
    box-shadow: none;
  }

  &.is-default {
    color: #B4B4B4;
  }

  span {
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
  }

  svg {
    margin-left: 5px;
    flex-shrink: 0;
  }
}
.list {
  display: none;
  position: absolute;
  z-index: 2;
  border-radius: 4px;
  background: #FFFEFB;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  top: 100%;
  margin-top: 5px;
  left: 0;
  right: 0;
  padding: 5px 0;
}
.item {
  padding: 5px 15px;
  cursor: pointer;
  transition: background 0.3s;

  &:hover,
  &:focus {
    background: rgba(0, 0, 0, 0.05);
    outline: none;
  }
}
</style>
