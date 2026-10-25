
> **Nota de preservación (2026-10-25):** estas tablas se generaron parseando los XML
> `assets/datas/*.dat` y `game_maps/*.tmx` del APK de Blade of Conquest v1.0.2
> (com.wmstudio.games.boc, desarrollador 田坤/Kevin_Tien86, juego abandonado retirado de
> Google Play en 2020). Se publican como material de análisis y referencia de diseño para
> el proyecto Valcoria: son tablas de datos y cifras reformateadas, no assets del juego.
> El APK original y la descompilación completa de Ghidra (5.750 funciones en `findings/decomp/`)
> se conservan en el espacio local del proyecto (`/home/z/my-project/rea/blade_of_conquest/`).
# Blade of Conquest — Mapa arquitectónico del código nativo

Fuente: `libcocos2dcpp.so` (ARM32 EABI5, Cocos2d-x 3.x, 27,6 MB, stripped pero con símbolos globales).
Total funciones globales: 16782 · Clases de juego (prefijos SG/AE/SGUI): 183

## Índice de clases de juego

| Clase | Métodos |
|---|---|
| AEPlayerData | 116 |
| SGRoleObj | 104 |
| SGBattleScene | 97 |
| AESandTableScene | 81 |
| AEGameShared | 73 |
| AECityScene | 68 |
| AECtlCmdsPanel | 63 |
| AEVictoryScene | 57 |
| SGBattleField | 56 |
| AEPartyScene | 55 |
| AEInventoryScene | 48 |
| SGCharacterData | 45 |
| SGMapUnitObj | 42 |
| AEGarrisonScene | 42 |
| AESkillBox | 40 |
| AETradeBox | 40 |
| dtNavMesh | 40 |
| SGMapSiteObj | 39 |
| AEBattlePrepare | 39 |
| SGLegion | 38 |
| AERoomScene | 37 |
| AESkillSelBox | 37 |
| AECharactorScene | 37 |
| SGGeneral | 37 |
| p2t::Sweep | 36 |
| AEPrisonBox | 34 |
| SGMergeMap | 33 |
| dtNavMeshQuery | 33 |
| AECreateFileScene | 33 |
| AEGameUtils | 32 |
| AEStoreScene | 31 |
| AEPlatforms | 29 |
| p2t::Triangle | 29 |
| tinyxml2::XMLPrinter | 29 |
| AEAlertDlg | 28 |
| AEMapEditorScene | 28 |
| AESelectGameScene | 27 |
| AEGameMapScene | 26 |
| AEWeeklyBudget | 26 |
| AECharInfoViewer | 26 |
| MyMath | 26 |
| AETalentBox | 25 |
| CocosDenshion::SimpleAudioEngine | 25 |
| AETextInputDlg | 25 |
| AEUpgradeUnitBox | 24 |
| CocosDenshion::android::AndroidJavaEngine | 23 |
| AEGameDataManager | 23 |
| AEMainScene | 22 |
| AECharSelBox | 22 |
| AESiteSelBox | 22 |
| AETalkingDlg | 22 |
| dtCrowd | 22 |
| AETerritoryBox | 21 |
| AESettingsScene | 21 |
| AETimerRunningBox | 21 |
| SGEffects | 20 |
| AEGameDatas | 19 |
| dtTileCache | 19 |
| AEUnitListView | 19 |
| AECharListView | 18 |
| AESiteInfoViewer | 18 |
| AECaptiveListView | 18 |
| AESound | 18 |
| tinyxml2::XMLElement | 18 |
| tinyxml2::XMLDocument | 18 |
| SGWarband | 17 |
| AECtlComboBox | 16 |
| AEAnimatSprite | 16 |
| AECtlNumSelector | 16 |
| p2t::SweepContext | 16 |
| SGUnitsData | 15 |
| AEBeginingScene | 15 |
| SGSoldier | 15 |
| AEGuideLayer | 14 |
| dtPathCorridor | 14 |
| SGSkillInfoData | 14 |
| tinyxml2::XMLNode | 14 |
| AECtlMinimap | 13 |
| AEPauseScene | 13 |
| AEGameOverScene | 13 |
| tinyxml2::XMLAttribute | 13 |
| tinyxml2::XMLUtil | 13 |
| AECtlMoneyBox | 12 |
| AEPlayerInfoBox | 11 |
| AEFindPath | 10 |
| AELabelAtlas | 10 |
| AEZipUtility | 10 |
| duDisplayList | 10 |
| dtObstacleAvoidanceQuery | 10 |
| cocosplay | 10 |
| SceneManager | 9 |
| ArmatureNodeReader | 9 |
| StringTable | 8 |
| dtPathQueue | 8 |
| AEDownloader | 8 |
| AELoadingScene | 8 |
| BoneNodeReader | 8 |
| AECtlScrollCursor | 8 |
| SHA1 | 8 |
| AENetwork | 8 |
| CProfileNode | 7 |
| CProfileManager | 7 |
| dtProximityGrid | 7 |
| p2t::CDT | 7 |
| AECrypto | 7 |
| tinyxml2::StrPair | 7 |
| SGKingdom | 7 |
| __cxxabiv1::__class_type_info | 6 |
| dtNodePool | 6 |
| AppDelegate | 6 |
| dtLocalBoundary | 6 |
| CProfileIterator | 6 |
| SkeletonNodeReader | 6 |
| dtObstacleAvoidanceDebugData | 6 |
| tinyxml2::XMLComment | 6 |
| tinyxml2::XMLUnknown | 6 |
| tinyxml2::XMLDeclaration | 6 |
| AEGameTime | 5 |
| AETalentInfo | 5 |
| RoleTalentInfo | 5 |
| AEAlertDlgBtnCmd | 5 |
| SGSkillPointData | 5 |
| SphereTriangleDetector | 5 |
| p2t::AdvancingFront | 5 |
| AEVec3Data | 4 |
| __cxxabiv1::__si_class_type_info | 4 |
| __cxxabiv1::__vmi_class_type_info | 4 |
| SplashScene | 4 |
| dtNodeQueue | 4 |
| SGDamageInfo | 4 |
| AEMessageInfo | 4 |
| RoleStatuInfo | 4 |
| SGMapCellData | 4 |
| AEInstructInfo | 4 |
| AELinkPathNode | 4 |
| AEPropsCmdItem | 4 |
| WMSBezierMoves | 4 |
| AEPropsItemInfo | 4 |
| AEStoreItemInfo | 4 |
| AEUnitSellGroup | 4 |
| AEDelayOrderInfo | 4 |
| AENavMashPathStep | 4 |
| llvm | 4 |
| tinyobj | 4 |
| DateTime | 4 |
| tinyxml2::XMLText | 4 |
| BaseScene | 4 |
| SGBuffData | 3 |
| __cxxabiv1::__pointer_type_info | 3 |
| SGRoleModel | 3 |
| AEGameConfig | 3 |
| WMSLineMoves | 3 |
| AEKingdomAlarm | 3 |
| AEStateNumData | 3 |
| SGUnitInfoData | 3 |
| AEEnemyInfoData | 3 |
| AEGlobalDropInfo | 3 |
| AESubDropPropInfo | 3 |
| AEStateNumTypeData | 3 |
| AETalkingDlgBtnCmd | 3 |
| SGMapUnitModelData | 3 |
| AEKingdomRelationInfo | 3 |
| WMSMoves | 3 |
| AETipInfos | 2 |
| __cxxabiv1 | 2 |
| __cxxabiv1::__pbase_type_info | 2 |
| __cxxabiv1::__function_type_info | 2 |
| SGFormation | 2 |
| SGEffectData | 2 |
| SGCharTemplate | 2 |
| SGModelSkinInfo | 2 |
| SGAnimeActionData | 2 |
| SGModelAttActInfo | 2 |
| p2t | 2 |
| __cxxabiv1::__forced_unwind | 1 |
| __cxxabiv1::__foreign_exception | 1 |
| __cxxabiv1::__fundamental_type_info | 1 |
| AE2DEffects | 1 |
| duDebugDraw | 1 |
| CocosDenshion::android | 1 |
| dtQueryFilter | 1 |
| AEPlayerDataPreloadInfo | 1 |
| tinyobj::MaterialFileReader | 1 |

---

## AE2DEffects

- `AE2DEffects::playVMPsEft(std::unordered_map<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, cocos2d::Value, std::hash<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::equal_to<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<std::pair<std::basic_string<char, std::char_traits<char>, std::allocator<char> > const, cocos2d::Value> > >&, cocos2d::Node*, int, cocos2d::Vec2 const&)`

## AEAlertDlg

- `AEAlertDlg::AEAlertDlg()`
- `AEAlertDlg::addCmdBtnsList(cocos2d::Vector<AEAlertDlgBtnCmd*> const&)`
- `AEAlertDlg::addPriceCalculator(int, char const*)`
- `AEAlertDlg::backKeyPressed()`
- `AEAlertDlg::btnOnClickDone(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEAlertDlg::cleanUpScene()`
- `AEAlertDlg::closeAlertDlg()`
- `AEAlertDlg::getContentNode()`
- `AEAlertDlg::hideWaittingDlg()`
- `AEAlertDlg::initAlertDlg(int, cocos2d::Size const&, std::function<bool (int)>, cocos2d::EventListenerKeyboard*)`
- `AEAlertDlg::onAlertDlgCloseDone()`
- `AEAlertDlg::onBtnAddCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEAlertDlg::onBtnMinusCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEAlertDlg::onDlgAnimatBtnClicked(cocos2d::Ref*)`
- `AEAlertDlg::onDlgBtnClicked(cocos2d::Ref*)`
- `AEAlertDlg::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AEAlertDlg::setCurNumPercent(float)`
- `AEAlertDlg::setCurNumVal(int)`
- `AEAlertDlg::showAlert(char const*, cocos2d::Node*, int, std::function<bool (int)>, cocos2d::EventListenerKeyboard*)`
- `AEAlertDlg::showAsk3BtnDlg(char const*, cocos2d::Node*, int, std::function<bool (int)>, cocos2d::EventListenerKeyboard*)`
- `AEAlertDlg::showAskDlg(char const*, cocos2d::Node*, int, std::function<bool (int)>, cocos2d::EventListenerKeyboard*)`
- `AEAlertDlg::showDlgPage()`
- `AEAlertDlg::showEmptyDlg(int, cocos2d::Size const&, cocos2d::Vector<AEAlertDlgBtnCmd*> const&, cocos2d::Node*, int, std::function<bool (int)>, cocos2d::EventListenerKeyboard*)`
- `AEAlertDlg::showNumSelectorDlg(char const*, int, int, int, int, char const*, cocos2d::Node*, int, std::function<bool (int)>, cocos2d::EventListenerKeyboard*)`
- `AEAlertDlg::showWaittingDlg(char const*, cocos2d::Node*, int, std::function<bool (int)>, cocos2d::EventListenerKeyboard*)`
- `AEAlertDlg::sliderEvent(cocos2d::Ref*, cocos2d::ui::Slider::EventType)`
- `AEAlertDlg::updateCurNumSel()`
- `AEAlertDlg::~AEAlertDlg()`

## AEAlertDlgBtnCmd

- `AEAlertDlgBtnCmd::AEAlertDlgBtnCmd()`
- `AEAlertDlgBtnCmd::create(int, int, cocos2d::Vec2 const&, cocos2d::Size const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> >)`
- `AEAlertDlgBtnCmd::createAniBtn(std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::basic_string<char, std::char_traits<char>, std::allocator<char> >, int, cocos2d::Vec2 const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> >)`
- `AEAlertDlgBtnCmd::createLabelBtn(int, int, cocos2d::Vec2 const&, cocos2d::Size const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> >)`
- `AEAlertDlgBtnCmd::init(std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::basic_string<char, std::char_traits<char>, std::allocator<char> >, int, cocos2d::Vec2 const&)`

## AEAnimatSprite

- `AEAnimatSprite::AEAnimatSprite()`
- `AEAnimatSprite::clearSpecialDalays()`
- `AEAnimatSprite::createAnimat()`
- `AEAnimatSprite::getCurFrameSprite()`
- `AEAnimatSprite::initAnimat()`
- `AEAnimatSprite::onFrameIndexChanged(int)`
- `AEAnimatSprite::onLastFramePlayed()`
- `AEAnimatSprite::releaseFrames()`
- `AEAnimatSprite::setAnimat(char const*, unsigned short, unsigned short, unsigned short, float, short, unsigned short)`
- `AEAnimatSprite::setCurFrame(int)`
- `AEAnimatSprite::setFrameSpeedRatio(float)`
- `AEAnimatSprite::setFramesCount(int)`
- `AEAnimatSprite::setSpecialDelay(int, float)`
- `AEAnimatSprite::update(float)`
- `AEAnimatSprite::updateFrame()`
- `AEAnimatSprite::~AEAnimatSprite()`

## AEBattlePrepare

- `AEBattlePrepare::AEBattlePrepare()`
- `AEBattlePrepare::addCharTeamInfoBoxToList(cocos2d::ui::ListView*, SGCharacterData*, int, bool)`
- `AEBattlePrepare::backKeyPressed()`
- `AEBattlePrepare::battleOver()`
- `AEBattlePrepare::btnAutoBattleCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEBattlePrepare::btnCmdBattleCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEBattlePrepare::btnEscapeCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEBattlePrepare::checkBattleStat()`
- `AEBattlePrepare::cleanUpScene()`
- `AEBattlePrepare::createSceneLayer(void*)`
- `AEBattlePrepare::escapeFromBattle(SGLegion*)`
- `AEBattlePrepare::excueAutoBattle()`
- `AEBattlePrepare::isWarbandContainChar(SGCharacterData*, bool)`
- `AEBattlePrepare::onAISetBattleChar()`
- `AEBattlePrepare::onAutoBattleTimerActCallback(int)`
- `AEBattlePrepare::onAutoBattleTimerCountDone(int)`
- `AEBattlePrepare::onConfirmEscape(int)`
- `AEBattlePrepare::onCreate(void*)`
- `AEBattlePrepare::onEnter()`
- `AEBattlePrepare::onExit()`
- `AEBattlePrepare::onGuide1StepDone()`
- `AEBattlePrepare::onListItemCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEBattlePrepare::onNotify(unsigned int, void*)`
- `AEBattlePrepare::onPlayerAtuoSetBattleChar()`
- `AEBattlePrepare::onShowGuideStep1()`
- `AEBattlePrepare::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AEBattlePrepare::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AEBattlePrepare::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AEBattlePrepare::returnToMapScene()`
- `AEBattlePrepare::setBattleCharA(SGCharacterData*)`
- `AEBattlePrepare::setBattleCharB(SGCharacterData*)`
- `AEBattlePrepare::setControlEnable(bool)`
- `AEBattlePrepare::showWaitBattleDlg()`
- `AEBattlePrepare::startAutoBattle()`
- `AEBattlePrepare::switchToBattleScene()`
- `AEBattlePrepare::update(float)`
- `AEBattlePrepare::updateCurBattleInfo()`
- `AEBattlePrepare::victorySceneDismissed()`
- `AEBattlePrepare::~AEBattlePrepare()`

## AEBeginingScene

- `AEBeginingScene::AEBeginingScene()`
- `AEBeginingScene::backKeyPressed()`
- `AEBeginingScene::create()`
- `AEBeginingScene::onCleanUp()`
- `AEBeginingScene::onCreate()`
- `AEBeginingScene::onEnter()`
- `AEBeginingScene::onExit()`
- `AEBeginingScene::onShowUpPageDone()`
- `AEBeginingScene::onSwitchToNextScene()`
- `AEBeginingScene::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AEBeginingScene::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AEBeginingScene::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AEBeginingScene::showUpPage(cocos2d::EventListenerKeyboard*)`
- `AEBeginingScene::update(float)`
- `AEBeginingScene::~AEBeginingScene()`

## AECaptiveListView

- `AECaptiveListView::AECaptiveListView()`
- `AECaptiveListView::clearItemSelState()`
- `AECaptiveListView::create(cocos2d::Vector<SGCharacterData*>*, float)`
- `AECaptiveListView::getCurSeledChar()`
- `AECaptiveListView::getSelMode()`
- `AECaptiveListView::initCtl(cocos2d::Vector<SGCharacterData*>*, float)`
- `AECaptiveListView::lvCharListEventScrollView(cocos2d::Ref*, cocos2d::ui::ScrollView::EventType)`
- `AECaptiveListView::onCharBoxTouchCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AECaptiveListView::onEnter()`
- `AECaptiveListView::onExit()`
- `AECaptiveListView::setItemSelState(cocos2d::ui::Button*, bool)`
- `AECaptiveListView::setSelMode(short)`
- `AECaptiveListView::setSeledChar(int)`
- `AECaptiveListView::update(float)`
- `AECaptiveListView::updateListCursorSize()`
- `AECaptiveListView::updateListCursorView()`
- `AECaptiveListView::updateListView()`
- `AECaptiveListView::~AECaptiveListView()`

## AECharInfoViewer

- `AECharInfoViewer::AECharInfoViewer()`
- `AECharInfoViewer::backKeyPressed()`
- `AECharInfoViewer::cleanUpScene()`
- `AECharInfoViewer::clearSlotSelState()`
- `AECharInfoViewer::closePage()`
- `AECharInfoViewer::createSceneLayer(void*)`
- `AECharInfoViewer::menuBtnCloseCallback(cocos2d::Ref*)`
- `AECharInfoViewer::onCreate(void*)`
- `AECharInfoViewer::onEnter()`
- `AECharInfoViewer::onEquipSlotTouchCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AECharInfoViewer::onExit()`
- `AECharInfoViewer::onNotify(unsigned int, void*)`
- `AECharInfoViewer::onPageCloseDone()`
- `AECharInfoViewer::onShowBaseStatuInfos()`
- `AECharInfoViewer::onShowSkillInfos()`
- `AECharInfoViewer::onShowTalentInfos()`
- `AECharInfoViewer::onShowUnitInfos()`
- `AECharInfoViewer::onTabBtnClicked(cocos2d::Ref*)`
- `AECharInfoViewer::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AECharInfoViewer::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AECharInfoViewer::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AECharInfoViewer::setSlotSelOn(cocos2d::Node*)`
- `AECharInfoViewer::showUpPage(SGCharacterData*, cocos2d::EventListenerKeyboard*)`
- `AECharInfoViewer::update(float)`
- `AECharInfoViewer::updateInfoPage()`
- `AECharInfoViewer::~AECharInfoViewer()`

## AECharListView

- `AECharListView::AECharListView()`
- `AECharListView::clearItemSelState()`
- `AECharListView::create(cocos2d::Vector<SGCharacterData*>*, float)`
- `AECharListView::getCurSeledChar()`
- `AECharListView::initCtl(cocos2d::Vector<SGCharacterData*>*, float)`
- `AECharListView::lvCharListEventScrollView(cocos2d::Ref*, cocos2d::ui::ScrollView::EventType)`
- `AECharListView::onCharBoxTouchCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AECharListView::onEnter()`
- `AECharListView::onExit()`
- `AECharListView::onTestMoveOn(cocos2d::Vec2 const&)`
- `AECharListView::restoreTestSelState()`
- `AECharListView::setItemSelState(cocos2d::ui::Button*, bool)`
- `AECharListView::setSeledChar(int)`
- `AECharListView::update(float)`
- `AECharListView::updateListCursorSize()`
- `AECharListView::updateListCursorView()`
- `AECharListView::updateListView()`
- `AECharListView::~AECharListView()`

## AECharSelBox

- `AECharSelBox::AECharSelBox()`
- `AECharSelBox::addCharInfoToList(cocos2d::ui::ListView*, int, int, float, SGCharacterData*, std::function<void (cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)> const&)`
- `AECharSelBox::backKeyPressed()`
- `AECharSelBox::cleanUpScene()`
- `AECharSelBox::closePage()`
- `AECharSelBox::createSceneLayer(void*)`
- `AECharSelBox::fillCharInfoList(cocos2d::ui::ListView*, int, std::function<void (cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)> const&)`
- `AECharSelBox::menuBtnCloseCallback(cocos2d::Ref*)`
- `AECharSelBox::onCreate(void*)`
- `AECharSelBox::onEnter()`
- `AECharSelBox::onExit()`
- `AECharSelBox::onNotify(unsigned int, void*)`
- `AECharSelBox::onPageCloseDone()`
- `AECharSelBox::onSelTagCharCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AECharSelBox::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AECharSelBox::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AECharSelBox::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AECharSelBox::showCharSelector(std::basic_string<char, std::char_traits<char>, std::allocator<char> >, cocos2d::Node*, int, int, std::function<void (int)>, cocos2d::EventListenerKeyboard*)`
- `AECharSelBox::showUpPage(std::basic_string<char, std::char_traits<char>, std::allocator<char> >, int, std::function<void (int)>, cocos2d::EventListenerKeyboard*)`
- `AECharSelBox::update(float)`
- `AECharSelBox::updateSelectorPage()`
- `AECharSelBox::~AECharSelBox()`

## AECharactorScene

- `AECharactorScene::AECharactorScene()`
- `AECharactorScene::backKeyPressed()`
- `AECharactorScene::btnSkillsCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AECharactorScene::btnTalentsCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AECharactorScene::btnTerritoryCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AECharactorScene::cleanUpScene()`
- `AECharactorScene::closePage()`
- `AECharactorScene::createSceneLayer(void*)`
- `AECharactorScene::getUseableSp()`
- `AECharactorScene::lvCharListEventScrollView(cocos2d::Ref*, cocos2d::ui::ScrollView::EventType)`
- `AECharactorScene::menuBtnCLNextCallback(cocos2d::Ref*)`
- `AECharactorScene::menuBtnCLPrevCallback(cocos2d::Ref*)`
- `AECharactorScene::menuBtnCloseCallback(cocos2d::Ref*)`
- `AECharactorScene::onCharBoxTouchCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AECharactorScene::onCreate(void*)`
- `AECharactorScene::onEnter()`
- `AECharactorScene::onExit()`
- `AECharactorScene::onNotify(unsigned int, void*)`
- `AECharactorScene::onPageCloseDone()`
- `AECharactorScene::onResetCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AECharactorScene::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AECharactorScene::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AECharactorScene::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AECharactorScene::onValueChanged(cocos2d::Ref*, int)`
- `AECharactorScene::onValueChanging(cocos2d::Ref*, int, int)`
- `AECharactorScene::resetStatuPoints()`
- `AECharactorScene::saveStatuPoints()`
- `AECharactorScene::showUpPage(cocos2d::EventListenerKeyboard*)`
- `AECharactorScene::skillBoxDismissed(int, int)`
- `AECharactorScene::talentBoxDismissed()`
- `AECharactorScene::territoryBoxDismissed()`
- `AECharactorScene::update(float)`
- `AECharactorScene::updateAlertMarks()`
- `AECharactorScene::updateCharListScrollStat()`
- `AECharactorScene::updateCharsList()`
- `AECharactorScene::updateCharsStatus(SGCharacterData*)`
- `AECharactorScene::~AECharactorScene()`

## AECityScene

- `AECityScene::AECityScene()`
- `AECityScene::backKeyPressed()`
- `AECityScene::backToMenu()`
- `AECityScene::btnCityBtnClickDone(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AECityScene::btnCityFunctionCallback(cocos2d::Ref*)`
- `AECityScene::callRoomCmd(std::basic_string<char, std::char_traits<char>, std::allocator<char> >, int, int, int)`
- `AECityScene::cleanUpScene()`
- `AECityScene::closePage()`
- `AECityScene::createCityBtnTxt(cocos2d::Node*, char const*)`
- `AECityScene::createSceneLayer(void*)`
- `AECityScene::forceLeaveSite()`
- `AECityScene::hideSubMenuCmds()`
- `AECityScene::leaveCity()`
- `AECityScene::onCheckMsgInfos(float)`
- `AECityScene::onCityManageCallback(int)`
- `AECityScene::onConfirmBoostDefence(int)`
- `AECityScene::onConfirmBoostProsperity(int)`
- `AECityScene::onConfirmBuildTower(int)`
- `AECityScene::onConfirmLeaveCity(int)`
- `AECityScene::onCreate(void*)`
- `AECityScene::onCtlCmdsPanelBackToMenu()`
- `AECityScene::onCtlCmdsPanelPause()`
- `AECityScene::onCtlCmdsPanelResume()`
- `AECityScene::onCtlCmdsPanelSaveGame()`
- `AECityScene::onCtlCmdsPanelStartElapsing()`
- `AECityScene::onCtlCmdsPanelStopElapsing()`
- `AECityScene::onEnter()`
- `AECityScene::onExit()`
- `AECityScene::onGuide1TalkDone(int)`
- `AECityScene::onGuide2StepDone()`
- `AECityScene::onInSeigeTimerActCallback(int)`
- `AECityScene::onInSeigeTimerCountDone(int)`
- `AECityScene::onNotify(unsigned int, void*)`
- `AECityScene::onPageCloseDone()`
- `AECityScene::onRestBoxCallback(int)`
- `AECityScene::onRestTimerActCallback(int)`
- `AECityScene::onRestTimerCountDone(int)`
- `AECityScene::onSecondEvent(float)`
- `AECityScene::onSeledSiegeOpt(int)`
- `AECityScene::onShowUpMenusDone()`
- `AECityScene::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AECityScene::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AECityScene::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AECityScene::onVillageManageCallback(int)`
- `AECityScene::onVillageRecuitCallback(int)`
- `AECityScene::openBarracksScene()`
- `AECityScene::openBlackSmithScene()`
- `AECityScene::openCityHall()`
- `AECityScene::openGrocerScene()`
- `AECityScene::openPubScene()`
- `AECityScene::openTownInSiegeMenu()`
- `AECityScene::openTradeCenterScene()`
- `AECityScene::openVillageManageMenus()`
- `AECityScene::openVillageRecuit()`
- `AECityScene::openVillageRestMenus()`
- `AECityScene::openVillageTradeBox()`
- `AECityScene::removeMsgInfo(AEMessageInfo*)`
- `AECityScene::roomSceneDismissed()`
- `AECityScene::showGuideStep2()`
- `AECityScene::showMsgInfo(AEMessageInfo*)`
- `AECityScene::showUpMenus()`
- `AECityScene::showUpSubMenuCmds(cocos2d::Node*, cocos2d::Vector<cocos2d::MenuItemSprite*>&)`
- `AECityScene::startBattleWithTagSiteLegion(SGLegion*)`
- `AECityScene::startRestAct(int)`
- `AECityScene::tradeBoxDismissed()`
- `AECityScene::update(float)`
- `AECityScene::updateSiteInfos()`
- `AECityScene::~AECityScene()`

## AECreateFileScene

- `AECreateFileScene::AECreateFileScene()`
- `AECreateFileScene::backKeyPressed()`
- `AECreateFileScene::cleanUpScene()`
- `AECreateFileScene::closePage()`
- `AECreateFileScene::createSceneLayer(void*)`
- `AECreateFileScene::getRandomDefName()`
- `AECreateFileScene::getUseablePoints()`
- `AECreateFileScene::onBackCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AECreateFileScene::onBtnStartGameCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AECreateFileScene::onChangePlayerName(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)`
- `AECreateFileScene::onCreate(void*)`
- `AECreateFileScene::onEditNameCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AECreateFileScene::onEnter()`
- `AECreateFileScene::onExit()`
- `AECreateFileScene::onNotify(unsigned int, void*)`
- `AECreateFileScene::onPageCloseDone()`
- `AECreateFileScene::onResetCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AECreateFileScene::onSecondEvent(float)`
- `AECreateFileScene::onSelColorCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AECreateFileScene::onStartGame()`
- `AECreateFileScene::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AECreateFileScene::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AECreateFileScene::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AECreateFileScene::onValueChanged(cocos2d::Ref*, int)`
- `AECreateFileScene::onValueChanging(cocos2d::Ref*, int, int)`
- `AECreateFileScene::resetStatuPoints()`
- `AECreateFileScene::setCurColor(int)`
- `AECreateFileScene::setPlayerName(char const*)`
- `AECreateFileScene::showUpPage(int, cocos2d::EventListenerKeyboard*)`
- `AECreateFileScene::update(float)`
- `AECreateFileScene::updateColorSel()`
- `AECreateFileScene::updateInitStatus()`
- `AECreateFileScene::~AECreateFileScene()`

## AECrypto

- `AECrypto::MD5(void*, int, unsigned char*)`
- `AECrypto::decodeBase64(char const*, void*, int)`
- `AECrypto::encodeAESAlipay(std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::basic_string<char, std::char_traits<char>, std::allocator<char> >)`
- `AECrypto::encodeAESWithCBC(unsigned char*, unsigned int, unsigned char*, unsigned char*, int, unsigned char*)`
- `AECrypto::encodeAESWithCBCS(unsigned char*, unsigned int, char*, unsigned char*, int, unsigned char*)`
- `AECrypto::encodeBase64(void const*, int, char*, int)`
- `AECrypto::sha1(unsigned char*, int, unsigned char*, int, unsigned char*, int)`

## AECtlCmdsPanel

- `AECtlCmdsPanel::AECtlCmdsPanel()`
- `AECtlCmdsPanel::btnCharClick(cocos2d::Ref*)`
- `AECtlCmdsPanel::btnCmdClick(cocos2d::Ref*)`
- `AECtlCmdsPanel::btnInventoryClick(cocos2d::Ref*)`
- `AECtlCmdsPanel::btnPartyClick(cocos2d::Ref*)`
- `AECtlCmdsPanel::btnReportClick(cocos2d::Ref*)`
- `AECtlCmdsPanel::btnSettingClick(cocos2d::Ref*)`
- `AECtlCmdsPanel::charactorSceneDismissed()`
- `AECtlCmdsPanel::create(cocos2d::Node*, cocos2d::EventListenerKeyboard*)`
- `AECtlCmdsPanel::hideMenu()`
- `AECtlCmdsPanel::initCtl(cocos2d::Node*, cocos2d::EventListenerKeyboard*)`
- `AECtlCmdsPanel::inventorySceneDismissed()`
- `AECtlCmdsPanel::onCommandMenuClosed(int)`
- `AECtlCmdsPanel::onConfirmBackToMenu(int)`
- `AECtlCmdsPanel::onConfirmLordLeave(int)`
- `AECtlCmdsPanel::onConfirmQuit(int)`
- `AECtlCmdsPanel::onConfirmRecallTagSite(int)`
- `AECtlCmdsPanel::onDiplomacyMenuClosed(int)`
- `AECtlCmdsPanel::onDiplomacyTargetSeledDone(int)`
- `AECtlCmdsPanel::onEnter()`
- `AECtlCmdsPanel::onExit()`
- `AECtlCmdsPanel::onGrantSelTagSite(int)`
- `AECtlCmdsPanel::onGrantTalkDone(int)`
- `AECtlCmdsPanel::onGuide1StepDone()`
- `AECtlCmdsPanel::onLordsPolicyMenuClosed(int)`
- `AECtlCmdsPanel::onRecruitCapsTimerActCallback(int)`
- `AECtlCmdsPanel::onRecruitCapsTimerCountDone(int)`
- `AECtlCmdsPanel::onReportsMenuClosed(int)`
- `AECtlCmdsPanel::onSecondEvent(float)`
- `AECtlCmdsPanel::onSeledAllyExecutorDone(int)`
- `AECtlCmdsPanel::onSeledCapitalSite(int)`
- `AECtlCmdsPanel::onSeledFirendlyMoneyDone(int)`
- `AECtlCmdsPanel::onSeledFriendlyExecutorDone(int)`
- `AECtlCmdsPanel::onSeledGrantTagCharDone(int)`
- `AECtlCmdsPanel::onSeledRecallTagSite(int)`
- `AECtlCmdsPanel::onSeledRedeemCharDone(int)`
- `AECtlCmdsPanel::onSeledRedeemMoneyDone(int)`
- `AECtlCmdsPanel::onSeledTruceExecutorDone(int)`
- `AECtlCmdsPanel::onSeledTruceMoneyDone(int)`
- `AECtlCmdsPanel::onSeledViewTagCharDone(int)`
- `AECtlCmdsPanel::onShowKingdomRlCallback(int)`
- `AECtlCmdsPanel::onShowMsgRecordsCallback(int)`
- `AECtlCmdsPanel::onShowSaveGuide(cocos2d::Vec2)`
- `AECtlCmdsPanel::onSystemMenuClosed(int)`
- `AECtlCmdsPanel::onTerritoryAdminMenuClosed(int)`
- `AECtlCmdsPanel::partySceneDismissed()`
- `AECtlCmdsPanel::pauseGameScene()`
- `AECtlCmdsPanel::quitGame()`
- `AECtlCmdsPanel::resumeGameScene()`
- `AECtlCmdsPanel::saveCurGame()`
- `AECtlCmdsPanel::showCommandMenu()`
- `AECtlCmdsPanel::showDiplomacyMenu()`
- `AECtlCmdsPanel::showDiplomacyTargetList(int)`
- `AECtlCmdsPanel::showKingdomRelations()`
- `AECtlCmdsPanel::showLordsPolicyMenu()`
- `AECtlCmdsPanel::showMsgRecords()`
- `AECtlCmdsPanel::showReportsMenu()`
- `AECtlCmdsPanel::showSystemMenu()`
- `AECtlCmdsPanel::showTerritoryAdminMenu()`
- `AECtlCmdsPanel::showUpMenu()`
- `AECtlCmdsPanel::updateAlertMarks()`
- `AECtlCmdsPanel::updateCmdBtnsStats()`
- `AECtlCmdsPanel::~AECtlCmdsPanel()`

## AECtlComboBox

- `AECtlComboBox::AECtlComboBox()`
- `AECtlComboBox::addComboItem(int, char const*)`
- `AECtlComboBox::btnDropListCallback(cocos2d::Ref*)`
- `AECtlComboBox::btnOptionSeledCallback(cocos2d::Ref*)`
- `AECtlComboBox::clearComboItems()`
- `AECtlComboBox::create(float)`
- `AECtlComboBox::getComboBoxWidth()`
- `AECtlComboBox::getSeledValue()`
- `AECtlComboBox::hideDropDownList()`
- `AECtlComboBox::hideDropDownListOver()`
- `AECtlComboBox::initCtl(float)`
- `AECtlComboBox::openDropDownList()`
- `AECtlComboBox::setComboBoxWidth(float)`
- `AECtlComboBox::setSeledValue(int)`
- `AECtlComboBox::updateDorpDownList()`
- `AECtlComboBox::~AECtlComboBox()`

## AECtlMinimap

- `AECtlMinimap::AECtlMinimap()`
- `AECtlMinimap::create(float, float)`
- `AECtlMinimap::dragMinimapView(cocos2d::Vec2 const&)`
- `AECtlMinimap::getMinimapSiteIconName(int)`
- `AECtlMinimap::getTagPosByTestPos(cocos2d::Vec2 const&)`
- `AECtlMinimap::initCtl(float, float)`
- `AECtlMinimap::setCurPlayerPos(cocos2d::Vec2 const&, float)`
- `AECtlMinimap::setCurViewPos(cocos2d::Vec2 const&)`
- `AECtlMinimap::setIsShowSiteName(bool)`
- `AECtlMinimap::setMinimapViewPos(cocos2d::Vec2 const&)`
- `AECtlMinimap::setZoomLevel(int)`
- `AECtlMinimap::updateMinimap()`
- `AECtlMinimap::~AECtlMinimap()`

## AECtlMoneyBox

- `AECtlMoneyBox::AECtlMoneyBox()`
- `AECtlMoneyBox::StoreSceneDismissed()`
- `AECtlMoneyBox::btnAddCallback(cocos2d::Ref*)`
- `AECtlMoneyBox::create()`
- `AECtlMoneyBox::initCtl()`
- `AECtlMoneyBox::onEnter()`
- `AECtlMoneyBox::onExit()`
- `AECtlMoneyBox::onSecondEvent(float)`
- `AECtlMoneyBox::removeNodeSelf(cocos2d::Node*)`
- `AECtlMoneyBox::setAddBtnVisible(bool, cocos2d::EventListenerKeyboard*)`
- `AECtlMoneyBox::updateCurMoney(bool)`
- `AECtlMoneyBox::~AECtlMoneyBox()`

## AECtlNumSelector

- `AECtlNumSelector::AECtlNumSelector()`
- `AECtlNumSelector::create()`
- `AECtlNumSelector::getCurChangingTimeSpan(float)`
- `AECtlNumSelector::getCurChangingVal(float)`
- `AECtlNumSelector::initCtl()`
- `AECtlNumSelector::onBtnAddCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AECtlNumSelector::onBtnMinusCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AECtlNumSelector::onEnter()`
- `AECtlNumSelector::onExit()`
- `AECtlNumSelector::setBoxWidth(float)`
- `AECtlNumSelector::setIsLockAddNum(bool)`
- `AECtlNumSelector::setIsLockMinusNum(bool)`
- `AECtlNumSelector::setValue(int, bool)`
- `AECtlNumSelector::update(float)`
- `AECtlNumSelector::updateNumView()`
- `AECtlNumSelector::~AECtlNumSelector()`

## AECtlScrollCursor

- `AECtlScrollCursor::AECtlScrollCursor()`
- `AECtlScrollCursor::create(float, float, float, bool)`
- `AECtlScrollCursor::initCtl(float, float, float, bool)`
- `AECtlScrollCursor::setBarHeight(float)`
- `AECtlScrollCursor::setCurPercent(float)`
- `AECtlScrollCursor::setPageSize(float, float)`
- `AECtlScrollCursor::updateBarView()`
- `AECtlScrollCursor::~AECtlScrollCursor()`

## AEDelayOrderInfo

- `AEDelayOrderInfo::AEDelayOrderInfo()`
- `AEDelayOrderInfo::create(int)`
- `AEDelayOrderInfo::initData(int)`
- `AEDelayOrderInfo::~AEDelayOrderInfo()`

## AEDownloader

- `AEDownloader::AEDownloader()`
- `AEDownloader::cancelAllDownloader()`
- `AEDownloader::cancelDownload(AEDownloader*)`
- `AEDownloader::checkTimeOutList(float)`
- `AEDownloader::downloadFile(char const*, char const*, std::function<void (int, char const*)>, float)`
- `AEDownloader::onDownloadRequestCompleted(cocos2d::network::HttpClient*, cocos2d::network::HttpResponse*)`
- `AEDownloader::startDownloadFile()`
- `AEDownloader::~AEDownloader()`

## AEEnemyInfoData

- `AEEnemyInfoData::AEEnemyInfoData()`
- `AEEnemyInfoData::create()`
- `AEEnemyInfoData::initData()`

## AEFindPath

- `AEFindPath::AEFindPath(int, int, int, float)`
- `AEFindPath::drawDebugGrid(cocos2d::DrawNode*)`
- `AEFindPath::excuteFinding()`
- `AEFindPath::findingPath(cocos2d::Vec2 const&, cocos2d::Vec2 const&, std::function<int (cocos2d::Vec2 const&)>)`
- `AEFindPath::getCellInfo(int, int)`
- `AEFindPath::initFindingEnv()`
- `AEFindPath::invalidateMap()`
- `AEFindPath::markOnMap(int, int, int)`
- `AEFindPath::updateMapTransform(cocos2d::Vec2 const&, std::function<int (cocos2d::Vec2 const&)>)`
- `AEFindPath::~AEFindPath()`

## AEGameConfig

- `AEGameConfig::AEGameConfig()`
- `AEGameConfig::getInstance()`
- `AEGameConfig::~AEGameConfig()`

## AEGameDataManager

- `AEGameDataManager::AEGameDataManager()`
- `AEGameDataManager::createDefaultXMLDoc()`
- `AEGameDataManager::createXmlNode(char const*)`
- `AEGameDataManager::getBoolForKey(char const*, bool)`
- `AEGameDataManager::getDoubleForKey(char const*, double)`
- `AEGameDataManager::getFloatForKey(char const*, float)`
- `AEGameDataManager::getIntegerForKey(char const*, int)`
- `AEGameDataManager::getStringForKey(char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `AEGameDataManager::getXmlNodeForKey(char const*)`
- `AEGameDataManager::hasKey(char const*)`
- `AEGameDataManager::openDataFile(char const*)`
- `AEGameDataManager::openXMLFile(char const*)`
- `AEGameDataManager::safeOpenDataFile(char const*)`
- `AEGameDataManager::saveDataFile()`
- `AEGameDataManager::saveXMLFile(char const*)`
- `AEGameDataManager::setBoolForKey(char const*, bool)`
- `AEGameDataManager::setDoubleForKey(char const*, double)`
- `AEGameDataManager::setFloatForKey(char const*, float)`
- `AEGameDataManager::setIntegerForKey(char const*, int)`
- `AEGameDataManager::setStringForKey(char const*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `AEGameDataManager::setXmlNode(tinyxml2::XMLElement*)`
- `AEGameDataManager::setXmlNodeValue(tinyxml2::XMLElement*, char const*, char const*)`
- `AEGameDataManager::~AEGameDataManager()`

## AEGameDatas

- `AEGameDatas::AEGameDatas()`
- `AEGameDatas::FlushGameData()`
- `AEGameDatas::UpdateGameData()`
- `AEGameDatas::addMoney(int)`
- `AEGameDatas::addToInventory(AEPropsItemGroup const&)`
- `AEGameDatas::checkInventoryForItem(int, int)`
- `AEGameDatas::equipTagSlotItem(int)`
- `AEGameDatas::getInstance()`
- `AEGameDatas::getStorageNum(int)`
- `AEGameDatas::inventoryHasSpace(AEPropsItemGroup const&)`
- `AEGameDatas::loadInventoryData()`
- `AEGameDatas::loadStagesData()`
- `AEGameDatas::removeFromInventory(int, int)`
- `AEGameDatas::removeTagSlotEquip(int)`
- `AEGameDatas::removeTagSlotItem(int, int)`
- `AEGameDatas::saveInventoryData()`
- `AEGameDatas::saveStagesData()`
- `AEGameDatas::swapSlotItem(int, int)`
- `AEGameDatas::~AEGameDatas()`

## AEGameMapScene

- `AEGameMapScene::AEGameMapScene()`
- `AEGameMapScene::backKeyPressed()`
- `AEGameMapScene::btnAllSpotsCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEGameMapScene::btnGotoTagCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEGameMapScene::cancelSelTagSpot()`
- `AEGameMapScene::cleanUpScene()`
- `AEGameMapScene::closePage()`
- `AEGameMapScene::createSceneLayer(void*)`
- `AEGameMapScene::menuBtnCloseCallback(cocos2d::Ref*)`
- `AEGameMapScene::onCreate(void*)`
- `AEGameMapScene::onEnter()`
- `AEGameMapScene::onExit()`
- `AEGameMapScene::onMinimapViewChanged(cocos2d::Ref*)`
- `AEGameMapScene::onNotify(unsigned int, void*)`
- `AEGameMapScene::onPageCloseDone()`
- `AEGameMapScene::onSelTagSite(int)`
- `AEGameMapScene::onSelTagSpotDone()`
- `AEGameMapScene::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AEGameMapScene::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AEGameMapScene::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AEGameMapScene::setTagSelSpotPos(cocos2d::Vec2 const&)`
- `AEGameMapScene::showUpPage(SGMapUnitObj*, cocos2d::EventListenerKeyboard*)`
- `AEGameMapScene::startSelTagetSpot()`
- `AEGameMapScene::update(float)`
- `AEGameMapScene::updateMinimapCursor()`
- `AEGameMapScene::~AEGameMapScene()`

## AEGameOverScene

- `AEGameOverScene::AEGameOverScene()`
- `AEGameOverScene::backKeyPressed()`
- `AEGameOverScene::btnBackClicked(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEGameOverScene::create(int)`
- `AEGameOverScene::onCleanUp()`
- `AEGameOverScene::onCreate(int)`
- `AEGameOverScene::onShowUpPageDone()`
- `AEGameOverScene::onSwitchToNextScene()`
- `AEGameOverScene::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AEGameOverScene::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AEGameOverScene::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AEGameOverScene::showUpPage(cocos2d::EventListenerKeyboard*)`
- `AEGameOverScene::~AEGameOverScene()`

## AEGameShared

- `AEGameShared::AEGameShared()`
- `AEGameShared::addGameResFile(char const*)`
- `AEGameShared::addMapResFile(char const*)`
- `AEGameShared::clearGameResFile()`
- `AEGameShared::clearMapResFile()`
- `AEGameShared::clearParticleRes()`
- `AEGameShared::clearToastManager()`
- `AEGameShared::findNavMashPath(cocos2d::Vec2 const&, cocos2d::Vec2 const&)`
- `AEGameShared::getBFViewPos(cocos2d::Vec2 const&)`
- `AEGameShared::getCBZorderByPos(cocos2d::Vec2 const&)`
- `AEGameShared::getCharEquipsByStr(SGCharacterData*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `AEGameShared::getCharRedeemPrice(SGCharacterData*)`
- `AEGameShared::getCharStatusType(SGCharacterData*)`
- `AEGameShared::getCharTemplate(int)`
- `AEGameShared::getClassTotalSpCount(cocos2d::Vector<SGSkillPointData*> const&, int)`
- `AEGameShared::getColorByType(int)`
- `AEGameShared::getEffectData(char const*)`
- `AEGameShared::getEnemyInfo(int)`
- `AEGameShared::getFormation(int)`
- `AEGameShared::getGlobalDropProp(int, std::vector<AEPropsItemGroup, std::allocator<AEPropsItemGroup> >&)`
- `AEGameShared::getImgByID(int)`
- `AEGameShared::getInstance()`
- `AEGameShared::getItemCmdList(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, cocos2d::Vector<AEPropsCmdItem*>&)`
- `AEGameShared::getItemDropByStr(std::vector<AEPropsItemGroup, std::allocator<AEPropsItemGroup> >&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, int, float)`
- `AEGameShared::getItemsListByStr(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::vector<AEPropsItemGroup, std::allocator<AEPropsItemGroup> >&)`
- `AEGameShared::getItemsListStr(std::vector<AEPropsItemGroup, std::allocator<AEPropsItemGroup> >&)`
- `AEGameShared::getKingdom(int)`
- `AEGameShared::getLoadedParticle(char const*)`
- `AEGameShared::getMapSite(int)`
- `AEGameShared::getMapUnitModel(int)`
- `AEGameShared::getMoraleIconTexName(int)`
- `AEGameShared::getMoraleValTexName(int)`
- `AEGameShared::getMsgTypeColor(int)`
- `AEGameShared::getNearestLinkNode(cocos2d::Vec2 const&)`
- `AEGameShared::getOccupyTime(SGMapSiteObj*, SGLegion*)`
- `AEGameShared::getPathNode(int, int)`
- `AEGameShared::getPropItemRequireInfo(AEPropsItemInfo*)`
- `AEGameShared::getPropItemTexPath(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)`
- `AEGameShared::getPropItemTypeName(AEPropsItemInfo*)`
- `AEGameShared::getPropsInfo(int)`
- `AEGameShared::getRandomTipInfo()`
- `AEGameShared::getResNameML(char*)`
- `AEGameShared::getRoleModel(int)`
- `AEGameShared::getSkillClassName(int)`
- `AEGameShared::getSkillDistance(int)`
- `AEGameShared::getSkillLevel(cocos2d::Vector<SGSkillPointData*> const&, int)`
- `AEGameShared::getSkillSelMode(int)`
- `AEGameShared::getSpData(cocos2d::Vector<SGSkillPointData*> const&, int)`
- `AEGameShared::getSpListByStr(cocos2d::Vector<SGSkillPointData*>&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `AEGameShared::getStoreItemInfo(int)`
- `AEGameShared::getTagMashPathStep(int, int, cocos2d::Vector<AENavMashPathStep*>&)`
- `AEGameShared::getTalentInfo(char const*)`
- `AEGameShared::getTalentInfoByStr(RoleTalentInfo&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `AEGameShared::getTalentMaxValForChar(char const*, SGCharacterData*)`
- `AEGameShared::getTexResPathML(char*)`
- `AEGameShared::getUnitFaceTecPath(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)`
- `AEGameShared::getUnitRankIconName(int)`
- `AEGameShared::getUnitUpgradeInfos(int, int)`
- `AEGameShared::getViewLocationByMapPos(cocos2d::Vec2 const&)`
- `AEGameShared::getZorderByPos(cocos2d::Vec2 const&)`
- `AEGameShared::initGameDefaultDatas()`
- `AEGameShared::isEnableIAP()`
- `AEGameShared::isTagSkillCouldUpgrade(SGCharacterData*, int)`
- `AEGameShared::loadGameDatas()`
- `AEGameShared::preloadParticleFile(char const*)`
- `AEGameShared::removeGameResFile(char const*)`
- `AEGameShared::removeMapResFile(char const*)`
- `AEGameShared::showToastGetProps(AEPropsItemGroup const&, cocos2d::Node*, float)`
- `AEGameShared::showToastInfoDone(cocos2d::Node*)`
- `AEGameShared::showToastInfos(char const*, cocos2d::Node*, float)`
- `AEGameShared::updateSkillsCD(cocos2d::Vector<SGSkillPointData*> const&, float)`
- `AEGameShared::upgradeSkillRank(SGCharacterData*, int)`
- `AEGameShared::~AEGameShared()`

## AEGameTime

- `AEGameTime::AEGameTime()`
- `AEGameTime::AEGameTime(int, int)`
- `AEGameTime::addDays(int)`
- `AEGameTime::addHour(float)`
- `AEGameTime::isReachTagTime(AEGameTime const&)`

## AEGameUtils

- `AEGameUtils::AEGameUtils()`
- `AEGameUtils::addPropsToTagList(AEPropsItemGroup&, std::vector<AEPropsItemGroup, std::allocator<AEPropsItemGroup> >&)`
- `AEGameUtils::checkPlayerName(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `AEGameUtils::createAnimat(char const*, int, int, float, int, bool)`
- `AEGameUtils::createBtnIconAndText(cocos2d::Node*, char const*, char const*, float)`
- `AEGameUtils::createBtnLabel(cocos2d::Node*, char const*)`
- `AEGameUtils::createBtnText(cocos2d::Node*, char const*)`
- `AEGameUtils::createBtnView(cocos2d::Node*, char const*, cocos2d::Node*, float)`
- `AEGameUtils::createStandardBtn1(float, std::function<void (cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)> const&)`
- `AEGameUtils::createTagItemSlot(cocos2d::Node*, AEPropsItemGroup&)`
- `AEGameUtils::fillEquipAddInfos(cocos2d::Node*, cocos2d::Vec2 const&, int, int, int, float, float)`
- `AEGameUtils::fillPropItemInfo(cocos2d::Node*, float, AEPropsItemInfo*, int, int, int)`
- `AEGameUtils::fillStatInfos(cocos2d::Node*, cocos2d::Vec2 const&, RoleStatuInfo const&, float, int, float)`
- `AEGameUtils::fillUnitInfoBox(cocos2d::Node*, float, SGUnitsData*)`
- `AEGameUtils::findAllChildNodeByName(cocos2d::Node*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, cocos2d::Vector<cocos2d::Node*>&)`
- `AEGameUtils::findChildNodeByName(cocos2d::Node*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `AEGameUtils::getColorSprite(cocos2d::Sprite*)`
- `AEGameUtils::getItemColorByQuality(int)`
- `AEGameUtils::getPosByStr(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `AEGameUtils::getRandomBool(float)`
- `AEGameUtils::getRandomInt(int, int)`
- `AEGameUtils::getRandomOffsetPos(cocos2d::Vec2 const&)`
- `AEGameUtils::getRandomWordsInStrs(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `AEGameUtils::getStatuInfoStrList(RoleStatuInfo const&, bool)`
- `AEGameUtils::getValRatio(float, float)`
- `AEGameUtils::hidePropItemInfoBox(cocos2d::Node*)`
- `AEGameUtils::hideUnitInfoBox(cocos2d::Node*)`
- `AEGameUtils::initRandomSeed()`
- `AEGameUtils::replaceAll(std::basic_string<char, std::char_traits<char>, std::allocator<char> >&, std::basic_string<char, std::char_traits<char>, std::allocator<char> >&, std::basic_string<char, std::char_traits<char>, std::allocator<char> >&)`
- `AEGameUtils::showPropItemInfo(int, int, int, cocos2d::Node*, cocos2d::Vec2 const&, int, int)`
- `AEGameUtils::showUnitInfoBox(SGUnitsData*, cocos2d::Node*, cocos2d::Vec2 const&, int)`
- `AEGameUtils::~AEGameUtils()`

## AEGarrisonScene

- `AEGarrisonScene::AEGarrisonScene()`
- `AEGarrisonScene::backKeyPressed()`
- `AEGarrisonScene::btnDownMoveCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEGarrisonScene::btnDownMoveUnitCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEGarrisonScene::btnUpMoveCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEGarrisonScene::btnUpMoveUnitCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEGarrisonScene::btnUpgradeCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEGarrisonScene::checkCouldClose()`
- `AEGarrisonScene::cleanUpScene()`
- `AEGarrisonScene::closePage()`
- `AEGarrisonScene::createGarrisonScene(int)`
- `AEGarrisonScene::downMoveItem(SGCharacterData*)`
- `AEGarrisonScene::downMoveItemUnit(SGUnitsData*)`
- `AEGarrisonScene::menuBtnCloseCallback(cocos2d::Ref*)`
- `AEGarrisonScene::moveCharsUnitToOtherChar(SGCharacterData*, SGUnitsData*, SGCharacterData*)`
- `AEGarrisonScene::onCreate(int)`
- `AEGarrisonScene::onDragOpDone(cocos2d::Ref*, int, int)`
- `AEGarrisonScene::onDragging(cocos2d::Ref*, cocos2d::Vec2 const&, int)`
- `AEGarrisonScene::onEnter()`
- `AEGarrisonScene::onExit()`
- `AEGarrisonScene::onNotify(unsigned int, void*)`
- `AEGarrisonScene::onPageCloseDone()`
- `AEGarrisonScene::onPageShowUpDone()`
- `AEGarrisonScene::onSeledCharItemChanged(cocos2d::Ref*)`
- `AEGarrisonScene::onSeledItemChanged(cocos2d::Ref*)`
- `AEGarrisonScene::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AEGarrisonScene::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AEGarrisonScene::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AEGarrisonScene::showUpPage(cocos2d::EventListenerKeyboard*)`
- `AEGarrisonScene::upMoveItem(SGCharacterData*)`
- `AEGarrisonScene::upMoveItemUnit(SGUnitsData*)`
- `AEGarrisonScene::update(float)`
- `AEGarrisonScene::updateCharUnitsList()`
- `AEGarrisonScene::updateCharsBtns()`
- `AEGarrisonScene::updateGarrisonCharsList()`
- `AEGarrisonScene::updateGarrisonPage()`
- `AEGarrisonScene::updateGarrisonUnitsList()`
- `AEGarrisonScene::updatePartyCharsList()`
- `AEGarrisonScene::updateUnitsBtns()`
- `AEGarrisonScene::upgradeTagUnit(SGUnitsData*)`
- `AEGarrisonScene::upgradeUnitBoxDismissed()`
- `AEGarrisonScene::~AEGarrisonScene()`

## AEGlobalDropInfo

- `AEGlobalDropInfo::AEGlobalDropInfo()`
- `AEGlobalDropInfo::create()`
- `AEGlobalDropInfo::initData()`

## AEGuideLayer

- `AEGuideLayer::AEGuideLayer()`
- `AEGuideLayer::backKeyPressed()`
- `AEGuideLayer::cleanUpScene()`
- `AEGuideLayer::closeDlg()`
- `AEGuideLayer::getContentNode()`
- `AEGuideLayer::initGuideLayer(std::function<bool ()>, cocos2d::EventListenerKeyboard*)`
- `AEGuideLayer::onDlgCloseDone()`
- `AEGuideLayer::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AEGuideLayer::setRectGuideArea(cocos2d::Rect const&)`
- `AEGuideLayer::setRoundGuideArea(cocos2d::Vec2 const&, float)`
- `AEGuideLayer::showDlgPage()`
- `AEGuideLayer::showGuideWithRectArea(cocos2d::Rect const&, cocos2d::Node*, int, std::function<bool ()>, cocos2d::EventListenerKeyboard*)`
- `AEGuideLayer::showGuideWithRoundArea(cocos2d::Vec2 const&, float, cocos2d::Node*, int, std::function<bool ()>, cocos2d::EventListenerKeyboard*)`
- `AEGuideLayer::~AEGuideLayer()`

## AEInstructInfo

- `AEInstructInfo::AEInstructInfo()`
- `AEInstructInfo::create(int, int, int)`
- `AEInstructInfo::initData(int, int, int)`
- `AEInstructInfo::~AEInstructInfo()`

## AEInventoryScene

- `AEInventoryScene::AEInventoryScene()`
- `AEInventoryScene::backKeyPressed()`
- `AEInventoryScene::cleanUpScene()`
- `AEInventoryScene::clearDraggingItems()`
- `AEInventoryScene::clearEquipSlotSelState()`
- `AEInventoryScene::clearItemSlotSelState()`
- `AEInventoryScene::closePage()`
- `AEInventoryScene::closePropInfoBox()`
- `AEInventoryScene::createSceneLayer(void*)`
- `AEInventoryScene::dropTagSlotItem(int)`
- `AEInventoryScene::equipTagSlotItem(int)`
- `AEInventoryScene::getCurSelItemGroup()`
- `AEInventoryScene::itemListEventScrollView(cocos2d::Ref*, cocos2d::ui::ScrollView::EventType)`
- `AEInventoryScene::lvCharListEventScrollView(cocos2d::Ref*, cocos2d::ui::ScrollView::EventType)`
- `AEInventoryScene::menuBtnCLNextCallback(cocos2d::Ref*)`
- `AEInventoryScene::menuBtnCLPrevCallback(cocos2d::Ref*)`
- `AEInventoryScene::menuBtnCloseCallback(cocos2d::Ref*)`
- `AEInventoryScene::menuBtnClosePibCallback(cocos2d::Ref*)`
- `AEInventoryScene::onBtnPIB1Callback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEInventoryScene::onBtnPIB2Callback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEInventoryScene::onCharBoxTouchCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEInventoryScene::onConfirmDropItem(int)`
- `AEInventoryScene::onCreate(void*)`
- `AEInventoryScene::onEnter()`
- `AEInventoryScene::onExit()`
- `AEInventoryScene::onNotify(unsigned int, void*)`
- `AEInventoryScene::onPageCloseDone()`
- `AEInventoryScene::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AEInventoryScene::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AEInventoryScene::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AEInventoryScene::playDragCancelAnimat()`
- `AEInventoryScene::removeTagSlotEquip(int)`
- `AEInventoryScene::selTagCharFace(cocos2d::ui::Button*, bool)`
- `AEInventoryScene::setCurSelChar(int)`
- `AEInventoryScene::setEquipSlotSelOn(cocos2d::Node*)`
- `AEInventoryScene::setItemSlotSelOn(cocos2d::Node*)`
- `AEInventoryScene::showPropInfoBox(AEPropsItemGroup&)`
- `AEInventoryScene::showUpPage(cocos2d::EventListenerKeyboard*)`
- `AEInventoryScene::swapTwoItemSlot(int, int)`
- `AEInventoryScene::update(float)`
- `AEInventoryScene::updateCharListScrollStat()`
- `AEInventoryScene::updateCharsEquips(SGCharacterData*)`
- `AEInventoryScene::updateCharsList()`
- `AEInventoryScene::updateCharsStatus(SGCharacterData*)`
- `AEInventoryScene::updateInventoryList()`
- `AEInventoryScene::updateListCursor()`
- `AEInventoryScene::useTagSlotItem(int)`
- `AEInventoryScene::~AEInventoryScene()`

## AEKingdomAlarm

- `AEKingdomAlarm::AEKingdomAlarm()`
- `AEKingdomAlarm::create(float, float, int, int, int)`
- `AEKingdomAlarm::initData(float, float, int, int, int)`

## AEKingdomRelationInfo

- `AEKingdomRelationInfo::AEKingdomRelationInfo()`
- `AEKingdomRelationInfo::create(int, int, int, short)`
- `AEKingdomRelationInfo::initData(int, int, int, short)`

## AELabelAtlas

- `AELabelAtlas::create(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, int, int, int)`
- `AELabelAtlas::getCharSpace()`
- `AELabelAtlas::getDescription() const`
- `AELabelAtlas::getString() const`
- `AELabelAtlas::initWithString(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, cocos2d::Texture2D*, int, int, int)`
- `AELabelAtlas::initWithString(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, int, int, int)`
- `AELabelAtlas::setCharSpace(float)`
- `AELabelAtlas::setString(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `AELabelAtlas::updateAtlasValues()`
- `AELabelAtlas::updateColor()`

## AELinkPathNode

- `AELinkPathNode::AELinkPathNode()`
- `AELinkPathNode::create(float, float)`
- `AELinkPathNode::initData(float, float)`
- `AELinkPathNode::~AELinkPathNode()`

## AELoadingScene

- `AELoadingScene::AELoadingScene()`
- `AELoadingScene::create(int)`
- `AELoadingScene::loadingScene(int, cocos2d::Node*)`
- `AELoadingScene::onCleanUp()`
- `AELoadingScene::onCreate(int)`
- `AELoadingScene::onLoadNextScene()`
- `AELoadingScene::onSwitchToNextScene()`
- `AELoadingScene::~AELoadingScene()`

## AEMainScene

- `AEMainScene::AEMainScene()`
- `AEMainScene::StoreSceneDismissed()`
- `AEMainScene::backKeyPressed()`
- `AEMainScene::btnPlayClick(cocos2d::Ref*)`
- `AEMainScene::btnRateUsClick(cocos2d::Ref*)`
- `AEMainScene::btnSettingClick(cocos2d::Ref*)`
- `AEMainScene::cleanUpScene()`
- `AEMainScene::create(void*)`
- `AEMainScene::createFileSceneDismissed(int)`
- `AEMainScene::gameSelectSceneDismissed(int)`
- `AEMainScene::gotoSandboxScene()`
- `AEMainScene::initBgClouds()`
- `AEMainScene::moveTagCloud(cocos2d::Sprite*, float, cocos2d::Vec2 const&, float)`
- `AEMainScene::onCreate(void*)`
- `AEMainScene::onGotoBeginingScene()`
- `AEMainScene::onNotify(unsigned int, void*)`
- `AEMainScene::onQuitConfirm(int)`
- `AEMainScene::playPopSound()`
- `AEMainScene::runPlayBtnFlashAni()`
- `AEMainScene::settingsSceneDismissed()`
- `AEMainScene::showPlayBtnAni()`
- `AEMainScene::~AEMainScene()`

## AEMapEditorScene

- `AEMapEditorScene::AEMapEditorScene()`
- `AEMapEditorScene::backKeyPressed()`
- `AEMapEditorScene::btnOnClickDone(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEMapEditorScene::checkLinkNodeList()`
- `AEMapEditorScene::cleanUpScene()`
- `AEMapEditorScene::create(void*)`
- `AEMapEditorScene::excuteNodeListCheckFunc(AELinkPathNode*, cocos2d::Vector<AELinkPathNode*>&)`
- `AEMapEditorScene::getBlendNode(cocos2d::Vec2 const&, AELinkPathNode*)`
- `AEMapEditorScene::linkPathLine(AELinkPathNode*, AELinkPathNode*)`
- `AEMapEditorScene::onAddLinkNode()`
- `AEMapEditorScene::onCreate(void*)`
- `AEMapEditorScene::onEnter()`
- `AEMapEditorScene::onExit()`
- `AEMapEditorScene::onExtendLinkNode()`
- `AEMapEditorScene::onNotify(unsigned int, void*)`
- `AEMapEditorScene::onQuitBtnClicked()`
- `AEMapEditorScene::onSaveDlgConfirm(int)`
- `AEMapEditorScene::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AEMapEditorScene::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AEMapEditorScene::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AEMapEditorScene::opFinished()`
- `AEMapEditorScene::removeLinkNode(AELinkPathNode*)`
- `AEMapEditorScene::setCurMapViewPos(cocos2d::Vec2 const&)`
- `AEMapEditorScene::startOp(int)`
- `AEMapEditorScene::update(float)`
- `AEMapEditorScene::updateDrawNode()`
- `AEMapEditorScene::updateLocationInfo()`
- `AEMapEditorScene::~AEMapEditorScene()`

## AEMessageInfo

- `AEMessageInfo::AEMessageInfo()`
- `AEMessageInfo::create(int, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, short)`
- `AEMessageInfo::initData(int, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, short)`
- `AEMessageInfo::~AEMessageInfo()`

## AENavMashPathStep

- `AENavMashPathStep::AENavMashPathStep()`
- `AENavMashPathStep::create(int, int)`
- `AENavMashPathStep::initData(int, int)`
- `AENavMashPathStep::~AENavMashPathStep()`

## AENetwork

- `AENetwork::AENetwork()`
- `AENetwork::cancelRequestByTag(int)`
- `AENetwork::checkTimeOutList(float)`
- `AENetwork::httpRequest(char const*, std::function<void (int, char const*)>, int, float)`
- `AENetwork::httpRequestPOST(char const*, char const*, int, std::function<void (int, char const*)>, std::vector<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >, int, float)`
- `AENetwork::onHttpRequestCompleted(cocos2d::network::HttpClient*, cocos2d::network::HttpResponse*)`
- `AENetwork::startHttpRequest()`
- `AENetwork::~AENetwork()`

## AEPartyScene

- `AEPartyScene::AEPartyScene()`
- `AEPartyScene::backKeyPressed()`
- `AEPartyScene::btnDownMoveCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEPartyScene::btnReleaseCapCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEPartyScene::btnTalkToCharCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEPartyScene::btnUpMoveCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEPartyScene::btnUpgradeCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEPartyScene::btnViewCharCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEPartyScene::checkCouldClose()`
- `AEPartyScene::cleanUpScene()`
- `AEPartyScene::closePage()`
- `AEPartyScene::createSceneLayer(void*)`
- `AEPartyScene::downMoveItem(SGUnitsData*)`
- `AEPartyScene::menuBtnCloseCallback(cocos2d::Ref*)`
- `AEPartyScene::moveCharsUnitToOtherChar(SGCharacterData*, SGUnitsData*, SGCharacterData*)`
- `AEPartyScene::moveDepositUnitToTagChar(SGUnitsData*, SGCharacterData*)`
- `AEPartyScene::onClickTagCapItem(cocos2d::Ref*, int)`
- `AEPartyScene::onConfirmDisbandUnits(int)`
- `AEPartyScene::onConfirmReleaseCapUnit(int)`
- `AEPartyScene::onConfirmReleaseChar(int)`
- `AEPartyScene::onCreate(void*)`
- `AEPartyScene::onDragOpDone(cocos2d::Ref*, int, int)`
- `AEPartyScene::onDragging(cocos2d::Ref*, cocos2d::Vec2 const&, int)`
- `AEPartyScene::onEnter()`
- `AEPartyScene::onExit()`
- `AEPartyScene::onNotify(unsigned int, void*)`
- `AEPartyScene::onPageCloseDone()`
- `AEPartyScene::onPageShowUpDone()`
- `AEPartyScene::onPersuadeTalkDone(int)`
- `AEPartyScene::onRewardThxTalkDone(int)`
- `AEPartyScene::onSeledCapItemChanged(cocos2d::Ref*)`
- `AEPartyScene::onSeledCharItemChanged(cocos2d::Ref*)`
- `AEPartyScene::onSeledItemChanged(cocos2d::Ref*)`
- `AEPartyScene::onSeledRewardMoneyDone(int)`
- `AEPartyScene::onTalkToCaptiveDone(int)`
- `AEPartyScene::onTalkToPartnerDone(int)`
- `AEPartyScene::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AEPartyScene::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AEPartyScene::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AEPartyScene::persuadeTagChar(SGCharacterData*)`
- `AEPartyScene::releaseTagCapChar(SGCharacterData*)`
- `AEPartyScene::releaseTagCaptive(SGUnitsData*)`
- `AEPartyScene::showUpPage(cocos2d::EventListenerKeyboard*)`
- `AEPartyScene::upMoveItem(SGUnitsData*)`
- `AEPartyScene::update(float)`
- `AEPartyScene::updateCapsCharsList()`
- `AEPartyScene::updateCapsUnitsList()`
- `AEPartyScene::updateCaptiveBtns()`
- `AEPartyScene::updateCharUnitsList()`
- `AEPartyScene::updatePartyCharsList()`
- `AEPartyScene::updateTalkBtnState()`
- `AEPartyScene::updateUnitBtns()`
- `AEPartyScene::upgradeTagUnit(SGUnitsData*)`
- `AEPartyScene::upgradeUnitBoxDismissed()`
- `AEPartyScene::~AEPartyScene()`

## AEPauseScene

- `AEPauseScene::AEPauseScene()`
- `AEPauseScene::backKeyPressed()`
- `AEPauseScene::createScene()`
- `AEPauseScene::getCurHandlingRatio()`
- `AEPauseScene::hidePauseScene()`
- `AEPauseScene::hidePauseSceneOver()`
- `AEPauseScene::init()`
- `AEPauseScene::menuBackToMenuCallback(cocos2d::Ref*)`
- `AEPauseScene::menuContinueCallback(cocos2d::Ref*)`
- `AEPauseScene::menuReplayCallback(cocos2d::Ref*)`
- `AEPauseScene::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AEPauseScene::showPauseScene(cocos2d::EventListenerKeyboard*)`
- `AEPauseScene::~AEPauseScene()`

## AEPlatforms

- `AEPlatforms::AEPlatforms()`
- `AEPlatforms::deviceVibrate(int)`
- `AEPlatforms::getAppVersion()`
- `AEPlatforms::getGoogleIabList()`
- `AEPlatforms::getIOSIapList()`
- `AEPlatforms::getInstance()`
- `AEPlatforms::getIsHighPerformance()`
- `AEPlatforms::getIsSupportPurchase()`
- `AEPlatforms::getStoreInfoByPid(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `AEPlatforms::initPlatformEnvs()`
- `AEPlatforms::initStoreInfos()`
- `AEPlatforms::onAppPaused()`
- `AEPlatforms::onAppResume()`
- `AEPlatforms::onPurchaseCallback(AEStoreItemInfo*)`
- `AEPlatforms::onPurchaseSuccess(AEStoreItemInfo*)`
- `AEPlatforms::openRateUS()`
- `AEPlatforms::openSendMail()`
- `AEPlatforms::openURL(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)`
- `AEPlatforms::requestPurchaseTagItem(int)`
- `AEPlatforms::setAdPos(int)`
- `AEPlatforms::setAdView(bool)`
- `AEPlatforms::setPlatformAdPos(int)`
- `AEPlatforms::setPlatformAdVisible(bool)`
- `AEPlatforms::showInterAD()`
- `AEPlatforms::showPlatformInterAd()`
- `AEPlatforms::trackEvent(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `AEPlatforms::trackEventWithParams(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, float, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `AEPlatforms::updateStoreInfos(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)`
- `AEPlatforms::~AEPlatforms()`

## AEPlayerData

- `AEPlayerData::AEPlayerData()`
- `AEPlayerData::CreatePlayerData(int, std::basic_string<char, std::char_traits<char>, std::allocator<char> >, int, int, int, int)`
- `AEPlayerData::DeletePlayerData(int)`
- `AEPlayerData::IsPlayerDataExsit(int)`
- `AEPlayerData::LoadPlayerData(int)`
- `AEPlayerData::PreloadPlayerData(int, AEPlayerDataPreloadInfo*)`
- `AEPlayerData::SavePlayerData()`
- `AEPlayerData::SetUpAEnemy(int)`
- `AEPlayerData::assignCharToKingdomCity(SGCharacterData*, cocos2d::Vec2 const&)`
- `AEPlayerData::autoFightProgram(SGWarband*)`
- `AEPlayerData::autoFightUseSkill(SGCharacterData*, int)`
- `AEPlayerData::captiveEscaped(SGCharacterData*, cocos2d::Vector<SGCharacterData*>&, int, cocos2d::Vec2 const&)`
- `AEPlayerData::changeCharsCamp(SGCharacterData*, cocos2d::Vector<SGCharacterData*>&, int, bool, cocos2d::Node*)`
- `AEPlayerData::changeKingdomRlFv(int, int, int)`
- `AEPlayerData::charRetired(SGCharacterData*, cocos2d::Vector<SGCharacterData*>*)`
- `AEPlayerData::checkCharListLegal()`
- `AEPlayerData::cleanGameListDatas()`
- `AEPlayerData::dailyBalance()`
- `AEPlayerData::fillCharDefaultUnits(SGCharacterData*, int, int)`
- `AEPlayerData::fillEnemyDatasByStr(cocos2d::Vector<SGCharacterData*>&, AEEnemyInfoData*)`
- `AEPlayerData::finishLegionBattle(SGWarband*)`
- `AEPlayerData::gameTimeElapsing(float, float, cocos2d::Node*)`
- `AEPlayerData::geKingdomAlarmListByStr(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, cocos2d::Vector<AEKingdomAlarm*>&)`
- `AEPlayerData::generateCopyChar(int, int)`
- `AEPlayerData::generateNewUnit(int, int)`
- `AEPlayerData::getAutoFightAvailableSkill(SGCharacterData*)`
- `AEPlayerData::getAutoFightDamage(RoleStatuInfo const&, RoleStatuInfo const&)`
- `AEPlayerData::getAutoFightSkillDmgVal(SGCharacterData*, SGSkillInfoData*, int)`
- `AEPlayerData::getCapUnitSellPrice(cocos2d::Vector<SGUnitsData*>&)`
- `AEPlayerData::getCharInfo(int)`
- `AEPlayerData::getCharLegion(SGCharacterData*)`
- `AEPlayerData::getCharTerritoryCount(SGCharacterData*)`
- `AEPlayerData::getCharsListByStr(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, cocos2d::Vector<SGCharacterData*>&)`
- `AEPlayerData::getCharsListStrInfo(cocos2d::Vector<SGCharacterData*> const&)`
- `AEPlayerData::getCharsSite(SGCharacterData*)`
- `AEPlayerData::getCurGlobalLevel()`
- `AEPlayerData::getEnemyBindSite(AEEnemyInfoData*)`
- `AEPlayerData::getFileName(int)`
- `AEPlayerData::getGrantCharsList(cocos2d::Vector<SGCharacterData*>&, int)`
- `AEPlayerData::getInstance()`
- `AEPlayerData::getInstructsListByStr(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, cocos2d::Vector<AEInstructInfo*>&)`
- `AEPlayerData::getInstructsStrInfo(cocos2d::Vector<AEInstructInfo*> const&)`
- `AEPlayerData::getItemBuyInPrice(int, int, int, SGMapSiteObj*)`
- `AEPlayerData::getItemSellPrice(int, int, int, SGMapSiteObj*)`
- `AEPlayerData::getKingdomAlarmStrInfo(cocos2d::Vector<AEKingdomAlarm*> const&)`
- `AEPlayerData::getKingdomCapChars(cocos2d::Vector<SGCharacterData*>&, int)`
- `AEPlayerData::getKingdomRlInfo(int, int)`
- `AEPlayerData::getKingdomRlState(int, int)`
- `AEPlayerData::getKingdomRlStateColor(int)`
- `AEPlayerData::getKingdomRlStateName(int)`
- `AEPlayerData::getLegionByBindEnemy(int)`
- `AEPlayerData::getLegionByTagChar(SGCharacterData*)`
- `AEPlayerData::getNavStepsListByStr(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, cocos2d::Vector<AENavMashPathStep*>&)`
- `AEPlayerData::getNavStepsStrInfo(cocos2d::Vector<AENavMashPathStep*> const&)`
- `AEPlayerData::getNearbyFriendsPower(SGLegion*)`
- `AEPlayerData::getNearestAnyCity(cocos2d::Vec2 const&)`
- `AEPlayerData::getNearestEnemyBuilding(cocos2d::Vec2 const&, int)`
- `AEPlayerData::getNearestEnemyCity(cocos2d::Vec2 const&, int)`
- `AEPlayerData::getNearestEnemyVillage(cocos2d::Vec2 const&, int)`
- `AEPlayerData::getNearestFriendCity(SGCharacterData*, cocos2d::Vec2 const&, bool)`
- `AEPlayerData::getNearestMyCity(cocos2d::Vec2 const&, int)`
- `AEPlayerData::getPlayerLegionFoodKeepDays()`
- `AEPlayerData::getRandomQuestExecutor(int)`
- `AEPlayerData::getStateNumData(int, int)`
- `AEPlayerData::getStateNumFloatVal(int, int)`
- `AEPlayerData::getStateNumIntVal(int, int)`
- `AEPlayerData::getTerrainRate(SGMapSiteObj*)`
- `AEPlayerData::getUnitIdByInfo(int, int)`
- `AEPlayerData::getUnitSellPrice(SGUnitsData*)`
- `AEPlayerData::getUnitsListByStr(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, cocos2d::Vector<SGUnitsData*>&)`
- `AEPlayerData::getUnitsListStrInfo(cocos2d::Vector<SGUnitsData*> const&)`
- `AEPlayerData::getVec2ByStr(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)`
- `AEPlayerData::getWarband(int)`
- `AEPlayerData::getWarbandByLegion(SGLegion*)`
- `AEPlayerData::giveDelayOrder(int, int, SGCharacterData*, int, int, int, float)`
- `AEPlayerData::kingdomFall(int)`
- `AEPlayerData::loadInventoryData()`
- `AEPlayerData::onCharDeployCheck()`
- `AEPlayerData::onDailyDiplomancyCheck()`
- `AEPlayerData::onDailyEscapeBalance()`
- `AEPlayerData::onDailyFoodBalance()`
- `AEPlayerData::onDailySiteCaravanCheck()`
- `AEPlayerData::onDailySitePolicy()`
- `AEPlayerData::onExecuteDelayOrder(AEDelayOrderInfo*, cocos2d::Node*)`
- `AEPlayerData::onHourSitePolicy()`
- `AEPlayerData::onOrderDecided(bool, AEDelayOrderInfo*)`
- `AEPlayerData::onOrderExecutedDone(AEDelayOrderInfo*)`
- `AEPlayerData::onPlayerDipYesNoSelDone(int)`
- `AEPlayerData::onRestoreAct(float)`
- `AEPlayerData::onSiteAIRecruit()`
- `AEPlayerData::onTagCharRestoreAct(SGCharacterData*, float, float)`
- `AEPlayerData::onTagUnitRestoreAct(SGUnitsData*, float, float)`
- `AEPlayerData::parseCharInfoData(tinyxml2::XMLElement*, SGCharacterData*)`
- `AEPlayerData::parseKingdomRlInfo(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `AEPlayerData::playerRecruitUnits(int, int)`
- `AEPlayerData::readCharInfos()`
- `AEPlayerData::readListDatas()`
- `AEPlayerData::recruitFreeChar(SGCharacterData*, cocos2d::Vector<SGCharacterData*>&, int, bool, cocos2d::Node*)`
- `AEPlayerData::removeCopyChar(int)`
- `AEPlayerData::removeKingdomAlarms(int, int)`
- `AEPlayerData::resetFreeCharsList()`
- `AEPlayerData::resetStateNumByType(int)`
- `AEPlayerData::saveCharInfos()`
- `AEPlayerData::saveInventoryData()`
- `AEPlayerData::saveListDatas()`
- `AEPlayerData::sendBattleMessage(int, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `AEPlayerData::sendMessage(int, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `AEPlayerData::setKingdomRl(int, int, int, int)`
- `AEPlayerData::setKingdomRlState(int, int, int)`
- `AEPlayerData::setStateNumVal(int, int, int, float)`
- `AEPlayerData::spawnEnemyLegion(int)`
- `AEPlayerData::startAutoBattleProgram(SGLegion*, SGLegion*, int, int, int)`
- `AEPlayerData::startLegionBattle(SGLegion*, SGLegion*, int, int, int)`
- `AEPlayerData::upgradeTagCharsEquip(SGCharacterData*)`
- `AEPlayerData::weeklyBalance()`
- `AEPlayerData::~AEPlayerData()`

## AEPlayerDataPreloadInfo

- `AEPlayerDataPreloadInfo::AEPlayerDataPreloadInfo()`

## AEPlayerInfoBox

- `AEPlayerInfoBox::AEPlayerInfoBox()`
- `AEPlayerInfoBox::create()`
- `AEPlayerInfoBox::initCtl()`
- `AEPlayerInfoBox::onEnter()`
- `AEPlayerInfoBox::onExit()`
- `AEPlayerInfoBox::onSecondEvent(float)`
- `AEPlayerInfoBox::setCurTime(float)`
- `AEPlayerInfoBox::updateCurMoney()`
- `AEPlayerInfoBox::updateDaysLabel()`
- `AEPlayerInfoBox::updatePlayerInfos()`
- `AEPlayerInfoBox::~AEPlayerInfoBox()`

## AEPrisonBox

- `AEPrisonBox::AEPrisonBox()`
- `AEPrisonBox::backKeyPressed()`
- `AEPrisonBox::btnLeftMoveCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEPrisonBox::btnRightMoveCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEPrisonBox::btnTalk1Callback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEPrisonBox::btnTalk2Callback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEPrisonBox::btnViewChar1Callback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEPrisonBox::btnViewChar2Callback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEPrisonBox::checkCouldClose()`
- `AEPrisonBox::cleanUpScene()`
- `AEPrisonBox::closePage()`
- `AEPrisonBox::createPrisonScene(int)`
- `AEPrisonBox::leftMoveItem(SGCharacterData*)`
- `AEPrisonBox::menuBtnCloseCallback(cocos2d::Ref*)`
- `AEPrisonBox::onCreate(int)`
- `AEPrisonBox::onEnter()`
- `AEPrisonBox::onExit()`
- `AEPrisonBox::onNotify(unsigned int, void*)`
- `AEPrisonBox::onPageCloseDone()`
- `AEPrisonBox::onPageShowUpDone()`
- `AEPrisonBox::onSeledCapItemChanged(cocos2d::Ref*)`
- `AEPrisonBox::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AEPrisonBox::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AEPrisonBox::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AEPrisonBox::rightMoveItem(SGCharacterData*)`
- `AEPrisonBox::showUpPage(cocos2d::EventListenerKeyboard*)`
- `AEPrisonBox::talkToCaptiveChar(SGCharacterData*, cocos2d::Node*, cocos2d::EventListenerKeyboard*)`
- `AEPrisonBox::update(float)`
- `AEPrisonBox::updateBtnStates()`
- `AEPrisonBox::updateLegionCapsList()`
- `AEPrisonBox::updatePrisonCapsList()`
- `AEPrisonBox::updatePrisonPage()`
- `AEPrisonBox::viewTagCharInfo(SGCharacterData*, cocos2d::Node*, cocos2d::EventListenerKeyboard*)`
- `AEPrisonBox::~AEPrisonBox()`

## AEPropsCmdItem

- `AEPropsCmdItem::AEPropsCmdItem()`
- `AEPropsCmdItem::create(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, int, int, int)`
- `AEPropsCmdItem::init(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, int, int, int)`
- `AEPropsCmdItem::~AEPropsCmdItem()`

## AEPropsItemInfo

- `AEPropsItemInfo::AEPropsItemInfo()`
- `AEPropsItemInfo::getItemInfo(int)`
- `AEPropsItemInfo::getItemName(int)`
- `AEPropsItemInfo::~AEPropsItemInfo()`

## AERoomScene

- `AERoomScene::AERoomScene()`
- `AERoomScene::backKeyPressed()`
- `AERoomScene::btnRoomBtnClickDone(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AERoomScene::cleanUpScene()`
- `AERoomScene::closePage()`
- `AERoomScene::createSceneLayer(int, int)`
- `AERoomScene::garrisonSceneDismissed()`
- `AERoomScene::getTagSellGroup(int)`
- `AERoomScene::onCreate(int, int)`
- `AERoomScene::onEnter()`
- `AERoomScene::onExit()`
- `AERoomScene::onNotify(unsigned int, void*)`
- `AERoomScene::onPageCloseDone()`
- `AERoomScene::onPubTalkCallback(int)`
- `AERoomScene::onRecruitTalkDone(int)`
- `AERoomScene::onRecuitMercenaryCallback(int)`
- `AERoomScene::onRestBoxCallback(int)`
- `AERoomScene::onShowUpDone()`
- `AERoomScene::onTalkToFreeCharDone(int)`
- `AERoomScene::onTalkToSlaveTraderDone(int)`
- `AERoomScene::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AERoomScene::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AERoomScene::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AERoomScene::openGarrisonBox()`
- `AERoomScene::openPrisonBox()`
- `AERoomScene::openRecruitMercenaryBox()`
- `AERoomScene::openRestBox()`
- `AERoomScene::openTalkToCharsBox()`
- `AERoomScene::openTradeBox()`
- `AERoomScene::prisonSceneDismissed()`
- `AERoomScene::recruitTagChar(SGCharacterData*)`
- `AERoomScene::showRoomScene(int, int, cocos2d::Node*, AERoomSceneDelegate*, int, cocos2d::EventListenerKeyboard*)`
- `AERoomScene::showUpPage(cocos2d::EventListenerKeyboard*)`
- `AERoomScene::startRestAct(int)`
- `AERoomScene::tradeBoxDismissed()`
- `AERoomScene::update(float)`
- `AERoomScene::~AERoomScene()`

## AESandTableScene

- `AESandTableScene::AESandTableScene()`
- `AESandTableScene::backKeyPressed()`
- `AESandTableScene::backToMenu()`
- `AESandTableScene::breakPlayerLegionAct()`
- `AESandTableScene::btnMiniMinusClick(cocos2d::Ref*)`
- `AESandTableScene::btnMiniPlusClick(cocos2d::Ref*)`
- `AESandTableScene::btnMiniZoomClick(cocos2d::Ref*)`
- `AESandTableScene::cleanUpScene()`
- `AESandTableScene::create(void*)`
- `AESandTableScene::gameMapSceneDismissed(int, cocos2d::Vec2)`
- `AESandTableScene::hideLegionUnit(SGLegion*)`
- `AESandTableScene::intoTagCity(int)`
- `AESandTableScene::joinToWarband(SGWarband*)`
- `AESandTableScene::mapPaused()`
- `AESandTableScene::mapResume()`
- `AESandTableScene::onCheckMapUnitSpawnStates(float)`
- `AESandTableScene::onCheckMsgInfos(float)`
- `AESandTableScene::onCheckSpecialOp(float)`
- `AESandTableScene::onConfirmRobMoney(int)`
- `AESandTableScene::onCreate(void*)`
- `AESandTableScene::onCtlCmdsPanelBackToMenu()`
- `AESandTableScene::onCtlCmdsPanelPause()`
- `AESandTableScene::onCtlCmdsPanelResume()`
- `AESandTableScene::onCtlCmdsPanelSaveGame()`
- `AESandTableScene::onCtlCmdsPanelStopActions()`
- `AESandTableScene::onEnter()`
- `AESandTableScene::onEnterSandTableScene()`
- `AESandTableScene::onExit()`
- `AESandTableScene::onFightTalkDone(int)`
- `AESandTableScene::onGuide1TalkDone(int)`
- `AESandTableScene::onGuideStep1Done()`
- `AESandTableScene::onHandingMapUnitsAction()`
- `AESandTableScene::onInputCodeDone(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)`
- `AESandTableScene::onIntoTagCity()`
- `AESandTableScene::onJoinBattleSeledDone(int)`
- `AESandTableScene::onLegionContacted(SGLegion*, SGLegion*)`
- `AESandTableScene::onMapUnitPosChanged(cocos2d::Ref*, cocos2d::Vec2 const&)`
- `AESandTableScene::onMapUnitReachPos(cocos2d::Ref*)`
- `AESandTableScene::onMonasteryBoxCallback(int)`
- `AESandTableScene::onNotify(unsigned int, void*)`
- `AESandTableScene::onOccupyBoxCallback(int)`
- `AESandTableScene::onOccupyTimerActCallback(int)`
- `AESandTableScene::onOccupyTimerCountDone(int)`
- `AESandTableScene::onRaidBoxCallback(int)`
- `AESandTableScene::onRaidTimerActCallback(int)`
- `AESandTableScene::onRaidTimerCountDone(int)`
- `AESandTableScene::onRecuitMonksCallback(int)`
- `AESandTableScene::onSecondEvent(float)`
- `AESandTableScene::onSeigeBoxCallback(int)`
- `AESandTableScene::onSeigeTimerActCallback(int)`
- `AESandTableScene::onSeigeTimerCountDone(int)`
- `AESandTableScene::onTalkToBanditDone(int)`
- `AESandTableScene::onTestMapTouching(cocos2d::Vec2 const&)`
- `AESandTableScene::onThiefDenBoxCallback(int)`
- `AESandTableScene::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AESandTableScene::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AESandTableScene::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AESandTableScene::openMonasteryMenu(SGMapSiteObj*)`
- `AESandTableScene::openOccupyMenu(SGMapSiteObj*)`
- `AESandTableScene::openRaidMenu(SGMapSiteObj*)`
- `AESandTableScene::openSeigeMenu(SGMapSiteObj*)`
- `AESandTableScene::openThiefDenMenu(SGMapSiteObj*)`
- `AESandTableScene::removeMsgInfo(AEMessageInfo*)`
- `AESandTableScene::setGameTimeScale(float)`
- `AESandTableScene::setTimeEffect(float)`
- `AESandTableScene::showGuideStep2()`
- `AESandTableScene::showJoinBattleMenu(SGWarband*)`
- `AESandTableScene::showLegionUnit(SGLegion*)`
- `AESandTableScene::showMsgInfo(AEMessageInfo*)`
- `AESandTableScene::startBattleWithTagLegion(SGLegion*)`
- `AESandTableScene::startBattleWithTagSiteLegion(SGMapSiteObj*, SGLegion*)`
- `AESandTableScene::startOccupyTagSite(SGMapSiteObj*)`
- `AESandTableScene::startRaidTagSite(SGMapSiteObj*)`
- `AESandTableScene::startSeigeTagSite(SGMapSiteObj*)`
- `AESandTableScene::tradeBoxDismissed()`
- `AESandTableScene::update(float)`
- `AESandTableScene::updateLocationView(cocos2d::Vec2 const&)`
- `AESandTableScene::updateMapUnitViewState()`
- `AESandTableScene::updateMiniMapBtns()`
- `AESandTableScene::updateStaticNums()`
- `AESandTableScene::~AESandTableScene()`

## AESelectGameScene

- `AESelectGameScene::AESelectGameScene()`
- `AESelectGameScene::backKeyPressed()`
- `AESelectGameScene::cleanUpScene()`
- `AESelectGameScene::closePage()`
- `AESelectGameScene::createSceneLayer(void*)`
- `AESelectGameScene::fillFileStatisticNums(cocos2d::ui::Layout*, AEPlayerDataPreloadInfo*)`
- `AESelectGameScene::menuBtnCloseCallback(cocos2d::Ref*)`
- `AESelectGameScene::onBtnDeleteCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AESelectGameScene::onBtnStartGameCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AESelectGameScene::onCreate(void*)`
- `AESelectGameScene::onDeleteConfirm(int)`
- `AESelectGameScene::onEnter()`
- `AESelectGameScene::onExit()`
- `AESelectGameScene::onNotify(unsigned int, void*)`
- `AESelectGameScene::onPageCloseDone()`
- `AESelectGameScene::onSecondEvent(float)`
- `AESelectGameScene::onSlotBoxCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AESelectGameScene::onStartTagFileGame()`
- `AESelectGameScene::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AESelectGameScene::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AESelectGameScene::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AESelectGameScene::setCurSelBtn(cocos2d::ui::Widget*)`
- `AESelectGameScene::setSlotBtnSelState(cocos2d::ui::Widget*, bool)`
- `AESelectGameScene::showUpPage(cocos2d::EventListenerKeyboard*)`
- `AESelectGameScene::update(float)`
- `AESelectGameScene::updateGameFilePage()`
- `AESelectGameScene::~AESelectGameScene()`

## AESettingsScene

- `AESettingsScene::AESettingsScene()`
- `AESettingsScene::backKeyPressed()`
- `AESettingsScene::create()`
- `AESettingsScene::getCurHandlingRatio()`
- `AESettingsScene::hideSettingsScene()`
- `AESettingsScene::hideSettingsSceneOver()`
- `AESettingsScene::init()`
- `AESettingsScene::menuBsShowBarCallback(cocos2d::Ref*)`
- `AESettingsScene::menuBsShowNumCallback(cocos2d::Ref*)`
- `AESettingsScene::menuBtnCloseCallback(cocos2d::Ref*)`
- `AESettingsScene::menuChineseCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AESettingsScene::menuEnglishCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AESettingsScene::menuMusicCallback(cocos2d::Ref*)`
- `AESettingsScene::menuSoundCallback(cocos2d::Ref*)`
- `AESettingsScene::menuVibrateCallback(cocos2d::Ref*)`
- `AESettingsScene::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AESettingsScene::setIsShowLangSwitch(bool)`
- `AESettingsScene::showSettingsScene(cocos2d::EventListenerKeyboard*)`
- `AESettingsScene::sliderEvent(cocos2d::Ref*, cocos2d::ui::Slider::EventType)`
- `AESettingsScene::updateBtnStates()`
- `AESettingsScene::~AESettingsScene()`

## AESiteInfoViewer

- `AESiteInfoViewer::AESiteInfoViewer()`
- `AESiteInfoViewer::backKeyPressed()`
- `AESiteInfoViewer::cleanUpScene()`
- `AESiteInfoViewer::closePage()`
- `AESiteInfoViewer::createSceneLayer(void*)`
- `AESiteInfoViewer::menuBtnCloseCallback(cocos2d::Ref*)`
- `AESiteInfoViewer::onCreate(void*)`
- `AESiteInfoViewer::onEnter()`
- `AESiteInfoViewer::onExit()`
- `AESiteInfoViewer::onNotify(unsigned int, void*)`
- `AESiteInfoViewer::onPageCloseDone()`
- `AESiteInfoViewer::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AESiteInfoViewer::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AESiteInfoViewer::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AESiteInfoViewer::showUpPage(SGMapSiteObj*, cocos2d::EventListenerKeyboard*)`
- `AESiteInfoViewer::update(float)`
- `AESiteInfoViewer::updateInfoPage()`
- `AESiteInfoViewer::~AESiteInfoViewer()`

## AESiteSelBox

- `AESiteSelBox::AESiteSelBox()`
- `AESiteSelBox::addSiteInfoToList(cocos2d::ui::ListView*, int, int, float, SGMapSiteObj*, std::function<void (cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)> const&)`
- `AESiteSelBox::backKeyPressed()`
- `AESiteSelBox::cleanUpScene()`
- `AESiteSelBox::closePage()`
- `AESiteSelBox::createSceneLayer(void*)`
- `AESiteSelBox::fillSiteInfoList(cocos2d::ui::ListView*, int, std::function<void (cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)> const&)`
- `AESiteSelBox::menuBtnCloseCallback(cocos2d::Ref*)`
- `AESiteSelBox::onCreate(void*)`
- `AESiteSelBox::onEnter()`
- `AESiteSelBox::onExit()`
- `AESiteSelBox::onNotify(unsigned int, void*)`
- `AESiteSelBox::onPageCloseDone()`
- `AESiteSelBox::onSelTagSiteCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AESiteSelBox::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AESiteSelBox::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AESiteSelBox::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AESiteSelBox::showSiteSelector(std::basic_string<char, std::char_traits<char>, std::allocator<char> >, cocos2d::Node*, int, int, std::function<void (int)>, cocos2d::EventListenerKeyboard*)`
- `AESiteSelBox::showUpPage(std::basic_string<char, std::char_traits<char>, std::allocator<char> >, int, std::function<void (int)>, cocos2d::EventListenerKeyboard*)`
- `AESiteSelBox::update(float)`
- `AESiteSelBox::updateSelectorPage()`
- `AESiteSelBox::~AESiteSelBox()`

## AESkillBox

- `AESkillBox::AESkillBox()`
- `AESkillBox::addSkUpReqInfo(char const*, int)`
- `AESkillBox::backKeyPressed()`
- `AESkillBox::cancelDragSkill()`
- `AESkillBox::cleanUpScene()`
- `AESkillBox::closePage()`
- `AESkillBox::createSceneLayer(void*)`
- `AESkillBox::getSkillClassTxtName(int)`
- `AESkillBox::getSpData(int)`
- `AESkillBox::hideSkInfoBox()`
- `AESkillBox::initSkillPages()`
- `AESkillBox::isTagSkillCouldDrag(cocos2d::ui::Widget*)`
- `AESkillBox::menuBtnCloseCallback(cocos2d::Ref*)`
- `AESkillBox::menuSkInfoBoxCloseCallback(cocos2d::Ref*)`
- `AESkillBox::menuSkInfoBtnCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AESkillBox::menuSkillClassTabCallback(cocos2d::Ref*)`
- `AESkillBox::onCreate(void*)`
- `AESkillBox::onEnter()`
- `AESkillBox::onExit()`
- `AESkillBox::onNotify(unsigned int, void*)`
- `AESkillBox::onPageCloseDone()`
- `AESkillBox::onReleaseDragSkill(cocos2d::Vec2 const&)`
- `AESkillBox::onSkInfoBoxTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AESkillBox::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AESkillBox::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AESkillBox::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AESkillBox::resetSkillBoxSel()`
- `AESkillBox::setCurSelBtn(cocos2d::ui::Widget*)`
- `AESkillBox::setSkillBtnSelState(cocos2d::ui::Widget*, bool)`
- `AESkillBox::setTagQsSlotSel(cocos2d::Sprite*, bool)`
- `AESkillBox::showSkInfoBox()`
- `AESkillBox::showUpPage(int, SGCharacterData*, cocos2d::EventListenerKeyboard*)`
- `AESkillBox::startDragTagSkill(int, cocos2d::Vec2 const&)`
- `AESkillBox::update(float)`
- `AESkillBox::updateQuickSkillSlots()`
- `AESkillBox::updateSkInfoBox(int)`
- `AESkillBox::updateSkillPage()`
- `AESkillBox::updateSpNum()`
- `AESkillBox::useTagSkill(int)`
- `AESkillBox::~AESkillBox()`

## AESkillSelBox

- `AESkillSelBox::AESkillSelBox()`
- `AESkillSelBox::addSkillInfoToList(cocos2d::ui::ListView*, int, SGSkillPointData*, float, std::function<void (cocos2d::ui::Layout*, cocos2d::ui::ImageView*, int)>)`
- `AESkillSelBox::backKeyPressed()`
- `AESkillSelBox::cancelDragSkill()`
- `AESkillSelBox::checkDragItemCollide(cocos2d::Vec2 const&)`
- `AESkillSelBox::cleanUpScene()`
- `AESkillSelBox::closePage()`
- `AESkillSelBox::createSceneLayer(void*)`
- `AESkillSelBox::fillSkillsInfoList(cocos2d::ui::ListView*, cocos2d::Vector<SGSkillPointData*> const&, std::function<void (cocos2d::ui::Layout*, cocos2d::ui::ImageView*, int)>)`
- `AESkillSelBox::getSpData(int)`
- `AESkillSelBox::isTagSkillCouldDrag(cocos2d::ui::Widget*)`
- `AESkillSelBox::menuBtnCloseCallback(cocos2d::Ref*)`
- `AESkillSelBox::menuClickUseSkill(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AESkillSelBox::onCreate(void*)`
- `AESkillSelBox::onCreateSkillListItem(cocos2d::ui::Layout*, cocos2d::ui::ImageView*, int)`
- `AESkillSelBox::onEnter()`
- `AESkillSelBox::onExit()`
- `AESkillSelBox::onNotify(unsigned int, void*)`
- `AESkillSelBox::onPageCloseDone()`
- `AESkillSelBox::onReleaseDragSkill(cocos2d::Vec2 const&)`
- `AESkillSelBox::onSkillIconTouchCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AESkillSelBox::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AESkillSelBox::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AESkillSelBox::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AESkillSelBox::resetSkillBoxSel()`
- `AESkillSelBox::setBtnEnable(cocos2d::ui::Button*, bool)`
- `AESkillSelBox::setCurSelBtn(cocos2d::ui::Widget*)`
- `AESkillSelBox::setSkillBtnSelState(cocos2d::ui::Widget*, bool)`
- `AESkillSelBox::setTagQsSlotSel(cocos2d::Sprite*, bool)`
- `AESkillSelBox::showUpPage(SGGeneral*, cocos2d::EventListenerKeyboard*)`
- `AESkillSelBox::startDragTagSkill(int, cocos2d::Vec2 const&)`
- `AESkillSelBox::update(float)`
- `AESkillSelBox::updateQuickSkillSlots()`
- `AESkillSelBox::updateSkillPage()`
- `AESkillSelBox::updateTagSkillItem(cocos2d::ui::ImageView*, cocos2d::ui::Button*)`
- `AESkillSelBox::useTagSkill(int)`
- `AESkillSelBox::~AESkillSelBox()`

## AESound

- `AESound::AESound()`
- `AESound::getInstance()`
- `AESound::isPlaySound()`
- `AESound::pauseSoundBackground()`
- `AESound::playEffectSound(char const*)`
- `AESound::playGameSound(char const*)`
- `AESound::playGameSoundLoop(char const*, bool)`
- `AESound::playLastBackground()`
- `AESound::playRndGameSound(char const*, int)`
- `AESound::playRndSoundBackground(char const*, int)`
- `AESound::playSoundBackground(char const*)`
- `AESound::preloadBgMusic(char const*)`
- `AESound::preloadSoundEffect(char const*)`
- `AESound::resumeSoundBackground()`
- `AESound::stopSoundBackground()`
- `AESound::stopSoundEffect()`
- `AESound::stopTagGameSound(unsigned int)`
- `AESound::~AESound()`

## AEStateNumData

- `AEStateNumData::AEStateNumData()`
- `AEStateNumData::create(int, int, float)`
- `AEStateNumData::initData(int, int, float)`

## AEStateNumTypeData

- `AEStateNumTypeData::AEStateNumTypeData()`
- `AEStateNumTypeData::create(int)`
- `AEStateNumTypeData::initData(int)`

## AEStoreItemInfo

- `AEStoreItemInfo::AEStoreItemInfo()`
- `AEStoreItemInfo::getItemInfo(int)`
- `AEStoreItemInfo::getItemName(int)`
- `AEStoreItemInfo::~AEStoreItemInfo()`

## AEStoreScene

- `AEStoreScene::AEStoreScene()`
- `AEStoreScene::backKeyPressed()`
- `AEStoreScene::cleanUpScene()`
- `AEStoreScene::closeStorePage()`
- `AEStoreScene::createSceneLayer(void*)`
- `AEStoreScene::flipToPage(int, float)`
- `AEStoreScene::initStorePages()`
- `AEStoreScene::menuBtnCloseCallback(cocos2d::Ref*)`
- `AEStoreScene::menuBtnCoinsCallback(cocos2d::Ref*)`
- `AEStoreScene::menuBtnEquipsCallback(cocos2d::Ref*)`
- `AEStoreScene::menuBtnGroceriesCallback(cocos2d::Ref*)`
- `AEStoreScene::onBuyBtnClicked(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEStoreScene::onCreate(void*)`
- `AEStoreScene::onEnter()`
- `AEStoreScene::onExit()`
- `AEStoreScene::onNotify(unsigned int, void*)`
- `AEStoreScene::onSecUpdate(float)`
- `AEStoreScene::onStorePageCloseDone()`
- `AEStoreScene::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AEStoreScene::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AEStoreScene::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AEStoreScene::selectedItemEventScrollView(cocos2d::Ref*, cocos2d::ui::ScrollView::EventType)`
- `AEStoreScene::showStorePage(cocos2d::EventListenerKeyboard*)`
- `AEStoreScene::update(float)`
- `AEStoreScene::updateCoinsList()`
- `AEStoreScene::updateEquipsList()`
- `AEStoreScene::updateGroceriesList()`
- `AEStoreScene::updatePageTabs()`
- `AEStoreScene::updateScrollCursorView()`
- `AEStoreScene::updateTagList(cocos2d::ui::ListView*)`
- `AEStoreScene::~AEStoreScene()`

## AESubDropPropInfo

- `AESubDropPropInfo::AESubDropPropInfo()`
- `AESubDropPropInfo::create()`
- `AESubDropPropInfo::initData()`

## AETalentBox

- `AETalentBox::AETalentBox()`
- `AETalentBox::addTalentVal(char const*)`
- `AETalentBox::addTalentsInfoToList(cocos2d::ui::ListView*, int, AETalentInfo*, RoleTalentInfo const&, float, SGCharacterData*, int, std::function<void (cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)> const&)`
- `AETalentBox::backKeyPressed()`
- `AETalentBox::cleanUpScene()`
- `AETalentBox::closePage()`
- `AETalentBox::createSceneLayer(void*)`
- `AETalentBox::fillTalentsInfoList(cocos2d::ui::ListView*, RoleTalentInfo const&, SGCharacterData*, int, std::function<void (cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)> const&)`
- `AETalentBox::menuBtnCloseCallback(cocos2d::Ref*)`
- `AETalentBox::onAddTalentCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AETalentBox::onCreate(void*)`
- `AETalentBox::onEnter()`
- `AETalentBox::onExit()`
- `AETalentBox::onNotify(unsigned int, void*)`
- `AETalentBox::onPageCloseDone()`
- `AETalentBox::onResetCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AETalentBox::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AETalentBox::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AETalentBox::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AETalentBox::resetTalentsPoints()`
- `AETalentBox::saveTalentChange()`
- `AETalentBox::showUpPage(SGCharacterData*, cocos2d::EventListenerKeyboard*)`
- `AETalentBox::update(float)`
- `AETalentBox::updateTalentPage()`
- `AETalentBox::~AETalentBox()`

## AETalentInfo

- `AETalentInfo::AETalentInfo()`
- `AETalentInfo::create()`
- `AETalentInfo::getTagTalentValByCode(char const*, RoleTalentInfo const&)`
- `AETalentInfo::getTltInfo(int)`
- `AETalentInfo::getTltName(int)`

## AETalkingDlg

- `AETalkingDlg::AETalkingDlg()`
- `AETalkingDlg::addCmdBtnsList(cocos2d::Vector<AETalkingDlgBtnCmd*> const&)`
- `AETalkingDlg::backKeyPressed()`
- `AETalkingDlg::btnCharFaceClick(cocos2d::Ref*)`
- `AETalkingDlg::btnOnClickDone(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AETalkingDlg::cleanUpScene()`
- `AETalkingDlg::closeDlg()`
- `AETalkingDlg::initDlg(char const*, SGCharacterData*, bool, std::function<bool (int)>, cocos2d::EventListenerKeyboard*)`
- `AETalkingDlg::onDlgCloseDone()`
- `AETalkingDlg::onSelBoxShowOutDone()`
- `AETalkingDlg::onShowNextInfoPage()`
- `AETalkingDlg::onShowNextInfoPageDone()`
- `AETalkingDlg::onTapAction()`
- `AETalkingDlg::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AETalkingDlg::playShowPageAnimat(bool)`
- `AETalkingDlg::showContinueTipMark(bool)`
- `AETalkingDlg::showDlgPage()`
- `AETalkingDlg::showOutSelBox()`
- `AETalkingDlg::showTalkingDlg(char const*, SGCharacterData*, bool, cocos2d::Node*, int, std::function<bool (int)>, cocos2d::EventListenerKeyboard*)`
- `AETalkingDlg::showTalkingDlg(char const*, SGCharacterData*, bool, cocos2d::Vector<AETalkingDlgBtnCmd*> const&, cocos2d::Node*, int, std::function<bool (int)>, cocos2d::EventListenerKeyboard*)`
- `AETalkingDlg::startShowDlgInfo()`
- `AETalkingDlg::~AETalkingDlg()`

## AETalkingDlgBtnCmd

- `AETalkingDlgBtnCmd::AETalkingDlgBtnCmd()`
- `AETalkingDlgBtnCmd::create(std::basic_string<char, std::char_traits<char>, std::allocator<char> >, int)`
- `AETalkingDlgBtnCmd::init(std::basic_string<char, std::char_traits<char>, std::allocator<char> >, int)`

## AETerritoryBox

- `AETerritoryBox::AETerritoryBox()`
- `AETerritoryBox::addTerritoryInfoToList(cocos2d::ui::ListView*, int, float, SGCharacterData*, SGMapSiteObj*, std::function<void (cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)> const&)`
- `AETerritoryBox::backKeyPressed()`
- `AETerritoryBox::cleanUpScene()`
- `AETerritoryBox::closePage()`
- `AETerritoryBox::createSceneLayer(void*)`
- `AETerritoryBox::fillTerritoryInfoList(cocos2d::ui::ListView*, SGCharacterData*, std::function<void (cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)> const&)`
- `AETerritoryBox::menuBtnCloseCallback(cocos2d::Ref*)`
- `AETerritoryBox::onCreate(void*)`
- `AETerritoryBox::onEnter()`
- `AETerritoryBox::onExit()`
- `AETerritoryBox::onNotify(unsigned int, void*)`
- `AETerritoryBox::onPageCloseDone()`
- `AETerritoryBox::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AETerritoryBox::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AETerritoryBox::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AETerritoryBox::onViewTerritoryCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AETerritoryBox::showUpPage(SGCharacterData*, cocos2d::EventListenerKeyboard*)`
- `AETerritoryBox::update(float)`
- `AETerritoryBox::updateTerritoryPage()`
- `AETerritoryBox::~AETerritoryBox()`

## AETextInputDlg

- `AETextInputDlg::AETextInputDlg()`
- `AETextInputDlg::backKeyPressed()`
- `AETextInputDlg::callbackRemoveNodeWhenDidAction(cocos2d::Node*)`
- `AETextInputDlg::checkInputText()`
- `AETextInputDlg::getInputedText()`
- `AETextInputDlg::hideDlg()`
- `AETextInputDlg::hideDlgOver()`
- `AETextInputDlg::initTextInputerDlg(std::function<void (std::basic_string<char, std::char_traits<char>, std::allocator<char> >)>, cocos2d::EventListenerKeyboard*)`
- `AETextInputDlg::keyboardWillShow(cocos2d::IMEKeyboardNotificationInfo&)`
- `AETextInputDlg::menuCloseBtnCallback(cocos2d::Ref*)`
- `AETextInputDlg::menuOKBtnCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AETextInputDlg::onClickTrackNode(bool)`
- `AETextInputDlg::onDraw(cocos2d::TextFieldTTF*)`
- `AETextInputDlg::onEnter()`
- `AETextInputDlg::onExit()`
- `AETextInputDlg::onTextFieldAttachWithIME(cocos2d::TextFieldTTF*)`
- `AETextInputDlg::onTextFieldDeleteBackward(cocos2d::TextFieldTTF*, char const*, unsigned int)`
- `AETextInputDlg::onTextFieldDetachWithIME(cocos2d::TextFieldTTF*)`
- `AETextInputDlg::onTextFieldInsertText(cocos2d::TextFieldTTF*, char const*, unsigned int)`
- `AETextInputDlg::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AETextInputDlg::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AETextInputDlg::setDefaultText(char const*)`
- `AETextInputDlg::showInputDlg(char const*)`
- `AETextInputDlg::showTextInputer(char const*, cocos2d::Node*, int, std::function<void (std::basic_string<char, std::char_traits<char>, std::allocator<char> >)>, cocos2d::EventListenerKeyboard*)`
- `AETextInputDlg::~AETextInputDlg()`

## AETimerRunningBox

- `AETimerRunningBox::AETimerRunningBox()`
- `AETimerRunningBox::backKeyPressed()`
- `AETimerRunningBox::btnStopClickDone(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AETimerRunningBox::cleanUpScene()`
- `AETimerRunningBox::closeCurrentTimerBox()`
- `AETimerRunningBox::closeDlg()`
- `AETimerRunningBox::initDlg(char const*, AEGameTime const&, bool, std::function<void (int)>, std::function<void (int)>, cocos2d::EventListenerKeyboard*)`
- `AETimerRunningBox::onConfirmStop(int)`
- `AETimerRunningBox::onDlgCloseDone()`
- `AETimerRunningBox::onEnter()`
- `AETimerRunningBox::onExit()`
- `AETimerRunningBox::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AETimerRunningBox::pauseCurrentTimerBox()`
- `AETimerRunningBox::pauseTimer()`
- `AETimerRunningBox::resumeCurrentTimerBox()`
- `AETimerRunningBox::resumeTimer()`
- `AETimerRunningBox::showDlgPage()`
- `AETimerRunningBox::showTimerBox(char const*, AEGameTime const&, bool, cocos2d::Node*, int, std::function<void (int)>, std::function<void (int)>, cocos2d::EventListenerKeyboard*)`
- `AETimerRunningBox::stopCurAction()`
- `AETimerRunningBox::update(float)`
- `AETimerRunningBox::~AETimerRunningBox()`

## AETipInfos

- `AETipInfos::AETipInfos()`
- `AETipInfos::getTipInfo(int)`

## AETradeBox

- `AETradeBox::AETradeBox()`
- `AETradeBox::backKeyPressed()`
- `AETradeBox::btnBuyInCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AETradeBox::btnSellOutCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AETradeBox::buyInItem(int)`
- `AETradeBox::cleanUpScene()`
- `AETradeBox::clearCaptureSlotSelState()`
- `AETradeBox::clearDraggingItems()`
- `AETradeBox::clearItemSlotSelState()`
- `AETradeBox::closePage()`
- `AETradeBox::createSceneLayer(void*)`
- `AETradeBox::finishThisTrade()`
- `AETradeBox::getCurSelItemGroup()`
- `AETradeBox::getItemPrice(AEPropsItemGroup const&, bool)`
- `AETradeBox::isBuyInItem(AEPropsItemGroup const&)`
- `AETradeBox::isSellOutItem(AEPropsItemGroup const&)`
- `AETradeBox::menuBtnCloseCallback(cocos2d::Ref*)`
- `AETradeBox::onCreate(void*)`
- `AETradeBox::onEnter()`
- `AETradeBox::onExit()`
- `AETradeBox::onNotify(unsigned int, void*)`
- `AETradeBox::onPageCloseDone()`
- `AETradeBox::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AETradeBox::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AETradeBox::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AETradeBox::playDragCancelAnimat()`
- `AETradeBox::removeBuyInItem(AEPropsItemGroup const&)`
- `AETradeBox::removeSellOutItem(AEPropsItemGroup const&)`
- `AETradeBox::sellOutItem(int)`
- `AETradeBox::setCaptureSlotSelOn(cocos2d::Node*, int)`
- `AETradeBox::setItemSlotSelOn(cocos2d::Node*, int)`
- `AETradeBox::showUpPage(int, int, cocos2d::EventListenerKeyboard*)`
- `AETradeBox::update(float)`
- `AETradeBox::updateCapturesList()`
- `AETradeBox::updateInventoryList()`
- `AETradeBox::updateListCursorCap()`
- `AETradeBox::updateListCursorInv()`
- `AETradeBox::updateTab1BtnStats()`
- `AETradeBox::updateTradeBox()`
- `AETradeBox::~AETradeBox()`

## AEUnitListView

- `AEUnitListView::AEUnitListView()`
- `AEUnitListView::clearDraggingItems()`
- `AEUnitListView::clearItemSelState()`
- `AEUnitListView::create(float, float)`
- `AEUnitListView::getCurSeledUnit()`
- `AEUnitListView::hideUnitInfoBox()`
- `AEUnitListView::initCtl(float, float)`
- `AEUnitListView::onEnter()`
- `AEUnitListView::onExit()`
- `AEUnitListView::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AEUnitListView::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AEUnitListView::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AEUnitListView::playDragCancelAnimat()`
- `AEUnitListView::scrollToTop()`
- `AEUnitListView::setItemSelState(cocos2d::Sprite*, bool)`
- `AEUnitListView::update(float)`
- `AEUnitListView::updateListCursorView()`
- `AEUnitListView::updateListView()`
- `AEUnitListView::~AEUnitListView()`

## AEUnitSellGroup

- `AEUnitSellGroup::AEUnitSellGroup()`
- `AEUnitSellGroup::create(int)`
- `AEUnitSellGroup::initData(int)`
- `AEUnitSellGroup::~AEUnitSellGroup()`

## AEUpgradeUnitBox

- `AEUpgradeUnitBox::AEUpgradeUnitBox()`
- `AEUpgradeUnitBox::backKeyPressed()`
- `AEUpgradeUnitBox::btnSelTagUpgradeInfo(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEUpgradeUnitBox::btnUpgradeCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEUpgradeUnitBox::cleanUpScene()`
- `AEUpgradeUnitBox::closePage()`
- `AEUpgradeUnitBox::createSceneLayer(void*)`
- `AEUpgradeUnitBox::menuBtnBatchUpgradeCallback(cocos2d::Ref*)`
- `AEUpgradeUnitBox::menuBtnCloseCallback(cocos2d::Ref*)`
- `AEUpgradeUnitBox::onCreate(void*)`
- `AEUpgradeUnitBox::onEnter()`
- `AEUpgradeUnitBox::onExit()`
- `AEUpgradeUnitBox::onNotify(unsigned int, void*)`
- `AEUpgradeUnitBox::onPageCloseDone()`
- `AEUpgradeUnitBox::onPageShowUpDone()`
- `AEUpgradeUnitBox::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AEUpgradeUnitBox::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AEUpgradeUnitBox::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AEUpgradeUnitBox::showUpPage(SGCharacterData*, SGUnitsData*, cocos2d::EventListenerKeyboard*)`
- `AEUpgradeUnitBox::update(float)`
- `AEUpgradeUnitBox::updateBatchUpgradeBtnStates()`
- `AEUpgradeUnitBox::updateTagBoxInfoContent(cocos2d::ui::Layout*, bool)`
- `AEUpgradeUnitBox::updateUnitUpgradeInfo()`
- `AEUpgradeUnitBox::~AEUpgradeUnitBox()`

## AEVec3Data

- `AEVec3Data::AEVec3Data()`
- `AEVec3Data::create(float, float, float)`
- `AEVec3Data::initData(float, float, float)`
- `AEVec3Data::~AEVec3Data()`

## AEVictoryScene

- `AEVictoryScene::AEVictoryScene()`
- `AEVictoryScene::backKeyPressed()`
- `AEVictoryScene::btnTab1DownMoveAllCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEVictoryScene::btnTab1DownMoveCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEVictoryScene::btnTab1UpMoveCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEVictoryScene::btnTab2DownMoveAllCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEVictoryScene::btnTab2DownMoveCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEVictoryScene::btnTab2UpMoveCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEVictoryScene::cleanUpScene()`
- `AEVictoryScene::clearCaptureSlotSelState()`
- `AEVictoryScene::clearDraggingItems()`
- `AEVictoryScene::clearItemSlotSelState()`
- `AEVictoryScene::closePage()`
- `AEVictoryScene::createSceneLayer(void*)`
- `AEVictoryScene::downMoveAllCaptive()`
- `AEVictoryScene::downMoveAllItem()`
- `AEVictoryScene::downMoveCaptive(SGUnitsData*)`
- `AEVictoryScene::downMoveItem(int)`
- `AEVictoryScene::finishLoot()`
- `AEVictoryScene::getCurSelItemGroup()`
- `AEVictoryScene::menuBtnAutoLootCallback(cocos2d::Ref*)`
- `AEVictoryScene::menuBtnCloseCallback(cocos2d::Ref*)`
- `AEVictoryScene::menuBtnTabsCallback(cocos2d::Ref*)`
- `AEVictoryScene::onBtnOkCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEVictoryScene::onComfirmDropCaptive(int)`
- `AEVictoryScene::onComfirmDropCapture(int)`
- `AEVictoryScene::onCreate(void*)`
- `AEVictoryScene::onDragOpDone(cocos2d::Ref*, int, int)`
- `AEVictoryScene::onDragging(cocos2d::Ref*, cocos2d::Vec2 const&, int)`
- `AEVictoryScene::onEnter()`
- `AEVictoryScene::onExit()`
- `AEVictoryScene::onNotify(unsigned int, void*)`
- `AEVictoryScene::onPageCloseDone()`
- `AEVictoryScene::onSeledItemChanged(cocos2d::Ref*)`
- `AEVictoryScene::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AEVictoryScene::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AEVictoryScene::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AEVictoryScene::playDragCancelAnimat()`
- `AEVictoryScene::setCaptureSlotSelOn(cocos2d::Node*, int)`
- `AEVictoryScene::setItemSlotSelOn(cocos2d::Node*, int)`
- `AEVictoryScene::showUpPage(cocos2d::EventListenerKeyboard*)`
- `AEVictoryScene::swapTwoItemSlot(int, int, int, int)`
- `AEVictoryScene::upMoveCaptive(SGUnitsData*)`
- `AEVictoryScene::upMoveItem(int)`
- `AEVictoryScene::update(float)`
- `AEVictoryScene::updateCapturesList()`
- `AEVictoryScene::updateCurPageView()`
- `AEVictoryScene::updateInventoryList()`
- `AEVictoryScene::updateListCursorCap()`
- `AEVictoryScene::updateListCursorInv()`
- `AEVictoryScene::updateStaticNumView()`
- `AEVictoryScene::updateSwitchBtnStates()`
- `AEVictoryScene::updateTab1BtnStats()`
- `AEVictoryScene::updateTab1PageView()`
- `AEVictoryScene::updateTab2BtnStats()`
- `AEVictoryScene::updateTab2PageView()`
- `AEVictoryScene::~AEVictoryScene()`

## AEWeeklyBudget

- `AEWeeklyBudget::AEWeeklyBudget()`
- `AEWeeklyBudget::addIncomeOption(cocos2d::ui::ListView*, int, char const*, int)`
- `AEWeeklyBudget::backKeyPressed()`
- `AEWeeklyBudget::btnOkCallback(cocos2d::Ref*, cocos2d::ui::Widget::TouchEventType)`
- `AEWeeklyBudget::calculateNetIncomes(SGCharacterData*, cocos2d::ui::ListView*, bool)`
- `AEWeeklyBudget::cleanUpScene()`
- `AEWeeklyBudget::closePage()`
- `AEWeeklyBudget::confirmBudget()`
- `AEWeeklyBudget::createSceneLayer(void*)`
- `AEWeeklyBudget::getIncomeColor(int)`
- `AEWeeklyBudget::lvCharListEventScrollView(cocos2d::Ref*, cocos2d::ui::ScrollView::EventType)`
- `AEWeeklyBudget::menuBtnCloseCallback(cocos2d::Ref*)`
- `AEWeeklyBudget::onCreate(void*)`
- `AEWeeklyBudget::onEnter()`
- `AEWeeklyBudget::onExit()`
- `AEWeeklyBudget::onNotify(unsigned int, void*)`
- `AEWeeklyBudget::onPageCloseDone()`
- `AEWeeklyBudget::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `AEWeeklyBudget::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `AEWeeklyBudget::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `AEWeeklyBudget::showUpPage()`
- `AEWeeklyBudget::update(float)`
- `AEWeeklyBudget::updateBudgetPage()`
- `AEWeeklyBudget::updateListCursorView()`
- `AEWeeklyBudget::updateListViewSize()`
- `AEWeeklyBudget::~AEWeeklyBudget()`

## AEZipUtility

- `AEZipUtility::AEZipUtility()`
- `AEZipUtility::addFileToZip(char const*, char const*)`
- `AEZipUtility::addFileToZipWithMemory(void const*, unsigned long, char const*)`
- `AEZipUtility::closeZipFile()`
- `AEZipUtility::createZipFile(char const*, char const*)`
- `AEZipUtility::unzipCloseFile()`
- `AEZipUtility::unzipFile(char const*, bool)`
- `AEZipUtility::unzipFileToMemory(unsigned char**, unsigned long*)`
- `AEZipUtility::unzipOpenFile(char const*, char const*)`
- `AEZipUtility::~AEZipUtility()`

## AppDelegate

- `AppDelegate::AppDelegate()`
- `AppDelegate::applicationDidEnterBackground()`
- `AppDelegate::applicationDidFinishLaunching()`
- `AppDelegate::applicationWillEnterForeground()`
- `AppDelegate::initGLContextAttrs()`
- `AppDelegate::~AppDelegate()`

## ArmatureNodeReader

- `ArmatureNodeReader::ArmatureNodeReader()`
- `ArmatureNodeReader::createInstance()`
- `ArmatureNodeReader::createNodeWithFlatBuffers(flatbuffers::Table const*)`
- `ArmatureNodeReader::createOptionsWithFlatBuffers(tinyxml2::XMLElement const*, flatbuffers::FlatBufferBuilder*)`
- `ArmatureNodeReader::destroyInstance()`
- `ArmatureNodeReader::getArmatureName(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `ArmatureNodeReader::getInstance()`
- `ArmatureNodeReader::setPropsWithFlatBuffers(cocos2d::Node*, flatbuffers::Table const*)`
- `ArmatureNodeReader::~ArmatureNodeReader()`

## BaseScene

- `BaseScene::create(void*)`
- `BaseScene::init(void*)`
- `BaseScene::seekNodeByName(cocos2d::Node*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `BaseScene::seekNodeByTag(cocos2d::Node*, int)`

## BoneNodeReader

- `BoneNodeReader::BoneNodeReader()`
- `BoneNodeReader::createInstance()`
- `BoneNodeReader::createNodeWithFlatBuffers(flatbuffers::Table const*)`
- `BoneNodeReader::createOptionsWithFlatBuffers(tinyxml2::XMLElement const*, flatbuffers::FlatBufferBuilder*)`
- `BoneNodeReader::destroyInstance()`
- `BoneNodeReader::getInstance()`
- `BoneNodeReader::setPropsWithFlatBuffers(cocos2d::Node*, flatbuffers::Table const*)`
- `BoneNodeReader::~BoneNodeReader()`

## CProfileIterator

- `CProfileIterator::CProfileIterator(CProfileNode*)`
- `CProfileIterator::Enter_Child(int)`
- `CProfileIterator::Enter_Parent()`
- `CProfileIterator::First()`
- `CProfileIterator::Is_Done()`
- `CProfileIterator::Next()`

## CProfileManager

- `CProfileManager::Get_Time_Since_Reset()`
- `CProfileManager::Increment_Frame_Counter()`
- `CProfileManager::Reset()`
- `CProfileManager::Start_Profile(char const*)`
- `CProfileManager::Stop_Profile()`
- `CProfileManager::dumpAll()`
- `CProfileManager::dumpRecursive(CProfileIterator*, int)`

## CProfileNode

- `CProfileNode::CProfileNode(char const*, CProfileNode*)`
- `CProfileNode::Call()`
- `CProfileNode::CleanupMemory()`
- `CProfileNode::Get_Sub_Node(char const*)`
- `CProfileNode::Reset()`
- `CProfileNode::Return()`
- `CProfileNode::~CProfileNode()`

## CocosDenshion::SimpleAudioEngine

- `CocosDenshion::SimpleAudioEngine::SimpleAudioEngine()`
- `CocosDenshion::SimpleAudioEngine::end()`
- `CocosDenshion::SimpleAudioEngine::getBackgroundMusicVolume()`
- `CocosDenshion::SimpleAudioEngine::getEffectsVolume()`
- `CocosDenshion::SimpleAudioEngine::getInstance()`
- `CocosDenshion::SimpleAudioEngine::isBackgroundMusicPlaying()`
- `CocosDenshion::SimpleAudioEngine::pauseAllEffects()`
- `CocosDenshion::SimpleAudioEngine::pauseBackgroundMusic()`
- `CocosDenshion::SimpleAudioEngine::pauseEffect(unsigned int)`
- `CocosDenshion::SimpleAudioEngine::playBackgroundMusic(char const*, bool)`
- `CocosDenshion::SimpleAudioEngine::playEffect(char const*, bool, float, float, float)`
- `CocosDenshion::SimpleAudioEngine::preloadBackgroundMusic(char const*)`
- `CocosDenshion::SimpleAudioEngine::preloadEffect(char const*)`
- `CocosDenshion::SimpleAudioEngine::resumeAllEffects()`
- `CocosDenshion::SimpleAudioEngine::resumeBackgroundMusic()`
- `CocosDenshion::SimpleAudioEngine::resumeEffect(unsigned int)`
- `CocosDenshion::SimpleAudioEngine::rewindBackgroundMusic()`
- `CocosDenshion::SimpleAudioEngine::setBackgroundMusicVolume(float)`
- `CocosDenshion::SimpleAudioEngine::setEffectsVolume(float)`
- `CocosDenshion::SimpleAudioEngine::stopAllEffects()`
- `CocosDenshion::SimpleAudioEngine::stopBackgroundMusic(bool)`
- `CocosDenshion::SimpleAudioEngine::stopEffect(unsigned int)`
- `CocosDenshion::SimpleAudioEngine::unloadEffect(char const*)`
- `CocosDenshion::SimpleAudioEngine::willPlayBackgroundMusic()`
- `CocosDenshion::SimpleAudioEngine::~SimpleAudioEngine()`

## CocosDenshion::android

- `CocosDenshion::android::getFullPathWithoutAssetsPrefix(char const*)`

## CocosDenshion::android::AndroidJavaEngine

- `CocosDenshion::android::AndroidJavaEngine::AndroidJavaEngine()`
- `CocosDenshion::android::AndroidJavaEngine::getBackgroundMusicVolume()`
- `CocosDenshion::android::AndroidJavaEngine::getEffectsVolume()`
- `CocosDenshion::android::AndroidJavaEngine::isBackgroundMusicPlaying()`
- `CocosDenshion::android::AndroidJavaEngine::pauseAllEffects()`
- `CocosDenshion::android::AndroidJavaEngine::pauseBackgroundMusic()`
- `CocosDenshion::android::AndroidJavaEngine::pauseEffect(unsigned int)`
- `CocosDenshion::android::AndroidJavaEngine::playBackgroundMusic(char const*, bool)`
- `CocosDenshion::android::AndroidJavaEngine::playEffect(char const*, bool, float, float, float)`
- `CocosDenshion::android::AndroidJavaEngine::preloadBackgroundMusic(char const*)`
- `CocosDenshion::android::AndroidJavaEngine::preloadEffect(char const*)`
- `CocosDenshion::android::AndroidJavaEngine::resumeAllEffects()`
- `CocosDenshion::android::AndroidJavaEngine::resumeBackgroundMusic()`
- `CocosDenshion::android::AndroidJavaEngine::resumeEffect(unsigned int)`
- `CocosDenshion::android::AndroidJavaEngine::rewindBackgroundMusic()`
- `CocosDenshion::android::AndroidJavaEngine::setBackgroundMusicVolume(float)`
- `CocosDenshion::android::AndroidJavaEngine::setEffectsVolume(float)`
- `CocosDenshion::android::AndroidJavaEngine::stopAllEffects()`
- `CocosDenshion::android::AndroidJavaEngine::stopBackgroundMusic(bool)`
- `CocosDenshion::android::AndroidJavaEngine::stopEffect(unsigned int)`
- `CocosDenshion::android::AndroidJavaEngine::unloadEffect(char const*)`
- `CocosDenshion::android::AndroidJavaEngine::willPlayBackgroundMusic()`
- `CocosDenshion::android::AndroidJavaEngine::~AndroidJavaEngine()`

## DateTime

- `DateTime::DateTime()`
- `DateTime::DateTime(DateTime const&)`
- `DateTime::DateTime(long)`
- `DateTime::DateTime(tm const&)`

## MyMath

- `MyMath::DistanceLineToLine(cocos2d::Vec3 const&, cocos2d::Vec3 const&, cocos2d::Vec3 const&, cocos2d::Vec3 const&)`
- `MyMath::DistancePointToLine(cocos2d::Vec3 const&, cocos2d::Vec3 const&, cocos2d::Vec3 const&)`
- `MyMath::GetFootpt(cocos2d::Vec2 const&, cocos2d::Vec2 const&, cocos2d::Vec2 const&)`
- `MyMath::GetPtToPtLen(cocos2d::Vec2 const&, cocos2d::Vec2 const&)`
- `MyMath::GetRealPtToLine(cocos2d::Vec2 const&, cocos2d::Vec2 const&, cocos2d::Vec2 const&, cocos2d::Vec2&)`
- `MyMath::IsPtInLine(cocos2d::Vec2 const&, cocos2d::Vec2 const&, cocos2d::Vec2 const&, float)`
- `MyMath::IsPtInPolygon(cocos2d::Vec2, cocos2d::Vec2*, short)`
- `MyMath::betweenCmp(cocos2d::Vec2 const&, cocos2d::Vec2 const&, cocos2d::Vec2 const&)`
- `MyMath::compareAngle(short, short)`
- `MyMath::cross(cocos2d::Vec2 const&, cocos2d::Vec2 const&, cocos2d::Vec2 const&)`
- `MyMath::dP(double)`
- `MyMath::dblcmp(double)`
- `MyMath::det(double, double, double, double)`
- `MyMath::dot(cocos2d::Vec2 const&, cocos2d::Vec2 const&, cocos2d::Vec2 const&)`
- `MyMath::dotdet(double, double, double, double)`
- `MyMath::getCycleNumDiff(float, float, float)`
- `MyMath::getIncludedAngle(cocos2d::Vec2 const&, cocos2d::Vec2 const&)`
- `MyMath::getOriginAngle(cocos2d::Vec2 const&)`
- `MyMath::getPtRotateBy(cocos2d::Vec2 const&, float)`
- `MyMath::getRandomNumber(int, int)`
- `MyMath::getVectorByPoints(cocos2d::Vec2 const&, cocos2d::Vec2 const&)`
- `MyMath::getVectorBySpeedAndAngle(float, float)`
- `MyMath::getVectorLength(cocos2d::Vec2 const&)`
- `MyMath::getVectorScaleBy(cocos2d::Vec2 const&, float)`
- `MyMath::isLineCrossRect(cocos2d::Vec2 const&, cocos2d::Vec2 const&, cocos2d::Rect const&)`
- `MyMath::isSegCross(cocos2d::Vec2 const&, cocos2d::Vec2 const&, cocos2d::Vec2 const&, cocos2d::Vec2 const&, cocos2d::Vec2&)`

## RoleStatuInfo

- `RoleStatuInfo::RoleStatuInfo()`
- `RoleStatuInfo::parseInfo(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, int)`
- `RoleStatuInfo::parseStatInfoVal(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, RoleStatuInfo*, int, int, int)`
- `RoleStatuInfo::~RoleStatuInfo()`

## RoleTalentInfo

- `RoleTalentInfo::RoleTalentInfo()`
- `RoleTalentInfo::clear()`
- `RoleTalentInfo::parseInfo(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `RoleTalentInfo::toString()`
- `RoleTalentInfo::~RoleTalentInfo()`

## SGAnimeActionData

- `SGAnimeActionData::SGAnimeActionData()`
- `SGAnimeActionData::~SGAnimeActionData()`

## SGBattleField

- `SGBattleField::SGBattleField(SGBattleFieldDelegate*)`
- `SGBattleField::activeTagRole(SGRoleObj*)`
- `SGBattleField::addSoldierToBF(SGUnitsData*, SGGeneral*, bool)`
- `SGBattleField::automaticUseSkill(SGGeneral*, int)`
- `SGBattleField::battleOver()`
- `SGBattleField::battleStart()`
- `SGBattleField::changeArmysMorale(SGKingdom*, int)`
- `SGBattleField::checkStrategySkill(SGGeneral*, int, float)`
- `SGBattleField::checkUnitEscapeChance(float)`
- `SGBattleField::cleanUpBattleRes()`
- `SGBattleField::clearCurSeledAttackUnits()`
- `SGBattleField::clearCurSeledUnits()`
- `SGBattleField::eliminateTagUnit(SGRoleObj*)`
- `SGBattleField::findPath(cocos2d::Vec2 const&, float, cocos2d::Vec2 const&, float, SGRoleObj*)`
- `SGBattleField::getAreaSkillCastTag(SGRoleObj*, bool)`
- `SGBattleField::getBfPosByViewPos(cocos2d::Vec2 const&)`
- `SGBattleField::getClickedRoleInBF(cocos2d::Vec2 const&, int)`
- `SGBattleField::getEnablePositions(cocos2d::Vec2 const&, float, float, float, int)`
- `SGBattleField::getEnemyChiefOfTag(SGRoleObj*)`
- `SGBattleField::getHealCastTag(SGRoleObj*)`
- `SGBattleField::getOpPosByDir(cocos2d::Vec2 const&, bool)`
- `SGBattleField::getRoleEscapePos(SGRoleObj*)`
- `SGBattleField::getRoleName(SGRoleObj*)`
- `SGBattleField::getTerrianRate(SGRoleObj*)`
- `SGBattleField::getValidUnitCount(SGKingdom*, UNIT_MAIN_CLASS)`
- `SGBattleField::getViewPosByBfPos(cocos2d::Vec2 const&)`
- `SGBattleField::giveOrderToArmy(SGKingdom*, UNIT_MAIN_CLASS, ROLE_INTENTS)`
- `SGBattleField::initBattleUnits()`
- `SGBattleField::initUnitsArmy(SGGeneral*, SGFormation*)`
- `SGBattleField::isTagPosPassable(cocos2d::Vec2 const&, float)`
- `SGBattleField::keepCameraFocus(cocos2d::Vec2 const&, float, float)`
- `SGBattleField::loadBattleRes()`
- `SGBattleField::lockCameraFocus(cocos2d::Node*, float, cocos2d::Node*)`
- `SGBattleField::onAddEffect(cocos2d::Node*)`
- `SGBattleField::onBattleOverBalance()`
- `SGBattleField::onComputerStrategy(SGGeneral*)`
- `SGBattleField::onPause()`
- `SGBattleField::onRemoveEffect(cocos2d::Node*)`
- `SGBattleField::onResume()`
- `SGBattleField::onSecondEvent(float)`
- `SGBattleField::onSoliderSkillStrategy(SGSoldier*)`
- `SGBattleField::onTowerShootArrow(cocos2d::Vec2 const&)`
- `SGBattleField::onUnitsNumChanged()`
- `SGBattleField::playNumEffect(int, int, cocos2d::Vec2 const&, cocos2d::Node*, float, short)`
- `SGBattleField::restaticUnitsNum()`
- `SGBattleField::roleDead(cocos2d::Ref*)`
- `SGBattleField::roleEscaped(cocos2d::Ref*)`
- `SGBattleField::roleResurrection(cocos2d::Ref*)`
- `SGBattleField::selPlayerUnits(UNIT_MAIN_CLASS)`
- `SGBattleField::selTagBattleFieldPos(cocos2d::Vec2 const&)`
- `SGBattleField::setArchersPolicy(SGKingdom*, ARCHER_POLICY)`
- `SGBattleField::soliderDefect(SGRoleObj*)`
- `SGBattleField::stopBattleFieldRuning()`
- `SGBattleField::update(float)`
- `SGBattleField::updateArmysMorale(SGKingdom*)`
- `SGBattleField::~SGBattleField()`

## SGBattleScene

- `SGBattleScene::SGBattleScene()`
- `SGBattleScene::backKeyPressed()`
- `SGBattleScene::backToBPScene()`
- `SGBattleScene::battleStart()`
- `SGBattleScene::bindMinimapUnit(SGRoleObj*)`
- `SGBattleScene::btnAllUnitsAssaultPressed(cocos2d::Ref*)`
- `SGBattleScene::btnCommander1HeadPressed(cocos2d::Ref*)`
- `SGBattleScene::btnCommander2HeadPressed(cocos2d::Ref*)`
- `SGBattleScene::btnCommandsPressed(cocos2d::Ref*)`
- `SGBattleScene::btnInfosPressed(cocos2d::Ref*)`
- `SGBattleScene::btnIntentDrawBackPressed(cocos2d::Ref*)`
- `SGBattleScene::btnIntentFollowPressed(cocos2d::Ref*)`
- `SGBattleScene::btnIntentForwardPressed(cocos2d::Ref*)`
- `SGBattleScene::btnIntentHoldPressed(cocos2d::Ref*)`
- `SGBattleScene::btnMenuCallback(cocos2d::Ref*)`
- `SGBattleScene::btnPausePressed(cocos2d::Ref*)`
- `SGBattleScene::btnRetreatPressed(cocos2d::Ref*)`
- `SGBattleScene::btnSkillsPressed(cocos2d::Ref*)`
- `SGBattleScene::btnUnitAllPressed(cocos2d::Ref*)`
- `SGBattleScene::btnUnitArcherPressed(cocos2d::Ref*)`
- `SGBattleScene::btnUnitCavalryPressed(cocos2d::Ref*)`
- `SGBattleScene::btnUnitFootmanPressed(cocos2d::Ref*)`
- `SGBattleScene::cancelSkillCmd()`
- `SGBattleScene::cleanUpScene()`
- `SGBattleScene::clearCameraFocus()`
- `SGBattleScene::clearQuickSlotSels()`
- `SGBattleScene::clickOnMiniMap(cocos2d::Vec2 const&)`
- `SGBattleScene::cmdUseSkill(int, SGRoleObj*, cocos2d::Vec2 const&)`
- `SGBattleScene::create(void*)`
- `SGBattleScene::enableTagBtn(cocos2d::MenuItemSprite*)`
- `SGBattleScene::gamePause()`
- `SGBattleScene::gameResume()`
- `SGBattleScene::getCurCameraPos()`
- `SGBattleScene::getCurCameraRealPos()`
- `SGBattleScene::getMsgTypeColor(int)`
- `SGBattleScene::hideCmdBtns()`
- `SGBattleScene::hideQuickSlots()`
- `SGBattleScene::hideSkillSelTip()`
- `SGBattleScene::hideTagBtn(cocos2d::Node*)`
- `SGBattleScene::initFaceBox()`
- `SGBattleScene::initMinimap()`
- `SGBattleScene::keepBFCamera(cocos2d::Vec2 const&, float, float)`
- `SGBattleScene::keepCameraFocus(cocos2d::Vec2 const&, float, float)`
- `SGBattleScene::lockBFCameraFocus(cocos2d::Node*, float)`
- `SGBattleScene::lockCameraFocus(cocos2d::Node*, float)`
- `SGBattleScene::lockFocusToTag(cocos2d::Node*, float)`
- `SGBattleScene::moveBFCameraTo(cocos2d::Vec2 const&, float)`
- `SGBattleScene::moveCameraTo(cocos2d::Vec2 const&, int)`
- `SGBattleScene::onAddUnit(cocos2d::Ref*)`
- `SGBattleScene::onArmysMoraleChanged(cocos2d::Ref*)`
- `SGBattleScene::onBattleOver(int)`
- `SGBattleScene::onCheckMsgInfos(float)`
- `SGBattleScene::onCommanderStatuChanged(cocos2d::Ref*)`
- `SGBattleScene::onCreate(void*)`
- `SGBattleScene::onEnter()`
- `SGBattleScene::onExit()`
- `SGBattleScene::onGuide1StepDone()`
- `SGBattleScene::onNotify(unsigned int, void*)`
- `SGBattleScene::onRetreatConfirm(int)`
- `SGBattleScene::onSecondEvent(float)`
- `SGBattleScene::onShowCharFaceBoxA()`
- `SGBattleScene::onShowCharFaceBoxB()`
- `SGBattleScene::onSkillCmdExec(int)`
- `SGBattleScene::onSkillIntentExcuted(cocos2d::Ref*)`
- `SGBattleScene::onSkillStatUpdate(cocos2d::Ref*)`
- `SGBattleScene::onTouchBegan(cocos2d::Touch*, cocos2d::Event*)`
- `SGBattleScene::onTouchEnded(cocos2d::Touch*, cocos2d::Event*)`
- `SGBattleScene::onTouchMoved(cocos2d::Touch*, cocos2d::Event*)`
- `SGBattleScene::onUnitsStateChange(cocos2d::Ref*)`
- `SGBattleScene::playerPauseGame()`
- `SGBattleScene::playerResumeGame()`
- `SGBattleScene::removeMsgInfo(AEMessageInfo*)`
- `SGBattleScene::setBtnActive(cocos2d::MenuItemSprite*, bool)`
- `SGBattleScene::setControlEnable(bool)`
- `SGBattleScene::setControlRoleAttackTag(SGRoleObj*)`
- `SGBattleScene::setQuickSlotSelOn(cocos2d::Sprite*)`
- `SGBattleScene::setSkillSelArea(cocos2d::Vec2 const&)`
- `SGBattleScene::setSkillSelAreaMarkRad(float)`
- `SGBattleScene::setSkillSelDir(float)`
- `SGBattleScene::showBattleStartEffect()`
- `SGBattleScene::showCmdBtns()`
- `SGBattleScene::showIntentBtns(cocos2d::MenuItemSprite*)`
- `SGBattleScene::showMsgInfo(AEMessageInfo*)`
- `SGBattleScene::showQuickSlots()`
- `SGBattleScene::showSkillList()`
- `SGBattleScene::showSkillSelTip(int)`
- `SGBattleScene::showTagCmdBtn(cocos2d::MenuItemSprite*, cocos2d::Vec2)`
- `SGBattleScene::showTagIntentBtn(cocos2d::MenuItemSprite*, cocos2d::Vec2, cocos2d::Vec2)`
- `SGBattleScene::skillSelBoxDismissed(int, int)`
- `SGBattleScene::update(float)`
- `SGBattleScene::updateBtnStates()`
- `SGBattleScene::updateCameraView(float)`
- `SGBattleScene::updateQbManaStats()`
- `SGBattleScene::updateQuickBtnSlots()`
- `SGBattleScene::updateStatuBar(bool)`
- `SGBattleScene::updateUnitsStatics()`
- `SGBattleScene::~SGBattleScene()`

## SGBuffData

- `SGBuffData::SGBuffData(BUFF_CODES, bool, int)`
- `SGBuffData::create(BUFF_CODES, bool, int)`
- `SGBuffData::~SGBuffData()`

## SGCharTemplate

- `SGCharTemplate::SGCharTemplate()`
- `SGCharTemplate::~SGCharTemplate()`

## SGCharacterData

- `SGCharacterData::SGCharacterData()`
- `SGCharacterData::addExp(int)`
- `SGCharacterData::addMoney(int)`
- `SGCharacterData::addUnit(SGUnitsData*)`
- `SGCharacterData::changeExploitVal(int)`
- `SGCharacterData::changeHP(int)`
- `SGCharacterData::changeHonorVal(int)`
- `SGCharacterData::changeLoyalVal(int)`
- `SGCharacterData::changeMP(int)`
- `SGCharacterData::changeUnitsMorale(int)`
- `SGCharacterData::checkQuickSkill(int)`
- `SGCharacterData::checkTagItemCouldEquip(AEPropsItemInfo*, cocos2d::Node*)`
- `SGCharacterData::compareTwoCharsByExploit(SGCharacterData*, SGCharacterData*)`
- `SGCharacterData::compareTwoCharsBySpeakTalent(SGCharacterData*, SGCharacterData*)`
- `SGCharacterData::compareTwoCharsByTempField(SGCharacterData*, SGCharacterData*)`
- `SGCharacterData::deleteUnit(SGUnitsData*)`
- `SGCharacterData::equipTagItem(AEPropsItemGroup&, cocos2d::Node*)`
- `SGCharacterData::getBaseStatuType()`
- `SGCharacterData::getCampColor()`
- `SGCharacterData::getCharName(int)`
- `SGCharacterData::getCurRoleStatuInfo()`
- `SGCharacterData::getDefeatExp()`
- `SGCharacterData::getFaceImgID()`
- `SGCharacterData::getFightableUnitNum()`
- `SGCharacterData::getKingdom()`
- `SGCharacterData::getKingdomID()`
- `SGCharacterData::getLeadMaxCharCount()`
- `SGCharacterData::getLevelUpExp()`
- `SGCharacterData::getMoveSpeedOnMap()`
- `SGCharacterData::getSkillCDPct(int)`
- `SGCharacterData::getSkillCDTime(int)`
- `SGCharacterData::getTemplateInfo()`
- `SGCharacterData::getUnitCount()`
- `SGCharacterData::isKing()`
- `SGCharacterData::isTagSkillCouldUse(int)`
- `SGCharacterData::removeTagEquip(int)`
- `SGCharacterData::resetSkillCD(int)`
- `SGCharacterData::restoreAllSkillCD()`
- `SGCharacterData::restoreAllStatus()`
- `SGCharacterData::setKingdom(int)`
- `SGCharacterData::setQuickSkill(int, int)`
- `SGCharacterData::updateCharTime(float)`
- `SGCharacterData::updateLevelStatus()`
- `SGCharacterData::updateStatus()`
- `SGCharacterData::~SGCharacterData()`

## SGDamageInfo

- `SGDamageInfo::SGDamageInfo()`
- `SGDamageInfo::isBlockable()`
- `SGDamageInfo::isEvadeable()`
- `SGDamageInfo::~SGDamageInfo()`

## SGEffectData

- `SGEffectData::SGEffectData()`
- `SGEffectData::~SGEffectData()`

## SGEffects

- `SGEffects::ChangeState(EFFECT_STATES)`
- `SGEffects::SGEffects(SGBattleField*)`
- `SGEffects::addEffectToTag(cocos2d::Node*, int)`
- `SGEffects::checkHit()`
- `SGEffects::getCurPos()`
- `SGEffects::initEffect(EFFECT_TYPES, SGEffectData*)`
- `SGEffects::onEffectFinished()`
- `SGEffects::onEffectHited(SGRoleObj*)`
- `SGEffects::onFrameIndexChanged(int)`
- `SGEffects::onLastFramePlayed()`
- `SGEffects::removeEffectSelf()`
- `SGEffects::setCurPos(cocos2d::Vec2 const&)`
- `SGEffects::setEffectMoves(WMSMoves*, float, float, float)`
- `SGEffects::setInitState(bool)`
- `SGEffects::setIsByDir(EFFECT_DIRMODE, float)`
- `SGEffects::setMoveByFollowRole(SGRoleObj*, cocos2d::Vec2 const&, float, bool)`
- `SGEffects::setMoveByLockedTarget(SGRoleObj*, float)`
- `SGEffects::startEffect()`
- `SGEffects::update(float)`
- `SGEffects::~SGEffects()`

## SGFormation

- `SGFormation::SGFormation()`
- `SGFormation::~SGFormation()`

## SGGeneral

- `SGGeneral::ChangeState(ROLE_STATES)`
- `SGGeneral::SGGeneral()`
- `SGGeneral::changeHp(int)`
- `SGGeneral::changeMp(int)`
- `SGGeneral::controlKeepCamFocus(cocos2d::Vec2 const&, float, float)`
- `SGGeneral::controlLockCamFocus(cocos2d::Node*, float, cocos2d::Node*)`
- `SGGeneral::create(SGCharacterData*, SGBattleField*)`
- `SGGeneral::initGeneral(SGCharacterData*, SGBattleField*)`
- `SGGeneral::isStrategicAreaSkill(int)`
- `SGGeneral::onActionStepDone()`
- `SGGeneral::onCastDone(bool)`
- `SGGeneral::onLightShining(cocos2d::Vec2 const&, float, int)`
- `SGGeneral::onResTagUnit(SGRoleObj*, float)`
- `SGGeneral::onRestoreMp(int)`
- `SGGeneral::onRoleAction()`
- `SGGeneral::onRoleActionEvent(cocostudio::timeline::Frame*)`
- `SGGeneral::onSkillAction()`
- `SGGeneral::onSkillEffectHited(SGEffects*, SGRoleObj*)`
- `SGGeneral::onSkillEffectNoHit(SGEffects*)`
- `SGGeneral::onSkillFinished()`
- `SGGeneral::onSkillHitted()`
- `SGGeneral::playHolyBuffEft(cocos2d::Node*, cocos2d::Vec2 const&, int, float)`
- `SGGeneral::playHolyBuffEft2(cocos2d::Node*, cocos2d::Vec2 const&, int, float)`
- `SGGeneral::playHolyLightFlash(cocos2d::Node*, cocos2d::Vec2 const&, int)`
- `SGGeneral::playLightHealEft(cocos2d::Node*, cocos2d::Vec2 const&, int, float)`
- `SGGeneral::playPowerEft()`
- `SGGeneral::playResUnitEft(cocos2d::Node*, cocos2d::Vec2 const&, int, float)`
- `SGGeneral::playRoarEft(cocos2d::Node*, cocos2d::Vec2 const&, int)`
- `SGGeneral::playShieldEft(cocos2d::Node*, cocos2d::Vec2 const&, int)`
- `SGGeneral::playStorageEft()`
- `SGGeneral::playSummonEft(cocos2d::Node*, cocos2d::Vec2 const&, int, int, cocos2d::Color3B)`
- `SGGeneral::playWindWalkEft()`
- `SGGeneral::resTagUnit(SGRoleObj*, float)`
- `SGGeneral::startCasting(float)`
- `SGGeneral::update(float)`
- `SGGeneral::updateStatus()`
- `SGGeneral::~SGGeneral()`

## SGKingdom

- `SGKingdom::SGKingdom()`
- `SGKingdom::compareTwoAlarm(AEKingdomAlarm*, AEKingdomAlarm*)`
- `SGKingdom::getKingdomName(int)`
- `SGKingdom::getUrgentAlarm()`
- `SGKingdom::setAlarm(cocos2d::Vec2 const&, int, int)`
- `SGKingdom::updateKingdomStatistics()`
- `SGKingdom::~SGKingdom()`

## SGLegion

- `SGLegion::SGLegion()`
- `SGLegion::addToInventory(AEPropsItemGroup const&)`
- `SGLegion::breakLegionAction(int)`
- `SGLegion::breakLegionMove()`
- `SGLegion::checkInventoryForItem(int, int)`
- `SGLegion::create()`
- `SGLegion::dismissLegion()`
- `SGLegion::equipTagSlotItem(SGCharacterData*, int, cocos2d::Node*)`
- `SGLegion::executeCurInstruct()`
- `SGLegion::feedANavStep()`
- `SGLegion::getLegionFoodsNum()`
- `SGLegion::getStorageNum(int)`
- `SGLegion::getTagIndexItem(int)`
- `SGLegion::intoLargeMap()`
- `SGLegion::intoTagSite(int)`
- `SGLegion::inventoryHasSpace(AEPropsItemGroup const&)`
- `SGLegion::isActiveState()`
- `SGLegion::moveToNextNavStep(cocos2d::Vec2 const&, cocos2d::Vec2 const&)`
- `SGLegion::navMeshMoveTo(cocos2d::Vec2 const&)`
- `SGLegion::onDailyConsumeFood()`
- `SGLegion::onExecuteCurInstructDone()`
- `SGLegion::onExecuteMoveAct(float)`
- `SGLegion::onLegionActionDone()`
- `SGLegion::onNavStepDone()`
- `SGLegion::onReachFinalPot()`
- `SGLegion::onUpdateLegionMapAction(float)`
- `SGLegion::removeFromInventory(int, int)`
- `SGLegion::removeTagSlotEquip(SGCharacterData*, int)`
- `SGLegion::removeTagSlotItem(int, int)`
- `SGLegion::resumeLegionAction()`
- `SGLegion::resumeLegionMove()`
- `SGLegion::startLegionAction(int, float)`
- `SGLegion::startOccupyTagSite(int)`
- `SGLegion::startRaidTagVillage(int)`
- `SGLegion::startSeigeTagSite(int, float)`
- `SGLegion::swapSlotItem(int, int)`
- `SGLegion::updateLegion()`
- `SGLegion::~SGLegion()`

## SGMapCellData

- `SGMapCellData::SGMapCellData()`
- `SGMapCellData::clearMapPV()`
- `SGMapCellData::create()`
- `SGMapCellData::~SGMapCellData()`

## SGMapSiteObj

- `SGMapSiteObj::SGMapSiteObj()`
- `SGMapSiteObj::changeSiteDefence(int)`
- `SGMapSiteObj::changeSiteProsperity(int)`
- `SGMapSiteObj::compareTwoSitesByProsperity(SGMapSiteObj*, SGMapSiteObj*)`
- `SGMapSiteObj::createAMilitia()`
- `SGMapSiteObj::createCaravanTeam()`
- `SGMapSiteObj::createMapSite()`
- `SGMapSiteObj::createSandTableView(cocos2d::Node*, int, bool)`
- `SGMapSiteObj::getCampColor()`
- `SGMapSiteObj::getConstructDays(int)`
- `SGMapSiteObj::getMaxCharsSize()`
- `SGMapSiteObj::getSiteName(int)`
- `SGMapSiteObj::getSiteSoldiersCount()`
- `SGMapSiteObj::getSubLands()`
- `SGMapSiteObj::getTowerAtk()`
- `SGMapSiteObj::getTowerCount()`
- `SGMapSiteObj::getWeekRecruitNum()`
- `SGMapSiteObj::getWeeklyTaxInfo()`
- `SGMapSiteObj::getWeeklyTaxNum()`
- `SGMapSiteObj::initMapSite()`
- `SGMapSiteObj::isOccupyableBuilding()`
- `SGMapSiteObj::legionInTown(SGLegion*)`
- `SGMapSiteObj::occupySite(int)`
- `SGMapSiteObj::onCheckSiteState()`
- `SGMapSiteObj::onConstructionComplated(int)`
- `SGMapSiteObj::onDailyUpdate()`
- `SGMapSiteObj::onWeeklyUpdate()`
- `SGMapSiteObj::sendExpelArmy(cocos2d::Vec2 const&)`
- `SGMapSiteObj::sendInvasionArmy(SGMapSiteObj*)`
- `SGMapSiteObj::sendPatrolArmy()`
- `SGMapSiteObj::setCurStateView(int)`
- `SGMapSiteObj::setKingdom(int)`
- `SGMapSiteObj::setLordChar(SGCharacterData*)`
- `SGMapSiteObj::setMapPos(cocos2d::Vec2 const&)`
- `SGMapSiteObj::siteDestoryed(SGCharacterData*)`
- `SGMapSiteObj::siteStartConstruct(int)`
- `SGMapSiteObj::transferCharToTagSite(SGCharacterData*, SGMapSiteObj*)`
- `SGMapSiteObj::updateSiteView(cocos2d::Node*)`
- `SGMapSiteObj::~SGMapSiteObj()`

## SGMapUnitModelData

- `SGMapUnitModelData::SGMapUnitModelData()`
- `SGMapUnitModelData::getModelAction(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `SGMapUnitModelData::~SGMapUnitModelData()`

## SGMapUnitObj

- `SGMapUnitObj::ChangeState(MAP_UNIT_STATES)`
- `SGMapUnitObj::SGMapUnitObj()`
- `SGMapUnitObj::backToResumePos()`
- `SGMapUnitObj::cancelMoveAct()`
- `SGMapUnitObj::chaseTagLegion(SGLegion*)`
- `SGMapUnitObj::clearCurTagLegion()`
- `SGMapUnitObj::createMapUnit(SGMergeMap*, SGLegion*)`
- `SGMapUnitObj::escapeTagLegion(SGLegion*)`
- `SGMapUnitObj::executeLegionMoveNavMash(cocos2d::Vec2 const&)`
- `SGMapUnitObj::feedAStep()`
- `SGMapUnitObj::getTouchTestRect()`
- `SGMapUnitObj::initUnit(SGMergeMap*, SGLegion*)`
- `SGMapUnitObj::isUnitInGuardArea()`
- `SGMapUnitObj::moveToMapPos(cocos2d::Vec2 const&)`
- `SGMapUnitObj::moveToTagMapPosByNavMash(cocos2d::Vec2 const&)`
- `SGMapUnitObj::onBreakStepFinished()`
- `SGMapUnitObj::onCatchTagLegion()`
- `SGMapUnitObj::onExcuteMoveAct(float)`
- `SGMapUnitObj::onFrameIndexChanged(int)`
- `SGMapUnitObj::onHandingUnitMapAction()`
- `SGMapUnitObj::onIntNavMashStepFinished()`
- `SGMapUnitObj::onJoinBattleStepFinished()`
- `SGMapUnitObj::onLastFramePlayed()`
- `SGMapUnitObj::onMapUnitDisappeared()`
- `SGMapUnitObj::onMoveActFinished()`
- `SGMapUnitObj::onMoveActStepFinished()`
- `SGMapUnitObj::onMoveToNextPos(cocos2d::Vec2 const&, cocos2d::Vec2 const&)`
- `SGMapUnitObj::onNavMashMoveActFinished()`
- `SGMapUnitObj::onNavMashStepFinished()`
- `SGMapUnitObj::onReachBattleField()`
- `SGMapUnitObj::onReachBreakPoint()`
- `SGMapUnitObj::playAction(MAP_UNIT_ACTIONS)`
- `SGMapUnitObj::playAnimatAction(char const*, bool)`
- `SGMapUnitObj::removeSelfLater()`
- `SGMapUnitObj::setCurFrame(int)`
- `SGMapUnitObj::setCurMapPos(cocos2d::Vec2 const&)`
- `SGMapUnitObj::setIsFaceLeft(bool)`
- `SGMapUnitObj::startWandering(cocos2d::Vec2 const&, float)`
- `SGMapUnitObj::toJoinBattle(SGWarband*)`
- `SGMapUnitObj::update(float)`
- `SGMapUnitObj::updateUnit()`
- `SGMapUnitObj::~SGMapUnitObj()`

## SGMergeMap

- `SGMergeMap::SGMergeMap()`
- `SGMergeMap::addCloudToScene(bool)`
- `SGMergeMap::addMapUnit(SGMapUnitObj*)`
- `SGMergeMap::cleanUpScene()`
- `SGMergeMap::createMergeMap(int, bool)`
- `SGMergeMap::getCellMapFile(int, int)`
- `SGMergeMap::getNavStepsToTagPos(cocos2d::Vec2 const&, cocos2d::Vec2 const&, cocos2d::Vector<AEVec3Data*>&)`
- `SGMergeMap::getNearestEnemyUnitForTag(SGMapUnitObj*, float)`
- `SGMergeMap::getRandomCloudsPos(float, float, float, float)`
- `SGMergeMap::getTagAreaPV(cocos2d::Vec2 const&, float, float)`
- `SGMergeMap::getTagMapPosPV(cocos2d::Vec2 const&)`
- `SGMergeMap::getTagMapPosTR(cocos2d::Vec2 const&)`
- `SGMergeMap::getTagPosMapCell(cocos2d::Vec2 const&)`
- `SGMergeMap::getTagPosSiteObj(cocos2d::Vec2 const&)`
- `SGMergeMap::getTagZByPos(cocos2d::Vec2 const&)`
- `SGMergeMap::initCloudsEffect()`
- `SGMergeMap::initMergeMap(int, bool)`
- `SGMergeMap::mapPaused()`
- `SGMergeMap::mapResume()`
- `SGMergeMap::onEnter()`
- `SGMergeMap::onExit()`
- `SGMergeMap::onSecondEvent(float)`
- `SGMergeMap::preloadTagCell(SGMapCellData*, bool)`
- `SGMergeMap::removeMapUnit(SGMapUnitObj*)`
- `SGMergeMap::setCamera(int, cocos2d::Vec2 const&, cocos2d::Node*, float)`
- `SGMergeMap::setGameTimeScale(float)`
- `SGMergeMap::setMapSelMark(int, cocos2d::Vec2 const&, cocos2d::Node*)`
- `SGMergeMap::setViewPos(cocos2d::Vec2 const&)`
- `SGMergeMap::unloadTagCell(SGMapCellData*)`
- `SGMergeMap::update(float)`
- `SGMergeMap::updateCameraView(float)`
- `SGMergeMap::updateMapCells(cocos2d::Vec2 const&)`
- `SGMergeMap::~SGMergeMap()`

## SGModelAttActInfo

- `SGModelAttActInfo::SGModelAttActInfo()`
- `SGModelAttActInfo::~SGModelAttActInfo()`

## SGModelSkinInfo

- `SGModelSkinInfo::SGModelSkinInfo()`
- `SGModelSkinInfo::~SGModelSkinInfo()`

## SGRoleModel

- `SGRoleModel::SGRoleModel()`
- `SGRoleModel::create()`
- `SGRoleModel::~SGRoleModel()`

## SGRoleObj

- `SGRoleObj::ChangeState(ROLE_STATES)`
- `SGRoleObj::SGRoleObj()`
- `SGRoleObj::addBuff(SGBuffData*, int)`
- `SGRoleObj::addEffectToBf(cocos2d::Node*)`
- `SGRoleObj::attackTarget(SGRoleObj*)`
- `SGRoleObj::buffTick()`
- `SGRoleObj::changeHp(int)`
- `SGRoleObj::changeMorale(int)`
- `SGRoleObj::changeMp(int)`
- `SGRoleObj::changeUnitCamp(SGRoleObj*)`
- `SGRoleObj::chargeRun(float, float, float)`
- `SGRoleObj::chargeRunDone()`
- `SGRoleObj::checkAttackActions()`
- `SGRoleObj::excuteHoldPolicy(cocos2d::Vec2, float)`
- `SGRoleObj::faceToTag(SGRoleObj*)`
- `SGRoleObj::findNearestOne(cocos2d::Vector<SGRoleObj*>&, float)`
- `SGRoleObj::getBodyHitPos()`
- `SGRoleObj::getBodyPosByDir(cocos2d::Vec2)`
- `SGRoleObj::getBuffOverlay(BUFF_CODES)`
- `SGRoleObj::getCampColor()`
- `SGRoleObj::getCloseAttackableEnemy()`
- `SGRoleObj::getEscapePos()`
- `SGRoleObj::getExsitBuff(BUFF_CODES)`
- `SGRoleObj::getFinalDmgVal(int, float)`
- `SGRoleObj::getIsFaceToLeft()`
- `SGRoleObj::getIsSeledOn()`
- `SGRoleObj::getKingdom()`
- `SGRoleObj::getMaxHp()`
- `SGRoleObj::getMaxMp()`
- `SGRoleObj::getNearestEnemy(bool)`
- `SGRoleObj::getNearestFriend(bool)`
- `SGRoleObj::getNearestUnits(int, int)`
- `SGRoleObj::getNewFollowPos()`
- `SGRoleObj::getNextPassablePos()`
- `SGRoleObj::getNextStepToTagPos(cocos2d::Vec2 const&)`
- `SGRoleObj::getRealPosByCellPos(int, int)`
- `SGRoleObj::getRoleIntent()`
- `SGRoleObj::getRoleToPosDistance(cocos2d::Vec2 const&)`
- `SGRoleObj::getRoleToRoleDistance(SGRoleObj*)`
- `SGRoleObj::getSelMarkType()`
- `SGRoleObj::getShootTarget()`
- `SGRoleObj::getStepToTagPos(cocos2d::Vec2 const&, cocos2d::Vec2 const&)`
- `SGRoleObj::holdForWhile(float)`
- `SGRoleObj::initRole(int, SGBattleField*)`
- `SGRoleObj::intentUseSkill(int, SGRoleObj*, cocos2d::Vec2 const&)`
- `SGRoleObj::isActiveTarget(SGRoleObj*)`
- `SGRoleObj::isActiveUnit()`
- `SGRoleObj::isCouldAttackNow()`
- `SGRoleObj::isCouldShootOn(SGRoleObj*)`
- `SGRoleObj::isEnemy(SGRoleObj*)`
- `SGRoleObj::isFaceToTag(SGRoleObj*)`
- `SGRoleObj::isHaveBuff(bool)`
- `SGRoleObj::isInCloseRange(SGRoleObj*)`
- `SGRoleObj::isIntersectTo(cocos2d::Vec2 const&, SGRoleObj*)`
- `SGRoleObj::isTagPosPassable(cocos2d::Vec2 const&)`
- `SGRoleObj::loadArrow()`
- `SGRoleObj::moveAStep(cocos2d::Vec2 const&)`
- `SGRoleObj::onActionStepDone()`
- `SGRoleObj::onCastDone(bool)`
- `SGRoleObj::onChargeRunning(float)`
- `SGRoleObj::onDeadPlayedOver()`
- `SGRoleObj::onFrameEvent(cocostudio::timeline::Frame*)`
- `SGRoleObj::onLastFrameEvent()`
- `SGRoleObj::onMoveStepOver()`
- `SGRoleObj::onNormalAttackHited()`
- `SGRoleObj::onRoleAction()`
- `SGRoleObj::onRoleActionEvent(cocostudio::timeline::Frame*)`
- `SGRoleObj::onShootOut()`
- `SGRoleObj::onSkillAction()`
- `SGRoleObj::onSkillFinished()`
- `SGRoleObj::onSkillHitted()`
- `SGRoleObj::playAction(ROLE_ACTIONS)`
- `SGRoleObj::playAnimatAction(char const*, bool)`
- `SGRoleObj::playFlashEft(cocos2d::Node*, cocos2d::Vec2 const&, int)`
- `SGRoleObj::playHighLightFlash(cocos2d::Node*, cocos2d::Node*)`
- `SGRoleObj::removeAllBuffs()`
- `SGRoleObj::removeBuff(BUFF_CODES)`
- `SGRoleObj::removeTagEffect(cocos2d::Node*)`
- `SGRoleObj::resurrectionRole(float)`
- `SGRoleObj::roleAttackTo(SGRoleObj*)`
- `SGRoleObj::roleDeadDown()`
- `SGRoleObj::roleEscaped()`
- `SGRoleObj::roleGetComa(float)`
- `SGRoleObj::roleMoveTo(cocos2d::Vec2 const&)`
- `SGRoleObj::setAttackSelMark(bool)`
- `SGRoleObj::setCampColor(cocos2d::Color3B const&)`
- `SGRoleObj::setIsFaceToLeft(bool)`
- `SGRoleObj::setIsSeledOn(bool)`
- `SGRoleObj::setKingdom(SGKingdom*)`
- `SGRoleObj::setPosInBF(cocos2d::Vec2 const&)`
- `SGRoleObj::setRoleIntent(ROLE_INTENTS)`
- `SGRoleObj::shootTarget(SGRoleObj*)`
- `SGRoleObj::showHpBar(bool)`
- `SGRoleObj::startCasting(float)`
- `SGRoleObj::summonOutRole(float)`
- `SGRoleObj::underAttack(SGDamageInfo)`
- `SGRoleObj::update(float)`
- `SGRoleObj::updateMapMark(float, cocos2d::Vec2 const&)`
- `SGRoleObj::updateMapMarkPos()`
- `SGRoleObj::updateRoleBuffStates()`
- `SGRoleObj::updateRoleInfo()`
- `SGRoleObj::updateStatus()`
- `SGRoleObj::updateZorderInBF()`
- `SGRoleObj::~SGRoleObj()`

## SGSkillInfoData

- `SGSkillInfoData::SGSkillInfoData()`
- `SGSkillInfoData::getLimitLevel(int)`
- `SGSkillInfoData::getSkCD(int)`
- `SGSkillInfoData::getSkMp(int)`
- `SGSkillInfoData::getSkVal1(int)`
- `SGSkillInfoData::getSkVal2(int)`
- `SGSkillInfoData::getSkVal3(int)`
- `SGSkillInfoData::getSkVal4(int)`
- `SGSkillInfoData::getSkVal5(int)`
- `SGSkillInfoData::getSkillDesc(int, int)`
- `SGSkillInfoData::getSkillName(int)`
- `SGSkillInfoData::getSpCost(int)`
- `SGSkillInfoData::isMustEquipBowSkill()`
- `SGSkillInfoData::~SGSkillInfoData()`

## SGSkillPointData

- `SGSkillPointData::SGSkillPointData()`
- `SGSkillPointData::create(int, int)`
- `SGSkillPointData::getSkillInfo()`
- `SGSkillPointData::initSpData(int, int)`
- `SGSkillPointData::~SGSkillPointData()`

## SGSoldier

- `SGSoldier::ChangeState(ROLE_STATES)`
- `SGSoldier::SGSoldier()`
- `SGSoldier::create(SGUnitsData*, SGGeneral*, SGBattleField*)`
- `SGSoldier::getHealCDTime()`
- `SGSoldier::getHealManaCost()`
- `SGSoldier::initSoldier(SGUnitsData*, SGGeneral*, SGBattleField*)`
- `SGSoldier::onRoleActionEvent(cocostudio::timeline::Frame*)`
- `SGSoldier::onSkillAction()`
- `SGSoldier::onSkillFinished()`
- `SGSoldier::onSkillHitted()`
- `SGSoldier::playHealFlashEft(cocos2d::Node*, cocos2d::Vec2 const&, int)`
- `SGSoldier::playHealSkEft(cocos2d::Node*, cocos2d::Vec2 const&, int, float)`
- `SGSoldier::soldierUseSkill(int, SGRoleObj*, cocos2d::Vec2 const&)`
- `SGSoldier::update(float)`
- `SGSoldier::~SGSoldier()`

## SGUnitInfoData

- `SGUnitInfoData::SGUnitInfoData()`
- `SGUnitInfoData::getName(int)`
- `SGUnitInfoData::~SGUnitInfoData()`

## SGUnitsData

- `SGUnitsData::SGUnitsData(int)`
- `SGUnitsData::addExp(int)`
- `SGUnitsData::changeHP(int)`
- `SGUnitsData::changeMP(int)`
- `SGUnitsData::changeMorale(int)`
- `SGUnitsData::create(int)`
- `SGUnitsData::getDefeatExp()`
- `SGUnitsData::getIsEnableFight()`
- `SGUnitsData::getIsEnableUpgrade()`
- `SGUnitsData::getLevelUpExp()`
- `SGUnitsData::getWagesNum()`
- `SGUnitsData::setUnitType(int)`
- `SGUnitsData::updateStatus()`
- `SGUnitsData::upgradeUnit(int)`
- `SGUnitsData::~SGUnitsData()`

## SGWarband

- `SGWarband::SGWarband()`
- `SGWarband::battleOver(int)`
- `SGWarband::battleStart(SGLegion*, SGLegion*, int, int, int)`
- `SGWarband::checkIsWarOver()`
- `SGWarband::createWarband()`
- `SGWarband::dismissWarband()`
- `SGWarband::getCharLegion(SGCharacterData*)`
- `SGWarband::getFriendSide(SGLegion*)`
- `SGWarband::hideActAnimat()`
- `SGWarband::legionJoin(SGLegion*, bool, bool)`
- `SGWarband::legionQuit(SGLegion*)`
- `SGWarband::onAutoFightProgram(float)`
- `SGWarband::onCreateWarband()`
- `SGWarband::onFightOver()`
- `SGWarband::showActAnimat(cocos2d::Node*, int)`
- `SGWarband::startFight(SGCharacterData*, SGCharacterData*)`
- `SGWarband::updateWarband()`

## SHA1

- `SHA1::SHA1()`
- `SHA1::addBytes(unsigned char const*, int)`
- `SHA1::getDigest(unsigned char*, int)`
- `SHA1::hexPrinter(unsigned char*, int)`
- `SHA1::lrot(unsigned int, int)`
- `SHA1::process()`
- `SHA1::storeBigEndianUint32(unsigned char*, unsigned int)`
- `SHA1::~SHA1()`

## SceneManager

- `SceneManager::SceneManager()`
- `SceneManager::addManagedScene(BaseScene*)`
- `SceneManager::clearCurrentScene()`
- `SceneManager::getInstance()`
- `SceneManager::gotoScene(BaseScene*)`
- `SceneManager::removeManagedScene(BaseScene*)`
- `SceneManager::sendNotify(unsigned int, void*)`
- `SceneManager::setCurrentScene(BaseScene*)`
- `SceneManager::~SceneManager()`

## SkeletonNodeReader

- `SkeletonNodeReader::SkeletonNodeReader()`
- `SkeletonNodeReader::createInstance()`
- `SkeletonNodeReader::createNodeWithFlatBuffers(flatbuffers::Table const*)`
- `SkeletonNodeReader::destroyInstance()`
- `SkeletonNodeReader::getInstance()`
- `SkeletonNodeReader::~SkeletonNodeReader()`

## SphereTriangleDetector

- `SphereTriangleDetector::SphereTriangleDetector(btSphereShape*, btTriangleShape*, float)`
- `SphereTriangleDetector::collide(btVector3 const&, btVector3&, btVector3&, float&, float&, float)`
- `SphereTriangleDetector::facecontains(btVector3 const&, btVector3 const*, btVector3&)`
- `SphereTriangleDetector::getClosestPoints(btDiscreteCollisionDetectorInterface::ClosestPointInput const&, btDiscreteCollisionDetectorInterface::Result&, btIDebugDraw*, bool)`
- `SphereTriangleDetector::pointInTriangle(btVector3 const*, btVector3 const&, btVector3*)`

## SplashScene

- `SplashScene::gotoGameScene()`
- `SplashScene::init()`
- `SplashScene::runMain(float)`
- `SplashScene::scene()`

## StringTable

- `StringTable::StringTable()`
- `StringTable::getRC(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)`
- `StringTable::getRandomString()`
- `StringTable::getString(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)`
- `StringTable::loadRCFile()`
- `StringTable::loadSTFile()`
- `StringTable::reloadRsFiles()`
- `StringTable::~StringTable()`

## WMSBezierMoves

- `WMSBezierMoves::WMSBezierMoves(cocos2d::Vec2*, unsigned short)`
- `WMSBezierMoves::getCurMovePos(float)`
- `WMSBezierMoves::getMoveLength()`
- `WMSBezierMoves::~WMSBezierMoves()`

## WMSLineMoves

- `WMSLineMoves::WMSLineMoves(float, cocos2d::Vec2 const&, cocos2d::Vec2 const&)`
- `WMSLineMoves::getCurMovePos(float)`
- `WMSLineMoves::~WMSLineMoves()`

## WMSMoves

- `WMSMoves::WMSMoves(float)`
- `WMSMoves::getCurMovePos(float)`
- `WMSMoves::~WMSMoves()`

## __cxxabiv1

- `__cxxabiv1::__terminate(void (*)())`
- `__cxxabiv1::__unexpected(void (*)())`

## __cxxabiv1::__class_type_info

- `__cxxabiv1::__class_type_info::__do_catch(std::type_info const*, void**, unsigned int) const`
- `__cxxabiv1::__class_type_info::__do_dyncast(int, __cxxabiv1::__class_type_info::__sub_kind, __cxxabiv1::__class_type_info const*, void const*, __cxxabiv1::__class_type_info const*, void const*, __cxxabiv1::__class_type_info::__dyncast_result&) const`
- `__cxxabiv1::__class_type_info::__do_find_public_src(int, void const*, __cxxabiv1::__class_type_info const*, void const*) const`
- `__cxxabiv1::__class_type_info::__do_upcast(__cxxabiv1::__class_type_info const*, void const*, __cxxabiv1::__class_type_info::__upcast_result&) const`
- `__cxxabiv1::__class_type_info::__do_upcast(__cxxabiv1::__class_type_info const*, void**) const`
- `__cxxabiv1::__class_type_info::~__class_type_info()`

## __cxxabiv1::__forced_unwind

- `__cxxabiv1::__forced_unwind::~__forced_unwind()`

## __cxxabiv1::__foreign_exception

- `__cxxabiv1::__foreign_exception::~__foreign_exception()`

## __cxxabiv1::__function_type_info

- `__cxxabiv1::__function_type_info::__is_function_p() const`
- `__cxxabiv1::__function_type_info::~__function_type_info()`

## __cxxabiv1::__fundamental_type_info

- `__cxxabiv1::__fundamental_type_info::~__fundamental_type_info()`

## __cxxabiv1::__pbase_type_info

- `__cxxabiv1::__pbase_type_info::__do_catch(std::type_info const*, void**, unsigned int) const`
- `__cxxabiv1::__pbase_type_info::~__pbase_type_info()`

## __cxxabiv1::__pointer_type_info

- `__cxxabiv1::__pointer_type_info::__is_pointer_p() const`
- `__cxxabiv1::__pointer_type_info::__pointer_catch(__cxxabiv1::__pbase_type_info const*, void**, unsigned int) const`
- `__cxxabiv1::__pointer_type_info::~__pointer_type_info()`

## __cxxabiv1::__si_class_type_info

- `__cxxabiv1::__si_class_type_info::__do_dyncast(int, __cxxabiv1::__class_type_info::__sub_kind, __cxxabiv1::__class_type_info const*, void const*, __cxxabiv1::__class_type_info const*, void const*, __cxxabiv1::__class_type_info::__dyncast_result&) const`
- `__cxxabiv1::__si_class_type_info::__do_find_public_src(int, void const*, __cxxabiv1::__class_type_info const*, void const*) const`
- `__cxxabiv1::__si_class_type_info::__do_upcast(__cxxabiv1::__class_type_info const*, void const*, __cxxabiv1::__class_type_info::__upcast_result&) const`
- `__cxxabiv1::__si_class_type_info::~__si_class_type_info()`

## __cxxabiv1::__vmi_class_type_info

- `__cxxabiv1::__vmi_class_type_info::__do_dyncast(int, __cxxabiv1::__class_type_info::__sub_kind, __cxxabiv1::__class_type_info const*, void const*, __cxxabiv1::__class_type_info const*, void const*, __cxxabiv1::__class_type_info::__dyncast_result&) const`
- `__cxxabiv1::__vmi_class_type_info::__do_find_public_src(int, void const*, __cxxabiv1::__class_type_info const*, void const*) const`
- `__cxxabiv1::__vmi_class_type_info::__do_upcast(__cxxabiv1::__class_type_info const*, void const*, __cxxabiv1::__class_type_info::__upcast_result&) const`
- `__cxxabiv1::__vmi_class_type_info::~__vmi_class_type_info()`

## cocosplay

- `cocosplay::fileExists(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `cocosplay::getGameRoot()`
- `cocosplay::isDemo()`
- `cocosplay::isEnabled()`
- `cocosplay::lazyInit()`
- `cocosplay::notifyDemoEnded()`
- `cocosplay::notifyFileLoaded(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `cocosplay::purgeCachedByFile(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`
- `cocosplay::purgeCachedEntries()`
- `cocosplay::updateAssets(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)`

## dtCrowd

- `dtCrowd::addAgent(float const*, dtCrowdAgentParams const*)`
- `dtCrowd::checkPathValidity(dtCrowdAgent**, int, float)`
- `dtCrowd::dtCrowd()`
- `dtCrowd::getActiveAgents(dtCrowdAgent**, int)`
- `dtCrowd::getAgent(int)`
- `dtCrowd::getAgentCount() const`
- `dtCrowd::getEditableAgent(int)`
- `dtCrowd::getEditableAgentAnim(int)`
- `dtCrowd::getObstacleAvoidanceParams(int) const`
- `dtCrowd::init(int, float, dtNavMesh*)`
- `dtCrowd::purge()`
- `dtCrowd::removeAgent(int)`
- `dtCrowd::requestMoveTarget(int, unsigned int, float const*)`
- `dtCrowd::requestMoveTargetReplan(int, unsigned int, float const*)`
- `dtCrowd::requestMoveVelocity(int, float const*)`
- `dtCrowd::resetMoveTarget(int)`
- `dtCrowd::setObstacleAvoidanceParams(int, dtObstacleAvoidanceParams const*)`
- `dtCrowd::update(float, dtCrowdAgentDebugInfo*)`
- `dtCrowd::updateAgentParameters(int, dtCrowdAgentParams const*)`
- `dtCrowd::updateMoveRequest(float)`
- `dtCrowd::updateTopologyOptimization(dtCrowdAgent**, int, float)`
- `dtCrowd::~dtCrowd()`

## dtLocalBoundary

- `dtLocalBoundary::addSegment(float, float const*)`
- `dtLocalBoundary::dtLocalBoundary()`
- `dtLocalBoundary::isValid(dtNavMeshQuery*, dtQueryFilter const*)`
- `dtLocalBoundary::reset()`
- `dtLocalBoundary::update(unsigned int, float const*, float, dtNavMeshQuery*, dtQueryFilter const*)`
- `dtLocalBoundary::~dtLocalBoundary()`

## dtNavMesh

- `dtNavMesh::addTile(unsigned char*, int, int, unsigned int, unsigned int*)`
- `dtNavMesh::baseOffMeshLinks(dtMeshTile*)`
- `dtNavMesh::calcTileLoc(float const*, int*, int*) const`
- `dtNavMesh::closestPointOnPoly(unsigned int, float const*, float*, bool*) const`
- `dtNavMesh::connectExtLinks(dtMeshTile*, dtMeshTile*, int)`
- `dtNavMesh::connectExtOffMeshLinks(dtMeshTile*, dtMeshTile*, int)`
- `dtNavMesh::connectIntLinks(dtMeshTile*)`
- `dtNavMesh::dtNavMesh()`
- `dtNavMesh::findConnectingPolys(float const*, float const*, dtMeshTile const*, int, unsigned int*, float*, int) const`
- `dtNavMesh::findNearestPolyInTile(dtMeshTile const*, float const*, float const*, float*) const`
- `dtNavMesh::getMaxTiles() const`
- `dtNavMesh::getNeighbourTilesAt(int, int, int, dtMeshTile**, int) const`
- `dtNavMesh::getOffMeshConnectionByRef(unsigned int) const`
- `dtNavMesh::getOffMeshConnectionPolyEndPoints(unsigned int, unsigned int, float*, float*) const`
- `dtNavMesh::getParams() const`
- `dtNavMesh::getPolyArea(unsigned int, unsigned char*) const`
- `dtNavMesh::getPolyFlags(unsigned int, unsigned short*) const`
- `dtNavMesh::getPolyRefBase(dtMeshTile const*) const`
- `dtNavMesh::getTile(int)`
- `dtNavMesh::getTile(int) const`
- `dtNavMesh::getTileAndPolyByRef(unsigned int, dtMeshTile const**, dtPoly const**) const`
- `dtNavMesh::getTileAndPolyByRefUnsafe(unsigned int, dtMeshTile const**, dtPoly const**) const`
- `dtNavMesh::getTileAt(int, int, int) const`
- `dtNavMesh::getTileByRef(unsigned int) const`
- `dtNavMesh::getTileRef(dtMeshTile const*) const`
- `dtNavMesh::getTileRefAt(int, int, int) const`
- `dtNavMesh::getTileStateSize(dtMeshTile const*) const`
- `dtNavMesh::getTilesAt(int, int, dtMeshTile const**, int) const`
- `dtNavMesh::getTilesAt(int, int, dtMeshTile**, int) const`
- `dtNavMesh::init(dtNavMeshParams const*)`
- `dtNavMesh::init(unsigned char*, int, int)`
- `dtNavMesh::isValidPolyRef(unsigned int) const`
- `dtNavMesh::queryPolygonsInTile(dtMeshTile const*, float const*, float const*, unsigned int*, int) const`
- `dtNavMesh::removeTile(unsigned int, unsigned char**, int*)`
- `dtNavMesh::restoreTileState(dtMeshTile*, unsigned char const*, int)`
- `dtNavMesh::setPolyArea(unsigned int, unsigned char)`
- `dtNavMesh::setPolyFlags(unsigned int, unsigned short)`
- `dtNavMesh::storeTileState(dtMeshTile const*, unsigned char*, int) const`
- `dtNavMesh::unconnectExtLinks(dtMeshTile*, dtMeshTile*)`
- `dtNavMesh::~dtNavMesh()`

## dtNavMeshQuery

- `dtNavMeshQuery::appendPortals(int, int, float const*, unsigned int const*, float*, unsigned char*, unsigned int*, int*, int, int) const`
- `dtNavMeshQuery::appendVertex(float const*, unsigned char, unsigned int, float*, unsigned char*, unsigned int*, int*, int) const`
- `dtNavMeshQuery::closestPointOnPoly(unsigned int, float const*, float*, bool*) const`
- `dtNavMeshQuery::closestPointOnPolyBoundary(unsigned int, float const*, float*) const`
- `dtNavMeshQuery::dtNavMeshQuery()`
- `dtNavMeshQuery::finalizeSlicedFindPath(unsigned int*, int*, int)`
- `dtNavMeshQuery::finalizeSlicedFindPathPartial(unsigned int const*, int, unsigned int*, int*, int)`
- `dtNavMeshQuery::findDistanceToWall(unsigned int, float const*, float, dtQueryFilter const*, float*, float*, float*) const`
- `dtNavMeshQuery::findLocalNeighbourhood(unsigned int, float const*, float, dtQueryFilter const*, unsigned int*, unsigned int*, int*, int) const`
- `dtNavMeshQuery::findNearestPoly(float const*, float const*, dtQueryFilter const*, unsigned int*, float*) const`
- `dtNavMeshQuery::findPath(unsigned int, unsigned int, float const*, float const*, dtQueryFilter const*, unsigned int*, int*, int) const`
- `dtNavMeshQuery::findPolysAroundCircle(unsigned int, float const*, float, dtQueryFilter const*, unsigned int*, unsigned int*, float*, int*, int) const`
- `dtNavMeshQuery::findPolysAroundShape(unsigned int, float const*, int, dtQueryFilter const*, unsigned int*, unsigned int*, float*, int*, int) const`
- `dtNavMeshQuery::findRandomPoint(dtQueryFilter const*, float (*)(), unsigned int*, float*) const`
- `dtNavMeshQuery::findRandomPointAroundCircle(unsigned int, float const*, float, dtQueryFilter const*, float (*)(), unsigned int*, float*) const`
- `dtNavMeshQuery::findStraightPath(float const*, float const*, unsigned int const*, int, float*, unsigned char*, unsigned int*, int*, int, int) const`
- `dtNavMeshQuery::getEdgeMidPoint(unsigned int, dtPoly const*, dtMeshTile const*, unsigned int, dtPoly const*, dtMeshTile const*, float*) const`
- `dtNavMeshQuery::getEdgeMidPoint(unsigned int, unsigned int, float*) const`
- `dtNavMeshQuery::getPolyHeight(unsigned int, float const*, float*) const`
- `dtNavMeshQuery::getPolyWallSegments(unsigned int, dtQueryFilter const*, float*, unsigned int*, int*, int) const`
- `dtNavMeshQuery::getPortalPoints(unsigned int, dtPoly const*, dtMeshTile const*, unsigned int, dtPoly const*, dtMeshTile const*, float*, float*) const`
- `dtNavMeshQuery::getPortalPoints(unsigned int, unsigned int, float*, float*, unsigned char&, unsigned char&) const`
- `dtNavMeshQuery::init(dtNavMesh const*, int)`
- `dtNavMeshQuery::initSlicedFindPath(unsigned int, unsigned int, float const*, float const*, dtQueryFilter const*, unsigned int)`
- `dtNavMeshQuery::isInClosedList(unsigned int) const`
- `dtNavMeshQuery::isValidPolyRef(unsigned int, dtQueryFilter const*) const`
- `dtNavMeshQuery::moveAlongSurface(unsigned int, float const*, float const*, dtQueryFilter const*, float*, unsigned int*, int*, int) const`
- `dtNavMeshQuery::queryPolygons(float const*, float const*, dtQueryFilter const*, unsigned int*, int*, int) const`
- `dtNavMeshQuery::queryPolygonsInTile(dtMeshTile const*, float const*, float const*, dtQueryFilter const*, unsigned int*, int) const`
- `dtNavMeshQuery::raycast(unsigned int, float const*, float const*, dtQueryFilter const*, float*, float*, unsigned int*, int*, int) const`
- `dtNavMeshQuery::raycast(unsigned int, float const*, float const*, dtQueryFilter const*, unsigned int, dtRaycastHit*, unsigned int) const`
- `dtNavMeshQuery::updateSlicedFindPath(int, int*)`
- `dtNavMeshQuery::~dtNavMeshQuery()`

## dtNodePool

- `dtNodePool::clear()`
- `dtNodePool::dtNodePool(int, int)`
- `dtNodePool::findNode(unsigned int, unsigned char)`
- `dtNodePool::findNodes(unsigned int, dtNode**, int)`
- `dtNodePool::getNode(unsigned int, unsigned char)`
- `dtNodePool::~dtNodePool()`

## dtNodeQueue

- `dtNodeQueue::bubbleUp(int, dtNode*)`
- `dtNodeQueue::dtNodeQueue(int)`
- `dtNodeQueue::trickleDown(int, dtNode*)`
- `dtNodeQueue::~dtNodeQueue()`

## dtObstacleAvoidanceDebugData

- `dtObstacleAvoidanceDebugData::addSample(float const*, float, float, float, float, float, float)`
- `dtObstacleAvoidanceDebugData::dtObstacleAvoidanceDebugData()`
- `dtObstacleAvoidanceDebugData::init(int)`
- `dtObstacleAvoidanceDebugData::normalizeSamples()`
- `dtObstacleAvoidanceDebugData::reset()`
- `dtObstacleAvoidanceDebugData::~dtObstacleAvoidanceDebugData()`

## dtObstacleAvoidanceQuery

- `dtObstacleAvoidanceQuery::addCircle(float const*, float, float const*, float const*)`
- `dtObstacleAvoidanceQuery::addSegment(float const*, float const*)`
- `dtObstacleAvoidanceQuery::dtObstacleAvoidanceQuery()`
- `dtObstacleAvoidanceQuery::init(int, int)`
- `dtObstacleAvoidanceQuery::prepare(float const*, float const*)`
- `dtObstacleAvoidanceQuery::processSample(float const*, float, float const*, float, float const*, float const*, float, dtObstacleAvoidanceDebugData*)`
- `dtObstacleAvoidanceQuery::reset()`
- `dtObstacleAvoidanceQuery::sampleVelocityAdaptive(float const*, float, float, float const*, float const*, float*, dtObstacleAvoidanceParams const*, dtObstacleAvoidanceDebugData*)`
- `dtObstacleAvoidanceQuery::sampleVelocityGrid(float const*, float, float, float const*, float const*, float*, dtObstacleAvoidanceParams const*, dtObstacleAvoidanceDebugData*)`
- `dtObstacleAvoidanceQuery::~dtObstacleAvoidanceQuery()`

## dtPathCorridor

- `dtPathCorridor::dtPathCorridor()`
- `dtPathCorridor::findCorners(float*, unsigned char*, unsigned int*, int, dtNavMeshQuery*, dtQueryFilter const*)`
- `dtPathCorridor::fixPathStart(unsigned int, float const*)`
- `dtPathCorridor::init(int)`
- `dtPathCorridor::isValid(int, dtNavMeshQuery*, dtQueryFilter const*)`
- `dtPathCorridor::moveOverOffmeshConnection(unsigned int, unsigned int*, float*, float*, dtNavMeshQuery*)`
- `dtPathCorridor::movePosition(float const*, dtNavMeshQuery*, dtQueryFilter const*)`
- `dtPathCorridor::moveTargetPosition(float const*, dtNavMeshQuery*, dtQueryFilter const*)`
- `dtPathCorridor::optimizePathTopology(dtNavMeshQuery*, dtQueryFilter const*)`
- `dtPathCorridor::optimizePathVisibility(float const*, float, dtNavMeshQuery*, dtQueryFilter const*)`
- `dtPathCorridor::reset(unsigned int, float const*)`
- `dtPathCorridor::setCorridor(float const*, unsigned int const*, int)`
- `dtPathCorridor::trimInvalidPath(unsigned int, float const*, dtNavMeshQuery*, dtQueryFilter const*)`
- `dtPathCorridor::~dtPathCorridor()`

## dtPathQueue

- `dtPathQueue::dtPathQueue()`
- `dtPathQueue::getPathResult(unsigned int, unsigned int*, int*, int)`
- `dtPathQueue::getRequestStatus(unsigned int) const`
- `dtPathQueue::init(int, int, dtNavMesh*)`
- `dtPathQueue::purge()`
- `dtPathQueue::request(unsigned int, unsigned int, float const*, float const*, dtQueryFilter const*)`
- `dtPathQueue::update(int)`
- `dtPathQueue::~dtPathQueue()`

## dtProximityGrid

- `dtProximityGrid::addItem(unsigned short, float, float, float, float)`
- `dtProximityGrid::clear()`
- `dtProximityGrid::dtProximityGrid()`
- `dtProximityGrid::getItemCountAt(int, int) const`
- `dtProximityGrid::init(int, float)`
- `dtProximityGrid::queryItems(float, float, float, float, unsigned short*, int) const`
- `dtProximityGrid::~dtProximityGrid()`

## dtQueryFilter

- `dtQueryFilter::dtQueryFilter()`

## dtTileCache

- `dtTileCache::addObstacle(float const*, float, float, unsigned int*)`
- `dtTileCache::addTile(unsigned char*, int, unsigned char, unsigned int*)`
- `dtTileCache::buildNavMeshTile(unsigned int, dtNavMesh*)`
- `dtTileCache::buildNavMeshTilesAt(int, int, dtNavMesh*)`
- `dtTileCache::calcTightTileBounds(dtTileCacheLayerHeader const*, float*, float*) const`
- `dtTileCache::dtTileCache()`
- `dtTileCache::getObstacleBounds(dtTileCacheObstacle const*, float*, float*) const`
- `dtTileCache::getObstacleByRef(unsigned int)`
- `dtTileCache::getObstacleRef(dtTileCacheObstacle const*) const`
- `dtTileCache::getTileAt(int, int, int)`
- `dtTileCache::getTileByRef(unsigned int) const`
- `dtTileCache::getTileRef(dtCompressedTile const*) const`
- `dtTileCache::getTilesAt(int, int, unsigned int*, int) const`
- `dtTileCache::init(dtTileCacheParams const*, dtTileCacheAlloc*, dtTileCacheCompressor*, dtTileCacheMeshProcess*)`
- `dtTileCache::queryTiles(float const*, float const*, unsigned int*, int*, int) const`
- `dtTileCache::removeObstacle(unsigned int)`
- `dtTileCache::removeTile(unsigned int, unsigned char**, int*)`
- `dtTileCache::update(float, dtNavMesh*)`
- `dtTileCache::~dtTileCache()`

## duDebugDraw

- `duDebugDraw::~duDebugDraw()`

## duDisplayList

- `duDisplayList::begin(duDebugDrawPrimitives, float)`
- `duDisplayList::clear()`
- `duDisplayList::depthMask(bool)`
- `duDisplayList::draw(duDebugDraw*)`
- `duDisplayList::duDisplayList(int)`
- `duDisplayList::end()`
- `duDisplayList::resize(int)`
- `duDisplayList::vertex(float const*, unsigned int)`
- `duDisplayList::vertex(float, float, float, unsigned int)`
- `duDisplayList::~duDisplayList()`

## llvm

- `llvm::ConvertCodePointToUTF8(unsigned int, char*&)`
- `llvm::ConvertUTF8toWide(unsigned int, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, char*&, unsigned char const*&)`
- `llvm::convertUTF16ToUTF8String(std::basic_string<char16_t, std::char_traits<char16_t>, std::allocator<char16_t> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> >&)`
- `llvm::hasUTF16ByteOrderMark(char const*, unsigned int)`

## p2t

- `p2t::InScanArea(p2t::Point const&, p2t::Point const&, p2t::Point const&, p2t::Point const&)`
- `p2t::Orient2d(p2t::Point const&, p2t::Point const&, p2t::Point const&)`

## p2t::AdvancingFront

- `p2t::AdvancingFront::AdvancingFront(p2t::Node&, p2t::Node&)`
- `p2t::AdvancingFront::FindSearchNode(double)`
- `p2t::AdvancingFront::LocateNode(double)`
- `p2t::AdvancingFront::LocatePoint(p2t::Point const*)`
- `p2t::AdvancingFront::~AdvancingFront()`

## p2t::CDT

- `p2t::CDT::AddHole(std::vector<p2t::Point*, std::allocator<p2t::Point*> > const&)`
- `p2t::CDT::AddPoint(p2t::Point*)`
- `p2t::CDT::CDT(std::vector<p2t::Point*, std::allocator<p2t::Point*> > const&)`
- `p2t::CDT::GetMap()`
- `p2t::CDT::GetTriangles()`
- `p2t::CDT::Triangulate()`
- `p2t::CDT::~CDT()`

## p2t::Sweep

- `p2t::Sweep::Angle(p2t::Point const*, p2t::Point const*, p2t::Point const*) const`
- `p2t::Sweep::AngleExceeds90Degrees(p2t::Point const*, p2t::Point const*, p2t::Point const*) const`
- `p2t::Sweep::AngleExceedsPlus90DegreesOrIsNegative(p2t::Point const*, p2t::Point const*, p2t::Point const*) const`
- `p2t::Sweep::BasinAngle(p2t::Node const&) const`
- `p2t::Sweep::EdgeEvent(p2t::SweepContext&, p2t::Edge*, p2t::Node*)`
- `p2t::Sweep::EdgeEvent(p2t::SweepContext&, p2t::Point&, p2t::Point&, p2t::Triangle*, p2t::Point&)`
- `p2t::Sweep::Fill(p2t::SweepContext&, p2t::Node&)`
- `p2t::Sweep::FillAdvancingFront(p2t::SweepContext&, p2t::Node&)`
- `p2t::Sweep::FillBasin(p2t::SweepContext&, p2t::Node&)`
- `p2t::Sweep::FillBasinReq(p2t::SweepContext&, p2t::Node*)`
- `p2t::Sweep::FillEdgeEvent(p2t::SweepContext&, p2t::Edge*, p2t::Node*)`
- `p2t::Sweep::FillLeftAboveEdgeEvent(p2t::SweepContext&, p2t::Edge*, p2t::Node*)`
- `p2t::Sweep::FillLeftBelowEdgeEvent(p2t::SweepContext&, p2t::Edge*, p2t::Node&)`
- `p2t::Sweep::FillLeftConcaveEdgeEvent(p2t::SweepContext&, p2t::Edge*, p2t::Node&)`
- `p2t::Sweep::FillLeftConvexEdgeEvent(p2t::SweepContext&, p2t::Edge*, p2t::Node&)`
- `p2t::Sweep::FillRightAboveEdgeEvent(p2t::SweepContext&, p2t::Edge*, p2t::Node*)`
- `p2t::Sweep::FillRightBelowEdgeEvent(p2t::SweepContext&, p2t::Edge*, p2t::Node&)`
- `p2t::Sweep::FillRightConcaveEdgeEvent(p2t::SweepContext&, p2t::Edge*, p2t::Node&)`
- `p2t::Sweep::FillRightConvexEdgeEvent(p2t::SweepContext&, p2t::Edge*, p2t::Node&)`
- `p2t::Sweep::FinalizationPolygon(p2t::SweepContext&)`
- `p2t::Sweep::FlipEdgeEvent(p2t::SweepContext&, p2t::Point&, p2t::Point&, p2t::Triangle*, p2t::Point&)`
- `p2t::Sweep::FlipScanEdgeEvent(p2t::SweepContext&, p2t::Point&, p2t::Point&, p2t::Triangle&, p2t::Triangle&, p2t::Point&)`
- `p2t::Sweep::HoleAngle(p2t::Node const&) const`
- `p2t::Sweep::Incircle(p2t::Point const&, p2t::Point const&, p2t::Point const&, p2t::Point const&) const`
- `p2t::Sweep::IsEdgeSideOfTriangle(p2t::Triangle&, p2t::Point&, p2t::Point&)`
- `p2t::Sweep::IsShallow(p2t::SweepContext&, p2t::Node&)`
- `p2t::Sweep::LargeHole_DontFill(p2t::Node const*) const`
- `p2t::Sweep::Legalize(p2t::SweepContext&, p2t::Triangle&)`
- `p2t::Sweep::NewFrontTriangle(p2t::SweepContext&, p2t::Point&, p2t::Node&)`
- `p2t::Sweep::NextFlipPoint(p2t::Point&, p2t::Point&, p2t::Triangle&, p2t::Point&)`
- `p2t::Sweep::NextFlipTriangle(p2t::SweepContext&, int, p2t::Triangle&, p2t::Triangle&, p2t::Point&, p2t::Point&)`
- `p2t::Sweep::PointEvent(p2t::SweepContext&, p2t::Point&)`
- `p2t::Sweep::RotateTrianglePair(p2t::Triangle&, p2t::Point&, p2t::Triangle&, p2t::Point&) const`
- `p2t::Sweep::SweepPoints(p2t::SweepContext&)`
- `p2t::Sweep::Triangulate(p2t::SweepContext&)`
- `p2t::Sweep::~Sweep()`

## p2t::SweepContext

- `p2t::SweepContext::AddHole(std::vector<p2t::Point*, std::allocator<p2t::Point*> > const&)`
- `p2t::SweepContext::AddPoint(p2t::Point*)`
- `p2t::SweepContext::AddToMap(p2t::Triangle*)`
- `p2t::SweepContext::CreateAdvancingFront(std::vector<p2t::Node*, std::allocator<p2t::Node*> > const&)`
- `p2t::SweepContext::GetMap()`
- `p2t::SweepContext::GetPoint(unsigned int)`
- `p2t::SweepContext::GetTriangles()`
- `p2t::SweepContext::InitEdges(std::vector<p2t::Point*, std::allocator<p2t::Point*> > const&)`
- `p2t::SweepContext::InitTriangulation()`
- `p2t::SweepContext::LocateNode(p2t::Point const&)`
- `p2t::SweepContext::MapTriangleToNodes(p2t::Triangle&)`
- `p2t::SweepContext::MeshClean(p2t::Triangle&)`
- `p2t::SweepContext::RemoveFromMap(p2t::Triangle*)`
- `p2t::SweepContext::RemoveNode(p2t::Node*)`
- `p2t::SweepContext::SweepContext(std::vector<p2t::Point*, std::allocator<p2t::Point*> > const&)`
- `p2t::SweepContext::~SweepContext()`

## p2t::Triangle

- `p2t::Triangle::Clear()`
- `p2t::Triangle::ClearDelunayEdges()`
- `p2t::Triangle::ClearNeighbor(p2t::Triangle const*)`
- `p2t::Triangle::ClearNeighbors()`
- `p2t::Triangle::DebugPrint()`
- `p2t::Triangle::EdgeIndex(p2t::Point const*, p2t::Point const*)`
- `p2t::Triangle::GetConstrainedEdgeCCW(p2t::Point const&)`
- `p2t::Triangle::GetConstrainedEdgeCW(p2t::Point const&)`
- `p2t::Triangle::GetDelunayEdgeCCW(p2t::Point const&)`
- `p2t::Triangle::GetDelunayEdgeCW(p2t::Point const&)`
- `p2t::Triangle::Index(p2t::Point const*)`
- `p2t::Triangle::Legalize(p2t::Point&)`
- `p2t::Triangle::Legalize(p2t::Point&, p2t::Point&)`
- `p2t::Triangle::MarkConstrainedEdge(int)`
- `p2t::Triangle::MarkConstrainedEdge(p2t::Edge&)`
- `p2t::Triangle::MarkConstrainedEdge(p2t::Point*, p2t::Point*)`
- `p2t::Triangle::MarkNeighbor(p2t::Point*, p2t::Point*, p2t::Triangle*)`
- `p2t::Triangle::MarkNeighbor(p2t::Triangle&)`
- `p2t::Triangle::NeighborAcross(p2t::Point const&)`
- `p2t::Triangle::NeighborCCW(p2t::Point const&)`
- `p2t::Triangle::NeighborCW(p2t::Point const&)`
- `p2t::Triangle::OppositePoint(p2t::Triangle&, p2t::Point const&)`
- `p2t::Triangle::PointCCW(p2t::Point const&)`
- `p2t::Triangle::PointCW(p2t::Point const&)`
- `p2t::Triangle::SetConstrainedEdgeCCW(p2t::Point const&, bool)`
- `p2t::Triangle::SetConstrainedEdgeCW(p2t::Point const&, bool)`
- `p2t::Triangle::SetDelunayEdgeCCW(p2t::Point const&, bool)`
- `p2t::Triangle::SetDelunayEdgeCW(p2t::Point const&, bool)`
- `p2t::Triangle::Triangle(p2t::Point&, p2t::Point&, p2t::Point&)`

## tinyobj

- `tinyobj::InitMaterial(tinyobj::material_t&)`
- `tinyobj::LoadMtl(std::map<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, int, std::less<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<std::pair<std::basic_string<char, std::char_traits<char>, std::allocator<char> > const, int> > >&, std::vector<tinyobj::material_t, std::allocator<tinyobj::material_t> >&, std::basic_istream<char, std::char_traits<char> >&)`
- `tinyobj::LoadObj(std::vector<tinyobj::shape_t, std::allocator<tinyobj::shape_t> >&, std::vector<tinyobj::material_t, std::allocator<tinyobj::material_t> >&, char const*, char const*)`
- `tinyobj::LoadObj(std::vector<tinyobj::shape_t, std::allocator<tinyobj::shape_t> >&, std::vector<tinyobj::material_t, std::allocator<tinyobj::material_t> >&, std::basic_istream<char, std::char_traits<char> >&, tinyobj::MaterialReader&)`

## tinyobj::MaterialFileReader

- `tinyobj::MaterialFileReader::operator()(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::vector<tinyobj::material_t, std::allocator<tinyobj::material_t> >&, std::map<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, int, std::less<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<std::pair<std::basic_string<char, std::char_traits<char>, std::allocator<char> > const, int> > >&)`

## tinyxml2::StrPair

- `tinyxml2::StrPair::CollapseWhitespace()`
- `tinyxml2::StrPair::GetStr()`
- `tinyxml2::StrPair::ParseName(char*)`
- `tinyxml2::StrPair::ParseText(char*, char const*, int)`
- `tinyxml2::StrPair::Reset()`
- `tinyxml2::StrPair::SetStr(char const*, int)`
- `tinyxml2::StrPair::~StrPair()`

## tinyxml2::XMLAttribute

- `tinyxml2::XMLAttribute::ParseDeep(char*, bool)`
- `tinyxml2::XMLAttribute::QueryBoolValue(bool*) const`
- `tinyxml2::XMLAttribute::QueryDoubleValue(double*) const`
- `tinyxml2::XMLAttribute::QueryFloatValue(float*) const`
- `tinyxml2::XMLAttribute::QueryIntValue(int*) const`
- `tinyxml2::XMLAttribute::QueryUnsignedValue(unsigned int*) const`
- `tinyxml2::XMLAttribute::SetAttribute(bool)`
- `tinyxml2::XMLAttribute::SetAttribute(char const*)`
- `tinyxml2::XMLAttribute::SetAttribute(double)`
- `tinyxml2::XMLAttribute::SetAttribute(float)`
- `tinyxml2::XMLAttribute::SetAttribute(int)`
- `tinyxml2::XMLAttribute::SetAttribute(unsigned int)`
- `tinyxml2::XMLAttribute::SetName(char const*)`

## tinyxml2::XMLComment

- `tinyxml2::XMLComment::Accept(tinyxml2::XMLVisitor*) const`
- `tinyxml2::XMLComment::ParseDeep(char*, tinyxml2::StrPair*)`
- `tinyxml2::XMLComment::ShallowClone(tinyxml2::XMLDocument*) const`
- `tinyxml2::XMLComment::ShallowEqual(tinyxml2::XMLNode const*) const`
- `tinyxml2::XMLComment::XMLComment(tinyxml2::XMLDocument*)`
- `tinyxml2::XMLComment::~XMLComment()`

## tinyxml2::XMLDeclaration

- `tinyxml2::XMLDeclaration::Accept(tinyxml2::XMLVisitor*) const`
- `tinyxml2::XMLDeclaration::ParseDeep(char*, tinyxml2::StrPair*)`
- `tinyxml2::XMLDeclaration::ShallowClone(tinyxml2::XMLDocument*) const`
- `tinyxml2::XMLDeclaration::ShallowEqual(tinyxml2::XMLNode const*) const`
- `tinyxml2::XMLDeclaration::XMLDeclaration(tinyxml2::XMLDocument*)`
- `tinyxml2::XMLDeclaration::~XMLDeclaration()`

## tinyxml2::XMLDocument

- `tinyxml2::XMLDocument::Accept(tinyxml2::XMLVisitor*) const`
- `tinyxml2::XMLDocument::Identify(char*, tinyxml2::XMLNode**)`
- `tinyxml2::XMLDocument::InitDocument()`
- `tinyxml2::XMLDocument::LoadFile(__sFILE*)`
- `tinyxml2::XMLDocument::LoadFile(char const*)`
- `tinyxml2::XMLDocument::NewComment(char const*)`
- `tinyxml2::XMLDocument::NewDeclaration(char const*)`
- `tinyxml2::XMLDocument::NewElement(char const*)`
- `tinyxml2::XMLDocument::NewText(char const*)`
- `tinyxml2::XMLDocument::NewUnknown(char const*)`
- `tinyxml2::XMLDocument::Parse(char const*, unsigned int)`
- `tinyxml2::XMLDocument::Print(tinyxml2::XMLPrinter*)`
- `tinyxml2::XMLDocument::PrintError() const`
- `tinyxml2::XMLDocument::SaveFile(__sFILE*, bool)`
- `tinyxml2::XMLDocument::SaveFile(char const*, bool)`
- `tinyxml2::XMLDocument::SetError(tinyxml2::XMLError, char const*, char const*)`
- `tinyxml2::XMLDocument::XMLDocument(bool, tinyxml2::Whitespace)`
- `tinyxml2::XMLDocument::~XMLDocument()`

## tinyxml2::XMLElement

- `tinyxml2::XMLElement::Accept(tinyxml2::XMLVisitor*) const`
- `tinyxml2::XMLElement::Attribute(char const*, char const*) const`
- `tinyxml2::XMLElement::DeleteAttribute(char const*)`
- `tinyxml2::XMLElement::FindAttribute(char const*)`
- `tinyxml2::XMLElement::FindAttribute(char const*) const`
- `tinyxml2::XMLElement::FindOrCreateAttribute(char const*)`
- `tinyxml2::XMLElement::GetText() const`
- `tinyxml2::XMLElement::ParseAttributes(char*)`
- `tinyxml2::XMLElement::ParseDeep(char*, tinyxml2::StrPair*)`
- `tinyxml2::XMLElement::QueryBoolText(bool*) const`
- `tinyxml2::XMLElement::QueryDoubleText(double*) const`
- `tinyxml2::XMLElement::QueryFloatText(float*) const`
- `tinyxml2::XMLElement::QueryIntText(int*) const`
- `tinyxml2::XMLElement::QueryUnsignedText(unsigned int*) const`
- `tinyxml2::XMLElement::ShallowClone(tinyxml2::XMLDocument*) const`
- `tinyxml2::XMLElement::ShallowEqual(tinyxml2::XMLNode const*) const`
- `tinyxml2::XMLElement::XMLElement(tinyxml2::XMLDocument*)`
- `tinyxml2::XMLElement::~XMLElement()`

## tinyxml2::XMLNode

- `tinyxml2::XMLNode::DeleteChild(tinyxml2::XMLNode*)`
- `tinyxml2::XMLNode::DeleteChildren()`
- `tinyxml2::XMLNode::FirstChildElement(char const*) const`
- `tinyxml2::XMLNode::InsertAfterChild(tinyxml2::XMLNode*, tinyxml2::XMLNode*)`
- `tinyxml2::XMLNode::InsertEndChild(tinyxml2::XMLNode*)`
- `tinyxml2::XMLNode::InsertFirstChild(tinyxml2::XMLNode*)`
- `tinyxml2::XMLNode::LastChildElement(char const*) const`
- `tinyxml2::XMLNode::NextSiblingElement(char const*) const`
- `tinyxml2::XMLNode::ParseDeep(char*, tinyxml2::StrPair*)`
- `tinyxml2::XMLNode::PreviousSiblingElement(char const*) const`
- `tinyxml2::XMLNode::SetValue(char const*, bool)`
- `tinyxml2::XMLNode::Unlink(tinyxml2::XMLNode*)`
- `tinyxml2::XMLNode::XMLNode(tinyxml2::XMLDocument*)`
- `tinyxml2::XMLNode::~XMLNode()`

## tinyxml2::XMLPrinter

- `tinyxml2::XMLPrinter::CloseElement()`
- `tinyxml2::XMLPrinter::OpenElement(char const*)`
- `tinyxml2::XMLPrinter::Print(char const*, ...)`
- `tinyxml2::XMLPrinter::PrintSpace(int)`
- `tinyxml2::XMLPrinter::PrintString(char const*, bool)`
- `tinyxml2::XMLPrinter::PushAttribute(char const*, bool)`
- `tinyxml2::XMLPrinter::PushAttribute(char const*, char const*)`
- `tinyxml2::XMLPrinter::PushAttribute(char const*, double)`
- `tinyxml2::XMLPrinter::PushAttribute(char const*, int)`
- `tinyxml2::XMLPrinter::PushAttribute(char const*, unsigned int)`
- `tinyxml2::XMLPrinter::PushComment(char const*)`
- `tinyxml2::XMLPrinter::PushDeclaration(char const*)`
- `tinyxml2::XMLPrinter::PushHeader(bool, bool)`
- `tinyxml2::XMLPrinter::PushText(bool)`
- `tinyxml2::XMLPrinter::PushText(char const*, bool)`
- `tinyxml2::XMLPrinter::PushText(double)`
- `tinyxml2::XMLPrinter::PushText(float)`
- `tinyxml2::XMLPrinter::PushText(int)`
- `tinyxml2::XMLPrinter::PushText(unsigned int)`
- `tinyxml2::XMLPrinter::PushUnknown(char const*)`
- `tinyxml2::XMLPrinter::SealElement()`
- `tinyxml2::XMLPrinter::Visit(tinyxml2::XMLComment const&)`
- `tinyxml2::XMLPrinter::Visit(tinyxml2::XMLDeclaration const&)`
- `tinyxml2::XMLPrinter::Visit(tinyxml2::XMLText const&)`
- `tinyxml2::XMLPrinter::Visit(tinyxml2::XMLUnknown const&)`
- `tinyxml2::XMLPrinter::VisitEnter(tinyxml2::XMLDocument const&)`
- `tinyxml2::XMLPrinter::VisitEnter(tinyxml2::XMLElement const&, tinyxml2::XMLAttribute const*)`
- `tinyxml2::XMLPrinter::VisitExit(tinyxml2::XMLElement const&)`
- `tinyxml2::XMLPrinter::XMLPrinter(__sFILE*, bool)`

## tinyxml2::XMLText

- `tinyxml2::XMLText::Accept(tinyxml2::XMLVisitor*) const`
- `tinyxml2::XMLText::ParseDeep(char*, tinyxml2::StrPair*)`
- `tinyxml2::XMLText::ShallowClone(tinyxml2::XMLDocument*) const`
- `tinyxml2::XMLText::ShallowEqual(tinyxml2::XMLNode const*) const`

## tinyxml2::XMLUnknown

- `tinyxml2::XMLUnknown::Accept(tinyxml2::XMLVisitor*) const`
- `tinyxml2::XMLUnknown::ParseDeep(char*, tinyxml2::StrPair*)`
- `tinyxml2::XMLUnknown::ShallowClone(tinyxml2::XMLDocument*) const`
- `tinyxml2::XMLUnknown::ShallowEqual(tinyxml2::XMLNode const*) const`
- `tinyxml2::XMLUnknown::XMLUnknown(tinyxml2::XMLDocument*)`
- `tinyxml2::XMLUnknown::~XMLUnknown()`

## tinyxml2::XMLUtil

- `tinyxml2::XMLUtil::ConvertUTF32ToUTF8(unsigned long, char*, int*)`
- `tinyxml2::XMLUtil::GetCharacterRef(char const*, char*, int*)`
- `tinyxml2::XMLUtil::ReadBOM(char const*, bool*)`
- `tinyxml2::XMLUtil::ToBool(char const*, bool*)`
- `tinyxml2::XMLUtil::ToDouble(char const*, double*)`
- `tinyxml2::XMLUtil::ToFloat(char const*, float*)`
- `tinyxml2::XMLUtil::ToInt(char const*, int*)`
- `tinyxml2::XMLUtil::ToStr(bool, char*, int)`
- `tinyxml2::XMLUtil::ToStr(double, char*, int)`
- `tinyxml2::XMLUtil::ToStr(float, char*, int)`
- `tinyxml2::XMLUtil::ToStr(int, char*, int)`
- `tinyxml2::XMLUtil::ToStr(unsigned int, char*, int)`
- `tinyxml2::XMLUtil::ToUnsigned(char const*, unsigned int*)`
