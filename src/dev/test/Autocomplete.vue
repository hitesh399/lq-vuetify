<template>
<v-app id="app">
    <lq-v-form name="_test">
        <lq-v-autocomplete v-bind="$attrs"/>
    </lq-v-form>
</v-app>
</template>
<script>
export default {
    props: {
        formName: String
    }
}
</script>