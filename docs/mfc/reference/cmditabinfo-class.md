---
title: Klasa CMDITabInfo
ms.date: 11/04/2016
f1_keywords:
- CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo::Serialize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bAutoColor
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bDocumentMenu
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bEnableTabSwap
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bFlatFrame
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCloseButton
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCustomTooltips
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabIcons
- AFXMDICLIENTAREAWND/CMDITabInfo::m_nTabBorderSize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_style
- AFXMDICLIENTAREAWND/CMDITabInfo::m_tabLocation
helpviewer_keywords:
- CMDITabInfo [MFC], Serialize
- CMDITabInfo [MFC], m_bAutoColor
- CMDITabInfo [MFC], m_bDocumentMenu
- CMDITabInfo [MFC], m_bEnableTabSwap
- CMDITabInfo [MFC], m_bFlatFrame
- CMDITabInfo [MFC], m_bTabCloseButton
- CMDITabInfo [MFC], m_bTabCustomTooltips
- CMDITabInfo [MFC], m_bTabIcons
- CMDITabInfo [MFC], m_nTabBorderSize
- CMDITabInfo [MFC], m_style
- CMDITabInfo [MFC], m_tabLocation
ms.assetid: 988ae1b7-4f7f-4239-b88f-7e28b3291c5e
ms.openlocfilehash: a42128d097c9d63d82243090e2e215a250ff432b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276341"
---
# <a name="cmditabinfo-class"></a>Klasa CMDITabInfo

`CMDITabInfo` Klasa jest używana do przekazywania parametrów do [CMDIFrameWndEx::EnableMDITabbedGroups](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups) metody. Ustaw elementy członkowskie tej klasy do sterowania zachowaniem MDI grupy z kartami.

## <a name="syntax"></a>Składnia

```
class CMDITabInfo
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMDITabInfo::CMDITabInfo`|Domyślny konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMDITabInfo::Serialize](#serialize)|Odczytuje lub zapisuje ten obiekt z lub do archiwum.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMDITabInfo::m_bActiveTabCloseButton;](#m_bactivetabclosebutton_)|Określa, czy **Zamknij** przycisk jest wyświetlany na etykiecie aktywną kartę.|
|[CMDITabInfo::m_bAutoColor](#m_bautocolor)|Określa, czy kolor na kartach MDI.|
|[CMDITabInfo::m_bDocumentMenu](#m_bdocumentmenu)|Określa, czy grupa kart Wyświetla menu podręczne, które pokazanie listy otwartych dokumentów lub wyświetla przyciski przewijania.|
|[CMDITabInfo::m_bEnableTabSwap](#m_benabletabswap)|Określa, czy użytkownika można zamienić położenie karty, przeciągając.|
|[CMDITabInfo::m_bFlatFrame](#m_bflatframe)|Określa, czy karty mają płaskie ramki.|
|[CMDITabInfo::m_bTabCloseButton](#m_btabclosebutton)|Określa, czy każda etykieta karty wyświetla **Zamknij** przycisku.|
|[CMDITabInfo::m_bTabCustomTooltips](#m_btabcustomtooltips)|Określa, czy włączono niestandardowe etykietki narzędzi.|
|[CMDITabInfo::m_bTabIcons](#m_btabicons)|Określa, czy mają być wyświetlane ikony na kartach MDI.|
|[CMDITabInfo::m_nTabBorderSize](#m_ntabbordersize)|Określa rozmiar obramowania oknem każdej karty.|
|[CMDITabInfo::m_style](#m_style)|Określa styl etykiety kart.|
|[CMDITabInfo::m_tabLocation](#m_tablocation)|Określa, czy etykiety karty znajdują się u góry lub u dołu strony.|

## <a name="remarks"></a>Uwagi

Ta klasa określa parametry grup kart MDI, tworzonych w ramach.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak można ustawić wartości różne zmienne Członkowskie `CMDITabInfo` klasy.

[!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmdiclientareawnd.h

##  <a name="m_bactivetabclosebutton_"></a>  CMDITabInfo::m_bActiveTabCloseButton;

Określa, czy **Zamknij** przycisk jest wyświetlany na etykiecie aktywną kartę.

```
BOOL m_bActiveTabCloseButton;
```

### <a name="remarks"></a>Uwagi

W przypadku wartości TRUE spowoduje wyświetlenie etykiety aktywną kartę **Zamknij** przycisku. **Zamknij** przycisk zostanie usunięty w prawym górnym rogu obszaru karty. W przeciwnym razie nie będą wyświetlane etykiety aktywną kartę **Zamknij** przycisku. **Zamknij** przycisk pojawi się w prawym górnym rogu obszaru karty.

##  <a name="m_bautocolor"></a>  CMDITabInfo::m_bAutoColor

Określa, czy każdej karcie MDI ma swój własny kolorów.

```
BOOL m_bAutoColor;
```

### <a name="remarks"></a>Uwagi

Jeśli PRAWDA, każda karta będzie miał swój własny kolor. Zestaw kolorów jest zarządzane przez bibliotekę MFC. W przeciwnym razie karty są wyświetlane w białym. Wartość domyślna to FALSE.

##  <a name="m_bdocumentmenu"></a>  CMDITabInfo::m_bDocumentMenu

Określa, czy każda karta wyświetla menu podręcznego, który wyświetla listę otwartych dokumentów przy prawej krawędzi obszaru karty.

```
BOOL m_bDocumentMenu;
```

### <a name="remarks"></a>Uwagi

W przypadku opcji TRUE każdy system windows kartę wyświetli menu podręcznego, który wyświetla listę otwartych dokumentów przy prawej krawędzi obszaru karty; W przeciwnym wypadku okno karty wyświetla przyciski przewijania przy prawej krawędzi obszaru karty. Wartość domyślna to FALSE.

##  <a name="m_benabletabswap"></a>  CMDITabInfo::m_bEnableTabSwap

Określa, czy użytkownika można zamienić położenie karty, przeciągając.

```
BOOL m_bEnableTabSwap;
```

### <a name="remarks"></a>Uwagi

W przypadku opcji TRUE użytkownik może zmienić położenie karty, przeciągając kart. W przeciwnym razie użytkownik nie może zmienić położenie karty. Wartość domyślna to TRUE.

##  <a name="m_bflatframe"></a>  CMDITabInfo::m_bFlatFrame

Określa, czy każde okno karta ma prostego ramki.

```
BOOL m_bFlatFrame;
```

##  <a name="m_btabclosebutton"></a>  CMDITabInfo::m_bTabCloseButton

Określa, czy każde okno karty wyświetla **Zamknij** przycisku.

```
BOOL m_bTabCloseButton;
```

### <a name="remarks"></a>Uwagi

W przypadku opcji TRUE oknem każdej karty wyświetla **Zamknij** przycisk na prawej krawędzi karty. W przeciwnym razie **Zamknij** przycisk nie jest wyświetlana. Wartość domyślna to TRUE.

##  <a name="m_btabcustomtooltips"></a>  CMDITabInfo::m_bTabCustomTooltips

Określa, czy na kartach są wyświetlane etykietki narzędzi.

```
BOOL m_bTabCustomTooltips;
```

### <a name="remarks"></a>Uwagi

W przypadku opcji TRUE, aplikacja wysyła komunikat AFX_WM_ON_GET_TAB_TOOLTIP do głównej ramki. Ten komunikat może obsługiwać za pomocą ON_REGISTERED_MESSAGE — makro.

##  <a name="m_btabicons"></a>  CMDITabInfo::m_bTabIcons

Określa, czy mają być wyświetlane ikony na kartach MDI.

```
BOOL m_bTabIcons;
```

### <a name="remarks"></a>Uwagi

W przypadku opcji TRUE ikony są wyświetlane na poszczególnych kartach MDI. W przeciwnym razie ikony nie są wyświetlane na kartach. Wartość domyślna to FALSE.

##  <a name="m_ntabbordersize"></a>  CMDITabInfo::m_nTabBorderSize

Określa rozmiar obramowania okna w pikselach, każdej karty.

```
int m_nTabBorderSize;
```

### <a name="remarks"></a>Uwagi

[CMFCVisualManager::GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize) zwraca wartość domyślną.

##  <a name="m_style"></a>  CMDITabInfo::m_style

Określa styl etykiety kart.

```
CMFCTabCtrl::Style m_style
```

### <a name="remarks"></a>Uwagi

Określ jedną z następujących stylów dla etykiet karty:

|||
|-|-|
|STYLE_3D|Styl 3W.  |
|STYLE_3D_ONENOTE|Styl programu Microsoft OneNote.  |
|STYLE_3D_VS2005|Microsoft Visual Studio 2005 style.  |
|STYLE_3D_SCROLLED|Styl 3D z etykietami kartę prostokąta.  |
|STYLE_FLAT_SHARED_HORZ_SCROLL|Płaski z udostępnionego poziomy pasek przewijania.  |
|STYLE_3D_ROUNDED_SCROLL|Styl 3D z etykietami round kartę.  |

##  <a name="m_tablocation"></a>  CMDITabInfo::m_tabLocation

Określa, czy etykiety karty znajdują się u góry lub u dołu strony.

```
CMFCTabCtrl::Location m_tabLocation;
```

### <a name="remarks"></a>Uwagi

Stosuje się do karty jeden z następujących flag lokalizacji:

- LOCATION_BOTTOM: etykiety karty znajdują się w dolnej części strony.

- LOCATION_TOP: etykiety karty znajdują się w górnej części strony

##  <a name="serialize"></a>  CMDITabInfo::Serialize

Odczytuje lub zapisuje ten obiekt z archiwum lub archiwum.

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*<br/>
[in] A [klasie CArchive](../../mfc/reference/carchive-class.md) obiektu do zserializowania.

## <a name="see-also"></a>Zobacz także

[Klasa CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)<br/>
[Grupy z kartami MDI](../../mfc/mdi-tabbed-groups.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
