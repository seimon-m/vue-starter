<template>
    <div v-for="commute in commutes" :key="commute.person">
        <Commute
            :person="commute.fields.person"
            :start="commute.fields.startLocation"
            :destination="commute.fields.endLocation"
        />
    </div>
</template>

<script>
// @ is an alias to /src
import Commute from "@/components/Commute.vue";
import contentfulClient from "@/modules/contentful.js";

export default {
    name: "Home",
    components: {
        Commute,
    },
    data: function() {
        return {
            commutes: [],
        };
    },
    created: async function() {
        let result = await contentfulClient.getEntries({
            content_type: "hsluCommute",
        });
        this.commutes = result.items;
    },
};
</script>
