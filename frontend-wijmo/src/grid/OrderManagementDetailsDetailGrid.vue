<template>
    <wj-flex-grid
        ref="flexGridDetails"
        :autoGenerateColumns="false"
        :allowAddNew="false"
        :allowDelete="true"
        :allowPinning="'SingleColumn'"
        :newRowAtTop="false"
        :showMarquee="true"
        :selectionMode="'MultiRange'"
        :validateEdits="false"
        :itemsSource="selectedGrid"
        :initialized="flexDetailsInitialized"
        style="margin-top:10px; max-height:65vh;"
    >
        <wj-flex-grid-column binding="index" header="Number" width="2*" :isReadOnly="true" align="center" />
        <wj-flex-grid-column binding="uniqueNumber" header="uniqueNumber" width="2*" :isReadOnly="true" align="center" />
        <wj-flex-grid-column binding="itemCode" header="itemCode" width="2*" :isReadOnly="true" align="center" />
        <wj-flex-grid-column binding="itemName" header="itemName" width="2*" :isReadOnly="true" align="center" />
        <wj-flex-grid-column binding="itemSpecification" header="itemSpecification" width="2*" :isReadOnly="true" align="center" />
    </wj-flex-grid>
</template>

<script>
import '@grapecity/wijmo.touch';
import '@grapecity/wijmo.vue2.grid';

export default {
    name: 'orderManagementDetailsDetailGrid',
    props: {
        selectedGrid: {
            type: Array,
            required: true
        }
    },
    methods: {
        flexDetailsInitialized(flexGridDetails) {
            this.$refs.flexGridDetails = flexGridDetails;
        },
    },
}
</script>

