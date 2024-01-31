<template>
    <!--  BEGIN SIDEBAR  -->
    <div class="sidebar-wrapper sidebar-theme">
        <nav ref="menu" id="sidebar">
            <div class="shadow-bottom"></div>

            <perfect-scrollbar class="list-unstyled menu-categories" tag="ul"
                :options="{ wheelSpeed: 0.5, swipeEasing: !0, minScrollbarLength: 40, maxScrollbarLength: 300, suppressScrollX: true }">
                <!-- DASHBOARD -->
                <li class="menu">
                    <a class="dropdown-toggle" data-bs-toggle="collapse" data-bs-target="#dashboard"
                        aria-controls="dashboard" aria-expanded="false">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-home">
                                <path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"></path>
                                <polyline points="9 22 9 12 15 12 15 22"></polyline>
                            </svg>
                            <span>{{ $t('dashboard') }}</span>
                        </div>
                        <div>
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-chevron-right">
                                <polyline points="9 18 15 12 9 6"></polyline>
                            </svg>
                        </div>
                    </a>

                    <ul id="dashboard" class="collapse submenu list-unstyled" data-bs-parent="#sidebar">
                        <li>
                            <router-link to="/" @click="toggleMobileMenu">
                                {{ $t('sales') }}
                            </router-link>
                        </li>
                        <li>
                            <router-link to="/index2" @click="toggleMobileMenu">
                                {{ $t('analytics') }}
                            </router-link>
                        </li>
                    </ul>
                </li>
                <!-- EPS -->
                <li class="menu">
                    <router-link to="/eps" class="dropdown-toggle" @click="toggleMobileMenu">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" height="24" width="24">
                                <path stroke="#000000" stroke-linecap="round" stroke-linejoin="round"
                                    d="m0.887648 4.98462 10.957352 0 0 17.97718 -10.957353 0L0.887648 4.98462Z"
                                    stroke-width="1"></path>
                                <path stroke="#000000" stroke-linecap="round" stroke-linejoin="round"
                                    d="m11.845 15.0571 8.0263 0 0 7.9045 -8.0263 0 0 -7.9045Z" stroke-width="1"></path>
                                <path stroke="#000000" stroke-linecap="round" stroke-linejoin="round"
                                    d="M4.89282 12.8594V8.43848m2.94728 0v4.42092m-2.94728 -2.3947H7.8401" stroke-width="1">
                                </path>
                                <path stroke="#000000" stroke-linecap="round" stroke-linejoin="round"
                                    d="M23.1123 4.57532c0 2.03401 -3.6759 6.94338 -3.6759 6.94338s-3.6759 -4.90937 -3.6759 -6.94338c0 -0.97491 0.3873 -1.90989 1.0766 -2.59926 0.6894 -0.68936 1.6244 -1.076646 2.5993 -1.076646 0.9749 0 1.9099 0.387286 2.5993 1.076646 0.6893 0.68937 1.0766 1.62435 1.0766 2.59926v0Z"
                                    stroke-width="1"></path>
                                <path stroke="#000000" stroke-linecap="round" stroke-linejoin="round"
                                    d="M19.4364 5.80764c0.7091 0 1.284 -0.57487 1.284 -1.28401 0 -0.70914 -0.5749 -1.28401 -1.284 -1.28401 -0.7092 0 -1.2841 0.57487 -1.2841 1.28401 0 0.70914 0.5749 1.28401 1.2841 1.28401Z"
                                    stroke-width="1"></path>
                                <path stroke="#000000" stroke-linecap="round" stroke-linejoin="round"
                                    d="m4.77783 18.4926 3.17676 0 0 4.4692 -3.17676 0 0 -4.4692Z" stroke-width="1"></path>
                            </svg>
                            <span>{{ $t('EPS') }}</span>
                        </div>
                    </router-link>
                </li>
                <!-- MEDICO -->
                <li class="menu">
                    <router-link to="/medico" class="dropdown-toggle" @click="toggleMobileMenu">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" height="24" width="24">
                                <path stroke="#000000" stroke-linecap="round" stroke-linejoin="round"
                                    d="M13.5 11c-0.4327 0.3246 -0.9591 0.5 -1.5 0.5s-1.0673 -0.1754 -1.5 -0.5"
                                    stroke-width="1"></path>
                                <path stroke="#000000" stroke-linecap="round" stroke-linejoin="round"
                                    d="M23 23.5v-3.106c0.0022 -0.3047 -0.0663 -0.6059 -0.1998 -0.8798 -0.1336 -0.2739 -0.3287 -0.5132 -0.5702 -0.6992C20.9 17.8 17.73 16 12 16c-5.72995 0 -8.89495 1.8 -10.22995 2.815 -0.24142 0.186 -0.43655 0.4253 -0.57012 0.6992 -0.13358 0.2739 -0.201991 0.5751 -0.19988 0.8798V23.5"
                                    stroke-width="1"></path>
                                <path stroke="#000000" stroke-linecap="round" stroke-linejoin="round"
                                    d="M18 6.5c0 -1.5913 -0.6321 -3.11742 -1.7574 -4.24264C15.1174 1.13214 13.5913 0.5 12 0.5c-1.5913 0 -3.11742 0.63214 -4.24264 1.75736C6.63214 3.38258 6 4.9087 6 6.5v2c0 1.5913 0.63214 3.1174 1.75736 4.2426C8.88258 13.8679 10.4087 14.5 12 14.5s3.1174 -0.6321 4.2426 -1.7574C17.3679 11.6174 18 10.0913 18 8.5v-2Z"
                                    stroke-width="1"></path>
                                <path stroke="#000000" stroke-linecap="round" stroke-linejoin="round"
                                    d="M18 6.5c-1.327 0 -4.058 0.337 -6 -2 -1.942 2.337 -4.673 2 -6 2" stroke-width="1">
                                </path>
                                <path stroke="#000000" stroke-linecap="round" stroke-linejoin="round" d="M12 16v7.5"
                                    stroke-width="1"></path>
                                <path stroke="#000000" stroke-linecap="round" stroke-linejoin="round"
                                    d="M7 23.5c0.82843 0 1.5 -0.6716 1.5 -1.5s-0.67157 -1.5 -1.5 -1.5 -1.5 0.6716 -1.5 1.5 0.67157 1.5 1.5 1.5Z"
                                    stroke-width="1"></path>
                                <path stroke="#000000" stroke-linecap="round" stroke-linejoin="round" d="M7 20.5v-5"
                                    stroke-width="1"></path>
                                <path stroke="#000000" stroke-linecap="round" stroke-linejoin="round" d="M17 20.5v-5"
                                    stroke-width="1"></path>
                                <path stroke="#000000" stroke-linecap="round" stroke-linejoin="round"
                                    d="m19.5 23.5 -0.772 -2.316c-0.0663 -0.1992 -0.1937 -0.3725 -0.364 -0.4952 -0.1704 -0.1228 -0.375 -0.1889 -0.585 -0.1888h-1.558c-0.21 -0.0001 -0.4146 0.066 -0.585 0.1888 -0.1703 0.1227 -0.2977 0.296 -0.364 0.4952L14.5 23.5"
                                    stroke-width="1"></path>
                                <path stroke="#000000"
                                    d="M10 8.75c-0.13807 0 -0.25 -0.11193 -0.25 -0.25s0.11193 -0.25 0.25 -0.25"
                                    stroke-width="1"></path>
                                <path stroke="#000000"
                                    d="M10 8.75c0.1381 0 0.25 -0.11193 0.25 -0.25s-0.1119 -0.25 -0.25 -0.25"
                                    stroke-width="1"></path>
                                <g>
                                    <path stroke="#000000"
                                        d="M14 8.75c-0.1381 0 -0.25 -0.11193 -0.25 -0.25s0.1119 -0.25 0.25 -0.25"
                                        stroke-width="1"></path>
                                    <path stroke="#000000"
                                        d="M14 8.75c0.1381 0 0.25 -0.11193 0.25 -0.25s-0.1119 -0.25 -0.25 -0.25"
                                        stroke-width="1"></path>
                                </g>
                            </svg>
                            <span>{{ $t('Medicos') }}</span>
                        </div>
                    </router-link>
                </li>
                <!-- CONSULTATION_TYPE -->
                <li class="menu">
                    <router-link to="/consultationType" class="dropdown-toggle" @click="toggleMobileMenu">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" height="24" width="24">
                                <defs></defs>
                                <title>medical-files-medical-check</title>
                                <path
                                    d="M10.5 21.5H2A1.5 1.5 0 0 1 0.5 20V2A1.5 1.5 0 0 1 2 0.5h9.086a1 1 0 0 1 0.707 0.293l4.415 4.415a1 1 0 0 1 0.293 0.707V9.5"
                                    fill="none" stroke="#000000" stroke-linecap="round" stroke-linejoin="round"
                                    stroke-width="1"></path>
                                <path d="M11.5 0.59V5a0.5 0.5 0 0 0 0.5 0.5h4.411" fill="none" stroke="#000000"
                                    stroke-linecap="round" stroke-linejoin="round" stroke-width="1"></path>
                                <path d="m8.5 6.75 -3 3L4 8.25" fill="none" stroke="#000000" stroke-linecap="round"
                                    stroke-linejoin="round" stroke-width="1"></path>
                                <path d="m8.5 11.75 -3 3 -1.5 -1.5" fill="none" stroke="#000000" stroke-linecap="round"
                                    stroke-linejoin="round" stroke-width="1"></path>
                                <path d="M11.5 17.5a6 6 0 1 0 12 0 6 6 0 1 0 -12 0" fill="none" stroke="#000000"
                                    stroke-linecap="round" stroke-linejoin="round" stroke-width="1"></path>
                                <path
                                    d="M21 17a0.5 0.5 0 0 0 -0.5 -0.5h-2v-2a0.5 0.5 0 0 0 -0.5 -0.5h-1a0.5 0.5 0 0 0 -0.5 0.5v2h-2a0.5 0.5 0 0 0 -0.5 0.5v1a0.5 0.5 0 0 0 0.5 0.5h2v2a0.5 0.5 0 0 0 0.5 0.5h1a0.5 0.5 0 0 0 0.5 -0.5v-2h2a0.5 0.5 0 0 0 0.5 -0.5Z"
                                    fill="none" stroke="#000000" stroke-linecap="round" stroke-linejoin="round"
                                    stroke-width="1"></path>
                            </svg>
                            <span>{{ $t('Tipo Consulta') }}</span>
                        </div>
                    </router-link>
                </li>
                <!-- CONSULTATION -->
                <li class="menu">
                    <router-link to="/consultation" class="dropdown-toggle" @click="toggleMobileMenu">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" height="24" width="24">
                                <path stroke="#000000" stroke-linecap="round" stroke-linejoin="round"
                                    d="m17.612 21.4059 5.3115 1.5175 -0.7588 -4.5527 0 -6.9079c0 -0.4025 -0.1599 -0.7885 -0.4445 -1.0731 -0.2846 -0.2846 -0.6706 -0.44451 -1.0731 -0.44451h-9.8642c-0.4024 0 -0.78844 0.15991 -1.07304 0.44451 -0.28459 0.2846 -0.44448 0.6706 -0.44448 1.0731l0.00002 8.4255c0 0.4025 0.15988 0.7885 0.44448 1.0731 0.2846 0.2846 0.67062 0.4445 1.07312 0.4445h6.829Z"
                                    stroke-width="1"></path>
                                <path stroke="#000000" stroke-linecap="round" stroke-linejoin="round"
                                    d="M17.1677 12.4998h-2.6876l0 1.8744 -1.9476 0 0 2.6876h1.9476l0 1.8744h2.6876v-1.8744h1.8011v-2.6876l-1.8011 0v-1.8744Z"
                                    stroke-width="1"></path>
                                <path stroke="#000000" stroke-linecap="round" stroke-linejoin="round"
                                    d="M6.63663 13.8529H1.00244c0 -1.4583 0.57933 -2.857 1.61055 -3.88817 1.03121 -1.03121 2.42984 -1.61054 3.8882 -1.61054 0.61666 0 1.22264 0.10358 1.79467 0.30111"
                                    stroke-width="1"></path>
                                <path stroke="#000000" stroke-linecap="round" stroke-linejoin="round"
                                    d="M6.50128 8.35424c2.02458 0 3.66582 -1.64125 3.66582 -3.66583 0 -2.02458 -1.64124 -3.66583 -3.66582 -3.66583 -2.02458 0 -3.66583 1.64125 -3.66583 3.66583 0 2.02458 1.64125 3.66583 3.66583 3.66583Z"
                                    stroke-width="1"></path>
                            </svg>
                            <span>{{ $t('Consulta') }}</span>
                        </div>
                    </router-link>
                </li>
                <!-- SPECIALITY -->
                <li class="menu">
                    <router-link to="/speciality" class="dropdown-toggle" @click="toggleMobileMenu">
                        <div class="">
                            <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg" height="24" width="24">
                                <path d="M5.5 7a6.5 6.5 0 1 0 13 0 6.5 6.5 0 1 0 -13 0Z" fill="none" stroke="#000000"
                                    stroke-linecap="round" stroke-linejoin="round" stroke-width="1"></path>
                                <path
                                    d="M8.5 3.5h0a3.415 3.415 0 0 1 1 2.414v0.4A1.683 1.683 0 0 0 11.183 8h1.634A1.683 1.683 0 0 0 14.5 6.317v-0.4a3.415 3.415 0 0 1 1 -2.414h0"
                                    fill="none" stroke="#000000" stroke-linecap="round" stroke-linejoin="round"
                                    stroke-width="1"></path>
                                <path d="m12 3.5 0 7.5" fill="none" stroke="#000000" stroke-linecap="round"
                                    stroke-linejoin="round" stroke-width="1"></path>
                                <path d="m10.5 11 3 0" fill="none" stroke="#000000" stroke-linecap="round"
                                    stroke-linejoin="round" stroke-width="1"></path>
                                <path d="m11 3.5 2 0" fill="none" stroke="#000000" stroke-linecap="round"
                                    stroke-linejoin="round" stroke-width="1"></path>
                                <path d="M0.5 23.5h5a2 2 0 0 0 2 -2v-2a2 2 0 0 0 -2 -2h-5" fill="none" stroke="#000000"
                                    stroke-linecap="round" stroke-linejoin="round" stroke-width="1"></path>
                                <path d="M5.5 23.5H22c1.1 0 1.5 -0.895 1.5 -2v-2c0 -1.1 -0.4 -2 -1.5 -2H5.5" fill="none"
                                    stroke="#000000" stroke-linecap="round" stroke-linejoin="round" stroke-width="1"></path>
                                <path d="m19.5 17.5 0 6" fill="none" stroke="#000000" stroke-linecap="round"
                                    stroke-linejoin="round" stroke-width="1"></path>
                                <path d="m17.5 17.5 0 6" fill="none" stroke="#000000" stroke-linecap="round"
                                    stroke-linejoin="round" stroke-width="1"></path>
                                <path d="m13.5 17.5 0 6" fill="none" stroke="#000000" stroke-linecap="round"
                                    stroke-linejoin="round" stroke-width="1"></path>
                                <path d="m11.5 17.5 0 6" fill="none" stroke="#000000" stroke-linecap="round"
                                    stroke-linejoin="round" stroke-width="1"></path>
                                <path d="m5.5 21.5 -4 0" fill="none" stroke="#000000" stroke-linecap="round"
                                    stroke-linejoin="round" stroke-width="1"></path>
                                <path d="m5.5 19.5 -4 0" fill="none" stroke="#000000" stroke-linecap="round"
                                    stroke-linejoin="round" stroke-width="1"></path>
                            </svg>
                            <span>{{ $t('Especialidad') }}</span>
                        </div>
                    </router-link>
                </li>

                <!-- FACTURA -->
                <li class="menu">
                    <a href="#Invoice" class="dropdown-toggle" data-bs-toggle="collapse" aria-controls="dashboard"
                        aria-expanded="false">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" height="24" width="24">
                                <path stroke="#000000" stroke-linecap="round" stroke-linejoin="round"
                                    d="M18 2H6C4.89543 2 4 2.89543 4 4V20C4 21.1046 4.89543 22 6 22H18C19.1046 22 20 21.1046 20 20V4C20 2.89543 19.1046 2 18 2ZM8 15H16M8 11H16M8 7H12" stroke-width="1"></path>
                            </svg>
                            
                            <span>{{ $t('Factura') }}</span>
                        </div>
                        <div>
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-chevron-right">
                                <polyline points="9 18 15 12 9 6"></polyline>
                            </svg>
                        </div>
                    </a>

                    <ul id="Invoice" class="collapse submenu list-unstyled" data-bs-parent="#sidebar">
                        <li>
                            <router-link to="/invoices/list" @click="toggleMobileMenu">Lista</router-link>
                        </li>
                        <li>
                            <router-link to="/invoices/preview" @click="toggleMobileMenu">Avance</router-link>
                        </li>
                        <li>
                            <router-link to="/invoices/add" @click="toggleMobileMenu">Agregar</router-link>
                        </li>
                        <li>
                            <router-link to="/invoices/edit" @click="toggleMobileMenu">Editar</router-link>
                        </li>
                    </ul>
                </li>
                <li class="menu">
                    <a class="dropdown-toggle" data-bs-toggle="collapse" data-bs-target="#apps" aria-controls="apps"
                        aria-expanded="false">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-cpu">
                                <rect x="4" y="4" width="16" height="16" rx="2" ry="2"></rect>
                                <rect x="9" y="9" width="6" height="6"></rect>
                                <line x1="9" y1="1" x2="9" y2="4"></line>
                                <line x1="15" y1="1" x2="15" y2="4"></line>
                                <line x1="9" y1="20" x2="9" y2="23"></line>
                                <line x1="15" y1="20" x2="15" y2="23"></line>
                                <line x1="20" y1="9" x2="23" y2="9"></line>
                                <line x1="20" y1="14" x2="23" y2="14"></line>
                                <line x1="1" y1="9" x2="4" y2="9"></line>
                                <line x1="1" y1="14" x2="4" y2="14"></line>
                            </svg>
                            <span>{{ $t('apps') }}</span>
                        </div>
                        <div>
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-chevron-right">
                                <polyline points="9 18 15 12 9 6"></polyline>
                            </svg>
                        </div>
                    </a>
                    <ul id="apps" class="collapse submenu list-unstyled" data-bs-parent="#sidebar">
                        <li>
                            <router-link to="/apps/chat" @click="toggleMobileMenu">Chat</router-link>
                        </li>
                        <li>
                            <router-link to="/apps/mailbox" @click="toggleMobileMenu">Mailbox</router-link>
                        </li>
                        <li>
                            <router-link to="/apps/todo-list" @click="toggleMobileMenu">Todo List</router-link>
                        </li>
                        <li>
                            <router-link to="/apps/notes" @click="toggleMobileMenu">Notes</router-link>
                        </li>
                        <li>
                            <router-link to="/apps/scrumboard" @click="toggleMobileMenu">Scrumboard</router-link>
                        </li>
                        <li>
                            <router-link to="/apps/contacts" @click="toggleMobileMenu">Contacts</router-link>
                        </li>
                        <li>
                            <a class="dropdown-toggle" href="#appInvoice" data-bs-parent="#apps" data-bs-toggle="collapse"
                                role="button" aria-expanded="false">
                                Invoice
                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"
                                    fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"
                                    stroke-linejoin="round" class="feather feather-chevron-right">
                                    <polyline points="9 18 15 12 9 6"></polyline>
                                </svg>
                            </a>

                            <ul id="appInvoice" class="collapse list-unstyled sub-submenu">
                                <li>
                                    <router-link to="/apps/invoice/list" @click="toggleMobileMenu">List</router-link>
                                </li>
                                <li>
                                    <router-link to="/apps/invoice/preview" @click="toggleMobileMenu">Preview</router-link>
                                </li>
                                <li>
                                    <router-link to="/apps/invoice/add" @click="toggleMobileMenu">Add</router-link>
                                </li>
                                <li>
                                    <router-link to="/apps/invoice/edit" @click="toggleMobileMenu">Edit</router-link>
                                </li>
                            </ul>
                        </li>
                        <li>
                            <router-link to="/apps/calendar" @click="toggleMobileMenu">Calendar</router-link>
                        </li>
                    </ul>
                </li>

                <li class="menu">
                    <a class="dropdown-toggle" data-bs-toggle="collapse" data-bs-target="#components"
                        aria-controls="components" aria-expanded="false">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-box">
                                <path
                                    d="M21 16V8a2 2 0 0 0-1-1.73l-7-4a2 2 0 0 0-2 0l-7 4A2 2 0 0 0 3 8v8a2 2 0 0 0 1 1.73l7 4a2 2 0 0 0 2 0l7-4A2 2 0 0 0 21 16z">
                                </path>
                                <polyline points="3.27 6.96 12 12.01 20.73 6.96"></polyline>
                                <line x1="12" y1="22.08" x2="12" y2="12"></line>
                            </svg>
                            <span>{{ $t('components') }}</span>
                        </div>
                        <div>
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-chevron-right">
                                <polyline points="9 18 15 12 9 6"></polyline>
                            </svg>
                        </div>
                    </a>

                    <ul id="components" class="collapse submenu list-unstyled" data-bs-parent="#sidebar">
                        <li>
                            <router-link to="/components/tabs" @click="toggleMobileMenu">Tabs</router-link>
                        </li>
                        <li>
                            <router-link to="/components/accordions" @click="toggleMobileMenu">Accordions</router-link>
                        </li>
                        <li>
                            <router-link to="/components/modals" @click="toggleMobileMenu">Modals</router-link>
                        </li>
                        <li>
                            <router-link to="/components/cards" @click="toggleMobileMenu">Cards</router-link>
                        </li>
                        <li>
                            <router-link to="/components/carousel" @click="toggleMobileMenu">Carousel</router-link>
                        </li>
                        <li>
                            <router-link to="/components/countdown" @click="toggleMobileMenu">Countdown</router-link>
                        </li>
                        <li>
                            <router-link to="/components/counter" @click="toggleMobileMenu">Counter</router-link>
                        </li>
                        <li>
                            <router-link to="/components/sweetalert" @click="toggleMobileMenu">Sweet Alerts</router-link>
                        </li>
                        <li>
                            <router-link to="/components/timeline" @click="toggleMobileMenu">Timeline</router-link>
                        </li>
                        <li>
                            <router-link to="/components/notifications"
                                @click="toggleMobileMenu">Notifications</router-link>
                        </li>
                        <li>
                            <router-link to="/components/media-object" @click="toggleMobileMenu">Media Object</router-link>
                        </li>
                        <li>
                            <router-link to="/components/list-group" @click="toggleMobileMenu">List Group</router-link>
                        </li>
                        <li>
                            <router-link to="/components/pricing-table" @click="toggleMobileMenu">Pricing
                                Tables</router-link>
                        </li>
                        <li>
                            <router-link to="/components/lightbox" @click="toggleMobileMenu">Lightbox </router-link>
                        </li>
                    </ul>
                </li>

                <li class="menu">
                    <a class="dropdown-toggle" data-bs-toggle="collapse" data-bs-target="#elements" aria-controls="elements"
                        aria-expanded="false">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-zap">
                                <polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"></polygon>
                            </svg>
                            <span>{{ $t('elements') }}</span>
                        </div>
                        <div>
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-chevron-right">
                                <polyline points="9 18 15 12 9 6"></polyline>
                            </svg>
                        </div>
                    </a>

                    <ul id="elements" class="collapse submenu list-unstyled" data-bs-parent="#sidebar">
                        <li>
                            <router-link to="/elements/alerts" @click="toggleMobileMenu">Alerts</router-link>
                        </li>
                        <li>
                            <router-link to="/elements/avatar" @click="toggleMobileMenu">Avatar</router-link>
                        </li>
                        <li>
                            <router-link to="/elements/badges" @click="toggleMobileMenu">Badges</router-link>
                        </li>
                        <li>
                            <router-link to="/elements/breadcrumbs" @click="toggleMobileMenu">Breadcrumbs</router-link>
                        </li>
                        <li>
                            <router-link to="/elements/buttons" @click="toggleMobileMenu">Buttons</router-link>
                        </li>
                        <li>
                            <router-link to="/elements/buttons-group" @click="toggleMobileMenu">Button Groups</router-link>
                        </li>
                        <li>
                            <router-link to="/elements/color-library" @click="toggleMobileMenu">Color Library</router-link>
                        </li>
                        <li>
                            <router-link to="/elements/dropdown" @click="toggleMobileMenu">Dropdown</router-link>
                        </li>
                        <li>
                            <router-link to="/elements/infobox" @click="toggleMobileMenu">Infobox</router-link>
                        </li>
                        <li>
                            <router-link to="/elements/jumbotron" @click="toggleMobileMenu">Jumbotron</router-link>
                        </li>
                        <li>
                            <router-link to="/elements/loader" @click="toggleMobileMenu">Loader</router-link>
                        </li>
                        <li>
                            <router-link to="/elements/pagination" @click="toggleMobileMenu">Pagination</router-link>
                        </li>
                        <li>
                            <router-link to="/elements/popovers" @click="toggleMobileMenu">Popovers</router-link>
                        </li>
                        <li>
                            <router-link to="/elements/progress-bar" @click="toggleMobileMenu">Progress Bar</router-link>
                        </li>
                        <li>
                            <router-link to="/elements/search" @click="toggleMobileMenu">Search</router-link>
                        </li>
                        <li>
                            <router-link to="/elements/tooltips" @click="toggleMobileMenu">Tooltips</router-link>
                        </li>
                        <li>
                            <router-link to="/elements/treeview" @click="toggleMobileMenu">Treeview</router-link>
                        </li>
                        <li>
                            <router-link to="/elements/typography" @click="toggleMobileMenu">Typography</router-link>
                        </li>
                    </ul>
                </li>

                <li class="menu">
                    <router-link to="/font-icons" class="dropdown-toggle" @click="toggleMobileMenu">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-target">
                                <circle cx="12" cy="12" r="10"></circle>
                                <circle cx="12" cy="12" r="6"></circle>
                                <circle cx="12" cy="12" r="2"></circle>
                            </svg>
                            <span>{{ $t('font_icons') }}</span>
                        </div>
                    </router-link>
                </li>

                <li class="menu">
                    <router-link to="/widgets" class="dropdown-toggle" @click="toggleMobileMenu">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-airplay">
                                <path d="M5 17H4a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h16a2 2 0 0 1 2 2v10a2 2 0 0 1-2 2h-1"></path>
                                <polygon points="12 15 17 21 7 21 12 15"></polygon>
                            </svg>
                            <span>{{ $t('widgets') }}</span>
                        </div>
                    </router-link>
                </li>

                <li class="menu">
                    <router-link to="/tables" class="dropdown-toggle" @click="toggleMobileMenu">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-layout">
                                <rect x="3" y="3" width="18" height="18" rx="2" ry="2"></rect>
                                <line x1="3" y1="9" x2="21" y2="9"></line>
                                <line x1="9" y1="21" x2="9" y2="9"></line>
                            </svg>
                            <span>{{ $t('tables') }}</span>
                        </div>
                    </router-link>
                </li>

                <li class="menu">
                    <a class="dropdown-toggle" data-bs-toggle="collapse" data-bs-target="#datatables"
                        aria-controls="datatables" aria-expanded="false">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-layers">
                                <polygon points="12 2 2 7 12 12 22 7 12 2"></polygon>
                                <polyline points="2 17 12 22 22 17"></polyline>
                                <polyline points="2 12 12 17 22 12"></polyline>
                            </svg>
                            <span>{{ $t('datatables') }}</span>
                        </div>
                        <div>
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-chevron-right">
                                <polyline points="9 18 15 12 9 6"></polyline>
                            </svg>
                        </div>
                    </a>

                    <ul id="datatables" class="collapse submenu list-unstyled" data-bs-parent="#sidebar">
                        <li>
                            <a class="dropdown-toggle ms-3" href="#vue3-table" data-bs-parent="#apps"
                                data-bs-toggle="collapse" role="button" aria-expanded="false">
                                vue3-datatable
                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"
                                    fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"
                                    stroke-linejoin="round" class="feather feather-chevron-right">
                                    <polyline points="9 18 15 12 9 6"></polyline>
                                </svg>
                            </a>

                            <ul id="vue3-table" class="collapse list-unstyled sub-submenu">
                                <li>
                                    <router-link to="/tables/vue3-datatable/basic"
                                        @click="toggleMobileMenu">Basic</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/vue3-datatable/advance"
                                        @click="toggleMobileMenu">Advanced</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/vue3-datatable/order-sorting" @click="toggleMobileMenu">Order
                                        Sorting</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/vue3-datatable/alt-pagination" @click="toggleMobileMenu">Alt.
                                        Pagination</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/vue3-datatable/search"
                                        @click="toggleMobileMenu">Search</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/vue3-datatable/checkbox"
                                        @click="toggleMobileMenu">Checkbox</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/vue3-datatable/slot"
                                        @click="toggleMobileMenu">Slot</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/vue3-datatable/column-filter" @click="toggleMobileMenu">Column
                                        Filter</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/vue3-datatable/actions"
                                        @click="toggleMobileMenu">Actions</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/vue3-datatable/sticky-header" @click="toggleMobileMenu">Sticky
                                        Header</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/vue3-datatable/column-chooser" @click="toggleMobileMenu">Column
                                        Chooser</router-link>
                                </li>
                            </ul>
                        </li>
                        <li>
                            <a class="dropdown-toggle ms-3" href="#v3-table" data-bs-parent="#apps"
                                data-bs-toggle="collapse" role="button" aria-expanded="false">
                                v3-table
                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"
                                    fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"
                                    stroke-linejoin="round" class="feather feather-chevron-right">
                                    <polyline points="9 18 15 12 9 6"></polyline>
                                </svg>
                            </a>

                            <ul id="v3-table" class="collapse list-unstyled sub-submenu">
                                <li>
                                    <router-link to="/tables/v3-table/basic" @click="toggleMobileMenu">Basic</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/v3-table/striped" @click="toggleMobileMenu">Striped
                                        Table</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/v3-table/order-sorting" @click="toggleMobileMenu">Order
                                        Sorting</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/v3-table/multi-column" @click="toggleMobileMenu">Multi
                                        Column</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/v3-table/multiple-tables" @click="toggleMobileMenu">Multiple
                                        Tables</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/v3-table/alt-pagination" @click="toggleMobileMenu">Alt.
                                        Pagination</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/v3-table/custom" @click="toggleMobileMenu">Custom</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/v3-table/range-search" @click="toggleMobileMenu">Range
                                        Search</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/v3-table/export" @click="toggleMobileMenu">Export</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/v3-table/live-dom-ordering" @click="toggleMobileMenu">Live DOM
                                        ordering</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/v3-table/miscellaneous"
                                        @click="toggleMobileMenu">Miscellaneous</router-link>
                                </li>
                            </ul>
                        </li>
                    </ul>
                </li>

                <li class="menu">
                    <a class="dropdown-toggle" data-bs-toggle="collapse" data-bs-target="#forms" aria-controls="forms"
                        aria-expanded="false">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-clipboard">
                                <path d="M16 4h2a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2H6a2 2 0 0 1-2-2V6a2 2 0 0 1 2-2h2"></path>
                                <rect x="8" y="2" width="8" height="4" rx="1" ry="1"></rect>
                            </svg>
                            <span>{{ $t('forms') }}</span>
                        </div>
                        <div>
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-chevron-right">
                                <polyline points="9 18 15 12 9 6"></polyline>
                            </svg>
                        </div>
                    </a>

                    <ul id="forms" class="collapse submenu list-unstyled" data-bs-parent="#sidebar">
                        <li>
                            <router-link to="/forms/basic" @click="toggleMobileMenu">Basic</router-link>
                        </li>
                        <li>
                            <router-link to="/forms/input-group" @click="toggleMobileMenu">Input Group</router-link>
                        </li>
                        <li>
                            <router-link to="/forms/layouts" @click="toggleMobileMenu">Layouts</router-link>
                        </li>
                        <li>
                            <router-link to="/forms/validation" @click="toggleMobileMenu">Validation</router-link>
                        </li>
                        <li>
                            <router-link to="/forms/input-mask" @click="toggleMobileMenu">Input Mask</router-link>
                        </li>
                        <li>
                            <router-link to="/forms/select2" @click="toggleMobileMenu">Select2</router-link>
                        </li>
                        <li>
                            <router-link to="/forms/touchspin" @click="toggleMobileMenu">TouchSpin</router-link>
                        </li>
                        <li>
                            <router-link to="/forms/checkbox-radio" @click="toggleMobileMenu">Checkbox &amp;
                                Radio</router-link>
                        </li>
                        <li>
                            <router-link to="/forms/switches" @click="toggleMobileMenu">Switches</router-link>
                        </li>
                        <li>
                            <router-link to="/forms/wizards" @click="toggleMobileMenu">Wizards</router-link>
                        </li>
                        <li>
                            <router-link to="/forms/file-upload" @click="toggleMobileMenu">File Upload</router-link>
                        </li>
                        <li>
                            <router-link to="/forms/quill-editor" @click="toggleMobileMenu">Quill Editor</router-link>
                        </li>
                        <li>
                            <router-link to="/forms/markdown-editor" @click="toggleMobileMenu">Markdown Editor</router-link>
                        </li>
                        <li>
                            <router-link to="/forms/date-picker" @click="toggleMobileMenu">Date &amp; Range Picker
                            </router-link>
                        </li>
                        <li>
                            <router-link to="/forms/clipboard" @click="toggleMobileMenu">Clipboard</router-link>
                        </li>
                    </ul>
                </li>

                <li class="menu">
                    <a class="dropdown-toggle" data-bs-toggle="collapse" data-bs-target="#users" aria-controls="users"
                        aria-expanded="false">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-users">
                                <path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"></path>
                                <circle cx="9" cy="7" r="4"></circle>
                                <path d="M23 21v-2a4 4 0 0 0-3-3.87"></path>
                                <path d="M16 3.13a4 4 0 0 1 0 7.75"></path>
                            </svg>
                            <span>{{ $t('users') }}</span>
                        </div>
                        <div>
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-chevron-right">
                                <polyline points="9 18 15 12 9 6"></polyline>
                            </svg>
                        </div>
                    </a>

                    <ul id="users" class="collapse submenu list-unstyled" data-bs-parent="#sidebar">
                        <li>
                            <router-link to="/users/profile" @click="toggleMobileMenu">Profile</router-link>
                        </li>
                        <li>
                            <router-link to="/users/account-setting" @click="toggleMobileMenu">Account
                                Settings</router-link>
                        </li>
                    </ul>
                </li>

                <li class="menu">
                    <a class="dropdown-toggle" data-bs-toggle="collapse" data-bs-target="#pages" aria-controls="pages"
                        aria-expanded="false">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-file">
                                <path d="M13 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V9z"></path>
                                <polyline points="13 2 13 9 20 9"></polyline>
                            </svg>
                            <span>{{ $t('pages') }}</span>
                        </div>
                        <div>
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-chevron-right">
                                <polyline points="9 18 15 12 9 6"></polyline>
                            </svg>
                        </div>
                    </a>

                    <ul id="pages" class="collapse submenu list-unstyled" data-bs-parent="#sidebar">
                        <li>
                            <router-link to="/pages/helpdesk" @click="toggleMobileMenu">Helpdesk</router-link>
                        </li>
                        <li>
                            <router-link to="/pages/contact-us" @click="toggleMobileMenu">Contact Form</router-link>
                        </li>
                        <li>
                            <router-link to="/pages/faq" @click="toggleMobileMenu">FAQ</router-link>
                        </li>
                        <li>
                            <router-link to="/pages/faq2" @click="toggleMobileMenu">FAQ 2</router-link>
                        </li>
                        <li>
                            <router-link to="/pages/privacy-policy" @click="toggleMobileMenu">Privacy Policy</router-link>
                        </li>
                        <li @click="toggleMobileMenu"><a target="_blank" href="/pages/coming-soon">Coming Soon</a></li>

                        <li>
                            <a class="dropdown-toggle" href="#pages-error" data-bs-parent="#pages" data-bs-toggle="collapse"
                                role="button" aria-expanded="false">
                                Error
                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"
                                    fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"
                                    stroke-linejoin="round" class="feather feather-chevron-right">
                                    <polyline points="9 18 15 12 9 6"></polyline>
                                </svg>
                            </a>

                            <ul id="pages-error" class="collapse list-unstyled sub-submenu">
                                <li @click="toggleMobileMenu"><a target="_blank" href="/pages/error404">404</a></li>
                                <li @click="toggleMobileMenu"><a target="_blank" href="/pages/error500">500</a></li>
                                <li @click="toggleMobileMenu"><a target="_blank" href="/pages/error503">503</a></li>
                                <li @click="toggleMobileMenu"><a target="_blank" href="/pages/maintenence">Maintanence</a>
                                </li>
                            </ul>
                        </li>

                        <li>
                            <router-link to="/pages/blank-page" @click="toggleMobileMenu">Blank Page</router-link>
                        </li>
                        <li>
                            <router-link to="/pages/sample" @click="toggleMobileMenu">Sample Page</router-link>
                        </li>
                    </ul>
                </li>

                <li class="menu">
                    <a class="dropdown-toggle" data-bs-toggle="collapse" data-bs-target="#authentication"
                        aria-controls="authentication" aria-expanded="false">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-lock">
                                <rect x="3" y="11" width="18" height="11" rx="2" ry="2"></rect>
                                <path d="M7 11V7a5 5 0 0 1 10 0v4"></path>
                            </svg>
                            <span>{{ $t('authentication') }}</span>
                        </div>
                        <div>
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-chevron-right">
                                <polyline points="9 18 15 12 9 6"></polyline>
                            </svg>
                        </div>
                    </a>

                    <ul id="authentication" class="collapse submenu list-unstyled" data-bs-parent="#sidebar">
                        <li @click="toggleMobileMenu"><a target="_blank" href="/auth/login-boxed">Login Boxed</a></li>
                        <li @click="toggleMobileMenu"><a target="_blank" href="/auth/register-boxed">Register Boxed</a></li>
                        <li @click="toggleMobileMenu"><a target="_blank" href="/auth/lockscreen-boxed">Unlock Boxed</a></li>
                        <li @click="toggleMobileMenu"><a target="_blank" href="/auth/pass-recovery-boxed">Recover ID
                                Boxed</a></li>
                        <li @click="toggleMobileMenu"><a target="_blank" href="/auth/login">Login Cover</a></li>
                        <li @click="toggleMobileMenu"><a target="_blank" href="/auth/register">Register Cover</a></li>
                        <li @click="toggleMobileMenu"><a target="_blank" href="/auth/lockscreen">Unlock Cover</a></li>
                        <li @click="toggleMobileMenu"><a target="_blank" href="/auth/pass-recovery">Recover ID Cover</a>
                        </li>
                    </ul>
                </li>

                <li class="menu">
                    <router-link to="/dragndrop" class="dropdown-toggle" @click="toggleMobileMenu">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-move">
                                <polyline points="5 9 2 12 5 15"></polyline>
                                <polyline points="9 5 12 2 15 5"></polyline>
                                <polyline points="15 19 12 22 9 19"></polyline>
                                <polyline points="19 9 22 12 19 15"></polyline>
                                <line x1="2" y1="12" x2="22" y2="12"></line>
                                <line x1="12" y1="2" x2="12" y2="22"></line>
                            </svg>
                            <span>{{ $t('drag_and_drop') }}</span>
                        </div>
                    </router-link>
                </li>

                <li class="menu">
                    <router-link to="/charts/apex-chart" class="dropdown-toggle" @click="toggleMobileMenu">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-pie-chart">
                                <path d="M21.21 15.89A10 10 0 1 1 8 2.83"></path>
                                <path d="M22 12A10 10 0 0 0 12 2v10z"></path>
                            </svg>
                            <span>{{ $t('charts') }}</span>
                        </div>
                    </router-link>
                </li>

                <li class="menu" @click="toggleMobileMenu">
                    <a target="_blank" href="https://cork-vue.sbthemes.com" aria-expanded="false" class="dropdown-toggle">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                                stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                                class="feather feather-book">
                                <path d="M4 19.5A2.5 2.5 0 0 1 6.5 17H20"></path>
                                <path d="M6.5 2H20v20H6.5A2.5 2.5 0 0 1 4 19.5v-15A2.5 2.5 0 0 1 6.5 2z"></path>
                            </svg>
                            <span>{{ $t('documentation') }}</span>
                        </div>
                    </a>
                </li>
            </perfect-scrollbar>
        </nav>
    </div>
    <!--  END SIDEBAR  -->
</template>

<script setup>
import { onMounted, ref } from 'vue';
import { useStore } from 'vuex';
const store = useStore();

const menu_collapse = ref('dashboard');

onMounted(() => {
    const selector = document.querySelector('#sidebar a[href="' + window.location.pathname + '"]');
    if (selector) {
        const ul = selector.closest('ul.collapse');
        if (ul) {
            let ele = ul.closest('li.menu').querySelectorAll('.dropdown-toggle');
            if (ele) {
                ele = ele[0];
                setTimeout(() => {
                    ele.click();
                });
            }
        } else {
            selector.click();
        }
    }
});

const toggleMobileMenu = () => {
    if (window.innerWidth < 991) {
        store.commit('toggleSideBar', !store.state.is_show_sidebar);
    }
};
</script>
