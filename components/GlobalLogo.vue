<template>
    <nuxt-link
        to="/"
        :class="classes"
    >
        <svg-logo class="svg" />
    </nuxt-link>
</template>

<script>
// Svgs
import SvgLogo from "~/assets/svg/logo-jojx"

export default {
    components: {
        SvgLogo
    },
    props: {
        introActive: {
            type: Boolean,
            default: false
        }
    },
    computed: {
        classes() {
            return ["global-logo", { "intor-active": this.introActive }]
        }
    }
}
</script>

<style lang="scss" scoped>
.global-logo {
    position: fixed;
    z-index: 900;
    bottom: 35px;
    left: var(--unit-gap);
    mix-blend-mode: difference;
    transform-origin: bottom left;

    transform: scale(0.2); // 145 / 716 = .2
    transition: all 0.6s var(--easing-authentic-motion);

    .intro-is-active.route-index .is-scrolled &,
    .intro-is-active.route-index &,
    .route-index & {
        pointer-events: none;
        transform: translate(0, calc(-50vh + 100%));
    }
    .route-index .is-scrolled & {
        transform: scale(0.2); // 145 / 716 = .2
    }

    .svg path {
        fill: var(--color-white);
    }

    @media #{$has-hover} {
        &:hover {
            transform: scale(0.25); // 112 / 716 = .2
        }
    }

    // Breakpoints
    @media #{$lt-tablet} {
        transform: scale(0.25); // 177 / 716 = .25

        .intro-is-active.route-index .is-scrolled &,
        .intro-is-active.route-index &,
        .route-index & {
            transform: scale(0.4) translate(0, calc(-50vh - 300px)); //292 / 716 = .25
        }
        .route-index .is-scrolled & {
            transform: scale(0.25);
        }
    }
    @media #{$lt-phone} {
        bottom: 16px;
        transform: scale(0.15); // 112 / 716 = .15

        .route-index .is-scrolled & {
            transform: scale(0.15);
        }

        .route-directors &,
        .route-studio & {
            opacity: 0;
            pointer-events: none;
        }

        .menu-is-open.route-directors &,
        .menu-is-open.route-studio & {
            opacity: 1;
            pointer-events: all;
        }
    }
}
</style>
