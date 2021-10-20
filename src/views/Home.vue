<template>
    <div class="home">
        <div :class="introductionClass">
            <div class="introduction-promo"><h4>Our Forte.</h4>
            Import & Export,Farming & Training, Branding & Packaging</div>
            <p></p>
            <router-link to="/setup" class="action-button">GET STARTED</router-link>
            <img alt="devices" class="introduction-devices" src="../assets/images/home/intro-devices.png" />
        </div>

        <div class="features">
            <h4>OUR SERVICES</h4>
            <p>Picasynergy Holdings (M) Sdn. Bhd. (PHSB) is a local marketing company dealing in import and export that focusses on distributing fresh produce mainly fruit, from all across the globe, to Asian, European and Middle East Market.</p>

            <div class="p-grid">
                <div class="p-col-12 p-md-4">
                    <div class="feature-card">
                        <img alt="components" src="../assets/images/home/vue-components.png" />
                        <div class="feature-card-detail">
                            <div class="feature-name">DIRECT SOURCING</div>
                            <p>Enables the retailer to communicate with confidence to the consumer that.</p>
                        </div>
                    </div>
                </div>
                <div class="p-col-12 p-md-4">
                    <div class="feature-card">
                        <img alt="opensource" src="../assets/images/home/vue-opensource.png" />
                        <div class="feature-card-detail">
                            <div class="feature-name">FARMING & GROWING</div>
                            <p>Best practices that comply with global standards, e.g. non toxic chemicals are used.</p>
                        </div>
                    </div>
                </div>
                <div class="p-col-12 p-md-4">
                    <div class="feature-card">
                        <img alt="themes" src="../assets/images/home/vue-themes.png" />
                        <div class="feature-card-detail">
                            <div class="feature-name">PRODUCT PRACTICES</div>
                            <p>Our range product comes from farms that adhere o strict ethical labour practices.</p>
                        </div>
                    </div>
                </div>
                <div class="p-col-12 p-md-4">
                    <div class="feature-card">
                        <img alt="templates" src="../assets/images/home/vue-templates.png" />
                        <div class="feature-card-detail">
                            <div class="feature-name">OUR BRANDS</div>
                            <p>Our brand is handled in a hygienic environment and there is no contamination with foreign materials.</p>
                        </div>
                    </div>
                </div>
                <div class="p-col-12 p-md-4">
                    <div class="feature-card">
                        <img alt="accesibility" src="../assets/images/home/vue-accesibility.png" />
                        <div class="feature-card-detail">
                            <div class="feature-name">SUPPORT</div>
                            <p>Support full range product supply for 12 months of the year</p>
                        </div>
                    </div>
                </div>
                <div class="p-col-12 p-md-4">
                    <div class="feature-card">
                        <img alt="pro" src="../assets/images/home/vue-pro.png" />
                        <div class="feature-card-detail">
                            <div class="feature-name">RETAILER / SUPPLIER</div>
                            <p>Assisting retailer to merchandise, brand and sell the product to the consumer.</p>
                        </div>
                    </div>
                </div>
                <div class="p-col-12 p-md-4">
                    <div class="feature-card">
                        <img alt="productivity" src="../assets/images/home/vue-productivity.png" />
                        <div class="feature-card-detail">
                            <div class="feature-name">DELIVERY SERVICES</div>
                            <p>No delivery chain, resulting in reduced prices and more satisfied consumer.</p>
                        </div>
                    </div>
                </div>
                <div class="p-col-12 p-md-4">
                    <div class="feature-card">
                        <img alt="community" src="../assets/images/home/vue-community.png" />
                        <div class="feature-card-detail">
                            <div class="feature-name">PACKAGING</div>
                            <p>Reduction in carbon footprint through commitment to ‘green’ packaging design and purchasing.</p>
                        </div>
                    </div>
                </div>
                <div class="p-col-12 p-md-4">
                    <div class="feature-card">
                        <img alt="mobile" src="../assets/images/home/vue-mobile.png" />
                        <div class="feature-card-detail">
                            <div class="feature-name">COLD CHAIN MANAGEMENT(CCMS)</div>
                            <p>Proper cold storage and cold chain management is maintained, which equates to maximized product shelf life.</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div class="whouses">
            <h4>PHSB INTRODUCTION</h4>
            <p>Picasynergy Holdings (M) Sdn. Bhd. (PHSB) is a local marketing company dealing in import and export that focusses on distributing fresh produce mainly fruit, from all across the globe, to Asian, European and Middle East Market. The company initially started out as a division of a group of local agriculture company with the intent of supporting and increasing their business market. PHSB expanded their operations and opened a trading office in Malaysia. Upcoming PHSB has
acquired additional shareholders to secure reliable sources to produce a better quality
products, trading, branding on worldwide standard ang guidelines. With pineapple consumption continually on the rise due to increased availability from emerging growing locations, Picasynery Holdings (M) Sdn. Bhd. (PHSB) is now ready than ever to penetrade this market. Our vertically intergrated supply chain, world-wide distribution capabilities and consistent quality have been the basis for our company’s growth and success and it is in the areas of food safety traceabiliy, environmental responsibilty and social accountability that we have built on PHSB.</p>
        </div>


        <div class="primeblocks">
        </div>

        <div class="prosupport">
            <div class="p-grid">
                <div class="p-col-12 p-md-6">
                    <h4>MD2 hybrid</h4>
                    <p>MD2 hybrid was developed to satisfy a market looking for exceptional sweetness as well as uniformity and consistensy in size and ripeness.</p>
                    <router-link to="/support" class="action-button">LEARN MORE</router-link>
                </div>
                <div class="p-col-12 p-md-6">
                    <img alt="PRO" src="../assets/images/home/asset-pro.png" />
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import EventBus from '@/AppEventBus';

export default {
    data() {
        return {
            dark: false
        }
    },
    themeChangeListener: null,
    mounted() {
        let afId = this.$route.query['af_id'];
        if (afId) {
            let today = new Date();
            let expire = new Date();
            expire.setTime(today.getTime() + 3600000*24*7);
            document.cookie = 'primeaffiliateid=' + afId + ';expires=' + expire.toUTCString() + ';path=/; domain:primefaces.org';
        }

        this.themeChangeListener = (event) => {
            if (event.dark)
                this.dark = true;
            else
                this.dark = false;
        };
        EventBus.on('change-theme', this.themeChangeListener);
    },
    beforeUnmount() {
        EventBus.off('change-theme', this.themeChangeListener);
    },
    computed: {
        introductionClass() {
            return ['introduction', {'introduction-dark': this.dark}];
        }
    }
}
</script>
