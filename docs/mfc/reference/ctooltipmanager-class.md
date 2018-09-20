---
title: Klasa CTooltipManager | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager::CreateToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::DeleteToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipParams
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipText
- AFXTOOLTIPMANAGER/CTooltipManager::UpdateTooltips
dev_langs:
- C++
helpviewer_keywords:
- CTooltipManager [MFC], CreateToolTip
- CTooltipManager [MFC], DeleteToolTip
- CTooltipManager [MFC], SetTooltipParams
- CTooltipManager [MFC], SetTooltipText
- CTooltipManager [MFC], UpdateTooltips
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae35c6b38bbc5370d0b09341403f38c048bc3ae4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424745"
---
# <a name="ctooltipmanager-class"></a>Klasa CTooltipManager

Przechowuje informacje środowiska wykonawczego o podpowiedziach. `CTooltipManager` Klasy jest utworzona jeden raz w każdej aplikacji.

## <a name="syntax"></a>Składnia

```
class CTooltipManager : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTooltipManager::CreateToolTip](#createtooltip)|Tworzy formant etykietki narzędzia dla typów formantu Windows.|
|[CTooltipManager::DeleteToolTip](#deletetooltip)|Usuwa kontrolkę etykiety narzędzia.|
|[CTooltipManager::SetTooltipParams](#settooltipparams)|Dostosowuje wyglądu formantu etykietki narzędzia dla typów formantu Windows.|
|[CTooltipManager::SetTooltipText](#settooltiptext)|Ustawia tekst i opis dla kontrolki tooltip.|
|[CTooltipManager::UpdateTooltips](#updatetooltips)||

## <a name="remarks"></a>Uwagi

Użyj [klasa CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo`, i `CTooltipManager` ze sobą, aby implementować niestandardowe etykietki narzędzi w aplikacji. Na przykład dotyczące używania tych klas etykietki narzędzia zobacz [klasa CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md) tematu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtooltipmanager.h

##  <a name="createtooltip"></a>  CTooltipManager::CreateToolTip

Tworzy kontrolkę tooltip.

```
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,
    CWnd* pWndParent,
    UINT nType);
```

### <a name="parameters"></a>Parametry

*pToolTip*<br/>
[out] Odwołanie do wskaźnika etykietki narzędzia. Ustawiana jest punkt do nowo utworzonego etykietki narzędzia, gdy funkcja zwraca.

*pWndParent*<br/>
[in] Element nadrzędny elementu ToolTip.

*nNie*<br/>
[in] Typ elementu ToolTip.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli etykietka narzędzia został pomyślnie utworzony.

### <a name="remarks"></a>Uwagi

Należy wywołać [CTooltipManager::DeleteToolTip](#deletetooltip) do usuwania formantu etykietki narzędzia, który jest przekazywany w *pToolTip*.

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) zestawów parametrów wizualizacji do wyświetlenia każdego etykietki narzędzia, tworzy oparte na etykietkę narzędzia typu *nNie* określa. Aby zmienić parametry dla jednego lub więcej typów etykietki narzędzia, należy wywołać [CTooltipManager::SetTooltipParams](#settooltipparams).

Nieprawidłowa etykietka narzędzia typy są wymienione w poniższej tabeli:

|Typ etykietki narzędzia|Kategoria kontroli|Przykład typów|
|------------------|----------------------|-------------------|
|AFX_TOOLTIP_TYPE_BUTTON|Przycisk.|CMFCButton|
|AFX_TOOLTIP_TYPE_CAPTIONBAR|Pasek podpisu.|CMFCCaptionBar|
|AFX_TOOLTIP_TYPE_DEFAULT|Formant, który nie mieści się inną kategorię.|Brak.|
|AFX_TOOLTIP_TYPE_DOCKBAR|Okienko dokowalnych.|CDockablePane|
|AFX_TOOLTIP_TYPE_EDIT|Pole tekstowe.|Brak.|
|AFX_TOOLTIP_TYPE_MINIFRAME|Pływające.|CPaneFrameWnd|
|AFX_TOOLTIP_TYPE_PLANNER|Planner.|Brak.|
|AFX_TOOLTIP_TYPE_RIBBON|Pasek wstążki.|CMFCRibbonBar, cmfcribbonpanelmenubar —|
|AFX_TOOLTIP_TYPE_TAB|Formant karty.|CMFCTabCtrl|
|AFX_TOOLTIP_TYPE_TOOLBAR|Pasek narzędzi.|CMFCToolBar, CMFCPopupMenuBar|
|AFX_TOOLTIP_TYPE_TOOLBOX|Przybornika.|Brak.|

##  <a name="deletetooltip"></a>  CTooltipManager::DeleteToolTip

Usuwa kontrolkę etykiety narzędzia.

```
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```

### <a name="parameters"></a>Parametry

*pToolTip*<br/>
[out w] Odwołanie do wskaźnika do etykietkę narzędzia do zniszczenia.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody dla każdego [klasa CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) utworzony przez [CTooltipManager::CreateToolTip](#createtooltip). Kontrolki nadrzędnej powinna wywołać tę metodę z jego `OnDestroy` programu obsługi. Jest to wymagane, aby poprawnie usunąć etykietki narzędzia w ramach. Ta metoda ustawia *pToolTip* na wartość NULL, przed jego zwracaniem.

##  <a name="settooltipparams"></a>  CTooltipManager::SetTooltipParams

Dostosowuje wyglądu formantu etykietki narzędzia dla określonych typów formantu Windows.

```
void SetTooltipParams(
    UINT nTypes,
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),
    CMFCToolTipInfo* pParams=NULL);
```

### <a name="parameters"></a>Parametry

*nTypes*<br/>
[in] Określa typy kontrolek.

*pRTC*<br/>
[in] Klasa środowiska uruchomieniowego niestandardowa etykietka narzędzia.

*pParams*<br/>
[in] Parametry etykietki narzędzia.

### <a name="remarks"></a>Uwagi

Ta metoda zestawów środowiska uruchomieniowego klasy i parametry początkowe [CToolTipManager](../../mfc/reference/ctooltipmanager-class.md) używa podczas tworzenia etykietek narzędzi. Kiedy wywołuje kontrolki [CTooltipManager::CreateToolTip](#createtooltip) i przebiegów w etykietce narzędzia typ jednego z typów, wskazywanym przez *nTypes*, Menedżer etykietki narzędzia tworzy kontrolkę etykiety narzędzia, który jest wystąpieniem typu środowisko uruchomieniowe klasą określoną przez *pRTC* i przekazuje parametry określone przez *pParams* do nowego etykietki narzędzia.

Ta metoda jest wywoływana, wszystkich istniejących właścicieli etykietka narzędzia pojawia się komunikat o AFX_WM_UPDATETOOLTIPS i ich etykietki narzędzi należy utworzyć ponownie przy użyciu [CTooltipManager::CreateToolTip](#createtooltip).

*nTypes* może być dowolną kombinacją nieprawidłowa etykietka narzędzia typy, które [CTooltipManager::CreateToolTip](#createtooltip) AFX_TOOLTIP_TYPE_ALL może być używana lub go. W przypadku przekazania AFX_TOOLTIP_TYPE_ALL wpływają na wszystkie typy etykietki narzędzia.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób użycia `SetTooltipParams` metody `CTooltipManager` klasy. Ten fragment kodu jest częścią [Rysowanie Client sample](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#11](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]

##  <a name="settooltiptext"></a>  CTooltipManager::SetTooltipText

Ustawia tekst i opis etykietki narzędzia.

```
static void SetTooltipText(
    TOOLINFO* pTI,
    CToolTipCtrl* pToolTip,
    UINT nType,
    const CString strText,
    LPCTSTR lpszDescr=NULL);
```

### <a name="parameters"></a>Parametry

*pTI*<br/>
[in] Wskaźnik do obiektu TOOLINFO.

*pToolTip*<br/>
[out w] Wskaźnik do kontrolki tooltip, dla której chcesz ustawić tekst i opis.

*nNie*<br/>
[in] Określa typ kontrolki, z którą skojarzony jest ten etykietki narzędzia.

*strText*<br/>
[in] Tekst, który ma być ustawiony jako tekst etykietki narzędzia.

*lpszDescr*<br/>
[in] Wskaźnik do opis etykietki narzędzia. Może mieć wartości NULL.

### <a name="remarks"></a>Uwagi

Wartość *nNie* musi być taka sama wartość jak *nNie* parametru [CTooltipManager::CreateToolTip](#createtooltip) podczas tworzenia etykietki narzędzia.

##  <a name="updatetooltips"></a>  CTooltipManager::UpdateTooltips

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

```
void UpdateTooltips();
```

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)<br/>
[Klasa CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)
