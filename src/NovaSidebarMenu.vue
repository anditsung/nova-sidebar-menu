<template>
    <div v-on-clickaway="away">
        <h3 class="cursor-pointer flex items-center font-normal text-white mb-6 text-base no-underline" @click.prevent="toggle">
            <slot></slot>
            <svg v-if="expanded" class="ml-auto sidebar-icon" xmlns="http://www.w3.org/2000/svg"><path fill="var(--sidebar-icon)" d="M15.3 9.3a1 1 0 0 1 1.4 1.4l-4 4a1 1 0 0 1-1.4 0l-4-4a1 1 0 0 1 1.4-1.4l3.3 3.29 3.3-3.3z"/></svg>
            <svg v-else class="ml-auto sidebar-icon" xmlns="http://www.w3.org/2000/svg"><path fill="var(--sidebar-icon)" d="M9.3 8.7a1 1 0 0 1 1.4-1.4l4 4a1 1 0 0 1 0 1.4l-4 4a1 1 0 0 1-1.4-1.4l3.29-3.3-3.3-3.3z"/></svg>
        </h3>

        <ul v-show="expanded" class="list-reset -mt-3">

            <slot name="menu"></slot>

        </ul>
    </div>
</template>

<script>
    import { mixin as clickaway } from 'vue-clickaway'

    export default {
        mixins: [ clickaway ],

        props: {
            'autoClose': {
                type: Boolean,
                default: false,
            },
        },

        name: "NovaSidebarMenu",

        data: () => ({
            expanded: false,
        }),

        methods: {
            away: function() {
                if(this.autoClose) {
                    this.expanded = false
                }
            },
            toggle() {
                this.expanded = !this.expanded;
            }
        },
    }
</script>
