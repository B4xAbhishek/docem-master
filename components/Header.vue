<template>
  <div class="container">
    <div class="row">
      <div class="header-wrap clearfix">
        <div class="col-md-3">
          <div id="logo" class="logo">
            <NuxtLink :to="localePath('index')" exact>
              <img src="~assets/images/logo.png" alt="Docem Logo" />
            </NuxtLink>
          </div>
          <!-- /.logo -->
          <div class="btn-menu">
            <span></span>
          </div>
          <!-- //mobile menu button -->
        </div>
        <div class="col-md-9">
          <div class="nav-wrap">
            <!-- <ul class="menu menu-extra">
                <li class="cart">
                  <a href="#"><i class="fa fa-search"></i></a>
                </li>
              </ul> -->
            <nav id="mainnav" class="mainnav">
              <ul class="menu">
                <li>
                  <NuxtLink :to="localePath('index')">
                    {{ $t('links.home') }}
                  </NuxtLink>
                </li>
                <li>
                  <NuxtLink :to="localePath('brokerage')">
                    {{ $t('links.products') }}
                  </NuxtLink>
                </li>
                <li>
                  <NuxtLink :to="localePath('brokerage')">
                    {{ $t('links.association_boards') }}
                  </NuxtLink>
                </li>
                <li>
                  <NuxtLink :to="localePath('brokerage')">
                    {{ $t('links.brokerage') }}
                  </NuxtLink>
                </li>
                <li>
                  <NuxtLink :to="localePath('agent')">
                    {{ $t('links.agent') }}
                  </NuxtLink>
                </li>
                <li>
                  <NuxtLink :to="localePath('manager')">
                    {{ $t('links.manager') }}
                  </NuxtLink>
                </li>
                <li>
                  <NuxtLink :to="localePath('contact-us')">
                    {{ $t('links.contact') }}
                  </NuxtLink>
                </li>
              </ul>
              <!-- /.menu -->
            </nav>
            <!-- /.mainnav -->
          </div>
          <!-- /.nav-wrap -->
        </div>
      </div>
      <!-- /.header-inner -->
    </div>
    <!-- /.row -->
  </div>
</template>

<script>
import $ from 'jquery'
import config from '~/data/siteConfig'

export default {
  data() {
    return {
      siteName: config.siteTitle,
    }
  },
  mounted() {
    // Mobile Nav
    let menuType = 'desktop'
    $(window).on('load resize', function () {
      let currMenuType = 'desktop'

      if (matchMedia('only screen and (max-width: 991px)').matches) {
        currMenuType = 'mobile'
      }

      if (currMenuType !== menuType) {
        menuType = currMenuType

        if (currMenuType === 'mobile') {
          const $mobileMenu = $('#mainnav').attr('id', 'mainnav-mobi').hide()
          const hasChildMenu = $('#mainnav-mobi').find('li:has(ul)')

          $('#header').after($mobileMenu)
          hasChildMenu.children('ul').hide()
          hasChildMenu.children('a').after('<span class="btn-submenu"></span>')
          $('.btn-menu').removeClass('active')
        } else {
          const $desktopMenu = $('#mainnav-mobi')
            .attr('id', 'mainnav')
            .removeAttr('style')

          $desktopMenu.find('.submenu').removeAttr('style')
          $('#header').find('.nav-wrap').append($desktopMenu)
          $('.btn-submenu').remove()
        }
      }
    })

    $(document).on('click', '.btn-menu', function () {
      $('#mainnav-mobi').slideToggle(300)
      $(this).toggleClass('active')
      return false
    })

    $(document).on('click', '#mainnav-mobi li .btn-submenu', function (e) {
      $(this).toggleClass('active').next('ul').slideToggle(300)
      e.stopImmediatePropagation()
      return false
    })

    // Fixed Nav
    const nav = $('.header')
    if (nav.size() !== 0) {
      const offsetTop = $('.header').offset().top
      const headerHeight = $('.header').height()
      const injectSpace = $('<div />', { height: headerHeight }).insertAfter(
        nav
      )
      injectSpace.hide()

      $(window).on('load scroll', function () {
        if ($(window).scrollTop() > offsetTop + 120) {
          $('.header').addClass('downscrolled')
          injectSpace.show()
        } else {
          $('.header').removeClass('header-small downscrolled')
          injectSpace.hide()
        }

        if ($(window).scrollTop() > 500) {
          $('.header').addClass('header-small upscrolled')
        } else {
          $('.header').removeClass('upscrolled')
        }
      })
    }
  },
}
</script>
