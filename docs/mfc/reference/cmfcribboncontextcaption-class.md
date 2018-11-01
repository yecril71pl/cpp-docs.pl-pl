---
title: Klasa CMFCRibbonContextCaption
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetColor
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetRightTabX
helpviewer_keywords:
- CMFCRibbonContextCaption [MFC], GetColor
- CMFCRibbonContextCaption [MFC], GetRightTabX
ms.assetid: cce2c0a2-8370-4266-997e-f8d0eeb3d616
ms.openlocfilehash: 3e6d8dcd643a58b3df60488b50da08288a34bab9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628387"
---
# <a name="cmfcribboncontextcaption-class"></a>Klasa CMFCRibbonContextCaption

Implementuje kolorowy podpis, który pojawia się u góry kategorii Wstążki lub kontekstu.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonContextCaption : public CMFCRibbonButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCRibbonContextCaption::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|
|[CMFCRibbonContextCaption::GetColor](#getcolor)|Zwraca kolor podpis.|
|[CMFCRibbonContextCaption::GetRightTabX](#getrighttabx)||
|`CMFCRibbonContextCaption::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|

## <a name="remarks"></a>Uwagi

To nie można bezpośrednio utworzyć wystąpienia klasy. [Klasa CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md) klasa korzysta z tej klasy wewnętrznie można dodać kolor do kategorii wstążki.

Aby ustawić kolor dla kategorii wstążki, należy wywołać [CMFCRibbonCategory::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor). Aby ustawić kolor dla kontekstu kategorii, należy wywołać [CMFCRibbonBar::AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonContextCaption](../../mfc/reference/cmfcribboncontextcaption-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxRibbonBar.h

##  <a name="getcolor"></a>  CMFCRibbonContextCaption::GetColor

Zwraca kolor tła podpis.

```
AFX_RibbonCategoryColor GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwracana wartość może być jedną z poniższych wyliczonych wartości:

- `AFX_CategoryColor_None`

- `AFX_CategoryColor_Red`

- `AFX_CategoryColor_Orange`

- `AFX_CategoryColor_Yellow`

- `AFX_CategoryColor_Green`

- `AFX_CategoryColor_Blue`

- `AFX_CategoryColor_Indigo`

- `AFX_CategoryColor_Violet`

### <a name="remarks"></a>Uwagi

Można ustawić kolor podpis, wywołując [CMFCRibbonCategory::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor) lub [CMFCRibbonBar::AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory).

##  <a name="getrighttabx"></a>  CMFCRibbonContextCaption::GetRightTabX

Pobiera pozycji po prawej stronie krawędzi karty wstążki w tej kategorii.

```
int GetRightTabX() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca po prawej stronie X wartość prostokąt otaczający `CMFCRibbonCategory` karty wstążki obiektu lub wartość -1, jeśli karta zostanie obcięta.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[Klasa CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md)<br/>
[Klasa CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)
