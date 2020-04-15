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
ms.openlocfilehash: 01b73f44fcf26a820e43eb87a65e99c2ec186e64
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367666"
---
# <a name="cmfccustomcolorspropertypage-class"></a>Klasa CMFCCustomColorsPropertyPage

Reprezentuje stronę właściwości, która może zaznaczać kolory niestandardowe w oknie dialogowym koloru.

## <a name="syntax"></a>Składnia

```
class CMFCCustomColorsPropertyPage : public CPropertyPage
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|Domyślny konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|`CMFCCustomColorsPropertyPage::CreateObject`|Używany przez platformę do tworzenia dynamicznego wystąpienia tego typu klasy.|
|`CMFCCustomColorsPropertyPage::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|[CMFCCustomColorsPropertyPage::Setup](#setup)|Ustawia składniki koloru strony właściwości.|

### <a name="remarks"></a>Uwagi

Klasa `CMFCColorDialog` używa tej klasy do wyświetlania strony właściwości niestandardowego koloru. Aby uzyskać `CMFCColorDialog`więcej informacji na temat , zobacz [CMFCColorDialog Class](../../mfc/reference/cmfccolordialog-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak skonstruować `CMFCCustomColorsPropertyPage` obiekt i ustawić składniki koloru strony właściwości.

[!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[Cpropertypage](../../mfc/reference/cpropertypage-class.md)

[CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcustomcolorspropertypage.h

## <a name="cmfccustomcolorspropertypagesetup"></a><a name="setup"></a>CMFCCustomColorsPropertyPage::Setup

Ustawia składniki koloru strony właściwości.

```
void Setup(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*R*|[w] Czerwony składnik wartości RGB.|
|*G*|[w] Zielony składnik wartości RGB.|
|*B*|[w] Niebieski składnik wartości RGB.|

### <a name="remarks"></a>Uwagi

Ta metoda aktualizuje bieżące RGB i skojarzone HLS (odcień, lekkość i nasycenie) wartości kolorów strony właściwości. [METODA CMFCColorDialog::SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo) wywołuje tę metodę, gdy struktura inicjuje okno dialogowe kolorów lub użytkownik naciśnie lewy przycisk myszy. Aby uzyskać `CMFCColorDialog`więcej informacji na temat , zobacz [CMFCColorDialog Class](../../mfc/reference/cmfccolordialog-class.md).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)<br/>
[Klasa CMFCStandardColorsPropertyPage](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
