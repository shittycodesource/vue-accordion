<template>
    <div class="accordion" :class="{'open': isContentOpen}">
        <div class="accordion__header">
            <h3 class="accordion__title">{{title}}</h3>
            <button 
                class="accordion__button" 
                type="button"
                @click="toggleContent"
            >
                <svg><use xlink:href="#down"></use></svg>
            </button>
        </div>
        <transition name="accordion-content">
            <div 
                v-if="isContentOpen"
                class="accordion__content-wrapper"
            >
                <div class="accordion__content">
                    <p>{{text}}</p>
                </div>
            </div>
        </transition>
    </div>
</template>

<script>
    export default {
        name: 'Accordion',
        data() {
            return {
                isContentOpen: this.isOpen,
            }
        },
        props: {
            isOpen: {
                type: Boolean,
                default: false,
            },
            title: {
                type: String,
                default: 'Title',
            },
            text: {
                type: String,
                default: "accordion text"
            }
        },
        methods: {
            toggleContent() {
                this.isContentOpen = !this.isContentOpen;
            }
        },
    }
</script>

<style lang="scss">
    .accordion {
        margin-bottom: 20px;
        max-width: 680px;
        width: 100%;

        transition: height .2s ease;

        &__header {
            display: flex;
            align-items: center;
            justify-content: space-between;

            padding: 15px 20px;

            background: #1E1E1E;
            border: 1px solid #353535;
            border-radius: 18px;
        }

        &__title {
            font-size: 16px;
            font-weight: 400;

            padding-right: 20px;

            overflow: hidden;
            text-overflow: ellipsis;
            display: -webkit-box;
            word-break: break-all;
            line-clamp: 1; 
            -webkit-line-clamp: 1;
            -webkit-box-orient: vertical;
            white-space: pre-line;
        }

        &__button {
            background: none;
            border: none;
            cursor: pointer;

            font-family: inherit;
            color: #fff;         
            
            svg {
                width: 24px;
                height: 15px;
                fill: #fff;

                transition: transform .2s ease-in-out;
            }
        }

        &__content-wrapper {
            margin-top: 10px;
            position: relative;
        }

        &__content {
            // position: absolute;
            // top:0;
            // left:0;

            width: 100%;

            padding: 15px 20px;

            background: #1E1E1E;
            border: 1px solid #353535;
            border-radius: 18px;
            box-shadow: 0px 0px 15px rgba(0, 0, 0, 0.25);
            
            p {
                font-size: 16px;
                line-height: 1.6;
                word-break: break-word;
            }
        }

        &.open {
            svg {
                transform: rotate(180deg);
            }
        }
    }

    .accordion-content {
        &-enter-active {
            animation: accordionContentAppears .3s ease;
        }

        &-leave-active {
            animation: accordionContentAppears .3s ease reverse;
        }
    }

    @keyframes accordionContentAppears {
        0% {
            opacity: 0;
            transform: translateY(-20px);
        }

        80% {
            opacity: 1;
            transform: translateY(2px);
        }

        100% {
            opacity: 1;
            transform: translateY(0px);
        }
    }
</style>