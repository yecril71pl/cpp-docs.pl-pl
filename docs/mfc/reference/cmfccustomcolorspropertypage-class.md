---
title: Klasa CMFCCustomColorsPropertyPage
ms.date: 11/04/2016
f1_keywords:
- CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage::Setup
helpviewer_keywords:
- CMFCCustomColorsPropertyPage [MFC], Setup
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
ms.openlocfilehash: 07b369e8c47419db31bed3e49e159e3e7925d5ae
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844538"
---
# <a name="cmfccustomcolorspropertypage-class"></a>Klasa CMFCCustomColorsPropertyPage

Reprezentuje stronę właściwości, która umożliwia wybranie niestandardowych kolorów w oknie dialogowym koloru.

## <a name="syntax"></a>Składnia

```
class CMFCCustomColorsPropertyPage : public CPropertyPage
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|-|-|
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|Konstruktor domyślny.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|-|-|
|`CMFCCustomColorsPropertyPage::CreateObject`|Używane przez platformę do tworzenia wystąpienia dynamicznego tego typu klasy.|
|`CMFCCustomColorsPropertyPage::GetThisClass`|Używane przez platformę do uzyskania wskaźnika do obiektu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , który jest skojarzony z tym typem klasy.|
|[CMFCCustomColorsPropertyPage:: Setup](#setup)|Ustawia składniki koloru strony właściwości.|

### <a name="remarks"></a>Uwagi

`CMFCColorDialog`Klasa używa tej klasy do wyświetlania strony właściwości niestandardowego koloru. Aby uzyskać więcej informacji na temat `CMFCColorDialog` , zobacz [Klasa CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md).

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób konstruowania `CMFCCustomColorsPropertyPage` obiektu i ustawiania składników koloru strony właściwości.

[!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcustomcolorspropertypage. h

## <a name="cmfccustomcolorspropertypagesetup"></a><a name="setup"></a> CMFCCustomColorsPropertyPage:: Setup

Ustawia składniki koloru strony właściwości.

```cpp
void Setup(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parametry

*®*\
podczas Czerwony składnik wartości RGB.

*G*\
podczas Zielony składnik wartości RGB.

*B*\
podczas Niebieski składnik wartości RGB.

### <a name="remarks"></a>Uwagi

Ta metoda aktualizuje bieżące wartości RGB i skojarzone HLS (barwa, jasność i nasycenie) na stronie właściwości. Metoda [CMFCColorDialog:: SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo) wywołuje tę metodę, gdy struktura inicjuje okno dialogowe kolor lub naciśnie lewym przyciskiem myszy. Aby uzyskać więcej informacji na temat `CMFCColorDialog` , zobacz [Klasa CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)<br/>
[Klasa CMFCStandardColorsPropertyPage](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
