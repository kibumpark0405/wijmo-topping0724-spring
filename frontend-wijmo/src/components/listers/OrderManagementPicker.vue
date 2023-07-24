<template>
    <div>
        <v-select
            :items="list"
            item-text="name"
            item-value="name"
            label="OrderManagement"
            return-object
            v-model="selected"
            @change="select"
            solo
        ></v-select>
    </div>
</template>

<script>
    const axios = require('axios').default;

    export default {
        name: 'OrderManagementPicker',
        props: {
            value: [String, Object, Array, Number, Boolean],
            editMode: Boolean,
        },
        data: () => ({
            list: [],
            selected: null,
            referenceValue: null,
        }),
        async created() {
            var me = this;
            var temp = await axios.get(axios.fixUrl('/orderManagements'))
            if(temp.data) {
                me.list = temp.data._embedded.orderManagements;
            }

            if(me.value && typeof me.value == "object" && Object.values(me.value)[0]) {
                var idKey = 'id'
                
                
                
                
                
                
                
                
                
                
                
                
                var id = me.value[idKey];
                var tmpValue = await axios.get(axios.fixUrl('/orderManagements/' + id))
                if(tmpValue.data) {
                    var val = tmpValue.data
                    
                    
                    
                    
                    
                    
                    
                    
                    
                    
                    me.selected = me.list.find((item) => item.personInChargeId == val.personInChargeId)
                    
                    
                    me.referenceValue = val
                }
            }
        },
        methods: {
            select(val) {
                this.referenceValue = val;
                if (val) {
                    var uriParts = val._links.self.href.split('/');
                    var obj = Number(uriParts.pop());
                    
                    
                    
                    
                    
                    
                    
                    
                    
                    
                    
                    
                    this.$emit('input', obj);
                } else {
                    this.$emit('input', null);
                }
            },
        },
    };
</script>
