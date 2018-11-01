---
title: Klasa CMFCStandardColorsPropertyPage
ms.date: 11/04/2016
helpviewer_keywords:
- CMFCStandardColorsPropertyPage class [MFC]
ms.assetid: b84b7cfb-bb24-4c65-804a-5b642cb64400
ms.openlocfilehash: 7663f85b20ab88c999af7ba37b260237d0fd869e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520669"
---
# <a name="cmfcstandardcolorspropertypage-class"></a>Klasa CMFCStandardColorsPropertyPage

Reprezentuje stronę właściwości, z którego użytkownicy wybierz kolory standardowe okno dialogowe kolorów.

## <a name="syntax"></a>Składnia

```
class CMFCStandardColorsPropertyPage : public CPropertyPage
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|`CMFCStandardColorsPropertyPage::CMFCStandardColorsPropertyPage`|Domyślny konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|`CMFCStandardColorsPropertyPage::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|
|`CMFCStandardColorsPropertyPage::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|

### <a name="remarks"></a>Uwagi

`CMFCColorDialog` Klasa korzysta z tej klasy można wyświetlić strony właściwości Kolor standardowy. Aby uzyskać więcej informacji na temat `CMFCColorDialog`, zobacz [klasa CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCStandardColorsPropertyPage](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxstandardcolorspropertypage.h

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)<br/>
[Klasa CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)
