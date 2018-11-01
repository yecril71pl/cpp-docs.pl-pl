---
title: Klasa CMFCRibbonCheckBox
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetCompactSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetIntermediateSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetRegularSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::IsDrawTooltipImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDraw
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawMenuImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawOnList
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::SetACCData
helpviewer_keywords:
- CMFCRibbonCheckBox [MFC], CMFCRibbonCheckBox
- CMFCRibbonCheckBox [MFC], GetCompactSize
- CMFCRibbonCheckBox [MFC], GetIntermediateSize
- CMFCRibbonCheckBox [MFC], GetRegularSize
- CMFCRibbonCheckBox [MFC], IsDrawTooltipImage
- CMFCRibbonCheckBox [MFC], OnDraw
- CMFCRibbonCheckBox [MFC], OnDrawMenuImage
- CMFCRibbonCheckBox [MFC], OnDrawOnList
- CMFCRibbonCheckBox [MFC], SetACCData
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
ms.openlocfilehash: 067f38522c1be112d6e12200c2c10e1d439e5057
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612423"
---
# <a name="cmfcribboncheckbox-class"></a>Klasa CMFCRibbonCheckBox

`CMFCRibbonCheckBox` Klasa implementuje pole wyboru, które można dodać do menu panelu, pasek narzędzi Szybki dostęp lub okna podręcznego wstążki.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonCheckBox : public CMFCRibbonButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|(Przesłania [CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|(Przesłania [CMFCRibbonButton::GetIntermediateSize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize).)|
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|(Przesłania [CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|(Przesłania `CMFCRibbonButton::IsDrawTooltipImage`).|
|[CMFCRibbonCheckBox::OnDraw](#ondraw)|(Przesłania [CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(Przesłania [CMFCRibbonBaseElement::OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|(Przesłania `CMFCRibbonButton::OnDrawOnList`).|
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|(Przesłania [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|

## <a name="remarks"></a>Uwagi

Aby użyć `CMFCRibbonCheckBox` w aplikacji Dodaj następujący Konstruktor w kodzie:

```
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)
```
gdzie *nID* jest Identyfikatorem polecenia pole wyboru i *lpszText* jest tekst etykiety pola wyboru.

Można dodać pole do panelu wstążki przy użyciu [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribboncheckbox.h

##  <a name="cmfcribboncheckbox"></a>  CMFCRibbonCheckBox::CMFCRibbonCheckBox

Konstruktor obiektu pola wyboru wstążki

```
CMFCRibbonCheckBox(
    UINT nID,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
[in] Określa identyfikator polecenia.

*lpszText*<br/>
[in] Określa etykietę tekstową.

### <a name="return-value"></a>Wartość zwracana

Tworzy obiekt pola wyboru wstążki.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCRibbonCheckBox` klasy.

[!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]

##  <a name="getcompactsize"></a>  CMFCRibbonCheckBox::GetCompactSize

W przypadku przesłonięcia pobiera compact rozmiar pola wyboru.

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do przechwytywania zmian danych skojarzony z polem wyboru.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CSize` obiekt, który zawiera compact rozmiar pola wyboru.

### <a name="remarks"></a>Uwagi

Jeśli nie zostanie zastąpiona, zwraca wartość pośredni rozmiar pola wyboru.

##  <a name="getintermediatesize"></a>  CMFCRibbonCheckBox::GetIntermediateSize

Pobiera pośrednich rozmiar pola wyboru.

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do przechwytywania zmian danych skojarzonych z tego pola wyboru.

### <a name="return-value"></a>Wartość zwracana

A `CSize` obiekt zawierający pośredni rozmiar pola wyboru.

### <a name="remarks"></a>Uwagi

Jeśli nie zostanie zastąpiona, oblicza rozmiar pośrednich jako domyślny rozmiar pola wyboru ( `AFX_CHECK_BOX_DEFAULT_SIZE`) oraz rozmiar tekstu, a także marginesy.

##  <a name="getregularsize"></a>  CMFCRibbonCheckBox::GetRegularSize

Pobiera zwykłego rozmiaru pola wyboru.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do obiektu przechwytywania zmian danych skojarzonych z tego pola wyboru.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CSize` obiekt, który zawiera zwykłego rozmiaru pola wyboru.

### <a name="remarks"></a>Uwagi

Jeśli nie zostanie zastąpiona, zwraca wartość pośredni rozmiar pola wyboru.

##  <a name="isdrawtooltipimage"></a>  CMFCRibbonCheckBox::IsDrawTooltipImage

Wskazuje, czy obraz etykietki narzędzia, skojarzony z polem wyboru.

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli skojarzony z polem wyboru lub wartość FALSE, jeśli nie ma obrazu etykietki narzędzia.

### <a name="remarks"></a>Uwagi

##  <a name="ondraw"></a>  CMFCRibbonCheckBox::OnDraw

Metoda wywoływana przez platformę, by narysować pole wyboru przy użyciu kontekstu określonego urządzenia.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do przechwytywania zmian danych, w której ma zostać Rysuj pole wyboru.

### <a name="remarks"></a>Uwagi

##  <a name="ondrawmenuimage"></a>  CMFCRibbonCheckBox::OnDrawMenuImage

Metoda wywoływana przez platformę, by narysować obraz menu dla tego pola wyboru.

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>Parametry

[in] *Przechwytywania zmian danych&#42;*<br/>
Wskaźnik do przechwytywania zmian danych skojarzony z polem wyboru.

*CRect*<br/>
[in] A `CRect` określający prostokąta do rysowania obraz menu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli obraz, który został wystawiony, lub FAŁSZ, jeśli nie.

### <a name="remarks"></a>Uwagi

Zwraca wartość FAŁSZ, jeśli nie zostanie zastąpiona.

##  <a name="ondrawonlist"></a>  CMFCRibbonCheckBox::OnDrawOnList

Metoda wywoływana przez platformę, by narysować pole wyboru w polu listy poleceń.

```
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do kontekstu urządzenia, w której ma zostać Rysuj pole wyboru.

*strText*<br/>
[in] Tekst wyświetlany.

*nTextOffset*<br/>
[in] Odległość w pikselach, po lewej stronie pola listy do wyświetlania tekstu.

*Rect*<br/>
[in] Prostokąt wyświetlana dla tego pola wyboru.

*bIsSelected*<br/>
[in] Wartość TRUE, jeśli pole nie zostanie wybrane, lub FAŁSZ, jeśli nie.

*bHighlighted*<br/>
[in] Wartość TRUE, jeśli pole wyboru jest wyróżniony, lub FAŁSZ, jeśli nie.

### <a name="remarks"></a>Uwagi

##  <a name="setaccdata"></a>  CMFCRibbonCheckBox::SetACCData

Ustawia dane ułatwień dostępu dla tego pola wyboru.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
Okno nadrzędne pola wyboru.

*Dane*<br/>
Dane ułatwień dostępu dla tego pola wyboru.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda ustawia dane ułatwień dostępu dla tego pola wyboru i zawsze zwraca wartość PRAWDA. Zastępuje tę metodę do zestawu danych ułatwień dostępu i zwracają wartość, która wskazuje powodzenie lub niepowodzenie.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)
