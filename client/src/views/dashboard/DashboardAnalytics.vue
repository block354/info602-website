<script setup>
import Navigation from "../../components/Navigation.vue";
import DashboardSideNavigation from "../../components/dashboard/DashboardSideNavigation.vue";
import Footer from "../../components/Footer.vue";
</script>

<template>
    <Navigation />
    <div class="_container">
        <div class="side-navigation">
            <DashboardSideNavigation />
        </div>
        <div class="content">
            <h2 class="report-title">Analytics</h2>
            <div class="controls">
                <!-- Example control, add as needed -->
                <label for="date-range">Date Range:&nbsp;</label>
                <input type="date" id="start-date">&nbsp;
                <input type="date" id="end-date">&nbsp;
                <button @click="applyFilters">Apply</button>
            </div>
            <loading-spinner v-if="isLoading" />
            <div class="iframe-wrapper" v-if="!isLoading">
                <iframe title="Main_Connection_3"
                    src="https://app.powerbi.com/reportEmbed?reportId=0384868a-6dcf-4d5d-b63d-d2d4688dadf8&autoAuth=true&ctid=f7bae8e1-a04b-4f86-9377-8eb84875e0a2"
                    frameborder="0" allowFullScreen="false"></iframe>
            </div>
        </div>
    </div>
    <Footer />
</template>

<style scoped>
._container {
    display: flex;
}

.side-navigation {
    padding: 0px;
}

.content {
    flex-grow: 1;
    padding: 50px 100px 50px 100px;
}

.breadcrumb {
    margin-bottom: 10px;
    font-size: 14px;
}

.report-title {
    margin-bottom: 10px;
    font-size: 24px;
    font-weight: bold;
}

.controls {
    margin-bottom: 10px;
}

.iframe-wrapper {
    width: 100%;
    height: 0;
    padding-bottom: 47.5%;
    /* Adjust based on aspect ratio */
    position: relative;
    border: 3px solid #000;
    /* 3px thick border */
}

iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}
</style>

<script>
export default {
    data() {
        return {
            isLoading: true
        };
    },
    mounted() {
        // Simulate loading time
        setTimeout(() => {
            this.isLoading = false;
        }, 2000);
    },
    methods: {
        applyFilters() {
            // Logic to apply filters to the Power BI report
        }
    }
};
</script>
