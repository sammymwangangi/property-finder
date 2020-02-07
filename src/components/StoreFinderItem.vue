<template>
  <div>
    <b-card no-body class="overflow-auto" style="max-width: 540px;">
      <b-row no-gutters>
          <b-col md="6">
              <b-card-img src="https://picsum.photos/400/400/?image=3" class="rounded-0"></b-card-img>
          </b-col>
          <b-col md="6">
              <b-card-body :title="name">
                  <b-card-text>
                      {{ address.postal_code }}
                      {{ address.town }}<br>
                      {{ address.street }}
                  </b-card-text>
                  <!-- {{beds}} Beds | {{baths}} Baths | {{acre}} Sq.ft -->
              </b-card-body>
          </b-col>
      </b-row>
    </b-card>
  </div>
</template>

<script>
import OpeningHours from './OpeningHours.vue';

export default {
  name: `StoreFinderItem`,
  components: {
    OpeningHours,
  },
  props: {
    address: {
      default: () => ({}),
      required: true,
      type: Object,
    },
    distance: {
      default: null,
      type: Number,
    },
    name: {
      default: ``,
      required: true,
      type: String,
    },
    openingHours: {
      default: () => ({}),
      required: true,
      type: Object,
    },
  },
  created() {
    // Create a Google Maps URL,
    // for directions to the shop.
    const url = `https://www.google.com/maps/dir/?api=1`;
    const destination = [
      this.address.street,
      `${this.address.postal_code} ${this.address.town}`,
    ].join(`, `);
    this.directionsUrl = `${url}&destination=${encodeURI(destination)}`;
  },
};
</script>

<style lang="scss">
@import '../assets/scss/settings/**/*';

.StoreFinderItem__headline {
  font-weight: bold;
}

.StoreFinderItem__section {
  &:not(:first-child) {
    margin-top: setting-spacing(s);
  }
}

.StoreFinderItem__distance {
  font-weight: normal;
  color: #999;
}
</style>
