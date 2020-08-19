<template>
  <div id="app" class="bg-gray-100 py-12">
    <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
      <h1 class="text-blue-500 text-3xl">NorthArc workshop</h1>

      <button
        @click="workflow1Click"
        class="underline mr-4"
        :class="{'text-blue-500': activeWorkflow === 1}"
      >Workflow 1</button>
      <button
        @click="activeWorkflow = 2"
        class="underline"
        :class="{'text-blue-500': activeWorkflow === 2}"
      >Workflow 2</button>

      <div class="max-w-3xl mt-8">
        <h2 class="text-xl leading-5 text-blue-800 font-semibold mb-2">Forklaring</h2>
        <p>
          NorthArc er et ruteplanlægningsværktøj, som assisterer servicevirksomheder (læs: planlæggere) i planlægning
          <br />
          <br />NorthArc skal have information omkring opgaver og medarbejderes arbejdstider, for at kunne planlægge en rute. En delmængde af de kunder NorthArc gerne vil
          have fat i, bruger allerede et andet administrativt system.
        </p>
      </div>

      <div class="max-w-3xl mt-8">
        <h2 class="text-xl leading-5 text-blue-800 font-semibold mb-2">Mål</h2>

        <label class="font-semibold">Lang sigt (2 år)</label>
        <p
          class="mb-4"
        >Målet er på sigt at have API-integrationer til de større administrative systemer, således synkronisering af data sker automatisk.</p>

        <label class="font-semibold">Kort sigt</label>
        <p>Finde et kompromis planlæggerne er tilfredse med. Selvom dette inkluderer trivielt arbejde til en vis grad, så er problemet meget mere håndgribeligt end selv at skulle planlægge opgaverne.</p>
      </div>

      <div class="max-w-3xl mt-8">
        <h2 class="text-xl leading-5 text-blue-800 font-semibold mb-2">Udfordring</h2>
        <p>
          Indtil en integration er på plads, skal der findes en arbejdsgang, der inkluderer planlæggeren, til at holde systemerne synkroniseret. Det er afgørende at opgaverne i NorthArc afspejler de rigtige
          tidspunkter mm. for at ruterne bliver korrekte.
        </p>
      </div>

      <div class="w-full border border-gray-500 my-12"></div>

      <template v-if="activeWorkflow === 1">
        <h1 class="text-xl leading-5 text-green-800 mb-2 mt-12">Workflow 1</h1>

        <p>Planlæggeren uploader en CSV fil med opgaver i et tidsrum, som bliver automatisk synkroniseret. Planlæggeren får opgaverne som har gennemgået en ændring (oprettet, rettet, slettet)</p>

        <!-- scenario 1 -->
        <div class="mt-12">
          <div
            class="max-w-lg flex justify-center mx-auto px-6 pt-5 pb-6 border-2 border-gray-300 border-dashed rounded-md"
          >
            <div class="text-center" @click="showWorkflow1 = true">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                stroke="currentColor"
                class="mx-auto h-12 w-12 text-gray-400"
                fill="currentColor"
                viewBox="0 0 20 20"
              >
                <path
                  d="M9 10V8h2v2h2v2h-2v2H9v-2H7v-2h2zm-5 8h12V6h-4V2H4v16zm-2 1V0h12l4 4v16H2v-1z"
                />
              </svg>

              <p class="mt-1 text-sm text-gray-600">
                <button
                  type="button"
                  class="font-medium text-indigo-600 hover:text-indigo-500 focus:outline-none focus:underline transition duration-150 ease-in-out"
                >Upload en fil</button>
                eller træk og slip
              </p>
              <p class="mt-1 text-xs text-gray-500">CSV</p>
            </div>
          </div>
          <p class="text-red-500 text-center text-cs font-semibold">(demo: tryk på upload en fil)</p>

          <div v-if="showWorkflow1">
            <div class="shadow overflow-hidden sm:rounded-md mt-24">
              <ul>
                <li class="bg-white">
                  <a
                    href="#"
                    class="block hover:bg-gray-50 focus:outline-none focus:bg-gray-50 transition duration-150 ease-in-out"
                  >
                    <div class="flex items-center px-4 py-4 sm:px-6">
                      <div class="min-w-0 flex-1 flex items-center">
                        <div class="flex-shrink-0">
                          <img
                            class="h-12 w-12 rounded-full"
                            src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
                            alt
                          />
                        </div>
                        <div class="min-w-0 flex-1 px-4 md:grid md:grid-cols-2 md:gap-4">
                          <div>
                            <div
                              class="text-sm leading-5 font-medium text-indigo-600 truncate"
                            >Ted Fox</div>
                            <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                              <svg
                                class="flex-shrink-0 mr-1.5 h-4 w-4 text-gray-400"
                                viewBox="0 0 20 20"
                                fill="none"
                                stroke="currentColor"
                              >
                                <path
                                  d="M10 20S3 10.87 3 7a7 7 0 1 1 14 0c0 3.87-7 13-7 13zm0-11a2 2 0 1 0 0-4 2 2 0 0 0 0 4z"
                                />
                              </svg>
                              <span class="truncate">Vestre Alle 54st, 9000 Aalborg</span>
                            </div>
                          </div>
                          <div class="hidden md:block">
                            <div>
                              <div class="text-sm leading-5 text-gray-900">
                                <time datetime="2020-01-07">August 20, 2020 - 14:00-16:00</time>
                              </div>
                              <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                                <svg
                                  class="flex-shrink-0 mr-1.5 h-5 w-5 text-green-400"
                                  viewBox="0 0 20 20"
                                  fill="currentColor"
                                >
                                  <path
                                    fill-rule="evenodd"
                                    d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
                                    clip-rule="evenodd"
                                  />
                                </svg>
                                Bekræftet af kunde
                              </div>
                            </div>
                          </div>
                        </div>
                      </div>
                      <div class="flex flex-col items-center w-32">
                        <div
                          class="h-8 w-8 rounded-full bg-green-200 flex justify-center items-center"
                        >
                          <svg
                            class="h-4 w-4 text-green-900"
                            viewBox="0 0 20 20"
                            fill="currentColor"
                          >
                            <path
                              fill-rule="evenodd"
                              d="M0 11l2-2 5 5L18 3l2 2L7 18z"
                              clip-rule="evenodd"
                            />
                          </svg>
                        </div>
                        <span class="text-sm leading-5 text-gray-800 mt-1">Oprettet</span>
                      </div>
                    </div>
                  </a>
                </li>
                <li class="border-t border-gray-200 bg-white">
                  <a
                    href="#"
                    class="block hover:bg-gray-50 focus:outline-none focus:bg-gray-50 transition duration-150 ease-in-out"
                  >
                    <div class="flex items-center px-4 py-4 sm:px-6">
                      <div class="min-w-0 flex-1 flex items-center">
                        <div class="flex-shrink-0">
                          <img
                            class="h-12 w-12 rounded-full"
                            src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
                            alt
                          />
                        </div>
                        <div class="min-w-0 flex-1 px-4 md:grid md:grid-cols-2 md:gap-4">
                          <div>
                            <div
                              class="text-sm leading-5 font-medium text-indigo-600 truncate"
                            >Paul Winker</div>
                            <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                              <svg
                                class="flex-shrink-0 mr-1.5 h-4 w-4 text-gray-400"
                                viewBox="0 0 20 20"
                                fill="none"
                                stroke="currentColor"
                              >
                                <path
                                  d="M10 20S3 10.87 3 7a7 7 0 1 1 14 0c0 3.87-7 13-7 13zm0-11a2 2 0 1 0 0-4 2 2 0 0 0 0 4z"
                                />
                              </svg>
                              <span class="truncate">Vestre Alle 54st, 9000 Aalborg</span>
                            </div>
                          </div>
                          <div class="hidden md:block">
                            <div>
                              <div class="text-sm leading-5 text-gray-900">
                                <time datetime="2020-01-07">August 20, 2020 - 14:00-16:00</time>
                              </div>
                              <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                                <svg
                                  class="flex-shrink-0 mr-1.5 h-5 w-5 text-green-400"
                                  viewBox="0 0 20 20"
                                  fill="currentColor"
                                >
                                  <path
                                    fill-rule="evenodd"
                                    d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
                                    clip-rule="evenodd"
                                  />
                                </svg>
                                Bekræftet af kunde
                              </div>
                            </div>
                          </div>
                        </div>
                      </div>
                      <div class="flex flex-col items-center w-32">
                        <div
                          class="h-8 w-8 rounded-full bg-green-200 flex justify-center items-center"
                        >
                          <svg
                            class="h-4 w-4 text-green-900"
                            viewBox="0 0 20 20"
                            fill="currentColor"
                          >
                            <path
                              fill-rule="evenodd"
                              d="M0 11l2-2 5 5L18 3l2 2L7 18z"
                              clip-rule="evenodd"
                            />
                          </svg>
                        </div>
                        <span class="text-sm leading-5 text-gray-800 mt-1">Oprettet</span>
                      </div>
                    </div>
                  </a>
                </li>
                <li class="border-t border-gray-200 bg-white">
                  <a
                    href="#"
                    class="block hover:bg-gray-50 focus:outline-none focus:bg-gray-50 transition duration-150 ease-in-out"
                  >
                    <div class="flex items-center px-4 py-4 sm:px-6">
                      <div class="min-w-0 flex-1 flex items-center">
                        <div class="flex-shrink-0">
                          <img
                            class="h-12 w-12 rounded-full"
                            src="https://images.unsplash.com/photo-1550525811-e5869dd03032?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
                            alt
                          />
                        </div>
                        <div class="min-w-0 flex-1 px-4 md:grid md:grid-cols-2 md:gap-4">
                          <div>
                            <div class="text-sm leading-5 font-medium text-indigo-600 truncate">Will</div>
                            <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                              <svg
                                class="flex-shrink-0 mr-1.5 h-4 w-4 text-gray-400"
                                viewBox="0 0 20 20"
                                fill="none"
                                stroke="currentColor"
                              >
                                <path
                                  d="M10 20S3 10.87 3 7a7 7 0 1 1 14 0c0 3.87-7 13-7 13zm0-11a2 2 0 1 0 0-4 2 2 0 0 0 0 4z"
                                />
                              </svg>
                              <span class="truncate">Sønder Alle 54st, 9000 Aalborg</span>
                            </div>
                          </div>
                          <div class="hidden md:block">
                            <div>
                              <div class="text-sm leading-5 text-gray-900">
                                <time datetime="2020-01-07">August 20, 2020 - 14:00-16:00</time>
                              </div>
                              <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                                <svg
                                  class="flex-shrink-0 mr-1.5 h-5 w-5 text-green-400"
                                  viewBox="0 0 20 20"
                                  fill="currentColor"
                                >
                                  <path
                                    fill-rule="evenodd"
                                    d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
                                    clip-rule="evenodd"
                                  />
                                </svg>
                                Bekræftet af kunde
                              </div>
                            </div>
                          </div>
                        </div>
                      </div>
                      <div class="flex flex-col items-center w-32">
                        <div
                          class="h-8 w-8 rounded-full bg-yellow-200 flex justify-center items-center"
                        >
                          <svg
                            class="h-4 w-4 text-yellow-900"
                            viewBox="0 0 20 20"
                            fill="currentColor"
                          >
                            <path
                              fill-rule="evenodd"
                              d="M12.3 3.7l4 4L4 20H0v-4L12.3 3.7zm1.4-1.4L16 0l4 4-2.3 2.3-4-4z"
                              clip-rule="evenodd"
                            />
                          </svg>
                        </div>
                        <span class="text-sm leading-5 text-gray-800 mt-1">Opdateret</span>
                      </div>
                    </div>
                  </a>
                </li>
                <li class="border-t border-gray-200 bg-white">
                  <a
                    href="#"
                    class="block hover:bg-gray-50 focus:outline-none focus:bg-gray-50 transition duration-150 ease-in-out"
                  >
                    <div class="flex items-center px-4 py-4 sm:px-6">
                      <div class="min-w-0 flex-1 flex items-center">
                        <div class="flex-shrink-0">
                          <img
                            class="h-12 w-12 rounded-full"
                            src="https://images.unsplash.com/photo-1500648767791-00dcc994a43e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
                            alt
                          />
                        </div>
                        <div class="min-w-0 flex-1 px-4 md:grid md:grid-cols-2 md:gap-4">
                          <div>
                            <div
                              class="text-sm leading-5 font-medium text-indigo-600 truncate"
                            >Smith Jenkin</div>
                            <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                              <svg
                                class="flex-shrink-0 mr-1.5 h-4 w-4 text-gray-400"
                                viewBox="0 0 20 20"
                                fill="none"
                                stroke="currentColor"
                              >
                                <path
                                  d="M10 20S3 10.87 3 7a7 7 0 1 1 14 0c0 3.87-7 13-7 13zm0-11a2 2 0 1 0 0-4 2 2 0 0 0 0 4z"
                                />
                              </svg>
                              <span class="truncate">Østre Alle 54st, 9000 Aalborg</span>
                            </div>
                          </div>
                          <div class="hidden md:block">
                            <div>
                              <div class="text-sm leading-5 text-gray-900">
                                <time datetime="2020-01-07">August 20, 2020 - 14:00-16:00</time>
                              </div>
                              <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                                <svg
                                  class="flex-shrink-0 mr-1.5 h-5 w-5 text-green-400"
                                  viewBox="0 0 20 20"
                                  fill="currentColor"
                                >
                                  <path
                                    fill-rule="evenodd"
                                    d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
                                    clip-rule="evenodd"
                                  />
                                </svg>
                                Bekræftet af kunde
                              </div>
                            </div>
                          </div>
                        </div>
                      </div>
                      <div class="flex flex-col items-center w-32">
                        <div
                          class="h-8 w-8 rounded-full bg-red-200 flex justify-center items-center"
                        >
                          <svg
                            class="h-4 w-4 text-red-900"
                            viewBox="0 0 20 20"
                            fill="currentColor"
                          >
                            <path
                              fill-rule="evenodd"
                              d="M6 2l2-2h4l2 2h4v2H2V2h4zM3 6h14l-1 14H4L3 6zm5 2v10h1V8H8zm3 0v10h1V8h-1z"
                              clip-rule="evenodd"
                            />
                          </svg>
                        </div>
                        <span class="text-sm leading-5 text-gray-800 mt-1">Slettet</span>
                      </div>
                    </div>
                  </a>
                </li>
                <li class="border-t border-gray-200 bg-white">
                  <a
                    href="#"
                    class="block hover:bg-gray-50 focus:outline-none focus:bg-gray-50 transition duration-150 ease-in-out"
                  >
                    <div class="flex items-center px-4 py-4 sm:px-6">
                      <div class="min-w-0 flex-1 flex items-center">
                        <div class="flex-shrink-0">
                          <img
                            class="h-12 w-12 rounded-full"
                            src="https://images.unsplash.com/photo-1550525811-e5869dd03032?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
                            alt
                          />
                        </div>
                        <div class="min-w-0 flex-1 px-4 md:grid md:grid-cols-2 md:gap-4">
                          <div>
                            <div
                              class="text-sm leading-5 font-medium text-indigo-600 truncate"
                            >Richard Cooper</div>
                            <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                              <svg
                                class="flex-shrink-0 mr-1.5 h-4 w-4 text-gray-400"
                                viewBox="0 0 20 20"
                                fill="none"
                                stroke="currentColor"
                              >
                                <path
                                  d="M10 20S3 10.87 3 7a7 7 0 1 1 14 0c0 3.87-7 13-7 13zm0-11a2 2 0 1 0 0-4 2 2 0 0 0 0 4z"
                                />
                              </svg>
                              <span class="truncate">Sønder Alle 54st, 9000 Aalborg</span>
                            </div>
                          </div>
                          <div class="hidden md:block">
                            <div>
                              <div class="text-sm leading-5 text-gray-900">
                                <time datetime="2020-01-07">August 20, 2020 - 14:00-16:00</time>
                              </div>
                              <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                                <svg
                                  class="flex-shrink-0 mr-1.5 h-5 w-5 text-green-400"
                                  viewBox="0 0 20 20"
                                  fill="currentColor"
                                >
                                  <path
                                    fill-rule="evenodd"
                                    d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
                                    clip-rule="evenodd"
                                  />
                                </svg>
                                Bekræftet af kunde
                              </div>
                            </div>
                          </div>
                        </div>
                      </div>
                      <div class="flex flex-col items-center w-32">
                        <div
                          class="h-8 w-8 rounded-full bg-yellow-200 flex justify-center items-center"
                        >
                          <svg
                            class="h-4 w-4 text-yellow-900"
                            viewBox="0 0 20 20"
                            fill="currentColor"
                          >
                            <path
                              fill-rule="evenodd"
                              d="M12.3 3.7l4 4L4 20H0v-4L12.3 3.7zm1.4-1.4L16 0l4 4-2.3 2.3-4-4z"
                              clip-rule="evenodd"
                            />
                          </svg>
                        </div>
                        <span class="text-sm leading-5 text-gray-800 mt-1">Opdateret</span>
                      </div>
                    </div>
                  </a>
                </li>
              </ul>
            </div>

            <div class="mt-8 flex justify-center">
              <span class="inline-flex rounded-md shadow-sm">
                <button
                  type="button"
                  class="inline-flex items-center px-6 py-3 border border-transparent text-base leading-6 font-medium rounded-md text-white bg-green-600 hover:bg-green-500 focus:outline-none focus:border-green-700 focus:shadow-outline-green active:bg-green-700 transition ease-in-out duration-150"
                >Godkend ændringer</button>
              </span>
            </div>
          </div>
        </div>
      </template>

      <template v-if="activeWorkflow === 2">
        <h1 class="text-xl leading-5 text-green-800 mb-2 mt-12">Workflow 2</h1>

        <p>Planlæggeren indtaster selv opgaver. Inden en planlægningssession foretages en inspektion af de opgaver, der ligger i perioden</p>
        <p>Dette workflow tager længere tid at udføre, men giver planlæggeren øget kontrol</p>

        <!-- scenario 2 -->
        <div class="mt-12">
          <div class="flex">
            <div class="w-64">
              <label class="block text-sm font-medium leading-5 text-gray-700">Fra dato</label>
              <div class="mt-1 rounded-md shadow-sm">
                <input
                  value="2020-08-21"
                  type="date"
                  class="form-input block w-full transition duration-150 ease-in-out sm:text-sm sm:leading-5"
                />
              </div>
            </div>

            <div class="w-64 ml-4">
              <label class="block text-sm font-medium leading-5 text-gray-700">Til dato</label>
              <div class="mt-1 rounded-md shadow-sm">
                <input
                  type="date"
                  value="2020-08-22"
                  class="form-input block w-full transition duration-150 ease-in-out sm:text-sm sm:leading-5"
                />
              </div>
            </div>
          </div>

          <div class="shadow overflow-hidden sm:rounded-md mt-12">
            <ul>
              <li class="bg-white">
                <a
                  href="#"
                  class="block hover:bg-gray-50 focus:outline-none focus:bg-gray-50 transition duration-150 ease-in-out"
                >
                  <div class="flex items-center px-4 py-4 sm:px-6">
                    <div class="min-w-0 flex-1 flex items-center">
                      <div class="flex-shrink-0">
                        <img
                          class="h-12 w-12 rounded-full"
                          src="https://images.unsplash.com/photo-1500648767791-00dcc994a43e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
                          alt
                        />
                      </div>
                      <div class="min-w-0 flex-1 px-4 md:grid md:grid-cols-3 md:gap-4">
                        <div>
                          <div
                            class="text-sm leading-5 font-medium text-indigo-600 truncate"
                          >Ted Fox</div>
                          <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                            <svg
                              class="flex-shrink-0 mr-1.5 h-4 w-4 text-gray-400"
                              viewBox="0 0 20 20"
                              fill="none"
                              stroke="currentColor"
                            >
                              <path
                                d="M10 20S3 10.87 3 7a7 7 0 1 1 14 0c0 3.87-7 13-7 13zm0-11a2 2 0 1 0 0-4 2 2 0 0 0 0 4z"
                              />
                            </svg>
                            <span class="truncate">Vestre Alle 54st, 9000 Aalborg</span>
                          </div>
                        </div>
                        <div class="hidden md:block">
                          <div>
                            <div class="text-sm leading-5 text-gray-900">
                              <time datetime="2020-01-07">August 20, 2020 - 14:00-16:00</time>
                            </div>
                            <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                              <svg
                                class="flex-shrink-0 mr-1.5 h-5 w-5 text-green-400"
                                viewBox="0 0 20 20"
                                fill="currentColor"
                              >
                                <path
                                  fill-rule="evenodd"
                                  d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
                                  clip-rule="evenodd"
                                />
                              </svg>
                              Bekræftet af kunde
                            </div>
                          </div>
                        </div>

                        <div class="hidden md:block">
                          <div>
                            <div class="text-sm leading-5 text-gray-900">
                              <div>Sidst valideret</div>
                            </div>
                            <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                              <svg
                                class="flex-shrink-0 mr-1.5 h-5 w-5 text-yellow-400"
                                viewBox="0 0 20 20"
                                fill="currentColor"
                              >
                                <path
                                  fill-rule="evenodd"
                                  d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
                                  clip-rule="evenodd"
                                />
                              </svg>
                              2 dage siden
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                    <span class="inline-flex rounded-md shadow-sm">
                      <button
                        type="button"
                        class="inline-flex items-center px-4 py-2 border border-gray-300 text-sm leading-5 font-medium rounded-md text-gray-700 bg-white hover:text-gray-500 focus:outline-none focus:border-blue-300 focus:shadow-outline-blue active:text-gray-800 active:bg-gray-50 transition ease-in-out duration-150"
                      >Godkend</button>
                    </span>
                  </div>
                </a>
              </li>
              <li class="border-t border-gray-200bg-white">
                <a
                  href="#"
                  class="block hover:bg-gray-50 focus:outline-none focus:bg-gray-50 transition duration-150 ease-in-out"
                >
                  <div class="flex items-center px-4 py-4 sm:px-6">
                    <div class="min-w-0 flex-1 flex items-center">
                      <div class="flex-shrink-0">
                        <img
                          class="h-12 w-12 rounded-full"
                          src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
                          alt
                        />
                      </div>
                      <div class="min-w-0 flex-1 px-4 md:grid md:grid-cols-3 md:gap-4">
                        <div>
                          <div
                            class="text-sm leading-5 font-medium text-indigo-600 truncate"
                          >Clarke Kent</div>
                          <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                            <svg
                              class="flex-shrink-0 mr-1.5 h-4 w-4 text-gray-400"
                              viewBox="0 0 20 20"
                              fill="none"
                              stroke="currentColor"
                            >
                              <path
                                d="M10 20S3 10.87 3 7a7 7 0 1 1 14 0c0 3.87-7 13-7 13zm0-11a2 2 0 1 0 0-4 2 2 0 0 0 0 4z"
                              />
                            </svg>
                            <span class="truncate">Søndre Alle 93, 9000 Aalborg</span>
                          </div>
                        </div>
                        <div class="hidden md:block">
                          <div>
                            <div class="text-sm leading-5 text-gray-900">
                              <time datetime="2020-01-07">August 21, 2020 - 14:00-16:00</time>
                            </div>
                            <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                              <svg
                                class="flex-shrink-0 mr-1.5 h-5 w-5 text-green-400"
                                viewBox="0 0 20 20"
                                fill="currentColor"
                              >
                                <path
                                  fill-rule="evenodd"
                                  d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
                                  clip-rule="evenodd"
                                />
                              </svg>
                              Bekræftet af kunde
                            </div>
                          </div>
                        </div>

                        <div class="hidden md:block">
                          <div>
                            <div class="text-sm leading-5 text-gray-900">
                              <div>Sidst valideret</div>
                            </div>
                            <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                              <svg
                                class="flex-shrink-0 mr-1.5 h-5 w-5 text-yellow-400"
                                viewBox="0 0 20 20"
                                fill="currentColor"
                              >
                                <path
                                  fill-rule="evenodd"
                                  d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
                                  clip-rule="evenodd"
                                />
                              </svg>
                              4 timer siden
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                    <span class="inline-flex rounded-md shadow-sm">
                      <button
                        type="button"
                        class="inline-flex items-center px-4 py-2 border border-gray-300 text-sm leading-5 font-medium rounded-md text-gray-700 bg-white hover:text-gray-500 focus:outline-none focus:border-blue-300 focus:shadow-outline-blue active:text-gray-800 active:bg-gray-50 transition ease-in-out duration-150"
                      >Godkend</button>
                    </span>
                  </div>
                </a>
              </li>

              <li class="border-t border-gray-200 bg-white">
                <a
                  href="#"
                  class="block hover:bg-gray-50 focus:outline-none focus:bg-gray-50 transition duration-150 ease-in-out"
                >
                  <div class="flex items-center px-4 py-4 sm:px-6">
                    <div class="min-w-0 flex-1 flex items-center">
                      <div class="flex-shrink-0">
                        <img
                          class="h-12 w-12 rounded-full"
                          src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
                          alt
                        />
                      </div>
                      <div class="min-w-0 flex-1 px-4 md:grid md:grid-cols-3 md:gap-4">
                        <div>
                          <div
                            class="text-sm leading-5 font-medium text-indigo-600 truncate"
                          >Declan Blake</div>
                          <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                            <svg
                              class="flex-shrink-0 mr-1.5 h-4 w-4 text-gray-400"
                              viewBox="0 0 20 20"
                              fill="none"
                              stroke="currentColor"
                            >
                              <path
                                d="M10 20S3 10.87 3 7a7 7 0 1 1 14 0c0 3.87-7 13-7 13zm0-11a2 2 0 1 0 0-4 2 2 0 0 0 0 4z"
                              />
                            </svg>
                            <span class="truncate">Jyllandsgade 93, 9000 Aalborg</span>
                          </div>
                        </div>
                        <div class="hidden md:block">
                          <div>
                            <div class="text-sm leading-5 text-gray-900">
                              <time datetime="2020-01-07">August 21, 2020 - 10:00-12:00</time>
                            </div>
                            <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                              <svg
                                class="flex-shrink-0 mr-1.5 h-5 w-5 text-green-400"
                                viewBox="0 0 20 20"
                                fill="currentColor"
                              >
                                <path
                                  fill-rule="evenodd"
                                  d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
                                  clip-rule="evenodd"
                                />
                              </svg>
                              Bekræftet af kunde
                            </div>
                          </div>
                        </div>

                        <div class="hidden md:block">
                          <div>
                            <div class="text-sm leading-5 text-gray-900">
                              <div>Sidst valideret</div>
                            </div>
                            <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                              <svg
                                class="flex-shrink-0 mr-1.5 h-5 w-5 text-yellow-400"
                                viewBox="0 0 20 20"
                                fill="currentColor"
                              >
                                <path
                                  fill-rule="evenodd"
                                  d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
                                  clip-rule="evenodd"
                                />
                              </svg>
                              1 dag siden
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                    <span class="inline-flex rounded-md shadow-sm">
                      <button
                        type="button"
                        class="inline-flex items-center px-4 py-2 border border-gray-300 text-sm leading-5 font-medium rounded-md text-gray-700 bg-white hover:text-gray-500 focus:outline-none focus:border-blue-300 focus:shadow-outline-blue active:text-gray-800 active:bg-gray-50 transition ease-in-out duration-150"
                      >Godkend</button>
                    </span>
                  </div>
                </a>
              </li>

              <li class="border-t border-gray-200 bg-white">
                <a
                  href="#"
                  class="block hover:bg-gray-50 focus:outline-none focus:bg-gray-50 transition duration-150 ease-in-out"
                >
                  <div class="flex items-center px-4 py-4 sm:px-6">
                    <div class="min-w-0 flex-1 flex items-center">
                      <div class="flex-shrink-0">
                        <img
                          class="h-12 w-12 rounded-full"
                          src="https://images.unsplash.com/photo-1491528323818-fdd1faba62cc?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
                          alt
                        />
                      </div>
                      <div class="min-w-0 flex-1 px-4 md:grid md:grid-cols-3 md:gap-4">
                        <div>
                          <div
                            class="text-sm leading-5 font-medium text-indigo-600 truncate"
                          >Teo Thomson</div>
                          <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                            <svg
                              class="flex-shrink-0 mr-1.5 h-4 w-4 text-gray-400"
                              viewBox="0 0 20 20"
                              fill="none"
                              stroke="currentColor"
                            >
                              <path
                                d="M10 20S3 10.87 3 7a7 7 0 1 1 14 0c0 3.87-7 13-7 13zm0-11a2 2 0 1 0 0-4 2 2 0 0 0 0 4z"
                              />
                            </svg>
                            <span class="truncate">Jyllandsgade 93, 9000 Aalborg</span>
                          </div>
                        </div>
                        <div class="hidden md:block">
                          <div>
                            <div class="text-sm leading-5 text-gray-900">
                              <time datetime="2020-01-07">August 21, 2020 - 10:00-12:00</time>
                            </div>
                            <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                              <svg
                                class="flex-shrink-0 mr-1.5 h-5 w-5 text-green-400"
                                viewBox="0 0 20 20"
                                fill="currentColor"
                              >
                                <path
                                  fill-rule="evenodd"
                                  d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
                                  clip-rule="evenodd"
                                />
                              </svg>
                              Bekræftet af kunde
                            </div>
                          </div>
                        </div>

                        <div class="hidden md:block">
                          <div>
                            <div class="text-sm leading-5 text-gray-900">
                              <div>Sidst valideret</div>
                            </div>
                            <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                              <svg
                                class="flex-shrink-0 mr-1.5 h-5 w-5 text-yellow-400"
                                viewBox="0 0 20 20"
                                fill="currentColor"
                              >
                                <path
                                  fill-rule="evenodd"
                                  d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
                                  clip-rule="evenodd"
                                />
                              </svg>
                              16 timer siden
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                    <span class="inline-flex rounded-md shadow-sm">
                      <button
                        type="button"
                        class="inline-flex items-center px-4 py-2 border border-gray-300 text-sm leading-5 font-medium rounded-md text-gray-700 bg-white hover:text-gray-500 focus:outline-none focus:border-blue-300 focus:shadow-outline-blue active:text-gray-800 active:bg-gray-50 transition ease-in-out duration-150"
                      >Godkend</button>
                    </span>
                  </div>
                </a>
              </li>

              <li class="border-t border-gray-200 bg-white">
                <a
                  href="#"
                  class="block hover:bg-gray-50 focus:outline-none focus:bg-gray-50 transition duration-150 ease-in-out"
                >
                  <div class="flex items-center px-4 py-4 sm:px-6">
                    <div class="min-w-0 flex-1 flex items-center">
                      <div class="flex-shrink-0">
                        <img
                          class="h-12 w-12 rounded-full"
                          src="https://images.unsplash.com/photo-1550525811-e5869dd03032?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
                          alt
                        />
                      </div>
                      <div class="min-w-0 flex-1 px-4 md:grid md:grid-cols-3 md:gap-4">
                        <div>
                          <div
                            class="text-sm leading-5 font-medium text-indigo-600 truncate"
                          >Mac Higgs</div>
                          <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                            <svg
                              class="flex-shrink-0 mr-1.5 h-4 w-4 text-gray-400"
                              viewBox="0 0 20 20"
                              fill="none"
                              stroke="currentColor"
                            >
                              <path
                                d="M10 20S3 10.87 3 7a7 7 0 1 1 14 0c0 3.87-7 13-7 13zm0-11a2 2 0 1 0 0-4 2 2 0 0 0 0 4z"
                              />
                            </svg>
                            <span class="truncate">Nytorv 15, 9000 Aalborg</span>
                          </div>
                        </div>
                        <div class="hidden md:block">
                          <div>
                            <div class="text-sm leading-5 text-gray-900">
                              <time datetime="2020-01-07">August 21, 2020 - 10:00-12:00</time>
                            </div>
                            <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                              <svg
                                class="flex-shrink-0 mr-1.5 h-5 w-5 text-green-400"
                                viewBox="0 0 20 20"
                                fill="currentColor"
                              >
                                <path
                                  fill-rule="evenodd"
                                  d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
                                  clip-rule="evenodd"
                                />
                              </svg>
                              Bekræftet af kunde
                            </div>
                          </div>
                        </div>

                        <div class="hidden md:block">
                          <div>
                            <div class="text-sm leading-5 text-gray-900">
                              <div>Sidst valideret</div>
                            </div>
                            <div class="mt-2 flex items-center text-sm leading-5 text-gray-500">
                              <svg
                                class="flex-shrink-0 mr-1.5 h-5 w-5 text-yellow-400"
                                viewBox="0 0 20 20"
                                fill="currentColor"
                              >
                                <path
                                  fill-rule="evenodd"
                                  d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
                                  clip-rule="evenodd"
                                />
                              </svg>
                              1 uge siden
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                    <span class="inline-flex rounded-md shadow-sm">
                      <button
                        type="button"
                        class="inline-flex items-center px-4 py-2 border border-gray-300 text-sm leading-5 font-medium rounded-md text-gray-700 bg-white hover:text-gray-500 focus:outline-none focus:border-blue-300 focus:shadow-outline-blue active:text-gray-800 active:bg-gray-50 transition ease-in-out duration-150"
                      >Godkend</button>
                    </span>
                  </div>
                </a>
              </li>
            </ul>
          </div>

          <div class="mt-8 flex justify-center">
            <span class="inline-flex rounded-md shadow-sm">
              <button
                type="button"
                class="inline-flex items-center px-6 py-3 border border-transparent text-base leading-6 font-medium rounded-md text-white bg-green-600 hover:bg-green-500 focus:outline-none focus:border-green-700 focus:shadow-outline-green active:bg-green-700 transition ease-in-out duration-150"
              >Start planlægning</button>
            </span>
          </div>
        </div>
      </template>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      showWorkflow1: false,
      activeWorkflow: 1,
    };
  },
  methods: {
    workflow1Click() {
      this.activeWorkflow = 1;
      this.showWorkflow1 = false;
    },
  },
};
</script>

<style>
</style>
