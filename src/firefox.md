# Firefox

## 垂直标签栏+隐藏水平标签栏

1. 安装垂直标签栏插件：Sidebery、树状标签页、Tab Center Reborn
2. 浏览器地址栏输入 about:config，将toolkit.legacyUserProfileCustomizations.stylesheets值改为true;浏览器地址栏输入about:support，打开配置文件夹，新建文件夹命名为chrome，新建一个名叫 userChrome.css 的文件，粘贴以下代码
   ```css
       @-moz-document url("chrome://browser/content/browser.xhtml") {

        /* 这一段是垂直标签栏和水平标签栏切换显示，但是我不需要水平标签栏
        :root:has(#browser > #sidebar-box:is([sidebarcommand="treestyletab_piro_sakura_ne_jp-sidebar-action"],
          [sidebarcommand="_3c078156-979c-498b-8990-85f7987dd929_-sidebar-action"], [sidebarcommand="tabcenter-reborn_ariasuni-sidebar-action"], [sidebarcommand="treetabs_jagiello_it-sidebar-action"], [sidebarcommand="_8d808887-ed13-4931-9f5a-4c0bff979a5a_-sidebar-action"], [sidebarcommand="sidebartabs_asamuzak_jp-sidebar-action"], [sidebarcommand="_f463182b-f93b-4b6d-9a68-b5e9d6d0fd40_-sidebar-action"]):not([hidden="true"]) {
        */
        :root:has(#browser > #sidebar-box) {
        --uc-control-width: 136.5px;
        /** 默认模式控制按钮高度 */
        --uc-control-height: 40px;

        &[uidensity="compact"] {
          /** 紧凑模式控制按钮高度 */
          --uc-control-height: 34px;
        }

        &[uidensity="touch"] {
          /** 触控模式控制按钮高度 */
          --uc-control-height: 44px;
        }

        #navigator-toolbox {
          position: relative;
        }

        &[tabsintitlebar] {
          #titlebar:has(#toolbar-menubar[inactive="true"]) {
            height: 0;

            .titlebar-buttonbox-container {
              background-color: var(--toolbar-bgcolor);
            }
          }

          #titlebar {
            height: calc(12px + 2 * var(--toolbarbutton-inner-padding));
          }

          .titlebar-buttonbox-container {
            position: absolute;
            top: 0;
            right: 0;

            @media (-moz-bool-pref: "layout.css.osx-font-smoothing.enabled") {
              right: unset;
              left: 0;
            }
          }
        }

        #TabsToolbar {
          --tabs-navbar-shadow-size: 0px;

          &>*:not(.titlebar-buttonbox-container) {
            display: none;
          }

          .titlebar-buttonbox-container {
            height: var(--uc-control-height, calc(12px + 2 * var(--toolbarbutton-inner-padding)));
          }
        }

        /** 菜单栏未激活时，在菜单栏里的控制按钮就不显示，不然控制按钮重叠显示 */
        #toolbar-menubar[inactive="true"] .titlebar-buttonbox-container {
          display: none !important;
        }

        #navigator-toolbox:has(#toolbar-menubar[inactive="true"]) {
          >#nav-bar {
            margin-inline: 0 var(--uc-control-width);

            @media (-moz-bool-pref: "layout.css.osx-font-smoothing.enabled") {
              margin-inline: var(--uc-control-width) 0;
            }
          }
        }
      }
    }
   ```