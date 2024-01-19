<template>
    <div class="form full-form auth-cover">
        <div class="form-container">
            <div class="form-form">
                <div class="form-form-wrap">
                    <div class="form-container">
                        <div class="form-content">
                            <h1 class="">
                                Iniciar Sesión en <router-link to="/"><span class="brand-name">CORK</span></router-link>
                            </h1>
                            <p class="signup-link">Crear Cuenta <router-link to="/auth/register">Aquí?</router-link></p>
                            <form class="text-start" @submit="loginUser">
                                <div class="form">
                                    <div id="username-field" class="field-wrapper input">
                                        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"
                                            fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"
                                            stroke-linejoin="round" class="feather feather-user">
                                            <path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"></path>
                                            <circle cx="12" cy="7" r="4"></circle>
                                        </svg>
                                        <input v-model="formData.email" type="email" class="form-control"
                                            placeholder="Correo" />
                                    </div>

                                    <div id="password-field" class="field-wrapper input mb-2">
                                        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"
                                            fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"
                                            stroke-linejoin="round" class="feather feather-lock">
                                            <rect x="3" y="11" width="18" height="11" rx="2" ry="2"></rect>
                                            <path d="M7 11V7a5 5 0 0 1 10 0v4"></path>
                                        </svg>
                                        <input v-model="formData.password" type="password" class="form-control"
                                            placeholder="Contraseña" />
                                    </div>
                                    <div class="d-sm-flex justify-content-between">
                                        <div class="field-wrapper toggle-pass d-flex align-items-center">
                                            <p class="d-inline-block">Mostrar Contraseña</p>
                                            <label class="switch s-primary mx-2">
                                                <input type="checkbox" class="custom-control-input" checked="" />
                                                <span class="slider round"></span>
                                            </label>
                                        </div>
                                        <div class="field-wrapper">
                                            <button type="submit" class="btn btn-primary">Iniciar</button>
                                        </div>
                                    </div>

                                    <div class="field-wrapper text-center keep-logged-in">
                                        <div class="checkbox-outline-primary custom-control custom-checkbox">
                                            <input type="checkbox" class="custom-control-input" value="true"
                                                id="chkRemember" />
                                            <label class="custom-control-label" for="chkRemember">Mantenme conectado</label>
                                        </div>
                                    </div>

                                    <div class="field-wrapper">
                                        <router-link to="/auth/pass-recovery" class="forgot-pass-link">Has olvidado tu
                                            contraseña?</router-link>
                                    </div>
                                </div>
                            </form>
                            <p class="terms-conditions">
                                © 2024 Todos los derechos reservados. <router-link to="/">CORK</router-link> es un producto
                                de Arrangic Solutions LLP. <a href="javascript:void(0);">Preferencias de cookies</a>, <a
                                    href="javascript:void(0);">Privacidad</a>, y
                                <a href="javascript:void(0);">Terminos</a>.
                            </p>
                        </div>
                    </div>
                </div>
            </div>
            <div class="form-image">
                <div class="l-image" ></div>
            </div>
        </div>
    </div>
</template>

<script setup>

import "/src/assets/sass/authentication/auth.scss";
import { ref, onBeforeMount } from 'vue';
import Swal from 'sweetalert2';
import { useMeta } from "/src/composables/use-meta";
import axios from "axios";


useMeta({ title: "Login Cover" });

const formData = ref({
    email: '',
    password: '',
});

const loginUser = async (event) => {
    event.preventDefault();
    if (!formData.value.email
        || !formData.value.password) {
        Swal.fire({
            title: 'Error!',
            text: 'Debe llenar todos los campos',
            icon: 'error',
            confirmButtonText: '¡Entendido!'
        });
        return;
    }

    try {
        const response = await axios.post('http://consultorio.test/api/login', formData.value,{
            headers: {
                Accept: 'application/json',
                'Content-Type': 'application/json',
                Authorization: `Bearer ${token}`, 
            },
        }
        );
        console.log(response);
        Swal.fire({
            title: response.data.message,
            icon: 'success',
            confirmButtonText: '¡Entendido!'
        });

        // se debe redirigir
    } catch (error) {
        Swal.fire({
            title: 'Error!',
            // text: error.response.data.message,
            icon: 'error',
            confirmButtonText: '¡Entendido!'
        });
    }

};
</script>
