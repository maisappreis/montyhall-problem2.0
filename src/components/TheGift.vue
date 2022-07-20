<template>
  <div class="gift">
    <div class="gift-tie-1"></div>
    <div class="gift-tie-2"></div>
    <div class="gift-top"></div>
    <div class="gift-body"></div>
  </div>
</template>

<script>
export default {
    name: "TheGift"
}
</script>

<style>

.gift {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    z-index: 10;
}

.gift-top {
    background-color: #5c7e32;
    width: 100px;
    height: 25px;
    border: 1px solid black;
}

.gift-body {
    background-color: #5c7e32;
    width: 90px;
    height: 60px;
    border: 1px solid black;
}

.gift-tie-1 {
    background-color: red;
    position: absolute;
    width: 15px;
    height: 88px;
    border: 1px solid black;
}

.gift-tie-2 {
    background-color: red;
    position: absolute;
    top: 35px;
    width: 90px;
    height: 15px;
    border: 1px solid black;
}

</style>