<template>
  <main class="home">
    <section class="hero">
      <div class="container">
        <div :class="{'logo': true, 'selfhosted': config.selfHosted }">
          <img alt="Sky logo" src="../assets/logo.svg">
          <div>
            <h1>SkyHaven</h1>
            <p>{{ $t('description') }}</p>
          </div>
        </div>

        <div class="download" v-if="!config.selfHosted">

        </div>
      </div>
    </section>


  </main>
</template>

<script>
export default {
  name: 'Home',

  metaInfo: {
    title: 'SkyHaven',
    titleTemplate: null,
  },

  data() {
    return {

    };
  },
  computed: {
    version() {
      return this.$store.getters.version;
    },
    config() {
      return this.$store.getters.config;
    },
    discordUserCount() {
      return this.$store.getters.discordUserCount;
    },
    patreonCount() {
      return this.$store.getters.patreonCount;
    },
  },
};
</script>

<style lang="scss">
  main.home {
    overflow-y: auto;

    .container {
      display: flex;

      &.selfhosted {
        justify-content: center;

        .resources {
          width: 50%;

          div {
            width: 100%;
          }
        }
      }
    }

    .logo {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 4rem 2rem;
      font-size: 1.5em;
      width: 100%;
      text-align: center;

      @include breakpoint($md) {
        padding: 4rem;
        width: 66%;
        flex-direction: row;
        text-align: left;
        justify-content: flex-start;

        div {
          max-width: 35rem;
        }
      }

      img {
        height: 13rem;
        width: auto;
        margin-bottom: 2rem;

        @include breakpoint($md) {
          margin-bottom: 0;
          margin-right: 2rem;
        }
      }

      &.selfhosted {
        justify-content: center;
        width: 100%;
      }
    }

    .download {
      width: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding-bottom: 4rem;

      @include breakpoint($md) {
        padding: 4rem;
        align-items: flex-end;
        width: 34%;
      }

      a {
        background: $brand-color;
        color: $navy;
        font-size: 1.5em;
        padding: 1rem 2rem;
        text-align: center;
        line-height: 1;
        text-decoration: none;
        border-radius: 2px;
        transition: background .2s;

        @include breakpoint($md) {
          font-size: 2em;
          margin-top: 2.5rem;
        }

        &:hover {
          background: lighten($brand-color, 10%);
        }

        span {
          display: block;
          font-weight: bold;

          svg {
            margin-right: .5rem;
            opacity: .5;
          }
        }

        small {
          font-size: 1rem;
          opacity: .75;

          @include breakpoint($md) {
            font-size: 1.25rem;
          }
        }
      }

      > small {
        max-width: 18rem;
        text-align: center;
        opacity: .5;
        margin-top: 1rem;

        @include breakpoint($md) {
          text-align: right;
        }
      }
    }
  }

  .tools {
    display: flex;

    a {
      background: $grey;
      color: $brand-color;
      font: inherit;
      font-weight: bold;
      flex: 1;
      margin: 1rem;
      padding: 2rem;
      display: flex;
      flex-direction: column;
      align-items: center;
      border-radius: 2px;
      text-decoration: none;
      text-align: center;

      @include breakpoint($sm) {
        font-size: 1.25rem;
      }

      svg {
        font-size: 3rem;
        display: block;
        opacity: .5;
        color: #FFF;
        margin-bottom: 1rem;

        @include breakpoint($sm) {
          font-size: 4rem;
        }
      }

      &:first-child {
        margin-left: 0;
      }

      &:last-child {
        margin-right: 0;
      }
    }
  }
</style>
