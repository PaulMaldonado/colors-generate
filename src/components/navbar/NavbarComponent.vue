<template>
  <div class="thedarkmode">
    <nav class="navbar navbar-expand-lg bg-light shadow-lg p-4">
        <div class="container">
            <a class="navbar-brand" href="/" style="display: flex; align-items: center;">
                <svg width="34" height="34" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path fill-rule="evenodd" clip-rule="evenodd" d="M12 22C16.4183 22 20 18.4183 20 14C20 9.58172 16.4183 6 12 6C7.58172 6 4 9.58172 4 14C4 18.4183 7.58172 22 12 22ZM12 20C15.3137 20 18 17.3137 18 14C18 10.6863 15.3137 8 12 8C8.68629 8 6 10.6863 6 14C6 17.3137 8.68629 20 12 20ZM14 11C14.5523 11 15 11.4477 15 12C15 12.5523 14.5523 13 14 13C13.4477 13 13 12.5523 13 12C13 11.4477 13.4477 11 14 11ZM12 11C12.5523 11 13 11.4477 13 12C13 12.5523 12.5523 13 12 13C11.4477 13 11 12.5523 11 12C11 11.4477 11.4477 11 12 11Z" fill="currentColor"/>
                </svg>
                Colors Generate
            </a>

            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse justify-content-end" id="navbarSupportedContent">
                <ul class="navbar-nav">
                    <li class="nav-item">
                        <ThemeButtonComponent />
                    </li>
                </ul>
            </div>

            
        </div>
    </nav>
  </div>
</template>

<script>
import ThemeButtonComponent from '../darkmode/ThemeButtonComponent.vue';

export default {
    name: 'NavbarComponent',
    components: {
        ThemeButtonComponent,
    }
}
</script>

<style scoped>
    :root {
        --background-color-primary: #ebebeb;
        --background-color-secondary: #fafafa;
        --accent-color: #cacaca;
        --text-primary-color: #222;
        --element-size: 4rem;
    }

    :root.dark-theme {
        --background-color-primary: #1e1e1e;
        --background-color-secondary: #2d2d30;
        --accent-color: #3f3f3f;
        --text-primary-color: #ddd;
        --border-color-primary: #52535b;
    }

    p {
        color: var(--text-primary-color);
    }

    .bg-light {
        background-color: var(--background-color-secondary) !important;
    }

    .navbar-brand {
        color: var(--text-primary-color) !important;
    }

    .nav-link {
        color: var(--text-primary-color) !important;
    }

    .navbar-toggler-icon {
        color: var(--text-primary-color) !important;
    }
</style>