<template>
  <div>
    <!-- Page title -->
    <PageTitle class="parallax3">
      <template v-slot:title>
        {{ $t('links.agent') }}
      </template>
      <template v-slot:breadcrumb>
        <li>
          <NuxtLink :to="localePath('agent')">
            {{ $t('links.agent') }}
          </NuxtLink>
        </li>
      </template>
    </PageTitle>

    <!-- Province Select -->
    <section class="flat-row background-theme row-promobox">
      <div class="container">
        <div class="row">
          <div class="col-md-12">
            <div class="flat-promobox style1 color-white">
              <div class="promobox-group-content">
                <h3>
                  <span v-if="selected === 1">{{ $t('province.on') }}</span>
                  <span v-else-if="selected === 2">{{
                    $t('province.qc')
                  }}</span>
                  <span v-else-if="selected === 3">{{
                    $t('province.bc')
                  }}</span>
                  <span v-else-if="selected === 4">{{
                    $t('province.ab')
                  }}</span>
                  <span v-else-if="selected === 5">{{
                    $t('province.sk')
                  }}</span>
                  <span v-else-if="selected === 6">{{
                    $t('province.mb')
                  }}</span>
                  <span v-else-if="selected === 7">{{
                    $t('province.ns')
                  }}</span>
                  <span v-else-if="selected === 8">{{
                    $t('province.nb')
                  }}</span>
                  <span v-else-if="selected === 9">{{
                    $t('province.pe')
                  }}</span>
                  <span v-else-if="selected === 10">{{
                    $t('province.nl')
                  }}</span>
                  <span v-else-if="selected === 11">{{
                    $t('province.nt')
                  }}</span>
                  <span v-else-if="selected === 12">{{
                    $t('province.nu')
                  }}</span>
                  <span v-else-if="selected === 13">{{
                    $t('province.yt')
                  }}</span>
                  <span v-else>{{ $t('province.choose') }}</span>
                </h3>
              </div>
              <div class="promobox-group-btn">
                <select v-model="selected" class="form-control mb-0">
                  <option
                    v-for="option in options"
                    :key="option.value"
                    :value="option.id"
                    >{{ option.province }}</option
                  >
                </select>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Video Section -->
    <VideoSection></VideoSection>

    <!-- <div v-if="selected != 0"> -->
    <div>
      <!-- Agent Features -->
      <section class="flat-row">
        <div class="container">
          <div class="row">
            <div class="col-md-12">
              <div class="title-section">
                <i class="fa fa-line-chart" aria-hidden="true"></i>
                <h1 class="title">{{ $t('features.agent.title') }}</h1>
                <div v-if="selected === 2" class="sub-title">
                  {{ $t('features.agent.subTitleQc') }}
                </div>
                <div v-else class="sub-title">
                  {{ $t('features.agent.subTitle') }}
                </div>
              </div>
            </div>
          </div>

          <div class="row">
            <!-- Features Icons -->
            <div class="col-md-8">
              <div class="row">
                <div class="col-md-6">
                  <div class="iconbox circle large">
                    <div class="row">
                      <div class="col-md-4">
                        <div class="box-header center">
                          <div><i class="fa fa-link"></i></div>
                        </div>
                      </div>
                      <div class="col-md-8">
                        <div class="box-header">
                          <div v-if="selected === 2" class="box-title">
                            {{ $t('features.brokerage.box1.titleQc') }}
                          </div>
                          <div v-else class="box-title">
                            {{ $t('features.brokerage.box1.title') }}
                          </div>
                        </div>
                        <div class="box-content">
                          <ul class="flat-list style2">
                            <li v-if="selected === 2">
                              {{ $t('features.brokerage.box1.list.list1Qc') }}
                            </li>
                            <li v-else>
                              {{ $t('features.brokerage.box1.list.list1') }}
                            </li>
                          </ul>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>

                <div class="col-md-6">
                  <div class="iconbox circle large">
                    <div class="row">
                      <div class="col-md-4">
                        <div class="box-header center">
                          <div><i class="fa fa-file"></i></div>
                        </div>
                      </div>
                      <div class="col-md-8">
                        <div class="box-header">
                          <div class="box-title">
                            {{ $t('features.agent.box2.title') }}
                          </div>
                        </div>
                        <div class="box-content">
                          <ul class="flat-list style2">
                            <li v-if="selected === 2">
                              {{ $t('features.agent.box2.list.list1') }}
                            </li>
                            <li>{{ $t('features.agent.box2.list.list2') }}</li>
                            <li v-if="selected === 1">
                              {{ $t('features.agent.box2.list.list3') }}
                            </li>
                            <li v-if="selected === 2">
                              {{ $t('features.agent.box2.list.list4') }}
                            </li>
                          </ul>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <div class="empty-space height30"></div>
              <div class="row">
                <div class="col-md-6">
                  <div class="iconbox circle large">
                    <div class="row">
                      <div class="col-md-4">
                        <div class="box-header center">
                          <div><i class="fa fa-check"></i></div>
                        </div>
                      </div>
                      <div class="col-md-8">
                        <div class="box-header">
                          <div class="box-title">
                            {{ $t('features.agent.box3.title') }}
                          </div>
                        </div>
                        <div class="box-content">
                          <ul class="flat-list style2">
                            <li v-if="selected === 1">
                              {{ $t('features.agent.box3.list.list1') }}
                            </li>
                            <!-- <li>{{ $t('features.agent.box3.list.list2') }}</li> -->
                            <li>{{ $t('features.agent.box3.list.list3') }}</li>
                            <li>{{ $t('features.agent.box3.list.list4') }}</li>
                            <li>{{ $t('features.agent.box3.list.list5') }}</li>
                          </ul>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <!-- <div class="col-md-6">
                  <div class="iconbox circle large">
                    <div class="row">
                      <div class="col-md-4">
                        <div class="box-header center">
                          <div><i class="fa fa-flag"></i></div>
                        </div>
                      </div>
                      <div class="col-md-8">
                        <div class="box-header">
                          <div class="box-title">
                            {{ $t('features.agent.box4.title') }}
                          </div>
                        </div>
                        <div class="box-content">
                          <ul class="flat-list style2">
                            <li>{{ $t('features.agent.box4.list.list1') }}</li>
                            <li>{{ $t('features.agent.box4.list.list2') }}</li>
                          </ul>
                        </div>
                      </div>
                    </div>
                  </div>
                </div> -->
              </div>
            </div>

            <!-- Pricing -->
            <div class="col-md-4">
              <div class="flat-price-table">
                <h4 class="price-title">
                  {{ $t('pricing.agent.plan1.title') }}
                </h4>
                <div class="sub-title">
                  {{ $t('pricing.agent.plan1.subTitle') }}
                </div>
                <div v-if="$i18n.locale == 'fr'" class="price">
                  <span class="money">29.99</span>
                  <span class="currency-unit">$</span>
                  <span class="time">{{ $t('pricing.agent.plan1.time') }}</span>
                </div>
                <div v-else class="price">
                  <span class="currency-unit">$</span>
                  <span class="money">29.99</span>
                  <span class="time">{{ $t('pricing.agent.plan1.time') }}</span>
                </div>
                <!-- <div class="sub-title pt-15">
                  * {{ $t('pricing.agent.plan1.creditNote') }}
                </div> -->
                <div class="p-15 background-light">
                  <label
                    for="province-select"
                    style="text-align: left; margin: 0 0 10px; display: block;"
                    >{{ $t('province.chooseAlt') }}:</label
                  >
                  <select
                    id="province-select"
                    v-model="selected"
                    class="form-control mb-0"
                  >
                    <option
                      v-for="option in options"
                      :key="option.value"
                      :value="option.id"
                      >{{ option.province }}</option
                    >
                  </select>
                </div>
                <div class="background-light">
                  <a
                    v-if="selected === 2"
                    href="https://qc.docem.ca/Team/Agent/Register"
                    class="price-buynow"
                    target="_blank"
                    >{{ $t('links.register') }}</a
                  >
                  <a
                    v-else-if="selected != 0"
                    href="https://on.docem.ca/Team/Agent/Register"
                    class="price-buynow"
                    target="_blank"
                    >{{ $t('links.register') }}</a
                  >
                  <!-- <a
                    v-if="selected === 3"
                    href="https://bc.docem.ca/Team/Agent/Register"
                    class="price-buynow"
                    target="_blank"
                    >{{ $t('links.register') }}</a
                  >
                  <a
                    v-if="selected === 4"
                    href="https://ab.docem.ca/Team/Agent/Register"
                    class="price-buynow"
                    target="_blank"
                    >{{ $t('links.register') }}</a
                  >
                  <a
                    v-if="selected === 5"
                    href="https://sk.docem.ca/Team/Agent/Register"
                    class="price-buynow"
                    target="_blank"
                    >{{ $t('links.register') }}</a
                  >
                  <a
                    v-if="selected === 6"
                    href="https://mb.docem.ca/Team/Agent/Register"
                    class="price-buynow"
                    target="_blank"
                    >{{ $t('links.register') }}</a
                  >
                  <a
                    v-if="selected === 7"
                    href="https://ns.docem.ca/Team/Agent/Register"
                    class="price-buynow"
                    target="_blank"
                    >{{ $t('links.register') }}</a
                  >
                  <a
                    v-if="selected === 8"
                    href="https://nb.docem.ca/Team/Agent/Register"
                    class="price-buynow"
                    target="_blank"
                    >{{ $t('links.register') }}</a
                  >
                  <a
                    v-if="selected === 9"
                    href="https://pe.docem.ca/Team/Agent/Register"
                    class="price-buynow"
                    target="_blank"
                    >{{ $t('links.register') }}</a
                  >
                  <a
                    v-if="selected === 10"
                    href="https://nl.docem.ca/Team/Agent/Register"
                    class="price-buynow"
                    target="_blank"
                    >{{ $t('links.register') }}</a
                  >
                  <a
                    v-if="selected === 11"
                    href="https://nt.docem.ca/Team/Agent/Register"
                    class="price-buynow"
                    target="_blank"
                    >{{ $t('links.register') }}</a
                  >
                  <a
                    v-if="selected === 12"
                    href="https://nu.docem.ca/Team/Agent/Register"
                    class="price-buynow"
                    target="_blank"
                    >{{ $t('links.register') }}</a
                  >
                  <a
                    v-if="selected === 13"
                    href="https://yt.docem.ca/Team/Agent/Register"
                    class="price-buynow"
                    target="_blank"
                    >{{ $t('links.register') }}</a
                  > -->
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Independant Broker Features -->
      <section class="flat-row background-color">
        <div class="container">
          <div class="row">
            <div class="col-md-12">
              <div class="title-section">
                <i class="fa fa-line-chart" aria-hidden="true"></i>
                <h1 class="title">{{ $t('features.agent.titleBroker') }}</h1>
                <div v-if="selected === 2" class="sub-title">
                  {{ $t('features.agent.subTitleBrokerQc') }}
                </div>
                <div v-else class="sub-title">
                  {{ $t('features.agent.subTitleBroker') }}
                </div>
              </div>
            </div>
          </div>

          <div class="row">
            <!-- Features Icons -->
            <div class="col-md-8">
              <!-- <div class="row">
                <div class="col-md-6">
                  <div class="iconbox circle large">
                    <div class="row">
                      <div class="col-md-4">
                        <div class="box-header center">
                          <div><i class="fa fa-link"></i></div>
                        </div>
                      </div>
                      <div class="col-md-8">
                        <div class="box-header">
                          <div v-if="selected === 2" class="box-title">
                            {{ $t('features.agent.box1.titleQc') }}
                          </div>
                          <div v-else class="box-title">
                            {{ $t('features.agent.box1.title') }}
                          </div>
                        </div>
                        <div class="box-content">
                          <ul class="flat-list style2">
                            <li v-if="selected === 2">
                              {{ $t('features.agent.box1.list.list1Qc') }}
                            </li>
                            <li v-else>
                              {{ $t('features.agent.box1.list.list1') }}
                            </li>
                          </ul>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>

                <div class="col-md-6">
                  <div class="iconbox circle large">
                    <div class="row">
                      <div class="col-md-4">
                        <div class="box-header center">
                          <div><i class="fa fa-file"></i></div>
                        </div>
                      </div>
                      <div class="col-md-8">
                        <div class="box-header">
                          <div class="box-title">
                            {{ $t('features.agent.box2.title') }}
                          </div>
                        </div>
                        <div class="box-content">
                          <ul class="flat-list style2">
                            <li v-if="selected === 2">
                              {{ $t('features.agent.box2.list.list1') }}
                            </li>
                            <li>{{ $t('features.agent.box2.list.list2') }}</li>
                            <li v-if="selected === 1">
                              {{ $t('features.agent.box2.list.list3') }}
                            </li>
                            <li v-if="selected === 2">
                              {{ $t('features.agent.box2.list.list4') }}
                            </li>
                          </ul>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div> -->
              <!-- <div class="empty-space height30"></div> -->
              <!-- <div class="row"> -->
              <!-- <div class="col-md-6">
                  <div class="iconbox circle large">
                    <div class="row">
                      <div class="col-md-4">
                        <div class="box-header center">
                          <div><i class="fa fa-check"></i></div>
                        </div>
                      </div>
                      <div class="col-md-8">
                        <div class="box-header">
                          <div class="box-title">
                            {{ $t('features.agent.box3.title') }}
                          </div>
                        </div>
                        <div class="box-content">
                          <ul class="flat-list style2">
                            <li v-if="selected === 1">
                              {{ $t('features.agent.box3.list.list1') }}
                            </li>
                            <li v-if="selected === 2">
                              {{ $t('features.agent.box3.list.list2Qc') }}
                            </li>
                            <li v-else>
                              {{ $t('features.agent.box3.list.list2') }}
                            </li>
                            <li v-if="selected === 2">
                              {{ $t('features.agent.box3.list.list3Qc') }}
                            </li>
                            <li v-else>
                              {{ $t('features.agent.box3.list.list3') }}
                            </li>
                            <li>{{ $t('features.agent.box3.list.list4') }}</li>
                            <li>{{ $t('features.agent.box3.list.list5') }}</li>
                          </ul>
                        </div>
                      </div>
                    </div>
                  </div>
                </div> -->
              <!-- <div class="col-md-6">
                  <div class="iconbox circle large">
                    <div class="row">
                      <div class="col-md-4">
                        <div class="box-header center">
                          <div><i class="fa fa-flag"></i></div>
                        </div>
                      </div>
                      <div class="col-md-8">
                        <div class="box-header">
                          <div class="box-title">
                            {{ $t('features.agent.box4.title') }}
                          </div>
                        </div>
                        <div class="box-content">
                          <ul class="flat-list style2">
                            <li>{{ $t('features.agent.box4.list.list1') }}</li>
                            <li>{{ $t('features.agent.box4.list.list2') }}</li>
                          </ul>
                        </div>
                      </div>
                    </div>
                  </div>
                </div> -->
              <!-- </div> -->

              <div class="row">
                <div class="col-md-3">
                  <div class="iconbox center circle large">
                    <div class="box-header">
                      <div><i class="fa fa-link"></i></div>
                      <div v-if="selected === 2" class="box-title">
                        {{ $t('features.brokerage.box1.titleQc') }}
                      </div>
                      <div v-else class="box-title">
                        {{ $t('features.brokerage.box1.title') }}
                      </div>
                    </div>
                    <div class="box-content">
                      <ul class="flat-list style2">
                        <li v-if="selected === 2">
                          {{ $t('features.brokerage.box1.list.list1Qc') }}
                        </li>
                        <li v-else>
                          {{ $t('features.brokerage.box1.list.list1') }}
                        </li>
                      </ul>
                    </div>
                  </div>
                </div>

                <div class="col-md-3">
                  <div class="iconbox center circle large">
                    <div class="box-header">
                      <div><i class="fa fa-book"></i></div>
                      <div class="box-title">
                        {{ $t('features.brokerage.box2.title') }}
                      </div>
                    </div>
                    <div class="box-content">
                      <ul class="flat-list style2">
                        <li>{{ $t('features.brokerage.box2.list.list1') }}</li>
                        <li>{{ $t('features.brokerage.box2.list.list2') }}</li>
                      </ul>
                    </div>
                  </div>
                </div>

                <div class="col-md-3">
                  <div class="iconbox center circle large">
                    <div class="box-header">
                      <div><i class="fa fa-list-ul"></i></div>
                      <div class="box-title">
                        {{ $t('features.brokerage.box12.title') }}
                      </div>
                    </div>
                    <div class="box-content">
                      <ul class="flat-list style2">
                        <li>{{ $t('features.brokerage.box12.list.list1') }}</li>
                        <li>{{ $t('features.brokerage.box12.list.list2') }}</li>
                      </ul>
                    </div>
                  </div>
                </div>

                <div class="col-md-3">
                  <div class="iconbox center circle large">
                    <div class="box-header">
                      <div><i class="fa fa-file"></i></div>
                      <div class="box-title">
                        {{ $t('features.brokerage.box8.title') }}
                      </div>
                    </div>
                    <div class="box-content">
                      <ul class="flat-list style2">
                        <li v-if="selected === 2">
                          {{ $t('features.brokerage.box8.list.list1') }}
                        </li>
                        <li>{{ $t('features.brokerage.box8.list.list2') }}</li>
                        <li v-if="selected === 1">
                          {{ $t('features.brokerage.box8.list.list3') }}
                        </li>
                        <li v-if="selected === 2">
                          {{ $t('features.brokerage.box8.list.list4') }}
                        </li>
                      </ul>
                    </div>
                  </div>
                </div>
              </div>
              <div class="empty-space height30"></div>
              <div class="row">
                <div class="col-md-3">
                  <div class="iconbox center circle large">
                    <div class="box-header">
                      <div><i class="fa fa-usd"></i></div>
                      <div class="box-title">
                        {{ $t('features.brokerage.box4.title') }}
                      </div>
                    </div>
                    <div class="box-content">
                      <ul class="flat-list style2">
                        <li>{{ $t('features.brokerage.box4.list.list1') }}</li>
                        <li>{{ $t('features.brokerage.box4.list.list2') }}</li>
                        <li>{{ $t('features.brokerage.box4.list.list3') }}</li>
                        <li>{{ $t('features.brokerage.box4.list.list4') }}</li>
                        <li>{{ $t('features.brokerage.box4.list.list5') }}</li>
                      </ul>
                    </div>
                  </div>
                </div>

                <div class="col-md-3">
                  <div class="iconbox center circle large">
                    <div class="box-header">
                      <div><i class="fa fa-university"></i></div>
                      <div class="box-title">
                        {{ $t('features.brokerage.box5.title') }}
                      </div>
                    </div>
                    <div class="box-content">
                      <ul class="flat-list style2">
                        <li>{{ $t('features.brokerage.box5.list.list1') }}</li>
                        <li>{{ $t('features.brokerage.box5.list.list2') }}</li>
                        <li>{{ $t('features.brokerage.box5.list.list3') }}</li>
                      </ul>
                    </div>
                  </div>
                </div>

                <div class="col-md-3">
                  <div class="iconbox center circle large">
                    <div class="box-header">
                      <div><i class="fa fa-envelope"></i></div>
                      <div class="box-title">
                        {{ $t('features.brokerage.box3.title') }}
                      </div>
                    </div>
                    <div class="box-content">
                      <ul class="flat-list style2">
                        <li>{{ $t('features.brokerage.box3.list.list1') }}</li>
                        <li>{{ $t('features.brokerage.box3.list.list2') }}</li>
                        <li>{{ $t('features.brokerage.box3.list.list3') }}</li>
                      </ul>
                    </div>
                  </div>
                </div>

                <div class="col-md-3">
                  <div class="iconbox center circle large">
                    <div class="box-header">
                      <div><i class="fa fa-file-text-o"></i></div>
                      <div class="box-title">
                        {{ $t('features.brokerage.box14.title') }}
                      </div>
                    </div>
                    <div class="box-content">
                      <ul class="flat-list style2">
                        <li>{{ $t('features.brokerage.box14.list.list1') }}</li>
                        <li>{{ $t('features.brokerage.box14.list.list2') }}</li>
                        <li>{{ $t('features.brokerage.box14.list.list3') }}</li>
                      </ul>
                    </div>
                  </div>
                </div>
              </div>
              <div class="empty-space height30"></div>
              <div v-if="showMore" class="row">
                <div class="col-md-3">
                  <div class="iconbox center circle large">
                    <div class="box-header">
                      <div><i class="fa fa-lock"></i></div>
                      <div class="box-title">
                        {{ $t('features.brokerage.box13.title') }}
                      </div>
                    </div>
                    <div class="box-content">
                      <ul class="flat-list style2">
                        <li v-if="selected === 2">
                          {{ $t('features.brokerage.box13.list.list1Qc') }}
                        </li>
                        <li v-else>
                          {{ $t('features.brokerage.box13.list.list1') }}
                        </li>
                        <li>{{ $t('features.brokerage.box13.list.list2') }}</li>
                      </ul>
                    </div>
                  </div>
                </div>
                <div class="col-md-3">
                  <div class="iconbox center circle large">
                    <div class="box-header">
                      <div><i class="fa fa-check"></i></div>
                      <div class="box-title">
                        {{ $t('features.brokerage.box9.title') }}
                      </div>
                    </div>
                    <div class="box-content">
                      <ul class="flat-list style2">
                        <li v-if="selected === 1">
                          {{ $t('features.brokerage.box9.list.list1') }}
                        </li>
                        <!-- <li v-if="selected === 2">
                          {{ $t('features.brokerage.box9.list.list2Qc') }}
                        </li>
                        <li v-else>
                          {{ $t('features.brokerage.box9.list.list2') }}
                        </li> -->
                        <li v-if="selected === 2">
                          {{ $t('features.brokerage.box9.list.list3Qc') }}
                        </li>
                        <li v-else>
                          {{ $t('features.brokerage.box9.list.list3') }}
                        </li>
                        <li>{{ $t('features.brokerage.box9.list.list4') }}</li>
                        <li>{{ $t('features.brokerage.box9.list.list5') }}</li>
                      </ul>
                    </div>
                  </div>
                </div>

                <div class="col-md-3">
                  <div class="iconbox center circle large">
                    <div class="box-header">
                      <div><i class="fa fa-calendar"></i></div>
                      <div class="box-title">
                        {{ $t('features.brokerage.box7.title') }}
                      </div>
                    </div>
                    <div class="box-content">
                      <ul class="flat-list style2">
                        <!-- <li>{{ $t('features.brokerage.box7.list.list1') }}</li> -->
                        <li>{{ $t('features.brokerage.box7.list.list2') }}</li>
                        <li v-if="selected === 2">
                          {{ $t('features.brokerage.box7.list.list3Qc') }}
                        </li>
                        <li v-else>
                          {{ $t('features.brokerage.box7.list.list3') }}
                        </li>
                        <li v-if="selected === 2">
                          {{ $t('features.brokerage.box7.list.list4') }}
                        </li>
                        <li v-else>
                          {{ $t('features.brokerage.box7.list.list4') }}
                        </li>
                        <li>{{ $t('features.brokerage.box7.list.list5') }}</li>
                        <li v-if="selected === 2">
                          {{ $t('features.brokerage.box7.list.list6') }}
                        </li>
                        <li v-else>
                          {{ $t('features.brokerage.box7.list.list6') }}
                        </li>
                        <li>{{ $t('features.brokerage.box7.list.list7') }}</li>
                      </ul>
                    </div>
                  </div>
                </div>

                <div class="col-md-3">
                  <div class="iconbox center circle large">
                    <div class="box-header">
                      <div><i class="fa fa-comment"></i></div>
                      <div class="box-title">
                        {{ $t('features.brokerage.box11.title') }}
                      </div>
                    </div>
                    <div class="box-content">
                      <ul class="flat-list style2">
                        <li>{{ $t('features.brokerage.box11.list.list1') }}</li>
                        <li>{{ $t('features.brokerage.box11.list.list2') }}</li>
                        <li>{{ $t('features.brokerage.box11.list.list3') }}</li>
                        <li v-if="selected === 2">
                          {{ $t('features.brokerage.box11.list.list4Qc') }}
                        </li>
                        <li v-else>
                          {{ $t('features.brokerage.box11.list.list4') }}
                        </li>
                        <li>{{ $t('features.brokerage.box11.list.list5') }}</li>
                        <li>{{ $t('features.brokerage.box11.list.list6') }}</li>
                      </ul>
                    </div>
                  </div>
                </div>
              </div>

              <div class="row">
                <div class="col-md-12">
                  <button
                    v-if="!showMore"
                    class="flat-button small border-radius-small pull-right background-dark"
                    @click="showMore = !showMore"
                  >
                    {{ $t('features.viewAll') }}
                  </button>
                  <button
                    v-else
                    class="flat-button small border-radius-small pull-right background-dark"
                    @click="showMore = !showMore"
                  >
                    {{ $t('features.viewLess') }}
                  </button>
                </div>
              </div>
            </div>

            <!-- RFP Alternative  -->
            <div class="col-md-4">
              <div class="request-prosopal rfp-alt clearfix">
                <h2 class="text-center">{{ $t('rfp.title') }}</h2>
                <h3 class="color-white text-center mb-15">
                  <span v-if="selected != 0">
                    {{ $t('rfp.starting') }}
                    <span v-if="$i18n.locale == 'fr'" class="label label-theme">
                      <span v-if="selected === 2">99 $</span>
                      <span v-else>149 $</span>
                    </span>
                    <span v-else class="label label-theme">
                      <span v-if="selected === 2">$99</span>
                      <span v-else>$149</span>
                    </span>
                  </span>
                </h3>
                <div class="mb-15">
                  <label for="province-select2">
                    {{ $t('province.choose') }}:
                  </label>
                  <select
                    id="province-select2"
                    v-model="selected"
                    class="form-control mb-0"
                  >
                    <option
                      v-for="option in options"
                      :key="option.value"
                      :value="option.id"
                      >{{ option.province }}</option
                    >
                  </select>
                </div>
                <form
                  id="getaudit"
                  action="https://preprod.docem.ca/faq/RequestPresentation"
                  method="post"
                  class="getautdit-style1"
                >
                  <p class="firstname">
                    <label>{{ $t('rfp.formName') }} *</label>
                    <input
                      id="firstname"
                      name="Firstname"
                      type="text"
                      value=""
                      aria-required="true"
                      required="required"
                    />
                  </p>

                  <p class="lastname">
                    <label>{{ $t('rfp.formLastname') }} *</label>
                    <input
                      id="lastname"
                      name="Lastname"
                      type="text"
                      value=""
                      aria-required="true"
                      required="required"
                    />
                  </p>

                  <p class="email">
                    <label>{{ $t('rfp.formEmail') }} *</label>
                    <input
                      id="email"
                      name="Email"
                      type="email"
                      value=""
                      aria-required="true"
                      required="required"
                    />
                  </p>

                  <p class="phone">
                    <label>{{ $t('rfp.formPhone') }} *</label>
                    <input
                      id="phone"
                      name="Phone"
                      type="text"
                      value=""
                      aria-required="true"
                      required="required"
                    />
                  </p>

                  <p class="website">
                    <label for="website">{{ $t('rfp.formWebsite') }}</label>
                    <input id="website" name="Website" type="text" />
                  </p>
                  <p class="form-submit pull-right">
                    <button name="submit" type="submit" class="pull-right">
                      <i
                        id="formLoader"
                        class="fa fa-spin fa-spinner mr-10"
                        style="display: none;"
                      ></i>
                      {{ $t('rfp.formSubmit') }}
                    </button>
                  </p>

                  <div class="clearfix"></div>
                  <div
                    id="formThanks"
                    class="alert alert-success mt-15"
                    style="display: none;"
                  >
                    <i class="fa fa-check"></i> {{ $t('rfp.thanks') }}
                  </div>
                  <div
                    id="formError"
                    class="alert alert-danger mt-15"
                    style="display: none;"
                  >
                    <i class="fa fa-times"></i> {{ $t('rfp.error') }}
                  </div>
                </form>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Testimonials -->
      <Testimonials></Testimonials>

      <!-- Promobox -->
      <Promobox></Promobox>
    </div>
  </div>
</template>

<script>
import $ from 'jquery'
import config from '~/data/siteConfig'
import PageTitle from '~/components/PageTitle.vue'
import VideoSection from '~/components/VideoSection.vue'
import Testimonials from '~/components/Testimonials.vue'
import Promobox from '~/components/Promobox.vue'

export default {
  components: {
    PageTitle,
    VideoSection,
    Testimonials,
    Promobox,
  },
  data() {
    return {
      metaTitle: this.$t('links.agent'),
      metaDesc: this.$t('meta.desc.home'),
      selected: '0',
      options: [
        { id: 0, value: '', province: this.$t('province.default') },
        { id: 1, value: 'on', province: this.$t('province.on') },
        { id: 2, value: 'qc', province: this.$t('province.qc') },
        { id: 3, value: 'bc', province: this.$t('province.bc') },
        { id: 4, value: 'ab', province: this.$t('province.ab') },
        { id: 5, value: 'sk', province: this.$t('province.sk') },
        { id: 6, value: 'mb', province: this.$t('province.mb') },
        { id: 7, value: 'ns', province: this.$t('province.ns') },
        { id: 8, value: 'nb', province: this.$t('province.nb') },
        { id: 9, value: 'pe', province: this.$t('province.pe') },
        { id: 10, value: 'nl', province: this.$t('province.nl') },
        { id: 11, value: 'nt', province: this.$t('province.nt') },
        { id: 12, value: 'nu', province: this.$t('province.nu') },
        { id: 13, value: 'yt', province: this.$t('province.yt') },
      ],
      showMore: false,
    }
  },
  mounted() {
    $('#getaudit').submit(function (e) {
      e.preventDefault()
      $('#formLoader').show()
      $.ajax({
        url: 'https://on.docem.ca/faq/RequestPresentation',
        type: 'post',
        data: $('#getaudit').serialize(),
        success() {
          $('#formThanks').show()
          $('#formLoader').hide()
        },
        error(msg) {
          if (msg.Success) {
            $('#formThanks').show()
            $('#formLoader').hide()
          } else {
            $('#formError').show()
            $('#formLoader').hide()
          }
        },
      })
    })
  },
  head() {
    return {
      title: this.metaTitle,
      meta: [
        {
          hid: 'twitter:title',
          name: 'twitter:title',
          content: `${this.metaTitle} - ${config.siteTitle}`,
        },
        {
          hid: 'og:title',
          property: 'og:title',
          content: `${this.metaTitle} - ${config.siteTitle}`,
        },
        {
          hid: 'description',
          name: 'description',
          content: this.metaDesc,
        },
        {
          hid: 'twitter:description',
          name: 'twitter:description',
          content: this.metaDesc,
        },
        {
          hid: 'og:description',
          property: 'og:description',
          content: this.metaDesc,
        },
        {
          hid: 'og:image',
          property: 'og:image',
          content: `${config.siteUrl}/img/${this.$t('meta.social.agent')}.jpg`,
        },
        {
          hid: 'twitter:image',
          property: 'og:image',
          content: `${config.siteUrl}/img/${this.$t('meta.social.agent')}.jpg`,
        },
      ],
    }
  },
}
</script>
