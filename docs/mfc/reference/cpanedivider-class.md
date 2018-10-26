---
title: Klasa CPaneDivider | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb7c7f18fa0d0b2b39ac8d8bc29802836495741d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50081056"
---
# <a name="cpanedivider-class"></a>Klasa CPaneDivider

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

`CPaneDivider` Klasy dzieli dwa okienka, dzieli się dwie grupy okienka lub oddziela grupę okienek z obszaru klienckiego okna ramki głównej.

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
|[CPaneDivider::AddPane](#addpane)||
|[CPaneDivider::AddRecentPane](#addrecentpane)||
|[CPaneDivider::CalcExpectedDockedRect](#calcexpecteddockedrect)||
|[CPaneDivider::CalcFixedLayout](#calcfixedlayout)|(Przesłania [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CPaneDivider::CheckVisibility](#checkvisibility)||
|[CPaneDivider::CreateEx](#createex)|(Przesłania [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).)|
|[CPaneDivider::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|(Przesłania [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CPaneDivider::DoesContainFloatingPane](#doescontainfloatingpane)||
|[CPaneDivider::FindPaneContainer](#findpanecontainer)||
|[CPaneDivider::FindTabbedPane](#findtabbedpane)||
|[CPaneDivider::GetDefaultWidth](#getdefaultwidth)||
|[CPaneDivider::GetFirstPane](#getfirstpane)||
|[CPaneDivider::GetPaneDividerStyle](#getpanedividerstyle)||
|[CPaneDivider::GetRootContainerRect](#getrootcontainerrect)||
|[CPaneDivider::GetWidth](#getwidth)||
|[CPaneDivider::Init](#init)||
|[CPaneDivider::InsertPane](#insertpane)||
|[CPaneDivider::IsAutoHideMode](#isautohidemode)|(Przesłania [CBasePane::IsAutoHideMode](../../mfc/reference/cbasepane-class.md#isautohidemode).)|
|[CPaneDivider::IsDefault](#isdefault)||
|[CPaneDivider::IsHorizontal](#ishorizontal)|(Przesłania [CBasePane::IsHorizontal](../../mfc/reference/cbasepane-class.md#ishorizontal).)|
|[CPaneDivider::Move](#move)||
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
|[CPaneDivider::GetPanes](#getpanes)|Zwraca listę wszystkich okienek, które znajdują się w [klasa CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Tę metodę należy wywoływać tylko w przypadku domyślnego okienka separatorów.|
|[CPaneDivider::GetPaneDividers](#getpanedividers)|Zwraca listę separatorów okienko, które znajdują się w [klasa CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Tę metodę należy wywoływać tylko w przypadku domyślnego okienka separatorów.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPaneDivider::m_nDefaultWidth](#m_ndefaultwidth)|Określa domyślną szerokość w pikselach wszystkich separator okienka w aplikacji.|
|[CPaneDivider::m_pSliderRTC](#m_psliderrtc)|Przechowuje wskaźnik do informacji o klasie czasu wykonywania o `CPaneDivider`-pochodnych obiektu.|

## <a name="remarks"></a>Uwagi

Szablon tworzy `CPaneDivider` obiekty automatycznie, gdy jest zadokowany w okienku.

Istnieją dwa rodzaje separator okienka:

- Separator okienka domyślne jest tworzone, gdy grupę okienek jest zadokowany do strony ramki głównego okna. Separator okienka domyślne przechowuje wskaźnik do [klasa CPaneContainerManager](../../mfc/reference/cpanecontainermanager-class.md) i przekierowuje większości operacji na grupę okienek (np. Zmienianie rozmiaru okienka lub dokowanie innego okienka lub kontener) do kontenera menedżera. Każde okienko dokowania przechowuje wskaźnik do jego domyślne dzielnik.

- Separator okienka regularnych tylko dzieli dwa okienka w kontenerze. Aby uzyskać więcej informacji, zobacz [klasa CPaneContainer](../../mfc/reference/cpanecontainer-class.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak uzyskać `CPaneDivider` obiektu z `CWorkspaceBar` obiektu. Ten fragment kodu jest częścią [próbka Demo kart MDI](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#5](../../mfc/reference/codesnippet/cpp/cpanedivider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md) [CPaneDivider](../../mfc/reference/cpanedivider-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxPaneDivider.h

##  <a name="setautohidemode"></a>  CPaneDivider::SetAutoHideMode

```
void SetAutoHideMode(BOOL bMode);
```

### <a name="parameters"></a>Parametry

[in] *bMode*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="setpanecontainermanager"></a>  CPaneDivider::SetPaneContainerManager

```
void SetPaneContainerManager(CPaneContainerManager* p);
```

### <a name="parameters"></a>Parametry

[in] *p*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="addpane"></a>  CPaneDivider::AddPane

```
virtual void AddPane(CDockablePane* pBar);
```

### <a name="parameters"></a>Parametry

[in] *pBar*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="addpanecontainer"></a>  CPaneDivider::AddPaneContainer

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

[in] *barContainerManager*<br/>
[in] *bOuterEdge*<br/>
[in] *pTargetBar*<br/>
[in] *dwAlignment*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="addrecentpane"></a>  CPaneDivider::AddRecentPane

```
virtual CDockablePane* AddRecentPane(CDockablePane* pBar);
```

### <a name="parameters"></a>Parametry

[in] *pBar*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="calcexpecteddockedrect"></a>  CPaneDivider::CalcExpectedDockedRect

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>Parametry

[in] *pWndToDock*<br/>
[in] *ptMouse*<br/>
[in] *rectResult*<br/>
[in] *bDrawTab*<br/>
[in] *ppTargetBar*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="calcfixedlayout"></a>  CPaneDivider::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

[in] *bStretch*<br/>
[in] *bHorz*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="checkvisibility"></a>  CPaneDivider::CheckVisibility

```
virtual BOOL CheckVisibility();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="cpanedivider"></a>  CPaneDivider::CPaneDivider

```
CPaneDivider();

CPaneDivider(
    BOOL bDefaultSlider,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>Parametry

[in] *bDefaultSlider*<br/>
[in] *pParent*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="createex"></a>  CPaneDivider::CreateEx

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

[in] *dwStyleEx*<br/>
[in] *dwStyle*<br/>
[in] *rect*<br/>
[in] *pParentWnd*<br/>
[in] *nID*<br/>
[in] *pContext*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="doesallowdyninsertbefore"></a>  CPaneDivider::DoesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="doescontainfloatingpane"></a>  CPaneDivider::DoesContainFloatingPane

```
virtual BOOL DoesContainFloatingPane();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="findpanecontainer"></a>  CPaneDivider::FindPaneContainer

```
CPaneContainer* FindPaneContainer(
    CDockablePane* pBar,
    BOOL& bLeftBar);
```

### <a name="parameters"></a>Parametry

[in] *pBar*<br/>
[in] *bLeftBar*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="findtabbedpane"></a>  CPaneDivider::FindTabbedPane

```
CDockablePane* FindTabbedPane(UINT nID);
```

### <a name="parameters"></a>Parametry

[in] *nID*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getdefaultwidth"></a>  CPaneDivider::GetDefaultWidth

```
static int __stdcall GetDefaultWidth();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getfirstpane"></a>  CPaneDivider::GetFirstPane

```
const CBasePane* GetFirstPane() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getpanedividers"></a>  CPaneDivider::GetPaneDividers

Zwraca listę separatorów okienko, które znajdują się w [klasa CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Tę metodę należy wywoływać tylko w przypadku domyślnego okienka separatorów.

```
void GetPaneDividers(CObList& lstSliders);
```

### <a name="parameters"></a>Parametry

*lstSliders*<br/>
[out] Zawiera listę separatorów okienko, które znajdują się w kontenerze okienka.

### <a name="remarks"></a>Uwagi

Ta metoda powinna być wywoływana dla domyślnego okienka tylko separatorów. Separator okienka domyślny jest separator, który zmienia rozmiar okienka całego kontenera.

##  <a name="getpanedividerstyle"></a>  CPaneDivider::GetPaneDividerStyle

```
DWORD GetPaneDividerStyle() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getpanes"></a>  CPaneDivider::GetPanes

Zwraca listę wszystkich okienek, które znajdują się w [klasa CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Tę metodę należy wywoływać tylko w celu pobrania separator okienka domyślne.

```
void GetPanes(CObList& lstBars);
```

### <a name="parameters"></a>Parametry

*lstBars*<br/>
[out] Zawiera listę okienek, które znajdują się w kontenerze okienka.

### <a name="remarks"></a>Uwagi

Ta metoda powinna być wywoływana dla domyślnego okienka tylko separatorów. Separator okienka domyślny jest separator, który zmienia rozmiar okienka całego kontenera.

##  <a name="getrootcontainerrect"></a>  CPaneDivider::GetRootContainerRect

```
CRect GetRootContainerRect();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getwidth"></a>  CPaneDivider::GetWidth

```
int GetWidth() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="init"></a>  CPaneDivider::Init

```
void Init(
    BOOL bDefaultSlider = FALSE,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>Parametry

[in] *bDefaultSlider*<br/>
[in] *pParent*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="insertpane"></a>  CPaneDivider::InsertPane

```
virtual BOOL InsertPane(
    CDockablePane* pBarToInsert,
    CDockablePane* pTargetBar,
    DWORD dwAlignment,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

[in] *pBarToInsert*<br/>
[in] *pTargetBar*<br/>
[in] *dwAlignment*<br/>
[in] *lprect —*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isautohidemode"></a>  CPaneDivider::IsAutoHideMode

```
BOOL IsAutoHideMode() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isdefault"></a>  CPaneDivider::IsDefault

```
BOOL IsDefault() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="ishorizontal"></a>  CPaneDivider::IsHorizontal

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="m_ndefaultwidth"></a>  CPaneDivider::m_nDefaultWidth

Określa domyślną szerokość w pikselach, wszystkie separator okienka w aplikacji.

```
AFX_IMPORT_DATA static int m_nDefaultWidth;
```

##  <a name="move"></a>  CPaneDivider::Move

```
virtual void Move(
    CPoint& ptOffset,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>Parametry

[in] *ptOffset*<br/>
[in] *bAdjustLayout*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="m_psliderrtc"></a>  CPaneDivider::m_pSliderRTC

Przechowuje wskaźnik do informacji o klasie czasu wykonywania o `CPaneDivider`-pochodnych obiektu.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pSliderRTC;
```

### <a name="remarks"></a>Uwagi

Jeśli tworzysz rozdzielacz okienka niestandardowe, należy ustawić tę zmienną elementu członkowskiego. Dzięki temu strukturę w celu utworzenia usługi dzielnik podczas rysowania okienka.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak ustawić `m_pSliderRTC` zmiennej elementu członkowskiego:

```
class CMySplitter : public CPaneDivider
{
...
};

CPaneDivider::m_pSliderRTC = RUNTIME_CLASS(CMySpliter);
```

##  <a name="notifyaboutrelease"></a>  CPaneDivider::NotifyAboutRelease

```
virtual void NotifyAboutRelease();
```

### <a name="remarks"></a>Uwagi

##  <a name="onshowpane"></a>  CPaneDivider::OnShowPane

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>Parametry

[in] *pBar*<br/>
[in] *bShow*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="releaseemptypanecontainers"></a>  CPaneDivider::ReleaseEmptyPaneContainers

```
void ReleaseEmptyPaneContainers();
```

### <a name="remarks"></a>Uwagi

##  <a name="removepane"></a>  CPaneDivider::RemovePane

```
virtual void RemovePane(CDockablePane* pBar);
```

### <a name="parameters"></a>Parametry

[in] *pBar*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="replacepane"></a>  CPaneDivider::ReplacePane

```
virtual BOOL ReplacePane(
    CDockablePane* pBarToReplace,
    CDockablePane* pBarToReplaceWith);
```

### <a name="parameters"></a>Parametry

[in] *pBarToReplace*<br/>
[in] *pBarToReplaceWith*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="repositionpanes"></a>  CPaneDivider::RepositionPanes

```
virtual void RepositionPanes(
    CRect& rectNew,
    HDWP& hdwp);
```

### <a name="parameters"></a>Parametry

[in] *rectNew*<br/>
[in] *hdwp*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="serialize"></a>  CPaneDivider::Serialize

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

[in] *ar*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="showwindow"></a>  CPaneDivider::ShowWindow

```
void ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>Parametry

[in] *nCmdShow*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="storerecentdocksiteinfo"></a>  CPaneDivider::StoreRecentDockSiteInfo

```
void StoreRecentDockSiteInfo(CDockablePane* pBar);
```

### <a name="parameters"></a>Parametry

[in] *pBar*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="storerecenttabrelatedinfo"></a>  CPaneDivider::StoreRecentTabRelatedInfo

```
void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>Parametry

[in] *pDockingBar*<br/>
[in] *pTabbedBar*<br/>

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CPaneContainerManager](../../mfc/reference/cpanecontainermanager-class.md)<br/>
[Klasa CPaneContainer](../../mfc/reference/cpanecontainer-class.md)<br/>
[Klasa CDockingManager](../../mfc/reference/cdockingmanager-class.md)<br/>
[Klasa CBasePane](../../mfc/reference/cbasepane-class.md)
