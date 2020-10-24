<script>
import BaseComponentMixin from '../../utils/BaseComponentMixin'
import VueComponentMixin from '../../utils/VueComponentMixin'


let FunctionalComponent = (component) => {
    component.functional = true
    component.render.props = component.props
    component.render.name = 'OMenuList'
    return component.render
}

let OMenuList = FunctionalComponent({
    name: 'OMenuList',
    mixins: [VueComponentMixin(), BaseComponentMixin],
    functional: true,
    props: {
        label: String,
        icon: String,
        iconPack: String,
        ariaRole: {
            type: String,
            default: ''
        },
        size: {
            type: String,
            default: 'is-small'
        }
    },
    render(props, context) {
        console.log('RENDER')
        let vlabel = null
        const slots = context.slots()
        if (context.props.label || slots.label) {
            vlabel = this.$createElement('p', { attrs: { 'class': 'menu-label' } },
                context.props.label
                    ? context.props.icon
                        ? [
                            this.$createElement('b-icon', {
                                props: {
                                    'icon': context.props.icon,
                                    'pack': context.props.iconPack,
                                    'size': context.props.size
                                }
                            }),
                            this.$createElement('span', {}, context.props.label)
                        ] : context.props.label
                    : slots.label)
        }
        const vnode = this.$createElement(
            'ul', { 
                attrs: { 
                    'class': 'menu-list', 
                    'role': context.props.ariaRole === 'menu' ? context.props.ariaRole : null 
                } 
            }, slots.default
        )
        console.log('BRENDER')
        return vlabel ? [ vlabel, vnode ] : vnode
    }
})

export default OMenuList
</script>