<!-- 
ExpressVPN Browser Extension:
Copyright 2017-2019 Express VPN International Ltd
Licensed GPL v2
-->
<template>
  <div>
    <error-icon iconName="Laptop2" />
    <div>
      <h1>{{ localize('error_subscription_expiring_title') }}</h1>
      <p>{{ localize('error_subscription_expiring_p1_text') }}</p>
    </div>
    <div class="button-container">
      <button class="primary" @click="createTab({ url: `${currentInfo.website_url}/order?utm_content=subscription_expiring_screen&utm_medium=apps&utm_source=browser_extension` })">{{ localize('error_subscription_expiring_renew_button_label') }}</button>
      <button class="secondary" @click="$store.dispatch('setIgnoreStateUpdates', false)">{{ localize('error_subscription_expiring_later_button_label') }}</button>
    </div>
  </div>
</template>
<script>
import errorIcon from '../partials/errorIcon.vue';
import mixinSubscription from '../../scripts/mixins/subscription';

export default {
  name: 'subscription_expiring',
  mixins: [mixinSubscription],
  mounted() {
    this.$store.dispatch('setIgnoreStateUpdates', true); // Prevent state updates from overwriting this screen
  },
  components: {
    errorIcon,
  },
};
</script>

<style lang="scss" scoped>
</style>