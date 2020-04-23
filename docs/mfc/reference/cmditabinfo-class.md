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
ms.openlocfilehash: 30bf7726b35d762be2bbbd119e0303894879cd3d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752649"
---
# <a name="cmditabinfo-class"></a>Klasa CMDITabInfo

Klasa `CMDITabInfo` jest używana do przekazywania parametrów do [metody CMDIFrameWndEx::EnableMDITabbedGroups.](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups) Ustaw członków tej klasy, aby kontrolować zachowanie grup z kartami MDI.

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
|[CMDITabInfo::m_bActiveTabCloseButton;](#m_bactivetabclosebutton_)|Określa, czy na etykiecie aktywnej karty jest wyświetlany przycisk **Zamknij.**|
|[CMDITabInfo::m_bAutoColor](#m_bautocolor)|Określa, czy karty MDI mają być kolorowe.|
|[CMDITabInfo::m_bDocumentMenu](#m_bdocumentmenu)|Określa, czy w grupie kart jest wyświetlane menu podręczne z listą otwartych dokumentów lub przyciskami przewijania.|
|[CMDITabInfo::m_bEnableTabSwap](#m_benabletabswap)|Określa, czy użytkownik może zamienić pozycje kart, przeciągając.|
|[CMDITabInfo::m_bFlatFrame](#m_bflatframe)|Określa, czy karty mają płaską ramkę.|
|[CMDITabInfo::m_bTabCloseButton](#m_btabclosebutton)|Określa, czy na każdej etykiecie karty jest wyświetlany przycisk **Zamknij.**|
|[CMDITabInfo::m_bTabCustomTooltips](#m_btabcustomtooltips)|Określa, czy niestandardowe etykietki narzędzi są włączone.|
|[CMDITabInfo::m_bTabIcons](#m_btabicons)|Określa, czy ikony mają być wyświetlane na kartach MDI.|
|[CMDITabInfo::m_nTabBorderSize](#m_ntabbordersize)|Określa rozmiar obramowania każdego okna karty.|
|[CMDITabInfo::m_style](#m_style)|Określa styl etykiet kart.|
|[CMDITabInfo::m_tabLocation](#m_tablocation)|Określa, czy etykiety kart znajdują się u góry, czy u dołu strony.|

## <a name="remarks"></a>Uwagi

Ta klasa określa parametry grup kart MDI, które tworzy struktura.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak ustawić wartości `CMDITabInfo` różnych zmiennych członkowskich w klasie.

[!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmdiclientareawnd.h

## <a name="cmditabinfom_bactivetabclosebutton"></a><a name="m_bactivetabclosebutton_"></a>CMDITabInfo::m_bActiveTabCloseButton;

Określa, czy na etykiecie aktywnej karty jest wyświetlany przycisk **Zamknij.**

```
BOOL m_bActiveTabCloseButton;
```

### <a name="remarks"></a>Uwagi

Jeśli true, na etykiecie aktywnej karty zostanie wyświetlony przycisk **Zamknij.** Przycisk **Zamknij** zostanie usunięty z prawego górnego rogu obszaru karty. W przeciwnym razie na etykiecie aktywnej karty nie zostanie wyświetlony przycisk **Zamknij.** Przycisk **Zamknij** pojawi się w prawym górnym rogu obszaru karty.

## <a name="cmditabinfom_bautocolor"></a><a name="m_bautocolor"></a>CMDITabInfo::m_bAutoColor

Określa, czy każda karta MDI ma swój własny kolor.

```
BOOL m_bAutoColor;
```

### <a name="remarks"></a>Uwagi

Jeśli true, każda karta będzie miała swój własny kolor. Zestaw kolorów jest zarządzany przez bibliotekę MFC. W przeciwnym razie karty są wyświetlane w kolorze białym. Wartością domyślną jest FAŁSZ.

## <a name="cmditabinfom_bdocumentmenu"></a><a name="m_bdocumentmenu"></a>CMDITabInfo::m_bDocumentMenu

Określa, czy na każdej karcie jest wyświetlane menu podręczne z listą otwartych dokumentów po prawej stronie obszaru karty.

```
BOOL m_bDocumentMenu;
```

### <a name="remarks"></a>Uwagi

Jeśli true, każdy windows karty wyświetla menu podręczne, które pokazuje listę otwartych dokumentów na prawej krawędzi obszaru karty; W przeciwnym razie w oknie karty zostaną wyświetlone przyciski przewijania po prawej stronie obszaru karty. Wartością domyślną jest FAŁSZ.

## <a name="cmditabinfom_benabletabswap"></a><a name="m_benabletabswap"></a>CMDITabInfo::m_bEnableTabSwap

Określa, czy użytkownik może zamienić pozycje kart, przeciągając.

```
BOOL m_bEnableTabSwap;
```

### <a name="remarks"></a>Uwagi

Jeśli true, użytkownik może zmienić pozycje kart, przeciągając karty. W przeciwnym razie użytkownik nie może zmienić pozycji kart. Wartością domyślną jest PRAWDA.

## <a name="cmditabinfom_bflatframe"></a><a name="m_bflatframe"></a>CMDITabInfo::m_bFlatFrame

Określa, czy każde okno karty ma płaską ramkę.

```
BOOL m_bFlatFrame;
```

## <a name="cmditabinfom_btabclosebutton"></a><a name="m_btabclosebutton"></a>CMDITabInfo::m_bTabCloseButton

Określa, czy w każdym oknie karty jest wyświetlany przycisk **Zamknij.**

```
BOOL m_bTabCloseButton;
```

### <a name="remarks"></a>Uwagi

Jeśli prawda, każde okno karty wyświetla przycisk **Zamknij** po prawej **Close** stronie karty. Wartością domyślną jest PRAWDA.

## <a name="cmditabinfom_btabcustomtooltips"></a><a name="m_btabcustomtooltips"></a>CMDITabInfo::m_bTabCustomTooltips

Określa, czy na kartach są wyświetlane etykietki narzędzi.

```
BOOL m_bTabCustomTooltips;
```

### <a name="remarks"></a>Uwagi

Jeśli true, aplikacja wysyła komunikat AFX_WM_ON_GET_TAB_TOOLTIP do ramki głównej. Ten komunikat można obsługiwać za pomocą makra ON_REGISTERED_MESSAGE.

## <a name="cmditabinfom_btabicons"></a><a name="m_btabicons"></a>CMDITabInfo::m_bTabIcons

Określa, czy ikony mają być wyświetlane na kartach MDI.

```
BOOL m_bTabIcons;
```

### <a name="remarks"></a>Uwagi

Jeśli true, ikony są wyświetlane na każdej karcie MDI. W przeciwnym razie ikony nie są wyświetlane na kartach. Wartością domyślną jest FAŁSZ.

## <a name="cmditabinfom_ntabbordersize"></a><a name="m_ntabbordersize"></a>CMDITabInfo::m_nTabBorderSize

Określa rozmiar obramowania w pikselach każdego okna karty.

```
int m_nTabBorderSize;
```

### <a name="remarks"></a>Uwagi

[CMFCVisualManager::GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize) zwraca wartość domyślną.

## <a name="cmditabinfom_style"></a><a name="m_style"></a>CMDITabInfo::m_style

Określa styl etykiet kart.

```
CMFCTabCtrl::Style m_style
```

### <a name="remarks"></a>Uwagi

Określ jeden z następujących stylów etykiet kart:

|||
|-|-|
|STYLE_3D|Styl 3D.  |
|STYLE_3D_ONENOTE|Styl programu Microsoft OneNote.  |
|STYLE_3D_VS2005|Styl programu Microsoft Visual Studio 2005.  |
|STYLE_3D_SCROLLED|Styl 3D z etykietami kart prostokąta.  |
|STYLE_FLAT_SHARED_HORZ_SCROLL|Płaski styl ze udostępnionym poziomym paskiem przewijania.  |
|STYLE_3D_ROUNDED_SCROLL|Styl 3D z okrągłymi etykietami kart.  |

## <a name="cmditabinfom_tablocation"></a><a name="m_tablocation"></a>CMDITabInfo::m_tabLocation

Określa, czy etykiety kart znajdują się u góry, czy u dołu strony.

```
CMFCTabCtrl::Location m_tabLocation;
```

### <a name="remarks"></a>Uwagi

Zastosuj do kart jedną z następujących flag lokalizacji:

- LOCATION_BOTTOM: etykiety kart znajdują się u dołu strony.

- LOCATION_TOP: etykiety kart znajdują się w górnej części strony

## <a name="cmditabinfoserialize"></a><a name="serialize"></a>CMDITabInfo::Serialize

Odczytuje lub zapisuje ten obiekt z archiwum lub do archiwum.

```cpp
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*Ar*<br/>
[w] A [CArchive Class](../../mfc/reference/carchive-class.md) obiektu do serializacji.

## <a name="see-also"></a>Zobacz też

[Klasa CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)<br/>
[Grupy z kartami MDI](../../mfc/mdi-tabbed-groups.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
