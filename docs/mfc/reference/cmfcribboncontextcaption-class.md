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
ms.openlocfilehash: 7aacbe23684914c91129d9962ae847d442cc411b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375218"
---
# <a name="cmfcribboncontextcaption-class"></a>Klasa CMFCRibbonContextCaption

Implementuje kolorowy podpis wyświetlany u góry kategorii wstążki lub kategorii kontekstu.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonContextCaption : public CMFCRibbonButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCRibbonContextCaption::CreateObject`|Używany przez platformę do tworzenia dynamicznego wystąpienia tego typu klasy.|
|[CMFCRibbonContextCaption::GetColor](#getcolor)|Zwraca kolor podpisu.|
|[CMFCRibbonContextCaption::GetRightTabX](#getrighttabx)||
|`CMFCRibbonContextCaption::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|

## <a name="remarks"></a>Uwagi

Tej klasy nie można bezpośrednio utworzyć wystąpienia. [Klasa CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md) używa tej klasy wewnętrznie, aby dodać kolor do kategorii wstążki.

Aby ustawić kolor dla kategorii wstążki, wywołanie [CMFCRibbon Kategoria::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor). Aby ustawić kolor dla kategorii kontekstu, wywołanie [CMFCRibbonBar::AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonContextCaption](../../mfc/reference/cmfcribboncontextcaption-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxRibbonBar.h

## <a name="cmfcribboncontextcaptiongetcolor"></a><a name="getcolor"></a>CMFCRibbonContextCaption::GetColor

Zwraca kolor tła podpisu.

```
AFX_RibbonCategoryColor GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwracana wartość może być jedną z następujących wyliczonych wartości:

- `AFX_CategoryColor_None`

- `AFX_CategoryColor_Red`

- `AFX_CategoryColor_Orange`

- `AFX_CategoryColor_Yellow`

- `AFX_CategoryColor_Green`

- `AFX_CategoryColor_Blue`

- `AFX_CategoryColor_Indigo`

- `AFX_CategoryColor_Violet`

### <a name="remarks"></a>Uwagi

Kolor podpisu można ustawić, wywołując [CMFCRibbonCategory::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor) lub [CMFCRibbonBar::AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory).

## <a name="cmfcribboncontextcaptiongetrighttabx"></a><a name="getrighttabx"></a>CMFCRibbonContextCaption::GetRightTabX

Pobiera położenie prawej krawędzi karty wstążki kategorii.

```
int GetRightTabX() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca po prawej stronie wartość X otaczającego prostokąta `CMFCRibbonCategory` karty wstążki obiektu lub wartość -1, jeśli karta jest obcięta.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[Klasa CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md)<br/>
[Klasa CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)
