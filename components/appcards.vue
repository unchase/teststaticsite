<template>
    <div class="row">
        <div class="col s6" v-for="cc in contactlist.results">
            <div class="card horizontal">
                <div class="card-stacked">
                    <div class="card-content">
                        <div class="img-profile-pic">
                            <img :src="cc.picture.medium" alt="" class="circle responsive-img">
                        </div>
                        <h5>{{ ucfirst(cc.name.title) }} {{ ucfirst(cc.name.first) }} {{ ucfirst(cc.name.last) }}<br><small>#{{ cc.id.name }}{{ cc.id.value }}</small></h5>
                        <p><i class="material-icons tiny">person</i> {{ ucfirst(cc.gender) }}</p>
                        <p><i class="material-icons tiny">email</i> {{ cc.email }}</p>
                        <p><i class="material-icons tiny">location_on</i> {{ ucfirst(cc.location.street) }} {{ ucfirst(cc.location.city) }} {{ ucfirst(cc.location.state) }} {{ cc.location.postcode }}</p>
                        <p><i class="material-icons tiny">local_phone</i> {{ cc.phone }}</p>
                        <p><i class="material-icons tiny">contact_phone</i> {{ cc.cell }}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    module.exports = {
        props: ['contactlist'],
        methods: {
            ucfirst: function (string) {
                return string.charAt(0).toUpperCase() + string.slice(1);
            }
        }
    }
</script>