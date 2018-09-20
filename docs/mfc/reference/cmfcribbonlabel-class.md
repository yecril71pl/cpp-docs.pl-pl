---
title: Klasa CMFCRibbonLabel | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::SetACCData
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonLabel [MFC], CMFCRibbonLabel
- CMFCRibbonLabel [MFC], SetACCData
ms.assetid: 0346c891-83bf-4f20-b8a1-c84cf2aadced
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9d54662663e2b3223f4122eae93327b9a05337b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382235"
---
# <a name="cmfcribbonlabel-class"></a>Klasa CMFCRibbonLabel

Implementuje etykietę tekstową nieinteraktywną na Wstążce.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonLabel : public CMFCRibbonButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonLabel::CMFCRibbonLabel](#cmfcribbonlabel)|Tworzy i inicjuje `CMFCRibbonLabel` obiektu z podanego ciągu znaków.|
|`CMFCRibbonLabel::~CMFCRibbonLabel`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCRibbonLabel::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|
|`CMFCRibbonLabel::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|
|[CMFCRibbonLabel::SetACCData](#setaccdata)|Określa dane ułatwień dostępu dla bieżącego elementu wstążki w etykiecie. (Przesłania [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|

### <a name="remarks"></a>Uwagi

Po utworzeniu etykietę wstążki, dodaj go do panelu, wywołując [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

Nie można dodać etykietę wstążki do paska narzędzi Szybki dostęp.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxRibbonLabel.h

##  <a name="cmfcribbonlabel"></a>  CMFCRibbonLabel::CMFCRibbonLabel

Tworzy i inicjuje [CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md) obiekt, który wyświetla określony tekst.

```
CMFCRibbonLabel(
    LPCTSTR lpszText,
    BOOL bIsMultiLine = FALSE);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
[in] Tekst wyświetlany w etykiecie.

*bIsMultiLine*<br/>
[in] Wartość TRUE, aby określić, że etykieta jest etykieta wielowierszowe; w przeciwnym razie wartość FALSE.

##  <a name="setaccdata"></a>  CMFCRibbonLabel::SetACCData

Określa dane ułatwień dostępu dla bieżącego elementu wstążki w etykiecie.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
[in] Reprezentuje okno nadrzędne bieżącej etykiety wstążki.

*Dane*<br/>
[out] Obiekt typu `CAccessibilityData` , jest wypełniana danymi dostępności bieżącej etykiety wstążki.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli *danych* parametr został pomyślnie wypełnione danymi ułatwień dostępu w bieżącej etykiety wstążki; w przeciwnym razie FALSE.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)
