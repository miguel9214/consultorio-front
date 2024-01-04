<template>
    <div class="form full-form auth-cover">
        <div class="form-container">
            <div class="form-form">
                <div class="form-form-wrap">
                    <div class="form-container">
                        <div class="form-content">
                            <h1 class="">Recuperar Contraseña</h1>
                            <p class="signup-link">Ingresa tu correo electrónico y te enviaremos las instrucciones!</p>
                            <form class="text-start">
                                <div class="form">
                                    <div id="email-field" class="field-wrapper input">
                                        <svg
                                            xmlns="http://www.w3.org/2000/svg"
                                            width="24"
                                            height="24"
                                            viewBox="0 0 24 24"
                                            fill="none"
                                            stroke="currentColor"
                                            stroke-width="2"
                                            stroke-linecap="round"
                                            stroke-linejoin="round"
                                            class="feather feather-at-sign"
                                        >
                                            <circle cx="12" cy="12" r="4"></circle>
                                            <path d="M16 8v5a3 3 0 0 0 6 0v-1a10 10 0 1 0-3.92 7.94"></path>
                                        </svg>
                                        <input type="email" class="form-control" placeholder="Correo" />
                                    </div>
                                    <div class="d-sm-flex justify-content-between">
                                        <div class="field-wrapper">
                                            <button type="submit" class="btn btn-primary">Reiniciar</button>
                                        </div>
                                    </div>
                                </div>
                            </form>
                            <p class="terms-conditions">
                                © 2024 Todos los derechos reservados. <router-link to="/">CORK</router-link> es un producto de Arrangic Solutions LLP. <a href="javascript:void(0);">Preferencias de cookies</a>, <a href="javascript:void(0);">Privacidad</a>, y
                                <a href="javascript:void(0);">Terminos</a>.
                            </p>
                        </div>
                    </div>
                </div>
            </div>
            <div class="form-image">
                <div class="l-image"></div>
            </div>
        </div>
    </div>
</template>

<script setup>
    import "/src/assets/sass/authentication/auth.scss";

    import { useMeta } from "/src/composables/use-meta";
    useMeta({ title: "Password Recovery Cover" });
</script>
