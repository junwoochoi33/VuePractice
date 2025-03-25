<template>
    <div class="modal" v-if="isModal">
        <div class="inner">
            <h3 v-if="country">{{ country.name.common }} ({{ country.name.official }})</h3>
            <p><strong>Code:</strong> {{ selected }}</p>
            <p v-if="country"><strong>Capital:</strong> {{ country.capital?.[0] || 'N/A' }}</p>
            <p v-if="country"><strong>Region:</strong> {{ country.region }}</p>
            <p v-if="country"><strong>Subregion:</strong> {{ country.subregion }}</p>
            <p v-if="country"><strong>Population:</strong> {{ country.population?.toLocaleString() }}</p>
            <p v-if="country"><strong>Currency:</strong> {{ currency.name }} ({{ currency.symbol }})</p>
            <p v-if="country"><strong>Languages:</strong> {{ languages }}</p>
            <p v-if="country"><strong>Timezone:</strong> {{ country.timezones?.join(', ') }}</p>
            <p v-if="country"><strong>Borders:</strong> {{ borders }}</p>
            <p v-if="country"><strong>Google Maps:</strong> <a :href="country.maps?.googleMaps" target="_blank">View</a></p>
            <img v-if="country" :src="country.flags?.svg" :alt="country.flags?.alt" width="100">
            <p v-else>Loading...</p>

            <div class="modal-footer">
                <button class="close-btn" @click="closeModal()">Close</button>
            </div>
        </div>
    </div>
</template>

<script>


export default {
    name: 'ModalComponent',
    props: {
        isModal: Boolean,
        selected: String
    },
    methods: {
        closeModal() {
            this.$emit('closeModal')
        },
        async fetchCountryData(code) {
            this.loading = true;
            this.country = null;
            try {
                const response = await fetch(`https://restcountries.com/v3.1/alpha/${code}`);
                const data = await response.json();
                this.country = data[0];
            } catch (error) {
                console.error("Failed to fetch country data:", error);
            } finally {
                this.loading = false;
            }
        },
    },
    data() {
        return {
            country: null,
            loading: false,
        }
    },
    watch: {
        selected: {
            immediate: true,
            handler(newCode) {
                if (newCode) {
                    this.fetchCountryData(newCode);
                }
            }
        }
    },
    computed: {
        currency() {
            return this.country?.currencies ? Object.values(this.country.currencies)[0] : {};
        },
        languages() {
            return this.country?.languages ? Object.values(this.country.languages).join(', ') : "N/A";
        },
        borders() {
            return this.country?.borders ? this.country.borders.join(', ') : "None";
        }
    },
}

</script>

<style>
.modal {
    background: rgba(0, 0, 0, 0.7);
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}

.modal .inner {
    background: #fff;
    width: 80%;
    padding: 20px;
    border-radius: 10px;
}

.modal-footer {
    display: flex;
    justify-content: center;
    align-items: center;
    border-top: 1px solid #ddd; 
    padding-top: 5px;
}

.close-btn {
    cursor: pointer;
}
</style>