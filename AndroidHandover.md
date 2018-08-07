# Android交接文档

> 相关页面功能都已经在“AndroidManifest”备注，在熟悉代码前先阅读readme文档，对项目的整体划分和git的规则都已经详细介绍

## 项目介绍
简介：项目是以电商为核心，围绕之结合一系列功能的项目，整个项目以简易的MVP框架实现，网络请求使用retrofit结合rxjava的方式，view的展示结合butterknife。
整体结构分为三个module: **app**、 **library** 、**push**

* **app 是项目的核心**
* **library 是第三方库**
* **push 推送相关**

**项目地址：[http://gitlab.yuntujk.net/Android/taipinghuihui]**

### app模块
*就比较详细的说明一下app模块，library和push就自行简单了解*   
.   
├── adapter **adapter相关**   
│   ├── MyPagerAdapter.java     
│   ├── base    
│   │   ├── BaseMultiItemQuickAdapter.java  **多种布局继承**      
│   │   ├── BaseQuickAdapter.java **一种布局继承**        
│   │   ├── BaseSectionQuickAdapter.java    
│   │   ├── BaseViewHolder.java     
│   │   ├── ListBaseAdapter.java    
│   │   └── TestHolder.java     
│   ├── divider     
│   │   ├── DividerGridItemDecoration.java
│   │   └── DividerItemDecoration.java
│   ├── entity
│   │   ├── H5PayDemoActivity.java
│   │   ├── MultiItemEntity.java
│   │   ├── PayDemoActivity.java
│   │   └── SectionEntity.java
│   ├── helper
│   │   ├── ItemTouchHelperAdapter.java
│   │   ├── ItemTouchHelperViewHolder.java
│   │   ├── OnStartDragListener.java
│   │   ├── PullRefreshHelper.java
│   │   ├── RecyclerViewHelper.java
│   │   └── SimpleItemTouchHelperCallback.java
│   └── listener
│       ├── OnItemMoveListener.java
│       ├── OnRecyclerViewItemClickListener.java
│       ├── OnRecyclerViewItemLongClickListener.java
│       ├── OnRemoveDataListener.java
│       └── OnRequestDataListener.java
├── apshare     **分享相关**
│   ├── CardShareActivity.java
│   ├── CenterGridviewAdapter.java
│   ├── FontSetAndShareActivity.java
│   ├── GoodShareActivity.java
│   ├── GoodShareGridviewAdapter.java
│   ├── KickBackAnimator.java
│   ├── MainCenterClick.java
│   ├── PicShareActivity.java
│   ├── PicShareAdapter.java
│   ├── ShareEntryActivity.java
│   ├── ShareGridAdapter.java
│   └── WBShareActivity.java
├── base    **application**
│   ├── ApiException.java
│   ├── TaipingApplication.java
│   ├── TaipingFunction.java
│   ├── YanweiApplication.java
│   └── YanweiFunction.java
├── bean    **modelBean**
│   ├── AuthorBaseBean.java
│   ├── AuthorBean.java
│   ├── BaseBean.java
│   ├── BaseDataBean.java
│   ├── BaseGestureBean.java
│   ├── BaseTestBean.java
│   ├── CircleLinkedList.java
│   ├── GuideBean.java
│   ├── Pagination.java
│   ├── TestBean.java
│   ├── UmengMessageBean.java
│   ├── area
│   │   ├── AreaBean.java
│   │   └── ProvincesBean.java
│   ├── base_bean
│   │   ├── BaseConfig.java
│   │   ├── Category.java
│   │   ├── CheckUpdateBean.java
│   │   ├── Guide_columns.java
│   │   ├── Imagepath.java
│   │   ├── Income.java
│   │   ├── JsData.java
│   │   ├── MessageBean.java
│   │   ├── MyJsInterface.java
│   │   ├── RootBase.java
│   │   ├── RootCode.java
│   │   ├── RootStartAd.java
│   │   ├── ScoreBiLi.java
│   │   ├── Sys_columns.java
│   │   ├── TicketJsonBean.java
│   │   └── lanmu
│   ├── cityclass
│   │   ├── AreaBean.java
│   │   ├── MCity.java
│   │   └── RootCity.java
│   ├── cms
│   │   ├── LocationBean.java
│   │   ├── ad
│   │   ├── article
│   │   ├── article_detail
│   │   ├── channel
│   │   └── other
│   ├── event_bean
│   │   ├── good_sub
│   │   ├── huodong
│   │   ├── meeting
│   │   └── order
│   ├── home_bean
│   │   ├── AuthorBean.java
│   │   ├── CircleInt.java
│   │   ├── NewsBean.java
│   │   ├── NewsBeanRoot.java
│   │   ├── NewsBeanRootAuthor.java
│   │   ├── NewsCollectMultiItem.java
│   │   ├── NewsListInfo.java
│   │   ├── NewsMultiItem.java
│   │   ├── NewsUtils.java
│   │   ├── ReadBaseBean.java
│   │   ├── ShortLinkBean.java
│   │   ├── ZhiboData.java
│   │   ├── author_sub
│   │   ├── comment
│   │   ├── news_detail
│   │   ├── score
│   │   ├── search
│   │   └── share
│   ├── index
│   │   ├── IndexBeanRoot.java
│   │   ├── IndexMultiBean.java
│   │   └── active
│   ├── login_bean
│   │   ├── BindPhonePost.java
│   │   ├── BindWeixinCheck.java
│   │   ├── BindWeixinPost.java
│   │   ├── CaptchaPost.java
│   │   ├── FirstSetPasswordPost.java
│   │   ├── LoginPost.java
│   │   ├── RootUserLoginInfo.java
│   │   ├── TpLoginPost.java
│   │   ├── TpUserOrgan.java
│   │   ├── WeixinLoginPost.java
│   │   └── malllogin
│   ├── mall
│   │   ├── address
│   │   ├── authorshop
│   │   ├── banner
│   │   ├── coin
│   │   ├── goodsdetails
│   │   ├── goodslist
│   │   ├── mallnavigation
│   │   ├── ordersend
│   │   ├── refounds
│   │   └── store
│   ├── mall_bean
│   │   ├── GoodsBean.java
│   │   ├── GoodsSelectType.java
│   │   ├── MallNavigationBean.java
│   │   ├── SearchHistory.java
│   │   ├── SelectTypeName.java
│   │   ├── ShopCartBean.java
│   │   ├── ShoppingCartBean.java
│   │   ├── SureOrderBean.java
│   │   ├── SureOrderListBean.java
│   │   ├── SureOrderMultiItem.java
│   │   ├── goods_sku
│   │   ├── homapage
│   │   ├── makeorder
│   │   ├── navigation
│   │   ├── order_detail
│   │   ├── order_list
│   │   ├── shoppingcart
│   │   ├── sureorder
│   │   └── youhui
│   ├── mine_bean
│   │   ├── BangDingShaoInfo.java
│   │   ├── BussinessInformation.java
│   │   ├── CollectBean.java
│   │   ├── CollectBeanRoot.java
│   │   ├── ConsumerInfo.java
│   │   ├── Factory.java
│   │   ├── Guarantee.java
│   │   ├── IntegralBean.java
│   │   ├── MySubBean.java
│   │   ├── RootConsumerInfo.java
│   │   ├── SettingBean.java
│   │   ├── ShangJiaLieBiao.java
│   │   ├── ShangJiaRemark.java
│   │   ├── SubscribeList.java
│   │   ├── card
│   │   ├── coin
│   │   ├── fanlist
│   │   ├── invoice
│   │   ├── lock
│   │   ├── message_center
│   │   ├── quan
│   │   ├── score
│   │   ├── tuijian_shangjia
│   │   ├── user_feedback
│   │   └── user_info
│   ├── share_bean
│   │   ├── GoodsLinkBean.java
│   │   ├── GoodsLinkBeanPost.java
│   │   ├── ShareContentBean.java
│   │   ├── WeixinJsonBean.java
│   │   └── WeixinPicPost.java
│   └── wallet
│       ├── WalletBean.java
│       ├── WalletDetailBean.java
│       ├── WalletPayBean.java
│       ├── WalletPayResultBean.java
│       ├── WalletTradeBean.java
│       ├── WalletTypeBean.java
│       └── sendbean
├── callback  **回调**
│   ├── Callback.java
│   ├── FragmentBackInterface.java
│   ├── IntCallback.java
│   ├── ObjectCallback.java
│   ├── ViewCallback.java
│   └── listener
│       └── OnAdapterItemClickListener.java
├── constant    **配置**
│   ├── ApiService
│   │   ├── ApiInterface.java
│   │   ├── IndexInterface.java
│   │   ├── MallInterface.java
│   │   └── ReadInterface.java
│   ├── AppConfig.java
│   ├── C.java
│   ├── Configure.java
│   ├── Constants.java
│   └── RequestConstants.java
├── ui  **界面（activity 和 fragment）**
│   ├── AdWebActivity.java
│   ├── FileDownLoader.java
│   ├── FileInfo.java
│   ├── LaunchActivity.java
│   ├── MainActivity.java
│   ├── SepecialPushActivity.java
│   ├── TestActivity.java
│   ├── WebViewActivity.java
│   ├── banner
│   │   ├── AlphaPageTransformer.java
│   │   └── GlideImageLoader.java
│   ├── base
│   │   ├── BackHandlerHelper.java
│   │   ├── BannerRecyclerFragment.java
│   │   ├── BaseActivity.java
│   │   ├── BaseFragment.java
│   │   ├── BaseListActivity.java
│   │   ├── BaseListActivityPresenter.java
│   │   ├── BaseListActivitySubscriber.java
│   │   ├── BaseListFragment.java
│   │   ├── BaseListFragmentPresenter.java
│   │   ├── BaseListFragmentSubscriber.java
│   │   ├── ColorStyleTransitionPagerTitleView.java
│   │   ├── DrawerActivity.java
│   │   ├── MQConnectService.java
│   │   ├── MQHelper.java
│   │   ├── MenuTabAdapter.java
│   │   ├── RecyclerViewFragment.java
│   │   └── ToolbarActivity.java
│   ├── event
│   │   ├── CardActivationActivity.java
│   │   ├── CardCodeUseActivity.java
│   │   ├── CardInvitedActivity.java
│   │   ├── CardRollActivity.java
│   │   ├── CardVoucherActivity.java
│   │   ├── EventFragment.java
│   │   ├── GoodSubActivity.java
│   │   ├── GoodSubAdapter.java
│   │   ├── GoodSubFragment.java
│   │   ├── GoodSubPresenter.java
│   │   ├── MeetingActivity.java
│   │   ├── MeetingAdapter.java
│   │   ├── MeetingFragment.java
│   │   ├── MeetingPresenter.java
│   │   ├── ReassignActivity.java
│   │   ├── ScanCardCodeActivity.java
│   │   ├── ScanCardVoucherActivity.java
│   │   ├── ScanCodeResultActivity.java
│   │   ├── VerificationSessionActivity.java
│   │   ├── adapter
│   │   ├── base
│   │   ├── bean
│   │   ├── huodong
│   │   ├── iv
│   │   ├── order
│   │   └── presenter
│   ├── excitation
│   │   ├── CollarCodeActivity.java
│   │   ├── ExcitationDetailActivity.java
│   │   ├── ExcitationErrorActivity.java
│   │   ├── ExcitationPopupActivity.java
│   │   ├── ExcitationProgramActivity.java
│   │   ├── ExcitationReceiveResultActivity.java
│   │   ├── ExcitationsActivity.java
│   │   ├── MaterialDetailActivity.java
│   │   ├── MoreCollarCodesActivity.java
│   │   ├── ScanInspireCodeActivity.java
│   │   ├── UseExcitationActivity.java
│   │   ├── VerificationExcitationActivity.java
│   │   ├── adapter
│   │   ├── base
│   │   ├── bean
│   │   ├── presenter
│   │   └── vu
│   ├── home
│   │   ├── ArticleListFragment.java
│   │   ├── ChannelActivity.java
│   │   ├── HomeFragment.java
│   │   ├── NewsFragment.java
│   │   ├── adapter
│   │   ├── authorcenter
│   │   ├── base
│   │   ├── chenxun
│   │   ├── cms
│   │   ├── comment
│   │   ├── event
│   │   ├── newsdetail
│   │   ├── presenter
│   │   └── search
│   ├── index
│   │   ├── ActiveAdapter.java
│   │   ├── IndexAdapter.java
│   │   ├── IndexFragment.java
│   │   └── IndexPresenter.java
│   ├── login
│   │   ├── GuideActicity.java
│   │   ├── InterestAdapter.java
│   │   ├── InterestFragment.java
│   │   ├── SexChoiceFragment.java
│   │   └── YingdaoPicFragment.java
│   ├── loginnew
│   │   ├── BindPhoneActivity.java
│   │   ├── LoginActivity.java
│   │   ├── LoginActivityPhone.java
│   │   ├── PassLoginFragment.java
│   │   ├── QuickLoginFragment.java
│   │   └── SetPassActivity.java
│   ├── mall
│   │   ├── AddressAddActivity.java
│   │   ├── AddressEditActivity.java
│   │   ├── AddressManagerActivity.java
│   │   ├── DiscountActivity.java
│   │   ├── GoodsDetailActivity.java
│   │   ├── GoodsResultFragment.java
│   │   ├── MallCategoriesActivity.java
│   │   ├── MallCategoriesFragment.java
│   │   ├── MallColumnActivity.java
│   │   ├── MallFragment.java
│   │   ├── MallFristFragment.java
│   │   ├── MallOtherFragment.java
│   │   ├── MallSearchResultActivity.java
│   │   ├── ScoreGoodslActivity.java
│   │   ├── ScoreSureOrderActivity.java
│   │   ├── SearchResultActivity.java
│   │   ├── ShopResultFragment.java
│   │   ├── StoreGoodsActivity.java
│   │   ├── StoreGoodsClassActivity.java
│   │   ├── StoreHomeActivity.java
│   │   ├── SubGoodDetailsActivity.java
│   │   ├── SureOrderActivityNew.java
│   │   ├── VpSimpleFragment.java
│   │   ├── adapter
│   │   ├── base
│   │   ├── bean
│   │   ├── goodsdetail
│   │   ├── goodslist
│   │   ├── goodsreturn
│   │   ├── homepage
│   │   ├── invoice
│   │   ├── listener
│   │   ├── order
│   │   ├── pay
│   │   ├── presenter
│   │   ├── search
│   │   ├── shopingcart
│   │   └── store
│   ├── mallpage
│   │   ├── GalleryAdapter.java
│   │   ├── MallHomeFragment.java
│   │   ├── MallHomeFragmentNew.java
│   │   └── MallPageFragment.java
│   ├── mine
│   │   ├── AboutAppActivity.java
│   │   ├── AboutUsActivity.java
│   │   ├── AccountManagerActivity.java
│   │   ├── ExcepOneFragment.java
│   │   ├── ExcepToMineActivity.java
│   │   ├── ExcepTwoFragment.java
│   │   ├── FeedbackActivity.java
│   │   ├── FollowerDetailActivity.java
│   │   ├── FollowersActivity.java
│   │   ├── MyArticleCollectActivity.java
│   │   ├── MySubActivity.java
│   │   ├── PassMangerActivity.java
│   │   ├── SetNewPassActivity.java
│   │   ├── SettingActivity.java
│   │   ├── ShipAddressActivity.java
│   │   ├── UserInfoActivityNew.java
│   │   ├── adapter
│   │   ├── bindphone
│   │   ├── card
│   │   ├── presenter
│   │   ├── score
│   │   ├── view
│   │   └── vu
│   ├── minenew
│   │   ├── ArticleBrowseRecordActivity.java
│   │   ├── ArticleRecordFragment.java
│   │   ├── AuthorApproveActivity.java
│   │   ├── CustomerManageActivity.java
│   │   ├── GuestManagerActivity.java
│   │   ├── ImageshowActivity.java
│   │   ├── InvoiceManagerActivity.java
│   │   ├── MallRecordFragment.java
│   │   ├── MineFragment.java
│   │   ├── MineFragmentNew.java
│   │   ├── NotPurchasedFragment.java
│   │   ├── PhotoActivity.java
│   │   ├── PurchasedFragment.java
│   │   ├── ShareAddressActivity.java
│   │   ├── ShareArticleClueDetailActivity.java
│   │   ├── ShareArticleClueFragment.java
│   │   ├── ShareClueActivity.java
│   │   ├── ShareMallClueFragment.java
│   │   ├── UserFragment.java
│   │   ├── adpter
│   │   ├── bean
│   │   ├── coins
│   │   ├── fans
│   │   ├── lock
│   │   ├── message_center
│   │   ├── presenter
│   │   ├── quan
│   │   ├── share
│   │   ├── tuijianshangjia
│   │   └── wallet
│   ├── pay
│   │   ├── PayTypeActivity.java
│   │   ├── alipay
│   │   ├── qqwalletpay
│   │   └── wxpay
│   ├── rehome
│   │   ├── ConferenceActivity.java
│   │   ├── HotInquiryActivity.java
│   │   ├── MyCluesActivity.java
│   │   ├── SupplementarySubActivity.java
│   │   ├── adapter
│   │   ├── bean
│   │   ├── presenter
│   │   └── view
│   └── wallet
│       ├── UIUtils.java
│       ├── WalletActivity.java
│       ├── WalletDetailActivity.java
│       ├── adapter
│       └── setting
├── util    **utils**
│   ├── ADFilterUtils.java
│   ├── ArithmeticUtils.java
│   ├── ArticleUtil.java
│   ├── Baseutils.java
│   ├── BigDeUtil.java
│   ├── CryptoUtils.java
│   ├── DataCleanManager.java
│   ├── DateUtil.java
│   ├── DisplayUtil.java
│   ├── DoubleClickUtils.java
│   ├── DpUtil.java
│   ├── FastBlurUtil.java
│   ├── FileUtil.java
│   ├── GsonUtil.java
│   ├── HttpUrl.java
│   ├── HttpUtil.java
│   ├── ImageFileUtils.java
│   ├── ImageUtil.java
│   ├── IntentUtil.java
│   ├── KeyBoardUtils.java
│   ├── Logl.java
│   ├── NavigationUtil.java
│   ├── PermissionUtil.java
│   ├── PhoneUtils.java
│   ├── RegularUtil.java
│   ├── RxUtils.java
│   ├── SharedPreferenceUtil.java
│   ├── SimpleSubscriber.java
│   ├── StatusBarColorCompat.java
│   ├── StringUtils.java
│   ├── TimeUtils.java
│   ├── ToastShow.java
│   ├── ToastUtil.java
│   ├── Util.java
│   ├── ViewPagerIndicatorHelper.java
│   ├── exception
│   │   └── StorageSpaceException.java
│   ├── http
│   │   ├── NetworkUtils.java
│   │   └── TokenInterceptor.java
│   ├── image
│   │   ├── GlideConfiguration.java
│   │   └── GlideHelper.java
│   ├── initapp
│   │   └── InitImageLoad.java
│   ├── sms
│   │   ├── DefaultSmsFilter.java
│   │   ├── SmsFilter.java
│   │   ├── SmsHandler.java
│   │   ├── SmsObserver.java
│   │   ├── SmsResponseCallback.java
│   │   └── VerificationCodeSmsFilter.java
│   └── toast
│       ├── CustomToast.java
│       ├── MCCustomToast.java
│       ├── ScoreToast.java
│       ├── ToastTools.java
│       └── ToastUtils.java
├── view    **自定义view**
│   ├── ClearEditText.java
│   ├── CustomSureDialog.java
│   ├── Djs60.java
│   ├── FiexedRotateTextView.java
│   ├── HorizontalRecyclerview.java
│   ├── ImageTab.java
│   ├── LoadingDialog.java
│   ├── MainNavigationItem.java
│   ├── MainNavigationView.java
│   ├── PassEditView.java
│   ├── PraiseView.java
│   ├── RippleView.java
│   ├── RippleViewLinearLayout.java
│   ├── RotateTextView.java
│   ├── ScrollTextView.java
│   ├── ShareDialog.java
│   ├── SkipAdCircle.java
│   ├── SpaceEditText.java
│   ├── SuperCustomToast.java
│   ├── SwitchTab.java
│   ├── TextTab.java
│   ├── TextTabNoRight.java
│   ├── TitleBarOrdinary.java
│   ├── UpdateDialog.java
│   ├── UploadFileView.java
│   ├── ZoomInScrollView.java
│   ├── base
│   │   └── Tab.java
│   ├── dialog
│   │   ├── CoinUseDialog.java
│   │   ├── HuoDongDialog.java
│   │   └── QuanDialog.java
│   ├── goods_detail
│   │   ├── ItemWebView.java
│   │   └── NoScrollViewPager.java
│   ├── home
│   │   └── EmptyLayout.java
│   ├── index
│   │   └── CluesLoopView.java
│   ├── loading
│   │   ├── LoadingView.java
│   │   ├── LoadingViewCopy.java
│   │   ├── LoadingViewNewYear.java
│   │   └── MallHomeLoadingView.java
│   ├── mall
│   │   ├── ChangeGoodsNumDailog.java
│   │   ├── CircleWebView.java
│   │   ├── DividerGridItemDecoration.java
│   │   ├── FluidLayout.java
│   │   ├── GoodsListPopupWindow.java
│   │   ├── GoodsNumView.java
│   │   ├── GoodsNumViewBig.java
│   │   ├── GoodsPriceGroup.java
│   │   ├── GoodsRectangleItem.java
│   │   ├── GoodsSquareItem.java
│   │   ├── LinearLayoutBaseAdapter.java
│   │   ├── MyLinearLayoutForListView.java
│   │   ├── PaySuccessView.java
│   │   ├── SelectFormatDialog.java
│   │   ├── SkuDialog.java
│   │   ├── SlideDetailsLayout.java
│   │   ├── SpaceItemDecoration.java
│   │   ├── TabsPopupWindow.java
│   │   ├── ZfbPayDialog.java
│   │   └── ZfbTryAgainDialog.java
│   ├── mine
│   │   ├── CardMoreDialog.java
│   │   ├── MineTabView.java
│   │   └── SelectMerchantDialog.java
│   ├── news
│   │   ├── DetailListView.java
│   │   ├── DetailScrollView.java
│   │   ├── DetailWebView.java
│   │   ├── NewsAdShowGroup.java
│   │   ├── NewsAdShowGroupEnd.java
│   │   ├── ShineTextView.java
│   │   └── XiangGuanLinear.java
│   └── sanmudialog
│       ├── AddPicDialog.java
│       ├── AreaDialogNew.java
│       ├── AreaDialogNewUserInfo.java
│       ├── BaseDialog.java
│       ├── ChoiceDialog.java
│       ├── ChoiceDialogI.java
│       ├── ChoiceDialogNew.java
│       ├── CodeDialog.java
│       ├── ConfirmDialog.java
│       ├── ConfirmDialogBack.java
│       ├── ConfirmDialogDouble.java
│       ├── DateDialogNew.java
│       ├── EditDialog.java
│       ├── LoadingDialog.java
│       ├── LongCodeDialog.java
│       ├── PayPassDialog.java
│       ├── PraiseDialog.java
│       └── PromptDialog.java
├── widget
│   ├── AdaptPopupWindow.java
│   ├── AppBarStateChangeListener.java
│   ├── Banner.java
│   ├── BannerVideoPlayer.java
│   ├── BoldTextView.java
│   ├── CalendarItemView.java
│   ├── CardPagerView.java
│   ├── CardRollView.java
│   ├── ContainsEmojiEditText.java
│   ├── CustomScrollView.java
│   ├── ExtendedWebView.java
│   ├── FlexibleScrollView.java
│   ├── GridViewunscroll.java
│   ├── HackyViewPager.java
│   ├── HorizontalIndicator.java
│   ├── HorizontialListView.java
│   ├── ListViewunscroll.java
│   ├── MProgressWheel.java
│   ├── MallConvenientBanner.java
│   ├── MyTextWatcher.java
│   ├── NestedListView.java
│   ├── NoScrollViewPager.java
│   ├── PagerAdapter.java
│   ├── PhotoViewPager.java
│   ├── PointView.java
│   ├── PointViewNew.java
│   ├── RLRecyclerView.java
│   ├── RatingBar.java
│   ├── ReboundScrollView.java
│   ├── RedPointView.java
│   ├── RefundsEditText.java
│   ├── RoundImageView.java
│   ├── ScrollWebView.java
│   ├── SwipeLVForScrollView.java
│   ├── TouchRecyclerView.java
│   ├── TranslateTabBar.java
│   ├── VerticalViewPager.java
│   ├── YanweiTextView.java
│   ├── bouncetab
│   │   ├── BounceScrollView.java
│   │   ├── RotatImageView.java
│   │   └── ViewPagerIndicator.java
│   ├── lock
│   │   ├── LockPatternIndicator.java
│   │   ├── LockPatternUtil.java
│   │   └── LockPatternView.java
│   ├── mallhome
│   │   ├── DaohangViewPager.java
│   │   ├── NewsDetailViewPager.java
│   │   └── PtrClassicRefreshLayout.java
│   └── rfrecyclerview
│       ├── AnimImageView.java
│       ├── AnimRFRecyclerView.java
│       ├── AnimView.java
│       ├── PullToLeftViewGroupl.java
│       ├── TopicRecyclerView.java
│       ├── decoration
│       ├── listener
│       └── manager
└── wxapi   **微信相关**
    ├── WXEntryActivity.java
    └── WXPayEntryActivity.java

以上是整个项目结构，每个模块的作用做了简单备注

## 重要内容
### 美恰
在线客服使用了美恰，封装类：**MQConnectService**
可在其中详细查看

### 激励方案
涉及到的类：
* **ExcitationPopupActivity** 激励方案提示
* **ExcitationsActivity** 激励方案列表
* **ExcitationDetailActivity** 激励方案详情
* **MaterialDetailActivity** 激励物品详情
* **MoreCollarCodesActivity** 激励领用码

### 评价
```
        <!--发布评论-->
        <activity
            android:name=".ui.minenew.coins.PublishCommentActivity"
            android:screenOrientation="portrait"
            android:windowSoftInputMode="adjustPan" />

        <!--待评价-->
        <activity
            android:name=".ui.minenew.coins.WaitCommentActivity"
            android:screenOrientation="portrait" />

        <!--评价中心-->
        <activity
            android:name=".ui.minenew.coins.CommentCenterActivity"
            android:screenOrientation="portrait" />

        <!--服务评价-->
        <activity
            android:name=".ui.minenew.coins.PublishServiceCommentActivity"
            android:screenOrientation="portrait" />

```

### 获客管理

```java
        <!--获客管理-->
        <activity
            android:name=".ui.minenew.CustomerManageActivity"
            android:screenOrientation="portrait" />

        <!--获客管理-->
        <activity
            android:name=".ui.minenew.GuestManagerActivity"
            android:screenOrientation="portrait" />

        <!--分享线索-->
        <activity
            android:name=".ui.minenew.ShareClueActivity"
            android:screenOrientation="portrait" />

        <!--文章分享线索详情-->
        <activity
            android:name=".ui.minenew.ShareArticleClueDetailActivity"
            android:screenOrientation="portrait" />

        <!--商品分享线索详情-->
        <activity
            android:name=".ui.minenew.wallet.ShareMallClueDetailActivity"
            android:screenOrientation="portrait" />

        <!--商品分享线索记录详情-->
        <activity
            android:name=".ui.minenew.ArticleBrowseRecordActivity"
            android:screenOrientation="portrait" />

        <!--分享地址-->
        <activity
            android:name=".ui.minenew.ShareAddressActivity"
            android:screenOrientation="portrait" />
```


