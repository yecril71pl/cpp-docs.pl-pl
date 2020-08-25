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
ms.openlocfilehash: 8e4053bf16672d693adc104c9e88bb46a67ba7dd
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845916"
---
# <a name="cmditabinfo-class"></a>Klasa CMDITabInfo

`CMDITabInfo`Klasa jest używana do przekazywania parametrów do metody [CMDIFrameWndEx:: EnableMDITabbedGroups](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups) . Ustaw elementy członkowskie tej klasy, aby kontrolować zachowanie grup z kartami MDI.

## <a name="syntax"></a>Składnia

```
class CMDITabInfo
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMDITabInfo::CMDITabInfo`|Konstruktor domyślny.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMDITabInfo:: serializować](#serialize)|Odczytuje lub zapisuje ten obiekt z lub do archiwum.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMDITabInfo:: m_bActiveTabCloseButton;](#m_bactivetabclosebutton_)|Określa, czy przycisk **zamykania** jest wyświetlany na etykiecie aktywnej karty.|
|[CMDITabInfo:: m_bAutoColor](#m_bautocolor)|Określa, czy mają być pokolorować karty MDI.|
|[CMDITabInfo:: m_bDocumentMenu](#m_bdocumentmenu)|Określa, czy grupa kart wyświetla menu podręczne, które pokazuje listę otwartych dokumentów lub wyświetla przyciski przewijania.|
|[CMDITabInfo:: m_bEnableTabSwap](#m_benabletabswap)|Określa, czy użytkownik może zamieniać położenia kart przez przeciąganie.|
|[CMDITabInfo:: m_bFlatFrame](#m_bflatframe)|Określa, czy karty mają płaską ramkę.|
|[CMDITabInfo:: m_bTabCloseButton](#m_btabclosebutton)|Określa, czy każda etykieta karty wyświetla przycisk **Zamknij** .|
|[CMDITabInfo:: m_bTabCustomTooltips](#m_btabcustomtooltips)|Określa, czy są włączone niestandardowe etykietki narzędzi.|
|[CMDITabInfo:: m_bTabIcons](#m_btabicons)|Określa, czy ikony na kartach MDI mają być wyświetlane.|
|[CMDITabInfo:: m_nTabBorderSize](#m_ntabbordersize)|Określa rozmiar obramowania każdego okna karty.|
|[CMDITabInfo:: m_style](#m_style)|Określa styl etykiet tabulacji.|
|[CMDITabInfo:: m_tabLocation](#m_tablocation)|Określa, czy etykiety kart znajdują się u góry, czy u dołu strony.|

## <a name="remarks"></a>Uwagi

Ta klasa określa parametry grup kart MDI tworzonych przez strukturę.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób ustawiania wartości różnych zmiennych składowych w `CMDITabInfo` klasie.

[!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmdiclientareawnd. h

## <a name="cmditabinfom_bactivetabclosebutton"></a><a name="m_bactivetabclosebutton_"></a> CMDITabInfo:: m_bActiveTabCloseButton;

Określa, czy przycisk **zamykania** jest wyświetlany na etykiecie aktywnej karty.

```
BOOL m_bActiveTabCloseButton;
```

### <a name="remarks"></a>Uwagi

Jeśli wartość jest równa TRUE, etykieta aktywnej karty będzie wyświetlać przycisk **Zamknij** . Przycisk **Zamknij** zostanie usunięty z prawego górnego rogu obszaru kart. W przeciwnym razie etykieta aktywnej karty nie będzie wyświetlać przycisku **Zamknij** . Przycisk **Zamknij** zostanie wyświetlony w prawym górnym rogu obszaru kart.

## <a name="cmditabinfom_bautocolor"></a><a name="m_bautocolor"></a> CMDITabInfo:: m_bAutoColor

Określa, czy każda karta MDI ma własny kolor.

```
BOOL m_bAutoColor;
```

### <a name="remarks"></a>Uwagi

Jeśli wartość jest równa TRUE, każda karta będzie mieć własny kolor. Zestaw kolorów jest zarządzany przez bibliotekę MFC. W przeciwnym razie karty są wyświetlane w kolorze białym. Wartość domyślna to FALSE.

## <a name="cmditabinfom_bdocumentmenu"></a><a name="m_bdocumentmenu"></a> CMDITabInfo:: m_bDocumentMenu

Określa, czy na każdej karcie jest wyświetlane menu podręczne, które pokazuje listę otwartych dokumentów znajdujących się na prawej krawędzi obszaru kart.

```
BOOL m_bDocumentMenu;
```

### <a name="remarks"></a>Uwagi

W przypadku wartości TRUE każda karta okna wyświetla menu podręczne, które pokazuje listę otwartych dokumentów na prawej krawędzi obszaru kart; W przeciwnym razie w oknie karty są wyświetlane przyciski przewijania znajdujące się po prawej krawędzi obszaru karty. Wartość domyślna to FALSE.

## <a name="cmditabinfom_benabletabswap"></a><a name="m_benabletabswap"></a> CMDITabInfo:: m_bEnableTabSwap

Określa, czy użytkownik może zamieniać położenia kart przez przeciąganie.

```
BOOL m_bEnableTabSwap;
```

### <a name="remarks"></a>Uwagi

W przypadku wartości TRUE użytkownik może zmienić położenia kart, przeciągając karty. W przeciwnym razie użytkownik nie może zmienić pozycji tabulatorów. Wartość domyślna to TRUE.

## <a name="cmditabinfom_bflatframe"></a><a name="m_bflatframe"></a> CMDITabInfo:: m_bFlatFrame

Określa, czy poszczególne okna kart mają płaską ramkę.

```
BOOL m_bFlatFrame;
```

## <a name="cmditabinfom_btabclosebutton"></a><a name="m_btabclosebutton"></a> CMDITabInfo:: m_bTabCloseButton

Określa, czy każde okno karty wyświetla przycisk **Zamknij** .

```
BOOL m_bTabCloseButton;
```

### <a name="remarks"></a>Uwagi

Jeśli wartość jest równa TRUE, każde okno karty wyświetla przycisk **Zamknij** po prawej krawędzi karty. w przeciwnym razie przycisk **Zamknij** nie jest wyświetlany. Wartość domyślna to TRUE.

## <a name="cmditabinfom_btabcustomtooltips"></a><a name="m_btabcustomtooltips"></a> CMDITabInfo:: m_bTabCustomTooltips

Określa, czy karty wyświetlają etykietki narzędzi.

```
BOOL m_bTabCustomTooltips;
```

### <a name="remarks"></a>Uwagi

W przypadku wartości TRUE aplikacja wysyła wiadomość AFX_WM_ON_GET_TAB_TOOLTIP do głównej ramki. Ten komunikat można obsłużyć za pomocą makra ON_REGISTERED_MESSAGE.

## <a name="cmditabinfom_btabicons"></a><a name="m_btabicons"></a> CMDITabInfo:: m_bTabIcons

Określa, czy ikony na kartach MDI mają być wyświetlane.

```
BOOL m_bTabIcons;
```

### <a name="remarks"></a>Uwagi

W przypadku wartości TRUE ikony są wyświetlane na poszczególnych kartach MDI. w przeciwnym razie ikony nie są wyświetlane na kartach. Wartość domyślna to FALSE.

## <a name="cmditabinfom_ntabbordersize"></a><a name="m_ntabbordersize"></a> CMDITabInfo:: m_nTabBorderSize

Określa rozmiar obramowania (w pikselach) każdego okna karty.

```
int m_nTabBorderSize;
```

### <a name="remarks"></a>Uwagi

[CMFCVisualManager:: GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize) zwraca wartość domyślną.

## <a name="cmditabinfom_style"></a><a name="m_style"></a> CMDITabInfo:: m_style

Określa styl etykiet tabulacji.

```
CMFCTabCtrl::Style m_style
```

### <a name="remarks"></a>Uwagi

Określ jeden z następujących stylów etykiet kart:

|Makro|Opis|
|-|-|
|STYLE_3D|styl 3W.  |
|STYLE_3D_ONENOTE|Styl programu Microsoft OneNote.  |
|STYLE_3D_VS2005|Microsoft Visual Studio styl 2005.  |
|STYLE_3D_SCROLLED|styl 3W z etykietami karty prostokąta.  |
|STYLE_FLAT_SHARED_HORZ_SCROLL|Styl płaski z udostępnionym poziomym paskiem przewijania.  |
|STYLE_3D_ROUNDED_SCROLL|styl 3W z etykietami kart okrągłych.  |

## <a name="cmditabinfom_tablocation"></a><a name="m_tablocation"></a> CMDITabInfo:: m_tabLocation

Określa, czy etykiety kart znajdują się u góry, czy u dołu strony.

```
CMFCTabCtrl::Location m_tabLocation;
```

### <a name="remarks"></a>Uwagi

Zastosuj do kart jedną z następujących flag lokalizacji:

- LOCATION_BOTTOM: etykiety kart znajdują się u dołu strony.

- LOCATION_TOP: etykiety kart znajdują się u góry strony

## <a name="cmditabinfoserialize"></a><a name="serialize"></a> CMDITabInfo:: serializować

Odczytuje lub zapisuje ten obiekt z archiwum lub archiwum.

```cpp
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ty*<br/>
podczas Obiekt [klasy CArchive](../../mfc/reference/carchive-class.md) do serializacji.

## <a name="see-also"></a>Zobacz też

[Klasa CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)<br/>
[Grupy z kartami MDI](../../mfc/mdi-tabbed-groups.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
