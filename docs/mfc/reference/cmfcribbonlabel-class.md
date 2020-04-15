---
title: Klasa CMFCRibbonLabel
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::SetACCData
helpviewer_keywords:
- CMFCRibbonLabel [MFC], CMFCRibbonLabel
- CMFCRibbonLabel [MFC], SetACCData
ms.assetid: 0346c891-83bf-4f20-b8a1-c84cf2aadced
ms.openlocfilehash: cd30e374441661368d3ea7abf5177424f8dffb3c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375121"
---
# <a name="cmfcribbonlabel-class"></a>Klasa CMFCRibbonLabel

Implementuje niekliceną etykietę tekstową wstążki.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonLabel : public CMFCRibbonButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonLabel::CMFCRibbonLabel](#cmfcribbonlabel)|Konstruuje i inicjuje `CMFCRibbonLabel` obiekt z określonym ciągiem tekstowym.|
|`CMFCRibbonLabel::~CMFCRibbonLabel`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCRibbonLabel::CreateObject`|Używany przez platformę do tworzenia dynamicznego wystąpienia tego typu klasy.|
|`CMFCRibbonLabel::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|[CMFCRibbonLabel::SetACCData](#setaccdata)|Określa dane ułatwień dostępu dla bieżącego elementu etykiety wstążki. (Zastępuje [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|

### <a name="remarks"></a>Uwagi

Po utworzeniu etykiety wstążki dodaj ją do panelu, wywołując [polecenie CMFCRibbonPanel::Dodaj](../../mfc/reference/cmfcribbonpanel-class.md#add).

Do paska narzędzi Szybki dostęp nie można dodać etykiety wstążki.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxRibbonLabel.h

## <a name="cmfcribbonlabelcmfcribbonlabel"></a><a name="cmfcribbonlabel"></a>CMFCRibbonLabel::CMFCRibbonLabel

Konstruuje i inicjuje [OBIEKT CMFCRibbonLabel,](../../mfc/reference/cmfcribbonlabel-class.md) który wyświetla określony ciąg tekstowy.

```
CMFCRibbonLabel(
    LPCTSTR lpszText,
    BOOL bIsMultiLine = FALSE);
```

### <a name="parameters"></a>Parametry

*lpszText (tekst)*<br/>
[w] Tekst ma być wyświetlany na etykiecie.

*bIsMultiLine*<br/>
[w] TRUE, aby określić, że etykieta jest etykietą wielowierszową; w przeciwnym razie FALSE.

## <a name="cmfcribbonlabelsetaccdata"></a><a name="setaccdata"></a>CMFCRibbonLabel::SetACCData

Określa dane ułatwień dostępu dla bieżącego elementu etykiety wstążki.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pRoczysz*<br/>
[w] Reprezentuje okno nadrzędne bieżącej etykiety wstążki.

*Danych*<br/>
[na zewnątrz] Obiekt typu, `CAccessibilityData` który jest wypełniany danymi ułatwień dostępu bieżącej etykiety wstążki.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli parametr *danych* został pomyślnie wypełniony danymi ułatwień dostępu bieżącej etykiety wstążki; w przeciwnym razie FALSE.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)
