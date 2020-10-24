
<template>
    <div class="menu">
        <slot />
    </div>
</template>

<script>
import BaseComponentMixin from '../../utils/BaseComponentMixin'
import VueComponentMixin from '../../utils/VueComponentMixin'

export default {
    name: 'OMenu',
    mixins: [VueComponentMixin(), BaseComponentMixin],
    props: {
        accordion: {
            type: Boolean,
            default: true
        },
        activable: {
            type: Boolean,
            default: true
        }
    },
    data() {
        return {
            _isMenu: true // Used by MenuItem
        }
    }
}
</script>