<template>
    <div class="form full-form auth-cover">
        <div class="form-container">
            <div class="form-form">
                <div class="form-form-wrap">
                    <div class="form-container">
                        <div class="form-content">
                            <h1 class="text-center">Registarte ó Crea tu cuenta</h1>
                            <p class="signup-link text-center">Ya tienes una cuenta? <router-link
                                    to="/auth/login">Ingresar</router-link></p>
                            <div class="row">
                                <div class="col-md-6">
                                    <form class="text-start">
                                        <div class="form">
                                            <!-- Tipo de Documento -->
                                            <div id="document-type-field" class="field-wrapper input">
                                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24"
                                                    viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
                                                    stroke-linecap="round" stroke-linejoin="round"
                                                    class="feather feather-document">
                                                    <rect x="2" y="2" width="20" height="20" rx="2" ry="2"></rect>
                                                    <line x1="9" y1="2" x2="9" y2="22"></line>
                                                    <line x1="15" y1="2" x2="15" y2="22"></line>
                                                </svg>
                                                <div style="margin-top: 1px">
                                                    <select v-model="formData.type_document"
                                                        class="form-control form-control-sm border-0 pt-0"
                                                        style="margin-left: 25px; width: 220px; font-family: inherit; font-weight: 600; font-size: 16px; padding: 1px 16px 9px 8px"
                                                        tabindex="1">
                                                        <option style="margin: 1px" value="" disabled selected>Tipo de
                                                            Documento</option>
                                                        <option value="RC">RC</option>
                                                        <option value="TI">TI</option>
                                                        <option value="CC">CC</option>
                                                        <option value="EX">EX</option>
                                                    </select>
                                                </div>

                                                <hr class="m-0 border-top-0"
                                                    style="border: 0.8px solid #bfc9d4; height: 0.8px" />

                                                <template v-if="errors.type_document.length > 0">
                                                    <b :key="e" v-for="e in errors.type_document" class="text-danger">
                                                        {{ e }}
                                                    </b>
                                                </template>
                                            </div>
                                            <!-- Nombre -->
                                            <div id="username-field" class="field-wrapper input">
                                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24"
                                                    viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
                                                    stroke-linecap="round" stroke-linejoin="round"
                                                    class="feather feather-user">
                                                    <path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"></path>
                                                    <circle cx="12" cy="7" r="4"></circle>
                                                </svg>
                                                <input v-model="formData.first_name" type="text" class="form-control"
                                                    placeholder="Nombre(s)" tabindex="3" />

                                                <template v-if="errors.first_name.length > 0">
                                                    <b :key="e" v-for="e in errors.first_name" class="text-danger">
                                                        {{ e }}
                                                    </b>
                                                </template>
                                            </div>
                                            <!-- Telefono -->
                                            <div id="username-field" class="field-wrapper input">
                                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24"
                                                    viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
                                                    stroke-linecap="round" stroke-linejoin="round"
                                                    class="feather feather-phone">
                                                    <!-- Auricular -->
                                                    <path
                                                        d="M22 6.6c0-1.07-.18-2.12-.47-3.13a1 1 0 0 0-1.62-.67c-2.6 2.25-5.61 3.41-8.72 3.52-1.11.04-2.18-.17-3.14-.56-.41-.17-.85-.32-1.29-.45a1 1 0 0 0-1.25.63l-1.85 5.55a1 1 0 0 0 .64 1.25c.18.07.36.1.54.1.41 0 .81-.16 1.11-.45.06-.05.12-.11.17-.17 1.67-1.67 3.65-2.92 5.8-3.67a1 1 0 0 0 .63-1.25l-1.89-5.66a1 1 0 0 0-1.25-.63c-.41.17-.85.32-1.29.45-1.05.42-2.14.6-3.23.56C4.89 4.88 2 7.87 2 11.4c0 3.5 2.89 6.5 6.5 6.5 3.44 0 6.31-2.73 6.48-6.13a13.77 13.77 0 0 0 1.97.14c.74 0 1.47-.07 2.2-.2a1 1 0 0 0 .93-1.05V7.62a1 1 0 0 0-.47-.84z">
                                                    </path>
                                                </svg>
                                                <input v-model="formData.phone" type="number" class="form-control"
                                                    placeholder="Teléfono" tabindex="5" />

                                                <template v-if="errors.phone.length > 0">
                                                    <b :key="e" v-for="e in errors.phone" class="text-danger">
                                                        {{ e }}
                                                    </b>
                                                </template>
                                            </div>
                                            <!-- Fecha de Nacimiento -->
                                            <div id="username-field" class="field-wrapper input">
                                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24"
                                                    viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
                                                    stroke-linecap="round" stroke-linejoin="round"
                                                    class="feather feather-calendar">
                                                    <rect x="2" y="2" width="20" height="20" rx="2" ry="2"></rect>
                                                    <line x1="6" y1="2" x2="18" y2="2"></line>
                                                    <line x1="6" y1="22" x2="18" y2="22"></line>
                                                    <line x1="8" y1="2" x2="8" y2="6"></line>
                                                    <line x1="12" y1="2" x2="12" y2="6"></line>
                                                    <line x1="16" y1="2" x2="16" y2="6"></line>
                                                    <circle cx="12" cy="15" r="2"></circle>
                                                </svg>
                                                <input v-model="formData.birthdate" type="date" class="form-control"
                                                    placeholder="Fecha de Nacimiento" tabindex="7" />

                                                <template v-if="errors.birthdate.length > 0">
                                                    <b :key="e" v-for="e in errors.birthdate" class="text-danger">
                                                        {{ e }}
                                                    </b>
                                                </template>
                                            </div>
                                            <!-- Ciudad -->
                                            <div id="city-field" class="field-wrapper input">
                                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24"
                                                    viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
                                                    stroke-linecap="round" stroke-linejoin="round"
                                                    class="feather feather-building">
                                                    <!-- Edificio -->
                                                    <rect x="3" y="6" width="18" height="14"></rect>
                                                    <path d="M9 6v8m0-8l6 4.5M3 6l6 4.5"></path>
                                                </svg>
                                                <input v-model="formData.city" type="text" class="form-control"
                                                    placeholder="Ciudad" tabindex="9" />

                                                <template v-if="errors.city.length > 0">
                                                    <b :key="e" v-for="e in errors.city" class="text-danger">
                                                        {{ e }}
                                                    </b>
                                                </template>
                                            </div>
                                            <!-- Direccion -->
                                            <div id="city-field" class="field-wrapper input">
                                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24"
                                                    viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
                                                    stroke-linecap="round" stroke-linejoin="round"
                                                    class="feather feather-building">
                                                    <!-- Edificio -->
                                                    <rect x="3" y="6" width="18" height="14"></rect>
                                                    <path d="M9 6v8m0-8l6 4.5M3 6l6 4.5"></path>
                                                </svg>
                                                <input v-model="formData.address" type="text" class="form-control"
                                                    placeholder="Dirección" tabindex="11" />

                                                <template v-if="errors.address.length > 0">
                                                    <b :key="e" v-for="e in errors.address" class="text-danger">
                                                        {{ e }}
                                                    </b>
                                                </template>
                                            </div>
                                            <!-- Tipo de Afiliacion -->
                                            <div id="affiliation-type-field" class="field-wrapper input">
                                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24"
                                                    viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
                                                    stroke-linecap="round" stroke-linejoin="round"
                                                    class="feather feather-affiliation-type">
                                                    <!-- Símbolo de tipo de afiliación -->
                                                    <circle cx="12" cy="12" r="10"></circle>
                                                    <line x1="12" y1="7" x2="12" y2="17"></line>
                                                    <line x1="7" y1="12" x2="17" y2="12"></line>
                                                </svg>
                                                <div style="margin-top: 1px">
                                                    <select v-model="formData.affilliate_type"
                                                        class="form-control form-control-sm p-2 border-0 pt-0"
                                                        style="margin-left: 25px; width: 220px; font-family: inherit; font-weight: 600; font-size: 16px; padding: 1px 16px 9px 16px"
                                                        tabindex="13">
                                                        <option style="margin: 1px" value="" disabled selected>Tipo de
                                                            Afiliación</option>
                                                        <option value="1">Contributivo</option>
                                                        <option value="2">Subsidiado</option>
                                                    </select>
                                                </div>
                                                <hr class="m-0 border-top-0"
                                                    style="border: 0.8px solid #bfc9d4; height: 0.8px" />

                                                <template v-if="errors.affilliate_type.length > 0">
                                                    <b :key="e" v-for="e in errors.affilliate_type" class="text-danger">
                                                        {{ e }}
                                                    </b>
                                                </template>
                                            </div>
                                            <!-- Contraseña -->
                                            <div id="password-field" class="field-wrapper input mb-2">
                                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24"
                                                    viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
                                                    stroke-linecap="round" stroke-linejoin="round"
                                                    class="feather feather-lock">
                                                    <rect x="3" y="11" width="18" height="11" rx="2" ry="2"></rect>
                                                    <path d="M7 11V7a5 5 0 0 1 10 0v4"></path>
                                                </svg>
                                                <input v-model="formData.password" :type="showPassword ? 'text' : 'password'" class="form-control"
                                                    placeholder="Contraseña" tabindex="15" />

                                                <template v-if="errors.password.length > 0">
                                                    <b :key="e" v-for="e in errors.password" class="text-danger">
                                                        {{ e }}
                                                    </b>
                                                </template>
                                            </div>
                                        </div>
                                    </form>
                                </div>
                                <div class="col-md-6">
                                    <form class="text-start">
                                        <div class="form">
                                            <!-- Documento -->
                                            <div id="username-field" class="field-wrapper input">
                                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24"
                                                    viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
                                                    stroke-linecap="round" stroke-linejoin="round"
                                                    class="feather feather-id-card">
                                                    <rect x="2" y="2" width="20" height="20" rx="2" ry="2"></rect>
                                                    <line x1="6" y1="2" x2="6" y2="22"></line>
                                                    <line x1="18" y1="2" x2="18" y2="22"></line>
                                                    <circle cx="12" cy="8" r="3"></circle>
                                                    <line x1="6" y1="15" x2="18" y2="15"></line>
                                                    <line x1="6" y1="18" x2="18" y2="18"></line>
                                                </svg>
                                                <input v-model="formData.document" type="number" class="form-control"
                                                    placeholder="Documento" tabindex="2" />

                                                <template v-if="errors.document.length > 0">
                                                    <b :key="e" v-for="e in errors.document" class="text-danger">
                                                        {{ e }}
                                                    </b>
                                                </template>
                                            </div>
                                            <!-- Apellidos -->
                                            <div id="username-field" class="field-wrapper input">
                                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24"
                                                    viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
                                                    stroke-linecap="round" stroke-linejoin="round"
                                                    class="feather feather-user">
                                                    <path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"></path>
                                                    <circle cx="12" cy="7" r="4"></circle>
                                                </svg>
                                                <input v-model="formData.last_name" type="text" class="form-control"
                                                    placeholder="Apellido(s)" tabindex="4" />

                                                <template v-if="errors.last_name.length > 0">
                                                    <b :key="e" v-for="e in errors.last_name" class="text-danger">
                                                        {{ e }}
                                                    </b>
                                                </template>
                                            </div>
                                            <!-- Sexo -->
                                            <div id="gender-field" class="field-wrapper input">
                                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24"
                                                    viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
                                                    stroke-linecap="round" stroke-linejoin="round"
                                                    class="feather feather-gender">
                                                    <!-- Símbolo de género -->
                                                    <circle cx="12" cy="12" r="10"></circle>
                                                    <line x1="12" y1="2" x2="12" y2="22"></line>
                                                    <line x1="2" y1="12" x2="22" y2="12"></line>
                                                </svg>
                                                <div style="margin-top: 1px">
                                                    <select v-model="formData.sex"
                                                        class="form-control form-control-sm p-2 border-0 pt-0"
                                                        style="margin-left: 25px; width: 220px; font-family: inherit; font-weight: 600; font-size: 16px; padding: 1px 16px 9px 16px"
                                                        tabindex="6">
                                                        <option style="margin: 1px" value="" disabled selected>Genero
                                                        </option>
                                                        <option value="1">Masculino</option>
                                                        <option value="2">Femenino</option>
                                                    </select>
                                                </div>
                                                <hr class="m-0 border-top-0"
                                                    style="border: 0.8px solid #bfc9d4; height: 0.8px" />

                                                <template v-if="errors.sex.length > 0">
                                                    <b :key="e" v-for="e in errors.sex" class="text-danger">
                                                        {{ e }}
                                                    </b>
                                                </template>
                                            </div>
                                            <!-- Correo -->
                                            <div id="email-field" class="field-wrapper input">
                                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24"
                                                    viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
                                                    stroke-linecap="round" stroke-linejoin="round"
                                                    class="feather feather-at-sign">
                                                    <circle cx="12" cy="12" r="4"></circle>
                                                    <path d="M16 8v5a3 3 0 0 0 6 0v-1a10 10 0 1 0-3.92 7.94"></path>
                                                </svg>
                                                <input v-model="formData.email" type="email" class="form-control"
                                                    placeholder="Correo" tabindex="8" />

                                                <template v-if="errors.email.length > 0">
                                                    <b :key="e" v-for="e in errors.email" class="text-danger">
                                                        {{ e }}
                                                    </b>
                                                </template>
                                            </div>
                                            <!-- Departamento -->
                                            <div id="region-field" class="field-wrapper input">
                                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24"
                                                    viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
                                                    stroke-linecap="round" stroke-linejoin="round"
                                                    class="feather feather-map-pin">
                                                    <!-- Marcador de mapa -->
                                                    <path
                                                        d="M12 2C9.79 2 8 3.79 8 6a4 4 0 0 0 8 0c0-2.21-1.79-4-4-4zM12 14c-2.21 0-4-1.79-4-4 0-3.48 4-9 4-9s4 5.52 4 9c0 2.21-1.79 4-4 4z">
                                                    </path>
                                                    <circle cx="12" cy="10" r="2"></circle>
                                                </svg>
                                                <input v-model="formData.state" type="text" class="form-control"
                                                    placeholder="Región" tabindex="10" />

                                                <template v-if="errors.state.length > 0">
                                                    <b :key="e" v-for="e in errors.state" class="text-danger">
                                                        {{ e }}
                                                    </b>
                                                </template>
                                            </div>
                                            <!-- Barrio -->
                                            <div id="city-field" class="field-wrapper input">
                                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24"
                                                    viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
                                                    stroke-linecap="round" stroke-linejoin="round"
                                                    class="feather feather-building">
                                                    <!-- Edificio -->
                                                    <rect x="3" y="6" width="18" height="14"></rect>
                                                    <path d="M9 6v8m0-8l6 4.5M3 6l6 4.5"></path>
                                                </svg>
                                                <input v-model="formData.neighborhood" type="text" class="form-control"
                                                    placeholder="Barrio" tabindex="12" />

                                                <template v-if="errors.neighborhood.length > 0">
                                                    <b :key="e" v-for="e in errors.neighborhood" class="text-danger">
                                                        {{ e }}
                                                    </b>
                                                </template>
                                            </div>
                                            <!-- EPS -->
                                            <div id="gender-field" class="field-wrapper input">
                                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24"
                                                    viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
                                                    stroke-linecap="round" stroke-linejoin="round"
                                                    class="feather feather-hospital">
                                                    <!-- Símbolo de hospital -->
                                                    <rect x="2" y="2" width="20" height="20" rx="4" ry="4"></rect>
                                                    <line x1="12" y1="7" x2="12" y2="17"></line>
                                                    <line x1="7" y1="12" x2="17" y2="12"></line>
                                                </svg>
                                                <div style="margin-top: 1px">
                                                    <select v-model="formData.eps_id"
                                                        class="form-control form-control-sm p-2 border-0 pt-0"
                                                        style="margin-left: 25px; width: 220px; font-family: inherit; font-weight: 600; font-size: 16px; padding: 1px 16px 9px 16px"
                                                        tabindex="14">
                                                        <option style="margin: 1px" value="" disabled selected>EPS</option>
                                                        <option value="1">EPS Sanitas</option>
                                                    </select>
                                                </div>
                                                <hr class="m-0 border-top-0"
                                                    style="border: 0.8px solid #bfc9d4; height: 0.8px" />

                                                <template v-if="errors.eps_id.length > 0">
                                                    <b :key="e" v-for="e in errors.eps_id" class="text-danger">
                                                        {{ e }}
                                                    </b>
                                                </template>
                                            </div>
                                            <!-- Confirmar Contraseña -->
                                            <div id="confirm-password-field" class="field-wrapper input">
                                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24"
                                                    viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
                                                    stroke-linecap="round" stroke-linejoin="round"
                                                    class="feather feather-lock">
                                                    <!-- Forma de candado -->
                                                    <rect x="3" y="11" width="18" height="11" rx="2" ry="2"></rect>
                                                    <circle cx="9" cy="8" r="4"></circle>
                                                    <path d="M17 11V7a5 5 0 0 0-10 0v4"></path>
                                                </svg>
                                                <input v-model="formData.password_confirmed" :type="showPassword ? 'text' : 'password'"
                                                    class="form-control" placeholder="Confirmar Contraseña" tabindex="16" />

                                                <template v-if="errors.password_confirmed.length > 0">
                                                    <b :key="e" v-for="e in errors.password_confirmed" class="text-danger">
                                                        {{ e }}
                                                    </b>
                                                </template>
                                            </div>
                                        </div>
                                    </form>
                                </div>
                            </div>
                            <div>
                                <div class="field-wrapper terms_condition">
                                    <div class="checkbox-outline-primary custom-control custom-checkbox">
                                        <input type="checkbox" class="custom-control-input" value="" id="chkTerms"
                                            v-model="formData.termsAccepted" required tabindex="16" />
                                        <label class="custom-control-label" for="chkTerms">
                                            Estoy de acuerdo con los <a href="#" @click="openTermsModal()" class="fw-bold"
                                                style="color: #0d6efd;">términos y condiciones</a>
                                        </label>
                                        <div>
                                            <span v-if="errors.termsAccepted" class="text-danger fw-bold">{{ errors.termsAccepted }}</span>
                                        </div>
                                    </div>
                                </div>
                                <!-- Modal de Términos y Condiciones -->
                                <div class="modal fade" id="termsModal" tabindex="-1" aria-labelledby="termsModalLabel"
                                    aria-hidden="true">
                                    <div class="modal-dialog modal-dialog-centered">
                                        <div class="modal-content">
                                            <div class="modal-header">
                                                <h5 class="modal-title" id="termsModalLabel">Términos y Condiciones</h5>
                                                <button type="button" class="btn-close" data-bs-dismiss="modal"
                                                    aria-label="Close"></button>
                                            </div>
                                            <div class="modal-body">
                                                <div class="font-monospace">
                                                    <p class="fw-bold">Términos y Condiciones del Consultorio Médico</p>

                                                    <p>
                                                        Bienvenido a nuestro consultorio médico. Antes de utilizar nuestros
                                                        servicios, te pedimos que leas detenidamente estos términos y
                                                        condiciones.
                                                    </p>

                                                    <p class="fw-bold">1. Aceptación de los Términos</p>

                                                    <p>
                                                        Al acceder y utilizar los servicios de nuestro consultorio médico,
                                                        aceptas cumplir con estos términos y condiciones. Si no estás de acuerdo
                                                        con alguno de estos términos, te instamos a que no utilices nuestros
                                                        servicios.
                                                    </p>

                                                    <p class="fw-bold">2. Uso Responsable</p>

                                                    <p>
                                                        Debes utilizar nuestros servicios de manera responsable y ética. No se
                                                        permite el uso indebido de la información proporcionada ni la violación
                                                        de la privacidad de otros usuarios.
                                                    </p>

                                                    <p class="fw-bold">3. Citas y Cancelaciones</p>

                                                    <p>
                                                        Te comprometes a cumplir con las citas programadas y a notificar con
                                                        anticipación si necesitas cancelar o reprogramar. Podrían aplicarse
                                                        cargos por cancelaciones tardías o falta de asistencia.
                                                    </p>

                                                    <p class="fw-bold">4. Información del Paciente</p>

                                                    <p>
                                                        Toda la información proporcionada al consultorio, ya sea personal o
                                                        médica, se manejará de acuerdo con nuestra política de privacidad. Nos
                                                        comprometemos a proteger la confidencialidad de tus datos.
                                                    </p>

                                                    <p class="fw-bold">5. Pago de Servicios</p>

                                                    <p>
                                                        Los servicios prestados por el consultorio están sujetos a tarifas y
                                                        pagos específicos. Asegúrate de comprender y aceptar las tarifas antes
                                                        de recibir los servicios. Los pagos deben realizarse según las políticas
                                                        establecidas.
                                                    </p>

                                                    <p class="fw-bold">6. Derechos de Propiedad Intelectual</p>

                                                    <p>
                                                        Todos los contenidos y materiales proporcionados por el consultorio,
                                                        incluyendo pero no limitado a textos, imágenes y logotipos, son
                                                        propiedad intelectual del consultorio y no pueden ser utilizados sin
                                                        autorización.
                                                    </p>

                                                    <p class="fw-bold">7. Cambios en los Términos</p>

                                                    <p>
                                                        El consultorio se reserva el derecho de modificar estos términos y
                                                        condiciones en cualquier momento. Las modificaciones entrarán en
                                                        vigencia tan pronto como se publiquen en nuestro sitio web.
                                                    </p>

                                                    <p class="fw-bold">8. Jurisdicción y Ley Aplicable</p>

                                                    <p>
                                                        Estos términos y condiciones están sujetos a las leyes de [jurisdicción]
                                                        y cualquier disputa se resolverá mediante arbitraje de conformidad con
                                                        dichas leyes.
                                                    </p>

                                                    <p>
                                                        Gracias por elegir nuestro consultorio médico. Si tienes alguna pregunta
                                                        o inquietud, no dudes en contactarnos.
                                                    </p>
                                                </div>
                                            </div>
                                            <div class="modal-footer mt-lg-2">
                                                <button type="button" class="btn btn-primary"
                                                    data-bs-dismiss="modal">Cerrar</button>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <div class="d-sm-flex justify-content-between">
                                <div class="field-wrapper toggle-pass d-flex align-items-center">
                                    <p class="d-inline-block">Mostrar Contraseña</p>
                                    <label class="switch s-primary mx-2">
                                        <input type="checkbox" class="custom-control-input" v-model="showPassword" tabindex="16" />
                                        <span class="slider round"></span>
                                    </label>
                                </div>
                                <div class="field-wrapper mt-lg-2">
                                    <button type="submit" class="btn btn-primary" tabindex="17"
                                        @click="registerUser">Registrarse!</button>
                                </div>
                            </div>
                            <p class="terms-conditions">
                                © 2024 Todos los derechos reservados. <router-link to="/">CORK</router-link> es un producto
                                de Arrangic Solutions LLP.
                                <a href="javascript:void(0);">Preferencias de cookies</a>,
                                <a href="javascript:void(0);">Privacidad</a>, y <a href="javascript:void(0);">Terminos</a>.
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
import '/src/assets/sass/authentication/auth.scss';

import { useMeta } from '/src/composables/use-meta';
import { useRouter } from 'vue-router';
useMeta({ title: 'Register Cover' });
const router = useRouter();

import { ref, onBeforeMount } from 'vue';
import axios from 'axios';
import Swal from 'sweetalert2';

const showPassword = ref(false);

const formData = ref({
    type_document: '',
    document: '',
    first_name: '',
    last_name: '',
    sex: '',
    phone: '',
    birthdate: '',
    address: '',
    city: '',
    state: '',
    neighborhood: '',
    email: '',
    password: '',
    password_confirmed: '',
    affilliate_type: '',
    eps_id: 1,
    termsAccepted: '',
});

const errors = ref({
    type_document: [],
    document: [],
    first_name: [],
    last_name: [],
    sex: [],
    phone: [],
    birthdate: [],
    address: [],
    city: [],
    state: [],
    neighborhood: [],
    email: [],
    password: [],
    password_confirmed: [],
    affilliate_type: [],
    eps_id: [],
    termsAccepted: '',
});

const registerUser = async () => {
    errorsClear()

    let has_error = false;
    Object.entries(formData.value).forEach(f => {
        const elemento = f[0]
        const value = f[1]
        if (value == "") {
            has_error = true
            errors.value[elemento] = "Este campo es obligatorio"
        }
    });

    if (has_error) return;

    try {
        const response = await axios.post('http://consultorio.test/api/register', formData.value);

        Swal.fire({
            title: 'Éxito!',
            text: 'Usuario registrado correctamente!',
            icon: 'success',
            confirmButtonText: '¡Entendido!'
        });

        router.push({ name: 'login' })

    } catch (error) {
        if (error.response && error.response.data && error.response.data.errors) {
            const errors_api = error.response.data.errors;
            Object.entries(errors_api).forEach(e => {
                const elemento = e[0]
                const mensaje = e[1]
                errors.value[elemento] = mensaje
            });
        } else {
            alert("server error")
        }
    }
};


const errorsClear = () => {
    errors.value = {
        type_document: [],
        document: [],
        first_name: [],
        last_name: [],
        sex: [],
        phone: [],
        birthdate: [],
        address: [],
        city: [],
        state: [],
        neighborhood: [],
        email: [],
        password: [],
        password_confirmed: [],
        affilliate_type: [],
        eps_id: [],
        termsAccepted: '',
    }
}

const openTermsModal = () => {
    // Abre el modal usando Bootstrap
    const modal = new bootstrap.Modal(document.getElementById('termsModal'), {
        keyboard: false,
        backdrop: 'static'
    });
    modal.show();
};

</script>
