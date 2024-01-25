<template>
    <!--  BEGIN SIDEBAR  -->
    <div class="sidebar-wrapper sidebar-theme">
        <nav ref="menu" id="sidebar">
            <div class="shadow-bottom"></div>

            <perfect-scrollbar class="list-unstyled menu-categories" tag="ul" :options="{ wheelSpeed: 0.5, swipeEasing: !0, minScrollbarLength: 40, maxScrollbarLength: 300, suppressScrollX: true }">
                <!-- DASHBOARD -->
                <li class="menu">
                    <a class="dropdown-toggle" data-bs-toggle="collapse" data-bs-target="#dashboard" aria-controls="dashboard" aria-expanded="false">
                        <div class="">
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
                                class="feather feather-home"
                            >
                                <path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"></path>
                                <polyline points="9 22 9 12 15 12 15 22"></polyline>
                            </svg>
                            <span>{{ $t('dashboard') }}</span>
                        </div>
                        <div>
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
                                class="feather feather-chevron-right"
                            >
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
                            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><!--!Font Awesome Free 6.5.1 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.--><path d="M96 352V96c0-35.3 28.7-64 64-64H416c35.3 0 64 28.7 64 64V293.5c0 17-6.7 33.3-18.7 45.3l-58.5 58.5c-12 12-28.3 18.7-45.3 18.7H160c-35.3 0-64-28.7-64-64zM272 128c-8.8 0-16 7.2-16 16v48H208c-8.8 0-16 7.2-16 16v32c0 8.8 7.2 16 16 16h48v48c0 8.8 7.2 16 16 16h32c8.8 0 16-7.2 16-16V256h48c8.8 0 16-7.2 16-16V208c0-8.8-7.2-16-16-16H320V144c0-8.8-7.2-16-16-16H272zm24 336c13.3 0 24 10.7 24 24s-10.7 24-24 24H136C60.9 512 0 451.1 0 376V152c0-13.3 10.7-24 24-24s24 10.7 24 24l0 224c0 48.6 39.4 88 88 88H296z"/></svg>
                            <span>{{ $t('EPS') }}</span>
                        </div>
                    </router-link>
                </li>
                <!-- MEDICO -->
                <li class="menu">
                    <router-link to="/medico" class="dropdown-toggle" @click="toggleMobileMenu">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg"
                                viewBox="0 0 576 512">
                                <path
                                    d="M142.4 21.9c5.6 16.8-3.5 34.9-20.2 40.5L96 71.1V192c0 53 43 96 96 96s96-43 96-96V71.1l-26.1-8.7c-16.8-5.6-25.8-23.7-20.2-40.5s23.7-25.8 40.5-20.2l26.1 8.7C334.4 19.1 352 43.5 352 71.1V192c0 77.2-54.6 141.6-127.3 156.7C231 404.6 278.4 448 336 448c61.9 0 112-50.1 112-112V265.3c-28.3-12.3-48-40.5-48-73.3c0-44.2 35.8-80 80-80s80 35.8 80 80c0 32.8-19.7 61-48 73.3V336c0 97.2-78.8 176-176 176c-92.9 0-168.9-71.9-175.5-163.1C87.2 334.2 32 269.6 32 192V71.1c0-27.5 17.6-52 43.8-60.7l26.1-8.7c16.8-5.6 34.9 3.5 40.5 20.2zM480 224a32 32 0 1 0 0-64 32 32 0 1 0 0 64z" />
                            </svg>

                            <span>{{ $t('Medicos') }}</span>
                        </div>
                    </router-link>
                </li>

                <!-- CONSULTATION_TYPE -->
                <li class="menu">
                    <router-link to="/consultation_type" class="dropdown-toggle" @click="toggleMobileMenu">
                        <div class="">
                            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512"><!--!Font Awesome Free 6.5.1 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.--><path d="M0 96C0 43 43 0 96 0H384h32c17.7 0 32 14.3 32 32V352c0 17.7-14.3 32-32 32v64c17.7 0 32 14.3 32 32s-14.3 32-32 32H384 96c-53 0-96-43-96-96V96zM64 416c0 17.7 14.3 32 32 32H352V384H96c-17.7 0-32 14.3-32 32zM208 112v48H160c-8.8 0-16 7.2-16 16v32c0 8.8 7.2 16 16 16h48v48c0 8.8 7.2 16 16 16h32c8.8 0 16-7.2 16-16V224h48c8.8 0 16-7.2 16-16V176c0-8.8-7.2-16-16-16H272V112c0-8.8-7.2-16-16-16H224c-8.8 0-16 7.2-16 16z"/></svg>
                            <span>{{ $t('Tipo Consulta') }}</span>
                        </div>
                    </router-link>
                </li>

                <!-- CONSULTATION -->
                <li class="menu">
                    <router-link to="/consultation" class="dropdown-toggle" @click="toggleMobileMenu">
                                <div class="">
                                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 576 512"><!--!Font Awesome Free 6.5.1 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.--><path d="M224 24V80H168c-13.3 0-24 10.7-24 24v48c0 13.3 10.7 24 24 24h56v56c0 13.3 10.7 24 24 24h48c13.3 0 24-10.7 24-24V176h56c13.3 0 24-10.7 24-24V104c0-13.3-10.7-24-24-24H320V24c0-13.3-10.7-24-24-24H248c-13.3 0-24 10.7-24 24zM559.7 392.2c17.8-13.1 21.6-38.1 8.5-55.9s-38.1-21.6-55.9-8.5L392.6 416H272c-8.8 0-16-7.2-16-16s7.2-16 16-16h16 64c17.7 0 32-14.3 32-32s-14.3-32-32-32H288 272 193.7c-29.1 0-57.3 9.9-80 28L68.8 384H32c-17.7 0-32 14.3-32 32v64c0 17.7 14.3 32 32 32H192 352.5c29 0 57.3-9.3 80.7-26.5l126.6-93.3zm-367-8.2l.9 0 0 0c-.3 0-.6 0-.9 0z"/></svg>
                                    <span>{{ $t('Consulta') }}</span>
                                </div>
                    </router-link>
                </li>

                <li class="menu">
                    <a class="dropdown-toggle" data-bs-toggle="collapse" data-bs-target="#apps" aria-controls="apps" aria-expanded="false">
                        <div class="">
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
                                class="feather feather-cpu"
                            >
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
                                class="feather feather-chevron-right"
                            >
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
                            <a class="dropdown-toggle" href="#appInvoice" data-bs-parent="#apps" data-bs-toggle="collapse" role="button" aria-expanded="false">
                                Invoice
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
                                    class="feather feather-chevron-right"
                                >
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
                    <a class="dropdown-toggle" data-bs-toggle="collapse" data-bs-target="#components" aria-controls="components" aria-expanded="false">
                        <div class="">
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
                                class="feather feather-box"
                            >
                                <path d="M21 16V8a2 2 0 0 0-1-1.73l-7-4a2 2 0 0 0-2 0l-7 4A2 2 0 0 0 3 8v8a2 2 0 0 0 1 1.73l7 4a2 2 0 0 0 2 0l7-4A2 2 0 0 0 21 16z"></path>
                                <polyline points="3.27 6.96 12 12.01 20.73 6.96"></polyline>
                                <line x1="12" y1="22.08" x2="12" y2="12"></line>
                            </svg>
                            <span>{{ $t('components') }}</span>
                        </div>
                        <div>
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
                                class="feather feather-chevron-right"
                            >
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
                            <router-link to="/components/notifications" @click="toggleMobileMenu">Notifications</router-link>
                        </li>
                        <li>
                            <router-link to="/components/media-object" @click="toggleMobileMenu">Media Object</router-link>
                        </li>
                        <li>
                            <router-link to="/components/list-group" @click="toggleMobileMenu">List Group</router-link>
                        </li>
                        <li>
                            <router-link to="/components/pricing-table" @click="toggleMobileMenu">Pricing Tables</router-link>
                        </li>
                        <li>
                            <router-link to="/components/lightbox" @click="toggleMobileMenu">Lightbox </router-link>
                        </li>
                    </ul>
                </li>

                <li class="menu">
                    <a class="dropdown-toggle" data-bs-toggle="collapse" data-bs-target="#elements" aria-controls="elements" aria-expanded="false">
                        <div class="">
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
                                class="feather feather-zap"
                            >
                                <polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"></polygon>
                            </svg>
                            <span>{{ $t('elements') }}</span>
                        </div>
                        <div>
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
                                class="feather feather-chevron-right"
                            >
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
                                class="feather feather-target"
                            >
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
                                class="feather feather-airplay"
                            >
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
                                class="feather feather-layout"
                            >
                                <rect x="3" y="3" width="18" height="18" rx="2" ry="2"></rect>
                                <line x1="3" y1="9" x2="21" y2="9"></line>
                                <line x1="9" y1="21" x2="9" y2="9"></line>
                            </svg>
                            <span>{{ $t('tables') }}</span>
                        </div>
                    </router-link>
                </li>

                <li class="menu">
                    <a class="dropdown-toggle" data-bs-toggle="collapse" data-bs-target="#datatables" aria-controls="datatables" aria-expanded="false">
                        <div class="">
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
                                class="feather feather-layers"
                            >
                                <polygon points="12 2 2 7 12 12 22 7 12 2"></polygon>
                                <polyline points="2 17 12 22 22 17"></polyline>
                                <polyline points="2 12 12 17 22 12"></polyline>
                            </svg>
                            <span>{{ $t('datatables') }}</span>
                        </div>
                        <div>
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
                                class="feather feather-chevron-right"
                            >
                                <polyline points="9 18 15 12 9 6"></polyline>
                            </svg>
                        </div>
                    </a>

                    <ul id="datatables" class="collapse submenu list-unstyled" data-bs-parent="#sidebar">
                        <li>
                            <a class="dropdown-toggle ms-3" href="#vue3-table" data-bs-parent="#apps" data-bs-toggle="collapse" role="button" aria-expanded="false">
                                vue3-datatable
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
                                    class="feather feather-chevron-right"
                                >
                                    <polyline points="9 18 15 12 9 6"></polyline>
                                </svg>
                            </a>

                            <ul id="vue3-table" class="collapse list-unstyled sub-submenu">
                                <li>
                                    <router-link to="/tables/vue3-datatable/basic" @click="toggleMobileMenu">Basic</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/vue3-datatable/advance" @click="toggleMobileMenu">Advanced</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/vue3-datatable/order-sorting" @click="toggleMobileMenu">Order Sorting</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/vue3-datatable/alt-pagination" @click="toggleMobileMenu">Alt. Pagination</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/vue3-datatable/search" @click="toggleMobileMenu">Search</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/vue3-datatable/checkbox" @click="toggleMobileMenu">Checkbox</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/vue3-datatable/slot" @click="toggleMobileMenu">Slot</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/vue3-datatable/column-filter" @click="toggleMobileMenu">Column Filter</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/vue3-datatable/actions" @click="toggleMobileMenu">Actions</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/vue3-datatable/sticky-header" @click="toggleMobileMenu">Sticky Header</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/vue3-datatable/column-chooser" @click="toggleMobileMenu">Column Chooser</router-link>
                                </li>
                            </ul>
                        </li>
                        <li>
                            <a class="dropdown-toggle ms-3" href="#v3-table" data-bs-parent="#apps" data-bs-toggle="collapse" role="button" aria-expanded="false">
                                v3-table
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
                                    class="feather feather-chevron-right"
                                >
                                    <polyline points="9 18 15 12 9 6"></polyline>
                                </svg>
                            </a>

                            <ul id="v3-table" class="collapse list-unstyled sub-submenu">
                                <li>
                                    <router-link to="/tables/v3-table/basic" @click="toggleMobileMenu">Basic</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/v3-table/striped" @click="toggleMobileMenu">Striped Table</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/v3-table/order-sorting" @click="toggleMobileMenu">Order Sorting</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/v3-table/multi-column" @click="toggleMobileMenu">Multi Column</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/v3-table/multiple-tables" @click="toggleMobileMenu">Multiple Tables</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/v3-table/alt-pagination" @click="toggleMobileMenu">Alt. Pagination</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/v3-table/custom" @click="toggleMobileMenu">Custom</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/v3-table/range-search" @click="toggleMobileMenu">Range Search</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/v3-table/export" @click="toggleMobileMenu">Export</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/v3-table/live-dom-ordering" @click="toggleMobileMenu">Live DOM ordering</router-link>
                                </li>
                                <li>
                                    <router-link to="/tables/v3-table/miscellaneous" @click="toggleMobileMenu">Miscellaneous</router-link>
                                </li>
                            </ul>
                        </li>
                    </ul>
                </li>

                <li class="menu">
                    <a class="dropdown-toggle" data-bs-toggle="collapse" data-bs-target="#forms" aria-controls="forms" aria-expanded="false">
                        <div class="">
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
                                class="feather feather-clipboard"
                            >
                                <path d="M16 4h2a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2H6a2 2 0 0 1-2-2V6a2 2 0 0 1 2-2h2"></path>
                                <rect x="8" y="2" width="8" height="4" rx="1" ry="1"></rect>
                            </svg>
                            <span>{{ $t('forms') }}</span>
                        </div>
                        <div>
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
                                class="feather feather-chevron-right"
                            >
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
                            <router-link to="/forms/checkbox-radio" @click="toggleMobileMenu">Checkbox &amp; Radio</router-link>
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
                            <router-link to="/forms/date-picker" @click="toggleMobileMenu">Date &amp; Range Picker </router-link>
                        </li>
                        <li>
                            <router-link to="/forms/clipboard" @click="toggleMobileMenu">Clipboard</router-link>
                        </li>
                    </ul>
                </li>

                <li class="menu">
                    <a class="dropdown-toggle" data-bs-toggle="collapse" data-bs-target="#users" aria-controls="users" aria-expanded="false">
                        <div class="">
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
                                class="feather feather-users"
                            >
                                <path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"></path>
                                <circle cx="9" cy="7" r="4"></circle>
                                <path d="M23 21v-2a4 4 0 0 0-3-3.87"></path>
                                <path d="M16 3.13a4 4 0 0 1 0 7.75"></path>
                            </svg>
                            <span>{{ $t('users') }}</span>
                        </div>
                        <div>
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
                                class="feather feather-chevron-right"
                            >
                                <polyline points="9 18 15 12 9 6"></polyline>
                            </svg>
                        </div>
                    </a>

                    <ul id="users" class="collapse submenu list-unstyled" data-bs-parent="#sidebar">
                        <li>
                            <router-link to="/users/profile" @click="toggleMobileMenu">Profile</router-link>
                        </li>
                        <li>
                            <router-link to="/users/account-setting" @click="toggleMobileMenu">Account Settings</router-link>
                        </li>
                    </ul>
                </li>

                <li class="menu">
                    <a class="dropdown-toggle" data-bs-toggle="collapse" data-bs-target="#pages" aria-controls="pages" aria-expanded="false">
                        <div class="">
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
                                class="feather feather-file"
                            >
                                <path d="M13 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V9z"></path>
                                <polyline points="13 2 13 9 20 9"></polyline>
                            </svg>
                            <span>{{ $t('pages') }}</span>
                        </div>
                        <div>
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
                                class="feather feather-chevron-right"
                            >
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
                            <a class="dropdown-toggle" href="#pages-error" data-bs-parent="#pages" data-bs-toggle="collapse" role="button" aria-expanded="false">
                                Error
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
                                    class="feather feather-chevron-right"
                                >
                                    <polyline points="9 18 15 12 9 6"></polyline>
                                </svg>
                            </a>

                            <ul id="pages-error" class="collapse list-unstyled sub-submenu">
                                <li @click="toggleMobileMenu"><a target="_blank" href="/pages/error404">404</a></li>
                                <li @click="toggleMobileMenu"><a target="_blank" href="/pages/error500">500</a></li>
                                <li @click="toggleMobileMenu"><a target="_blank" href="/pages/error503">503</a></li>
                                <li @click="toggleMobileMenu"><a target="_blank" href="/pages/maintenence">Maintanence</a></li>
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
                    <a class="dropdown-toggle" data-bs-toggle="collapse" data-bs-target="#authentication" aria-controls="authentication" aria-expanded="false">
                        <div class="">
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
                            <span>{{ $t('authentication') }}</span>
                        </div>
                        <div>
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
                                class="feather feather-chevron-right"
                            >
                                <polyline points="9 18 15 12 9 6"></polyline>
                            </svg>
                        </div>
                    </a>

                    <ul id="authentication" class="collapse submenu list-unstyled" data-bs-parent="#sidebar">
                        <li @click="toggleMobileMenu"><a target="_blank" href="/auth/login-boxed">Login Boxed</a></li>
                        <li @click="toggleMobileMenu"><a target="_blank" href="/auth/register-boxed">Register Boxed</a></li>
                        <li @click="toggleMobileMenu"><a target="_blank" href="/auth/lockscreen-boxed">Unlock Boxed</a></li>
                        <li @click="toggleMobileMenu"><a target="_blank" href="/auth/pass-recovery-boxed">Recover ID Boxed</a></li>
                        <li @click="toggleMobileMenu"><a target="_blank" href="/auth/login">Login Cover</a></li>
                        <li @click="toggleMobileMenu"><a target="_blank" href="/auth/register">Register Cover</a></li>
                        <li @click="toggleMobileMenu"><a target="_blank" href="/auth/lockscreen">Unlock Cover</a></li>
                        <li @click="toggleMobileMenu"><a target="_blank" href="/auth/pass-recovery">Recover ID Cover</a></li>
                    </ul>
                </li>

                <li class="menu">
                    <router-link to="/dragndrop" class="dropdown-toggle" @click="toggleMobileMenu">
                        <div class="">
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
                                class="feather feather-move"
                            >
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
                                class="feather feather-pie-chart"
                            >
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
                                class="feather feather-book"
                            >
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
