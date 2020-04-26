<template>
    <div class="container">
        <div class="row">
            <div class="col-xs-12">
                <br>
                <button class="btn btn-primary" @click="selectComponent" comp="Blue">Load Blue Template</button>
                <button class="btn btn-success" @click="selectComponent" comp="Green">Load Green Template</button>
                <button class="btn btn-danger" @click="selectComponent" comp="Red">Load Red Template</button>
                <hr>

                <component :is="selectedComponent" :class="{hide: isVisible}">
                    <h3>This is The Default text:</h3>
                </component>
                <app-blue :class="{hide: !isVisible}">
                    <article v-html="commonText"></article>
                </app-blue>
                <app-green :class="{hide: !isVisible}">
                    <article v-html="commonText"></article>
                </app-green>
                <app-red :class="{hide: !isVisible}">
                    <article v-html="commonText"></article>
                </app-red>
            </div>
        </div>
    </div>
</template>

<script>
    import Blue from './components/Blue.vue';
    import Green from './components/Green.vue';
    import Red from './components/Red.vue';

    export default {
        data() {
            return {
                commonText:'<h3>This is the default text</h3>',
                selectedComponent:'appBlue',
                isVisible:true

            }
        },
        methods:{
            selectComponent(e){
                this.isVisible = false
                this.selectedComponent='app'+e.target.attributes.comp.value
                console.log(this.selectedComponent)
            }
        },
        components: {
            appBlue: Blue,
            appGreen: Green,
            appRed: Red
        }
    }
</script>

<style>

.hide {
    display: none;
}
</style>
