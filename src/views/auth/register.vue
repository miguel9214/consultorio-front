<template>
    <div class="form full-form auth-cover">
        <div class="form-container">
            <div class="form-form">
                <div class="form-form-wrap">
                    <div class="form-container">
                        <div class="form-content">
                            <h1 class="text-center">
                                Registarte ó Crea tu cuenta
                            </h1>
                            <p class="signup-link text-center">Ya tienes una cuenta? <router-link to="/auth/login">Ingresar</router-link></p>
                            <div class="row">
                                <div class="col-md-6">
                                    <form class="text-start">
                                        <div class="form">
                                            <!-- Tipo de Documento -->
                                            <div id="document-type-field" class="field-wrapper input">
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
                                                    class="feather feather-document"
                                                >
                                                    <rect x="2" y="2" width="20" height="20" rx="2" ry="2"></rect>
                                                    <line x1="9" y1="2" x2="9" y2="22"></line>
                                                    <line x1="15" y1="2" x2="15" y2="22"></line>
                                                </svg>
                                                <div style="margin-top: 1px">
                                                    <select class="form-control form-control-sm border-0 pt-0" style="margin-left: 25px; width: 220px; font-family: inherit; font-weight: 600; font-size: 16px; padding: 1px 16px 9px 8px;">
                                                        <option style="margin: 1px" value="RC" disabled selected>Tipo de Documento</option>
                                                        <option value="RC">RC</option>
                                                        <option value="TI">TI</option>
                                                        <option value="CC">CC</option>
                                                        <option value="EX">EX</option>
                                                    </select>
                                                </div>
                                                
                                                <hr class="m-0 border-top-0" style="border: 0.8px solid #bfc9d4; height: 0.8px;">
                                            </div>                                            
                                            <!-- Nombre -->
                                            <div id="username-field" class="field-wrapper input">
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
                                                    class="feather feather-user"
                                                >
                                                    <path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"></path>
                                                    <circle cx="12" cy="7" r="4"></circle>
                                                </svg>
                                                <input type="text" class="form-control" placeholder="Nombre(s)" />
                                            </div>
                                            <!-- Telefono -->
                                            <div id="username-field" class="field-wrapper input">
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
                                                    class="feather feather-phone"
                                                >
                                                    <!-- Auricular -->
                                                    <path d="M22 6.6c0-1.07-.18-2.12-.47-3.13a1 1 0 0 0-1.62-.67c-2.6 2.25-5.61 3.41-8.72 3.52-1.11.04-2.18-.17-3.14-.56-.41-.17-.85-.32-1.29-.45a1 1 0 0 0-1.25.63l-1.85 5.55a1 1 0 0 0 .64 1.25c.18.07.36.1.54.1.41 0 .81-.16 1.11-.45.06-.05.12-.11.17-.17 1.67-1.67 3.65-2.92 5.8-3.67a1 1 0 0 0 .63-1.25l-1.89-5.66a1 1 0 0 0-1.25-.63c-.41.17-.85.32-1.29.45-1.05.42-2.14.6-3.23.56C4.89 4.88 2 7.87 2 11.4c0 3.5 2.89 6.5 6.5 6.5 3.44 0 6.31-2.73 6.48-6.13a13.77 13.77 0 0 0 1.97.14c.74 0 1.47-.07 2.2-.2a1 1 0 0 0 .93-1.05V7.62a1 1 0 0 0-.47-.84z"></path>
                                                </svg>
                                                <input type="text" class="form-control" placeholder="Teléfono" />
                                            </div>
                                            <!-- Fecha de Nacimiento -->
                                            <div id="username-field" class="field-wrapper input">
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
                                                    class="feather feather-calendar"
                                                >
                                                    <rect x="2" y="2" width="20" height="20" rx="2" ry="2"></rect>
                                                    <line x1="6" y1="2" x2="18" y2="2"></line>
                                                    <line x1="6" y1="22" x2="18" y2="22"></line>
                                                    <line x1="8" y1="2" x2="8" y2="6"></line>
                                                    <line x1="12" y1="2" x2="12" y2="6"></line>
                                                    <line x1="16" y1="2" x2="16" y2="6"></line>
                                                    <circle cx="12" cy="15" r="2"></circle>
                                                </svg>
                                                <input type="text" class="form-control" placeholder="Fecha de Nacimiento" />
                                            </div>
                                            <!-- Ciudad -->
                                            <div id="city-field" class="field-wrapper input">
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
                                                    class="feather feather-building"
                                                >
                                                    <!-- Edificio -->
                                                    <rect x="3" y="6" width="18" height="14"></rect>
                                                    <path d="M9 6v8m0-8l6 4.5M3 6l6 4.5"></path>
                                                </svg>
                                                <input type="text" class="form-control" placeholder="Ciudad" />
                                            </div>
                                            <!-- Contraseña -->
                                            <div id="password-field" class="field-wrapper input mb-2">
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
                                                    class="feather feather-lock"
                                                >
                                                    <rect x="3" y="11" width="18" height="11" rx="2" ry="2"></rect>
                                                    <path d="M7 11V7a5 5 0 0 1 10 0v4"></path>
                                                </svg>
                                                <input type="password" class="form-control" placeholder="Contraseña" />
                                            </div>

                                        </div>
                                    </form>
                                </div>
                                <div class="col-md-6">
                                    <form class="text-start">
                                        <div class="form">
                                            <!-- Documento -->
                                            <div id="username-field" class="field-wrapper input">
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
                                                    class="feather feather-id-card"
                                                >
                                                    <rect x="2" y="2" width="20" height="20" rx="2" ry="2"></rect>
                                                    <line x1="6" y1="2" x2="6" y2="22"></line>
                                                    <line x1="18" y1="2" x2="18" y2="22"></line>
                                                    <circle cx="12" cy="8" r="3"></circle>
                                                    <line x1="6" y1="15" x2="18" y2="15"></line>
                                                    <line x1="6" y1="18" x2="18" y2="18"></line>
                                                </svg>
                                                <input type="text" class="form-control" placeholder="Documento" />
                                            </div>
                                            <!-- Apellidos -->
                                            <div id="username-field" class="field-wrapper input">
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
                                                    class="feather feather-user"
                                                >
                                                    <path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"></path>
                                                    <circle cx="12" cy="7" r="4"></circle>
                                                </svg>
                                                <input type="text" class="form-control" placeholder="Apellido(s)" />
                                            </div>
                                            <!-- Sexo -->
                                            <div id="gender-field" class="field-wrapper input">
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
                                                    class="feather feather-gender"
                                                >
                                                    <!-- Símbolo de género -->
                                                    <circle cx="12" cy="12" r="10"></circle>
                                                    <line x1="12" y1="2" x2="12" y2="22"></line>
                                                    <line x1="2" y1="12" x2="22" y2="12"></line>
                                                </svg>
                                                <div style="margin-top: 1px">
                                                    <select class="form-control form-control-sm p-2 border-0 pt-0" style="margin-left: 25px; width: 220px; font-family: inherit; font-weight: 600; font-size: 16px; padding: 1px 16px 9px 16px;">
                                                        <option style="margin: 1px" value="RC" disabled selected>Genero</option>
                                                        <option value="1">Masculino</option>
                                                        <option value="2">Femenino</option>
                                                    </select>
                                                </div>
                                                <hr class="m-0 border-top-0" style="border: 0.8px solid #bfc9d4; height: 0.8px;">

                                            </div>
                                            <!-- Correo -->
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
                                            <!-- Departamento -->
                                            <div id="region-field" class="field-wrapper input">
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
                                                    class="feather feather-map-pin"
                                                >
                                                    <!-- Marcador de mapa -->
                                                    <path d="M12 2C9.79 2 8 3.79 8 6a4 4 0 0 0 8 0c0-2.21-1.79-4-4-4zM12 14c-2.21 0-4-1.79-4-4 0-3.48 4-9 4-9s4 5.52 4 9c0 2.21-1.79 4-4 4z"></path>
                                                    <circle cx="12" cy="10" r="2"></circle>
                                                </svg>
                                                <input type="text" class="form-control" placeholder="Región" />
                                            </div>                                            
                                            <!-- Confirmar Contraseña -->
                                            <div id="confirm-password-field" class="field-wrapper input">
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
                                                    class="feather feather-lock"
                                                >
                                                    <!-- Forma de candado -->
                                                    <rect x="3" y="11" width="18" height="11" rx="2" ry="2"></rect>
                                                    <circle cx="9" cy="8" r="4"></circle>
                                                    <path d="M17 11V7a5 5 0 0 0-10 0v4"></path>
                                                </svg>
                                                <input type="password" class="form-control" placeholder="Confirmar Contraseña" />
                                            </div>                                         

                                        </div>
                                    </form>
                                </div>
                            </div>
                            <div class="field-wrapper terms_condition">
                                <div class="checkbox-outline-primary custom-control custom-checkbox">
                                    <input type="checkbox" class="custom-control-input" value="true" id="chkTerms" />
                                    <label class="custom-control-label" for="chkTerms">Estoy de acuerdo con los <a href="javascript:void(0);"> terminos y condiciones </a></label>
                                </div>
                            </div>
                            <div class="d-sm-flex justify-content-between">
                                <div class="field-wrapper toggle-pass d-flex align-items-center">
                                    <p class="d-inline-block">Mostrar Contraseña</p>
                                    <label class="switch s-primary mx-2">
                                        <input type="checkbox" class="custom-control-input" checked="" />
                                        <span class="slider round"></span>
                                    </label>
                                </div>
                                <div class="field-wrapper mt-lg-2">
                                    <button type="submit" class="btn btn-primary">Iniciar!</button>
                                </div>
                            </div>
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
    useMeta({ title: "Register Cover" });
</script>
