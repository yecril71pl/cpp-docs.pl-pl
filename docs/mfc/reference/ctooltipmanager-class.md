---
title: Klasa CTooltipManager
ms.date: 11/04/2016
f1_keywords:
- CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager::CreateToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::DeleteToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipParams
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipText
- AFXTOOLTIPMANAGER/CTooltipManager::UpdateTooltips
helpviewer_keywords:
- CTooltipManager [MFC], CreateToolTip
- CTooltipManager [MFC], DeleteToolTip
- CTooltipManager [MFC], SetTooltipParams
- CTooltipManager [MFC], SetTooltipText
- CTooltipManager [MFC], UpdateTooltips
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
ms.openlocfilehash: 4e721740fc100a34ea08dd7ff5f9291eea2d9b36
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752168"
---
# <a name="ctooltipmanager-class"></a>Klasa CTooltipManager

Przechowuje informacje o czasie wykonywania etykietek narzędzi. Klasa `CTooltipManager` jest tworzone jeden raz na aplikację.

## <a name="syntax"></a>Składnia

```
class CTooltipManager : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTooltipManager::CreateToolTip](#createtooltip)|Tworzy formant etykietki narzędzia dla określonych typów formantów systemu Windows.|
|[CTooltipManager::DeleteToolTip](#deletetooltip)|Usuwa formant etykietki narzędzia.|
|[CTooltipManager::SetTooltipParams](#settooltipparams)|Dostosowuje wygląd formantu etykietki narzędzia dla określonych typów formantów systemu Windows.|
|[CTooltipManager::SetTooltipText](#settooltiptext)|Ustawia tekst i opis formantu etykietki narzędzia.|
|[CTooltipManager::UpdateTooltips](#updatetooltips)||

## <a name="remarks"></a>Uwagi

Użyj [CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md) `CMFCToolTipInfo`Class `CTooltipManager` , i razem, aby zaimplementować dostosowane etykietki narzędzi w aplikacji. Na przykład, jak korzystać z tych klas etykietki narzędzia, zobacz [CMFCToolTipCtrl temat klasy.](../../mfc/reference/cmfctooltipctrl-class.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ctooltipmanager](../../mfc/reference/ctooltipmanager-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtooltipmanager.h

## <a name="ctooltipmanagercreatetooltip"></a><a name="createtooltip"></a>CTooltipManager::CreateToolTip

Tworzy formant etykietki narzędzia.

```
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,
    CWnd* pWndParent,
    UINT nType);
```

### <a name="parameters"></a>Parametry

*pToolTip (etykietka pToolTip)*<br/>
[na zewnątrz] Odwołanie do wskaźnika etykietki narzędzia. Jest ustawiona na wskazywę nowo utworzonej etykietki narzędzia, gdy funkcja zwraca.

*pWndRodziciela*<br/>
[w] Element nadrzędny etykietki narzędzia.

*nTyp*<br/>
[w] Typ etykietki narzędzia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli etykietka narzędzia została utworzona pomyślnie.

### <a name="remarks"></a>Uwagi

Aby usunąć kontrolkę etykietki narzędzia przekazywana z powrotem w *pToolTip*należy wywołać [CTooltipManager::DeleteToolTip.](#deletetooltip)

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) ustawia parametry wyświetlania wizualnego każdej tworzonej etykietki narzędzia na podstawie typu etykietki narzędzia, który określa *nType.* Aby zmienić parametry dla jednego lub więcej typów etykietek narzędzi, zadzwoń [do CTooltipManager::SetTooltipParams](#settooltipparams).

Prawidłowe typy etykietek narzędzi są wymienione w poniższej tabeli:

|Typ etykietki narzędzia|Kategoria sterowania|Przykładowe typy|
|------------------|----------------------|-------------------|
|AFX_TOOLTIP_TYPE_BUTTON|Przycisk.|Cmfcbutton|
|AFX_TOOLTIP_TYPE_CAPTIONBAR|Pasek podpisu.|Cmfccaptionbar|
|AFX_TOOLTIP_TYPE_DEFAULT|Każdy formant, który nie pasuje do innej kategorii.|Brak.|
|AFX_TOOLTIP_TYPE_DOCKBAR|Okienko dokowane.|Cdockablepane|
|AFX_TOOLTIP_TYPE_EDIT|Pole tekstowe.|Brak.|
|AFX_TOOLTIP_TYPE_MINIFRAME|Miniframe.|Cpaneframewnd|
|AFX_TOOLTIP_TYPE_PLANNER|Planista.|Brak.|
|AFX_TOOLTIP_TYPE_RIBBON|Pasek wstążki.|CMFCRibbonBar, CMFCRibbonPanelMenuBar|
|AFX_TOOLTIP_TYPE_TAB|Kontrolka karty.|Cmfctabctrl|
|AFX_TOOLTIP_TYPE_TOOLBAR|Pasek narzędzi.|CMFCToolBar, CMFCPopupMenuBar|
|AFX_TOOLTIP_TYPE_TOOLBOX|Przybornik.|Brak.|

## <a name="ctooltipmanagerdeletetooltip"></a><a name="deletetooltip"></a>CTooltipManager::DeleteToolTip

Usuwa formant etykietki narzędzia.

```
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```

### <a name="parameters"></a>Parametry

*pToolTip (etykietka pToolTip)*<br/>
[w, na zewnątrz] Odwołanie do wskaźnika do etykietki narzędzia, które mają zostać zniszczone.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody dla każdej [klasy CToolTipCtrl,](../../mfc/reference/ctooltipctrl-class.md) która została utworzona przez [CTooltipManager::CreateToolTip](#createtooltip). Formant nadrzędny należy wywołać tę metodę z jego `OnDestroy` obsługi. Jest to wymagane, aby poprawnie usunąć etykietkę narzędzia z platformy. Ta metoda ustawia *pToolTip* na NULL przed jego zwrotem.

## <a name="ctooltipmanagersettooltipparams"></a><a name="settooltipparams"></a>CTooltipManager::SetTooltipParams

Dostosowuje wygląd formantu etykietki narzędzia dla określonych typów formantów systemu Windows.

```cpp
void SetTooltipParams(
    UINT nTypes,
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),
    CMFCToolTipInfo* pParams=NULL);
```

### <a name="parameters"></a>Parametry

*nTypy*<br/>
[w] Określa typy formantów.

*pRTC*<br/>
[w] Klasa środowiska uruchomieniowego etykietki narzędzia niestandardowego.

*pParams ( pParams )*<br/>
[w] Parametry etykietki narzędzia.

### <a name="remarks"></a>Uwagi

Ta metoda ustawia klasę środowiska uruchomieniowego i parametry początkowe używane przez [CToolTipManager](../../mfc/reference/ctooltipmanager-class.md) podczas tworzenia etykietek narzędzi. Gdy formant wywołuje [CTooltipManager::CreateToolTip](#createtooltip) i przekazuje w polup typu, który jest jednym z typów wskazanych przez *nTypes,* menedżer etykietki narzędzia tworzy formant etykietki narzędzia, który jest wystąpieniem klasy środowiska uruchomieniowego określonego przez *pRTC* i przekazuje parametry określone przez *pParams* do nowej etykietki narzędzia.

Po wywołaniu tej metody wszyscy istniejąci właściciele etykietek narzędzi otrzymują komunikat AFX_WM_UPDATETOOLTIPS i muszą ponownie utworzyć ich etykietki narzędzi za pomocą [CTooltipManager::CreateToolTip](#createtooltip).

*nTypes* może być dowolną kombinacją prawidłowych typów etykietki narzędzia, które [CTooltipManager::CreateToolTip](#createtooltip) używa lub może być AFX_TOOLTIP_TYPE_ALL. Jeśli przekażesz AFX_TOOLTIP_TYPE_ALL, dotyczy to wszystkich typów etykietek narzędzi.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać `SetTooltipParams` metody `CTooltipManager` klasy. Ten fragment kodu jest częścią [próbki Klienta rysowania](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#11](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]

## <a name="ctooltipmanagersettooltiptext"></a><a name="settooltiptext"></a>CTooltipManager::SetTooltipText

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

*Pti*<br/>
[w] Wskaźnik do obiektu TOOLINFO.

*pToolTip (etykietka pToolTip)*<br/>
[w, na zewnątrz] Wskaźnik do formantu etykietki narzędzia, dla którego należy ustawić tekst i opis.

*nTyp*<br/>
[w] Określa typ formantu, z którym jest skojarzona ta etykietka narzędzia.

*strText (tekst)*<br/>
[w] Tekst, który ma być ustawiony jako tekst etykietki narzędzia.

*lpszdescr*<br/>
[w] Wskaźnik do opisu etykietki narzędzia. Może mieć wartość NULL.

### <a name="remarks"></a>Uwagi

Wartość *nType* musi być taka sama wartość jak *nType* parametr [CTooltipManager::CreateToolTip](#createtooltip) podczas tworzenia etykietki narzędzia.

## <a name="ctooltipmanagerupdatetooltips"></a><a name="updatetooltips"></a>CTooltipManager::UpdateTooltips

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```cpp
void UpdateTooltips();
```

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)<br/>
[Klasa CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)
