---
title: Klasa CMFCStandardColorsPropertyPage
ms.date: 11/04/2016
helpviewer_keywords:
- CMFCStandardColorsPropertyPage class [MFC]
ms.assetid: b84b7cfb-bb24-4c65-804a-5b642cb64400
ms.openlocfilehash: c57715171816e83cd1e04872d88b452b51b39388
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843953"
---
# <a name="cmfcstandardcolorspropertypage-class"></a>Klasa CMFCStandardColorsPropertyPage

Reprezentuje stronę właściwości, za pomocą której użytkownicy wybierają kolory standardowe w kolorze okna dialogowego.

## <a name="syntax"></a>Składnia

```
class CMFCStandardColorsPropertyPage : public CPropertyPage
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|-|-|
|`CMFCStandardColorsPropertyPage::CMFCStandardColorsPropertyPage`|Konstruktor domyślny.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|-|-|
|`CMFCStandardColorsPropertyPage::CreateObject`|Używane przez platformę do tworzenia wystąpienia dynamicznego tego typu klasy.|
|`CMFCStandardColorsPropertyPage::GetThisClass`|Używane przez platformę do uzyskania wskaźnika do obiektu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , który jest skojarzony z tym typem klasy.|

### <a name="remarks"></a>Uwagi

`CMFCColorDialog`Klasa używa tej klasy do wyświetlania strony właściwości standardowego koloru. Aby uzyskać więcej informacji na temat `CMFCColorDialog` , zobacz [Klasa CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCStandardColorsPropertyPage](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxstandardcolorspropertypage. h

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)<br/>
[Klasa CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)
