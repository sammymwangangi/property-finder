<template>
  <div>
    <div>
        <!-- First Nav -->
        <b-navbar small toggleable="lg" type="dark" variant="dark">
            <b-navbar-brand href="#"> PASSIVITI</b-navbar-brand>

            <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

            <b-collapse id="nav-collapse" is-nav>
            <b-navbar-nav small>
                <b-nav-item href="#">Search</b-nav-item>
                <b-nav-item href="#">Property Finder</b-nav-item>
                <b-nav-item-dropdown text="Dashboard" right>
                <b-dropdown-item href="#">Owner Records</b-dropdown-item>
                <b-dropdown-item href="#">Add Property</b-dropdown-item>
                <b-dropdown-item href="#">Property Marketplace</b-dropdown-item>
                <b-dropdown-item href="#">Lead Management</b-dropdown-item>
                </b-nav-item-dropdown>
            </b-navbar-nav>

            <b-navbar-nav small class="ml-auto">
                <b-nav-item href="#"><b-button size="sm" pill variant="success">14-Day Free Trial</b-button></b-nav-item>
            </b-navbar-nav>

            <!-- Right aligned nav items -->
            <b-navbar-nav small class="ml-auto">
                <b-nav-item href="#"><b-button size="sm" pill variant="outline-light">PASSIVITIBOARD</b-button></b-nav-item>
                <b-nav-item href="#">Pricing</b-nav-item>
                <b-nav-item href="#">Saved Homes</b-nav-item>

                <b-nav-item-dropdown text="Help" right>
                <b-dropdown-item href="#">Help Center</b-dropdown-item>
                <b-dropdown-item href="#">Knowledge Center</b-dropdown-item>
                <b-dropdown-item href="#">Book a Demo</b-dropdown-item>
                <b-dropdown-item href="#">Report an Issue</b-dropdown-item>
                <b-dropdown-item href="#">Getting Started</b-dropdown-item>
                <b-dropdown-item href="#">Data Methodology</b-dropdown-item>
                <b-dropdown-item href="#">Passiviti Demo</b-dropdown-item>
                </b-nav-item-dropdown>

                <b-nav-item-dropdown right>
                    <!-- Using 'button-content' slot -->
                    <template v-slot:button-content>
                        <em>User</em>
                    </template>
                    <b-dropdown-item href="#">
                        <div>
                            <b-media>
                                <template v-slot:aside>
                                    <b-img blank blank-coloa="#ccc" width="64" alt="placeholder"></b-img>
                                </template>

                                <h5 class="mt-0">User Name</h5>
                                <a href="#">
                                    Edit Profile
                                </a>
                            </b-media>
                        </div>
                    </b-dropdown-item>
                    <b-dropdown-item href="#">Billing</b-dropdown-item>
                    <b-dropdown-item href="#">Sign Out</b-dropdown-item>
                </b-nav-item-dropdown>
            </b-navbar-nav>
            </b-collapse>
        </b-navbar>

        <!-- Second Nav -->
        <div small class="m-2 ml-4">
            <b-nav pills>
                <b-nav-form @submit.stop.prevent="alert('Form Submitted')" class="mr-4">
                    <b-form-input size="sm" class="mr-sm-2" placeholder="Search"></b-form-input>
                    <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
                </b-nav-form>
                Cash <b-form-checkbox switch></b-form-checkbox>
                <b-nav-item-dropdown
                id="my-nav-dropdown"
                text="Morgage"
                toggle-class="nav-link-custom"
                right
                >
                    <b-dropdown-item>One</b-dropdown-item>
                    <b-dropdown-item>Two</b-dropdown-item>
                    <b-dropdown-divider></b-dropdown-divider>
                    <b-dropdown-item>Three</b-dropdown-item>
                </b-nav-item-dropdown>
                <div>
                    <b-form inline>
                        <b-form-select
                        class="mb-2 mr-sm-2 mb-sm-0"
                        :value="null"
                        :options="{ '1': 'One', '2': 'Two', '3': 'Three' }"
                        id="inline-form-custom-select-pref"
                        >
                        <template v-slot:first>
                            <option :value="null">CoC Return</option>
                        </template>
                        </b-form-select>
                    </b-form>
                </div>
                <div>
                    <b-form inline>
                        <b-form-select
                        class="mb-2 mr-sm-2 mb-sm-0"
                        :value="null"
                        :options="{ '1': 'One', '2': 'Two', '3': 'Three' }"
                        id="inline-form-custom-select-pref"
                        >
                        <template v-slot:first>
                            <option :value="null">Cap Rate</option>
                        </template>
                        </b-form-select>
                    </b-form>
                </div>
                <div>
                    <b-form inline>
                        <b-form-select
                        class="mb-2 mr-sm-2 mb-sm-0"
                        :value="null"
                        :options="{ '1': 'One', '2': 'Two', '3': 'Three' }"
                        id="inline-form-custom-select-pref"
                        >
                        <template v-slot:first>
                            <option :value="null">Budget</option>
                        </template>
                        </b-form-select>
                    </b-form>
                </div>
                <div>
                    <b-form inline>
                        <b-form-select
                        class="mb-2 mr-sm-2 mb-sm-0"
                        :value="null"
                        :options="{ '1': 'One', '2': 'Two', '3': 'Three' }"
                        id="inline-form-custom-select-pref"
                        >
                        <template v-slot:first>
                            <option :value="null">Neighborhood</option>
                        </template>
                        </b-form-select>
                    </b-form>
                </div>
                <b-nav-item-dropdown
                id="my-nav-dropdown"
                text="More Filters"
                toggle-class="nav-link-custom"
                right
                >
                    <b-dropdown-item>One</b-dropdown-item>
                    <b-dropdown-item>Two</b-dropdown-item>
                    <b-dropdown-divider></b-dropdown-divider>
                    <b-dropdown-item>Three</b-dropdown-item>
                </b-nav-item-dropdown>
                <b-nav-item align="right" href="#"><b-button size="sm" variant="outline-info">Export</b-button></b-nav-item>
                
            </b-nav>
        </div>
    </div>
  
    <div class="b-container">
      <StoreFinder
        v-if="stores.length"
        :stores="stores"
        class="mt-4"
      />
    </div>
  </div>
</template>

<script>
import * as storeService from './services/store';

import StoreFinder from './components/StoreFinder.vue';

export default {
  name: `App`,
  components: {
    StoreFinder,
  },
  data() {
    return {
      stores: [],
    };
  },
  created() {
    // Initially fetch all stores.
    this.fetchStores();
  },
  methods: {
    async fetchStores() {
      this.stores = await storeService.list();
    },
  },
};
</script>

<style lang="scss">
@import './assets/scss/settings/**/*';
@import './assets/scss/generic/**/*';
@import '{
  .o-container,
} from ~@avalanche/object-container';

.App {
  padding-top: setting-spacing(xl);
  padding-bottom: setting-spacing(xl);
}

.App__headline {
  text-align: center;
}

.App__store-finder {
  margin-top: setting-spacing(xxl);
}
</style>
