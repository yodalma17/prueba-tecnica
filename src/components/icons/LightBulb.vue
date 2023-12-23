<template>
  <div class="container-icon">    
    <svg class="empty" width="32" height="32" viewBox="0 0 16 22" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M14.7231 12.0407C18.2239 6.34573 14.048 0 7.99608 0C1.94414 0 -2.22239 6.34573 1.27843 12.0407C2.71693 14.3786 3.52696 15.8938 3.98551 16.9399V21.3333H11.988V17.0013C12.4419 15.9527 13.2566 14.4252 14.7231 12.0382V12.0407ZM10.8661 20.1496H5.10743V18.1163H10.8661V20.1496ZM10.7939 16.9326H5.20753C4.75364 15.7833 3.8854 14.1035 2.22112 11.3973C1.53911 10.2872 1.17135 9.12567 1.12712 7.94935C1.08755 6.87863 1.32963 5.80546 1.82309 4.84525C2.98693 2.58593 5.35185 1.18368 7.99608 1.18368C9.33449 1.18368 10.624 1.54223 11.7297 2.22248C12.7795 2.86835 13.6267 3.77698 14.1784 4.85016C14.6718 5.81037 14.9139 6.88109 14.8743 7.95181C14.8324 9.12812 14.4647 10.2872 13.7827 11.3973C12.1184 14.1035 11.2502 15.7833 10.7963 16.9326H10.7939Z" fill="black"/>
    </svg>
    <svg class="visibility" :class="{ 'active': active }" width="32" height="32" viewBox="0 0 16 22" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M14.7231 12.0407C18.2239 6.34573 14.048 0 7.99608 0C1.94414 0 -2.22239 6.34573 1.27843 12.0407C2.71693 14.3786 3.52696 15.8938 3.98551 16.9399V21.3333H11.988V17.0013C12.4419 15.9527 13.2566 14.4252 14.7231 12.0382V12.0407ZM10.8661 20.1496H5.10743V18.1163H10.8661V20.1496Z" fill="#FFFBA5"/>
    </svg>
  </div>
</template>

<script>
export default {
  name: 'LightBulb',
  props: {
    active: {
      type: Boolean,
      default: false
    }
  }
};
</script>

<style lang="sass" scoped>
  .container-icon
    position: relative
    .visibility
      opacity: 0
      position: absolute
      transition: opacity 0.5s
      left: 0
      &.active
        opacity: 1
        left: 0
    .empty
      position: relative
      z-index: 1
</style>
