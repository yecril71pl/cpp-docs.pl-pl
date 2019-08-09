---
title: Klasa CPaneDivider
ms.date: 11/04/2016
f1_keywords:
- CPaneDivider
- AFXPANEDIVIDER/CPaneDivider
- AFXPANEDIVIDER/CPaneDivider::CPaneDivider
- AFXPANEDIVIDER/CPaneDivider::AddPaneContainer
- AFXPANEDIVIDER/CPaneDivider::AddPane
- AFXPANEDIVIDER/CPaneDivider::AddRecentPane
- AFXPANEDIVIDER/CPaneDivider::CalcExpectedDockedRect
- AFXPANEDIVIDER/CPaneDivider::CalcFixedLayout
- AFXPANEDIVIDER/CPaneDivider::CheckVisibility
- AFXPANEDIVIDER/CPaneDivider::CreateEx
- AFXPANEDIVIDER/CPaneDivider::DoesAllowDynInsertBefore
- AFXPANEDIVIDER/CPaneDivider::DoesContainFloatingPane
- AFXPANEDIVIDER/CPaneDivider::FindPaneContainer
- AFXPANEDIVIDER/CPaneDivider::FindTabbedPane
- AFXPANEDIVIDER/CPaneDivider::GetDefaultWidth
- AFXPANEDIVIDER/CPaneDivider::GetFirstPane
- AFXPANEDIVIDER/CPaneDivider::GetPaneDividerStyle
- AFXPANEDIVIDER/CPaneDivider::GetRootContainerRect
- AFXPANEDIVIDER/CPaneDivider::GetWidth
- AFXPANEDIVIDER/CPaneDivider::Init
- AFXPANEDIVIDER/CPaneDivider::InsertPane
- AFXPANEDIVIDER/CPaneDivider::IsAutoHideMode
- AFXPANEDIVIDER/CPaneDivider::IsDefault
- AFXPANEDIVIDER/CPaneDivider::IsHorizontal
- AFXPANEDIVIDER/CPaneDivider::Move
- AFXPANEDIVIDER/CPaneDivider::NotifyAboutRelease
- AFXPANEDIVIDER/CPaneDivider::OnShowPane
- AFXPANEDIVIDER/CPaneDivider::ReleaseEmptyPaneContainers
- AFXPANEDIVIDER/CPaneDivider::RemovePane
- AFXPANEDIVIDER/CPaneDivider::ReplacePane
- AFXPANEDIVIDER/CPaneDivider::RepositionPanes
- AFXPANEDIVIDER/CPaneDivider::Serialize
- AFXPANEDIVIDER/CPaneDivider::SetAutoHideMode
- AFXPANEDIVIDER/CPaneDivider::SetPaneContainerManager
- AFXPANEDIVIDER/CPaneDivider::ShowWindow
- AFXPANEDIVIDER/CPaneDivider::StoreRecentDockSiteInfo
- AFXPANEDIVIDER/CPaneDivider::StoreRecentTabRelatedInfo
- AFXPANEDIVIDER/CPaneDivider::GetPanes
- AFXPANEDIVIDER/CPaneDivider::GetPaneDividers
- AFXPANEDIVIDER/CPaneDivider::m_nDefaultWidth
- AFXPANEDIVIDER/CPaneDivider::m_pSliderRTC
helpviewer_keywords:
- CPaneDivider [MFC], CPaneDivider
- CPaneDivider [MFC], AddPaneContainer
- CPaneDivider [MFC], AddPane
- CPaneDivider [MFC], AddRecentPane
- CPaneDivider [MFC], CalcExpectedDockedRect
- CPaneDivider [MFC], CalcFixedLayout
- CPaneDivider [MFC], CheckVisibility
- CPaneDivider [MFC], CreateEx
- CPaneDivider [MFC], DoesAllowDynInsertBefore
- CPaneDivider [MFC], DoesContainFloatingPane
- CPaneDivider [MFC], FindPaneContainer
- CPaneDivider [MFC], FindTabbedPane
- CPaneDivider [MFC], GetDefaultWidth
- CPaneDivider [MFC], GetFirstPane
- CPaneDivider [MFC], GetPaneDividerStyle
- CPaneDivider [MFC], GetRootContainerRect
- CPaneDivider [MFC], GetWidth
- CPaneDivider [MFC], Init
- CPaneDivider [MFC], InsertPane
- CPaneDivider [MFC], IsAutoHideMode
- CPaneDivider [MFC], IsDefault
- CPaneDivider [MFC], IsHorizontal
- CPaneDivider [MFC], Move
- CPaneDivider [MFC], NotifyAboutRelease
- CPaneDivider [MFC], OnShowPane
- CPaneDivider [MFC], ReleaseEmptyPaneContainers
- CPaneDivider [MFC], RemovePane
- CPaneDivider [MFC], ReplacePane
- CPaneDivider [MFC], RepositionPanes
- CPaneDivider [MFC], Serialize
- CPaneDivider [MFC], SetAutoHideMode
- CPaneDivider [MFC], SetPaneContainerManager
- CPaneDivider [MFC], ShowWindow
- CPaneDivider [MFC], StoreRecentDockSiteInfo
- CPaneDivider [MFC], StoreRecentTabRelatedInfo
- CPaneDivider [MFC], GetPanes
- CPaneDivider [MFC], GetPaneDividers
- CPaneDivider [MFC], m_nDefaultWidth
- CPaneDivider [MFC], m_pSliderRTC
ms.assetid: 8e828a5d-232f-4127-b8e3-7fa45a7a476e
ms.openlocfilehash: d4888fbf2a95652b0a38adc8ecd059a7515636cb
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866112"
---
# <a name="cpanedivider-class"></a>Klasa CPaneDivider

Aby uzyskać więcej szczegółów, zobacz kod źródłowy znajdujący się w folderze **VC\\atlmfc\\src\\MFC** instalacji programu Visual Studio.

`CPaneDivider` Klasa dzieli dwa okienka, dzieli dwie grupy okienek lub oddziela grupę okienek od obszaru klienckiego okna głównego ramki.

## <a name="syntax"></a>Składnia

```
class CPaneDivider : public CBasePane
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPaneDivider::CPaneDivider](#cpanedivider)||

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPaneDivider::AddPaneContainer](#addpanecontainer)||
|[CPaneDivider:: Add— okienko](#addpane)||
|[CPaneDivider::AddRecentPane](#addrecentpane)||
|[CPaneDivider::CalcExpectedDockedRect](#calcexpecteddockedrect)||
|[CPaneDivider::CalcFixedLayout](#calcfixedlayout)|(Przesłania [CBasePane:: CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CPaneDivider::CheckVisibility](#checkvisibility)||
|[CPaneDivider::CreateEx](#createex)|(Przesłania [CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex).)|
|[CPaneDivider::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|(Przesłania [CBasePane::D oesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CPaneDivider::DoesContainFloatingPane](#doescontainfloatingpane)||
|[CPaneDivider::FindPaneContainer](#findpanecontainer)||
|[CPaneDivider::FindTabbedPane](#findtabbedpane)||
|[CPaneDivider::GetDefaultWidth](#getdefaultwidth)||
|[CPaneDivider::GetFirstPane](#getfirstpane)||
|[CPaneDivider::GetPaneDividerStyle](#getpanedividerstyle)||
|[CPaneDivider::GetRootContainerRect](#getrootcontainerrect)||
|[CPaneDivider:: getwidth](#getwidth)||
|[CPaneDivider::Init](#init)||
|[CPaneDivider::InsertPane](#insertpane)||
|[CPaneDivider::IsAutoHideMode](#isautohidemode)|(Przesłania [CBasePane::](../../mfc/reference/cbasepane-class.md#isautohidemode)autoukrywaniemode.)|
|[CPaneDivider:: IsDefault](#isdefault)||
|[CPaneDivider::IsHorizontal](#ishorizontal)|(Przesłania [CBasePane:: ispoziome](../../mfc/reference/cbasepane-class.md#ishorizontal))|
|[CPaneDivider:: Move](#move)||
|[CPaneDivider::NotifyAboutRelease](#notifyaboutrelease)||
|[CPaneDivider::OnShowPane](#onshowpane)||
|[CPaneDivider::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)||
|[CPaneDivider::RemovePane](#removepane)||
|[CPaneDivider::ReplacePane](#replacepane)||
|[CPaneDivider::RepositionPanes](#repositionpanes)||
|[CPaneDivider::Serialize](#serialize)|(Przesłania `CBasePane::Serialize`).|
|[CPaneDivider::SetAutoHideMode](#setautohidemode)||
|[CPaneDivider::SetPaneContainerManager](#setpanecontainermanager)||
|[CPaneDivider::ShowWindow](#showwindow)||
|[CPaneDivider::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||
|[CPaneDivider::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPaneDivider::GetPanes](#getpanes)|Zwraca listę okienek, które znajdują się w [klasie CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Tę metodę należy wywoływać tylko dla separatorów okienka domyślnego.|
|[CPaneDivider::GetPaneDividers](#getpanedividers)|Zwraca listę dzielników okienka, które znajdują się w [klasie CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Tę metodę należy wywoływać tylko dla separatorów okienka domyślnego.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPaneDivider::m_nDefaultWidth](#m_ndefaultwidth)|Określa domyślną szerokość (w pikselach) wszystkich podziałów okienka w aplikacji.|
|[CPaneDivider::m_pSliderRTC](#m_psliderrtc)|Przechowuje wskaźnik do informacji `CPaneDivider`o klasie środowiska uruchomieniowego dla obiektu pochodnego.|

## <a name="remarks"></a>Uwagi

Struktura tworzy `CPaneDivider` obiekty automatycznie, gdy okienko jest zadokowane.

Istnieją dwa typy rozdzielaczy okienka:

- domyślny podział okienka jest tworzony, gdy grupa okienka jest zadokowana po stronie okna głównego ramki. Separator okienka domyślnego zawiera wskaźnik do [klasy CPaneContainerManager](../../mfc/reference/cpanecontainermanager-class.md) i przekierowuje większość operacji w grupie okienek (takich jak zmienianie rozmiarów okienka lub dokowanie innego okienka lub kontenera) do Menedżera kontenerów. Każde okienko dokowania zachowuje wskaźnik do jego domyślnego rozdzielacza okienka.

- Podział okienka regularnego dzieli tylko dwa okienka w kontenerze. Aby uzyskać więcej informacji, zobacz [Klasa CPaneContainer](../../mfc/reference/cpanecontainer-class.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, `CPaneDivider` jak pobrać obiekt `CWorkspaceBar` z obiektu. Ten fragment kodu jest częścią [przykładu demonstracyjnego kart interfejsu MDI](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#5](../../mfc/reference/codesnippet/cpp/cpanedivider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp;[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CPaneDivider](../../mfc/reference/cpanedivider-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxPaneDivider. h

##  <a name="setautohidemode"></a>CPaneDivider:: autoukrywaniemode

```
void SetAutoHideMode(BOOL bMode);
```

### <a name="parameters"></a>Parametry

podczas *bMode*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="setpanecontainermanager"></a>CPaneDivider::SetPaneContainerManager

```
void SetPaneContainerManager(CPaneContainerManager* p);
```

### <a name="parameters"></a>Parametry

podczas *p*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="addpane"></a>CPaneDivider:: Add— okienko

```
virtual void AddPane(CDockablePane* pBar);
```

### <a name="parameters"></a>Parametry

podczas *pBar*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="addpanecontainer"></a>CPaneDivider::AddPaneContainer

```
virtual BOOL AddPaneContainer(
    CPaneContainerManager& barContainerManager,
    BOOL bOuterEdge);

virtual BOOL AddPaneContainer(
    CDockablePane* pTargetBar,
    CPaneContainerManager& barContainerManager,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Parametry

podczas *barContainerManager*<br/>
podczas *bOuterEdge*<br/>
podczas *pTargetBar*<br/>
podczas *dwAlignment*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="addrecentpane"></a>CPaneDivider::AddRecentPane

```
virtual CDockablePane* AddRecentPane(CDockablePane* pBar);
```

### <a name="parameters"></a>Parametry

podczas *pBar*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="calcexpecteddockedrect"></a>CPaneDivider::CalcExpectedDockedRect

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>Parametry

podczas *pWndToDock*<br/>
podczas *ptMouse*<br/>
podczas *rectResult*<br/>
podczas *bDrawTab*<br/>
podczas *ppTargetBar*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="calcfixedlayout"></a>CPaneDivider::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

podczas *bStretch*<br/>
podczas *bHorz*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="checkvisibility"></a>CPaneDivider::CheckVisibility

```
virtual BOOL CheckVisibility();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="cpanedivider"></a>CPaneDivider::CPaneDivider

```
CPaneDivider();

CPaneDivider(
    BOOL bDefaultSlider,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>Parametry

podczas *bDefaultSlider*<br/>
podczas *pParent*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="createex"></a>CPaneDivider::CreateEx

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Parametry

podczas *dwStyleEx*<br/>
podczas *dwStyle*<br/>
podczas *prostokąt*<br/>
podczas *pParentWnd*<br/>
podczas *NID*<br/>
podczas *pContext*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="doesallowdyninsertbefore"></a>CPaneDivider::D oesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="doescontainfloatingpane"></a>CPaneDivider::D oesContainFloatingPane

```
virtual BOOL DoesContainFloatingPane();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="findpanecontainer"></a>CPaneDivider::FindPaneContainer

```
CPaneContainer* FindPaneContainer(
    CDockablePane* pBar,
    BOOL& bLeftBar);
```

### <a name="parameters"></a>Parametry

podczas *pBar*<br/>
podczas *bLeftBar*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="findtabbedpane"></a>CPaneDivider::FindTabbedPane

```
CDockablePane* FindTabbedPane(UINT nID);
```

### <a name="parameters"></a>Parametry

podczas *NID*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getdefaultwidth"></a>CPaneDivider::GetDefaultWidth

```
static int __stdcall GetDefaultWidth();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getfirstpane"></a>CPaneDivider::GetFirstPane

```
const CBasePane* GetFirstPane() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getpanedividers"></a>CPaneDivider::GetPaneDividers

Zwraca listę dzielników okienka, które znajdują się w [klasie CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Tę metodę należy wywoływać tylko dla separatorów okienka domyślnego.

```
void GetPaneDividers(CObList& lstSliders);
```

### <a name="parameters"></a>Parametry

*lstSliders*<br/>
określoną Zawiera listę podziałów okienka, które znajdują się w kontenerze okienka.

### <a name="remarks"></a>Uwagi

Tę metodę należy wywoływać tylko dla separatorów okienka domyślnego. Domyślny podział okienka jest separatorem, który zmienia rozmiar całego kontenera okienka.

##  <a name="getpanedividerstyle"></a>CPaneDivider::GetPaneDividerStyle

```
DWORD GetPaneDividerStyle() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getpanes"></a>CPaneDivider:: getokienks

Zwraca listę okienek, które znajdują się w [klasie CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Ta metoda powinna być wywoływana tylko w celu pobrania separatorów okienka domyślnego.

```
void GetPanes(CObList& lstBars);
```

### <a name="parameters"></a>Parametry

*lstBars*<br/>
określoną Zawiera listę okienek, które znajdują się w kontenerze okienka.

### <a name="remarks"></a>Uwagi

Tę metodę należy wywoływać tylko dla separatorów okienka domyślnego. Domyślny podział okienka jest separatorem, który zmienia rozmiar całego kontenera okienka.

##  <a name="getrootcontainerrect"></a>CPaneDivider::GetRootContainerRect

```
CRect GetRootContainerRect();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getwidth"></a>CPaneDivider:: getwidth

```
int GetWidth() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="init"></a>CPaneDivider:: init

```
void Init(
    BOOL bDefaultSlider = FALSE,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>Parametry

podczas *bDefaultSlider*<br/>
podczas *pParent*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="insertpane"></a>CPaneDivider::InsertPane

```
virtual BOOL InsertPane(
    CDockablePane* pBarToInsert,
    CDockablePane* pTargetBar,
    DWORD dwAlignment,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

podczas *pBarToInsert*<br/>
podczas *pTargetBar*<br/>
podczas *dwAlignment*<br/>
podczas *lpRect*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isautohidemode"></a>CPaneDivider:: autoukrywaniemode

```
BOOL IsAutoHideMode() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isdefault"></a>CPaneDivider:: IsDefault

```
BOOL IsDefault() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="ishorizontal"></a>CPaneDivider:: ispoziome

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="m_ndefaultwidth"></a>CPaneDivider::m_nDefaultWidth

Określa domyślną szerokość (w pikselach) wszystkich podziałów okienka w aplikacji.

```
AFX_IMPORT_DATA static int m_nDefaultWidth;
```

##  <a name="move"></a>CPaneDivider:: Move

```
virtual void Move(
    CPoint& ptOffset,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>Parametry

podczas *ptOffset*<br/>
podczas *bAdjustLayout*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="m_psliderrtc"></a>  CPaneDivider::m_pSliderRTC

Przechowuje wskaźnik do informacji o klasie środowiska uruchomieniowego `CPaneDivider`dla obiektu pochodnego.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pSliderRTC;
```

### <a name="remarks"></a>Uwagi

Ustaw tę zmienną elementu członkowskiego, jeśli utworzysz rozdzielacz okienka niestandardowego. Dzięki temu struktura może utworzyć dzielnik okienka po narysowaniu okienka.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, `m_pSliderRTC` jak ustawić zmienną członkowską:

```
class CMySplitter : public CPaneDivider
{
...
};

CPaneDivider::m_pSliderRTC = RUNTIME_CLASS(CMySpliter);
```

##  <a name="notifyaboutrelease"></a>CPaneDivider::NotifyAboutRelease

```
virtual void NotifyAboutRelease();
```

### <a name="remarks"></a>Uwagi

##  <a name="onshowpane"></a>CPaneDivider::OnShowPane

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>Parametry

podczas *pBar*<br/>
podczas *bShow*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="releaseemptypanecontainers"></a>CPaneDivider::ReleaseEmptyPaneContainers

```
void ReleaseEmptyPaneContainers();
```

### <a name="remarks"></a>Uwagi

##  <a name="removepane"></a>CPaneDivider::RemovePane

```
virtual void RemovePane(CDockablePane* pBar);
```

### <a name="parameters"></a>Parametry

podczas *pBar*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="replacepane"></a>CPaneDivider::ReplacePane

```
virtual BOOL ReplacePane(
    CDockablePane* pBarToReplace,
    CDockablePane* pBarToReplaceWith);
```

### <a name="parameters"></a>Parametry

podczas *pBarToReplace*<br/>
podczas *pBarToReplaceWith*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="repositionpanes"></a>CPaneDivider::RepositionPanes

```
virtual void RepositionPanes(
    CRect& rectNew,
    HDWP& hdwp);
```

### <a name="parameters"></a>Parametry

podczas *rectNew*<br/>
podczas *hdwp*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="serialize"></a>CPaneDivider:: serializować

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

podczas *AR*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="showwindow"></a>CPaneDivider:: funkcja ShowWindow

```
void ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>Parametry

podczas *nCmdShow*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="storerecentdocksiteinfo"></a>CPaneDivider::StoreRecentDockSiteInfo

```
void StoreRecentDockSiteInfo(CDockablePane* pBar);
```

### <a name="parameters"></a>Parametry

podczas *pBar*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="storerecenttabrelatedinfo"></a>CPaneDivider::StoreRecentTabRelatedInfo

```
void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>Parametry

podczas *pDockingBar*<br/>
podczas *pTabbedBar*<br/>

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CPaneContainerManager](../../mfc/reference/cpanecontainermanager-class.md)<br/>
[Klasa CPaneContainer](../../mfc/reference/cpanecontainer-class.md)<br/>
[Klasa CDockingManager](../../mfc/reference/cdockingmanager-class.md)<br/>
[Klasa CBasePane](../../mfc/reference/cbasepane-class.md)
