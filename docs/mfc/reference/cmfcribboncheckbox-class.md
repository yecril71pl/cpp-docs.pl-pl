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
ms.openlocfilehash: a8048f860a2cce75c37a065cfdd2751141054f1b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446242"
---
# <a name="cmfcribboncheckbox-class"></a>Klasa CMFCRibbonCheckBox

Klasa `CMFCRibbonCheckBox` implementuje pole wyboru, które można dodać do panelu wstążki, paska narzędzi Szybki dostęp lub menu podręcznego.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonCheckBox : public CMFCRibbonButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|(Przesłania [CMFCRibbonButton:: GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|(Przesłania [CMFCRibbonButton:: GetIntermediateSize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize).)|
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|(Przesłania [CMFCRibbonButton:: GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|(Przesłania `CMFCRibbonButton::IsDrawTooltipImage`).|
|[CMFCRibbonCheckBox:: OnDraw](#ondraw)|(Przesłania [CMFCRibbonButton:: OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(Przesłania [CMFCRibbonBaseElement:: OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|(Przesłania `CMFCRibbonButton::OnDrawOnList`).|
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|(Przesłania [CMFCRibbonButton:: SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|

## <a name="remarks"></a>Uwagi

Aby użyć `CMFCRibbonCheckBox` w aplikacji, Dodaj następujący Konstruktor do kodu:

```
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)
```

gdzie *NID* to pole wyboru ID polecenia i *lpszText* jest etykietą tekstu pola wyboru.

Możesz dodać pole wyboru do panelu wstążki przy użyciu [CMFCRibbonPanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribboncheckbox. h

##  <a name="cmfcribboncheckbox"></a>CMFCRibbonCheckBox::CMFCRibbonCheckBox

Konstruktor obiektu pola wyboru wstążki

```
CMFCRibbonCheckBox(
    UINT nID,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
podczas Określa identyfikator polecenia.

*lpszText*<br/>
podczas Określa etykietę tekstową.

### <a name="return-value"></a>Wartość zwracana

Konstruuje obiekt pola wyboru wstążki.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób konstruowania obiektu klasy `CMFCRibbonCheckBox`.

[!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]

##  <a name="getcompactsize"></a>CMFCRibbonCheckBox::GetCompactSize

Gdy jest zastępowany, pobiera rozmiar kompaktowy pola wyboru.

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
podczas Wskaźnik do ramki przechwytywania skojarzonej z tym polem wyboru.

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt `CSize`, który zawiera rozmiar kompaktowy pola wyboru.

### <a name="remarks"></a>Uwagi

Jeśli nie zostanie zastąpiony, zwraca pośredni rozmiar pola wyboru.

##  <a name="getintermediatesize"></a>CMFCRibbonCheckBox::GetIntermediateSize

Pobiera pośredni rozmiar pola wyboru.

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
podczas Wskaźnik do ramki przechwytywania skojarzonej z tym polem wyboru.

### <a name="return-value"></a>Wartość zwracana

Obiekt `CSize` zawierający pośredni rozmiar pola wyboru.

### <a name="remarks"></a>Uwagi

Jeśli nie zostanie zastąpiony, program oblicza rozmiar pośredni jako domyślny rozmiar pola wyboru (`AFX_CHECK_BOX_DEFAULT_SIZE`), a rozmiar tekstu oraz marginesy.

##  <a name="getregularsize"></a>CMFCRibbonCheckBox::GetRegularSize

Pobiera zwykły rozmiar pola wyboru.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
podczas Wskaźnik do obiektu przerzutowania skojarzonego z tym polem wyboru.

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt `CSize`, który zawiera zwykły rozmiar pola wyboru.

### <a name="remarks"></a>Uwagi

Jeśli nie zostanie zastąpiony, zwraca pośredni rozmiar pola wyboru.

##  <a name="isdrawtooltipimage"></a>CMFCRibbonCheckBox::IsDrawTooltipImage

Wskazuje, czy istnieje obraz etykietki narzędzia skojarzony z tym polem wyboru.

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli istnieje obraz etykietki narzędzia skojarzony z polem wyboru lub wartość FALSE, jeśli nie.

### <a name="remarks"></a>Uwagi

##  <a name="ondraw"></a>CMFCRibbonCheckBox:: OnDraw

Wywoływane przez platformę, by narysować pole wyboru przy użyciu określonego kontekstu urządzenia.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
podczas Wskaźnik do tabeli przestawnej, w której ma zostać narysowane pole wyboru.

### <a name="remarks"></a>Uwagi

##  <a name="ondrawmenuimage"></a>CMFCRibbonCheckBox::OnDrawMenuImage

Wywoływane przez platformę, aby narysować obraz menu dla pola wyboru.

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>Parametry

podczas *Przechwytywanie&#42;*  zmian<br/>
Wskaźnik do ramki przechwytywania skojarzonej z tym polem wyboru.

*CRect*<br/>
podczas Obiekt `CRect` określający prostokąt, w którym ma zostać narysowany obraz menu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli obraz został narysowany, lub FALSE, jeśli nie.

### <a name="remarks"></a>Uwagi

Jeśli nie zostanie zastąpiony, zwraca wartość FALSE.

##  <a name="ondrawonlist"></a>CMFCRibbonCheckBox::OnDrawOnList

Wywoływane przez platformę, aby narysować pole wyboru w polu listy poleceń.

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

*Domeny*<br/>
podczas Wskaźnik do kontekstu urządzenia, w którym ma zostać narysowane pole wyboru.

*strText*<br/>
podczas Wyświetlany tekst.

*nTextOffset*<br/>
podczas Odległość w pikselach od lewej strony pola listy do wyświetlanego tekstu.

*cinania*<br/>
podczas Prostokąt wyświetlania pola wyboru.

*bIsSelected*<br/>
podczas Ma wartość TRUE, jeśli pole wyboru jest zaznaczone, lub wartość FAŁSZ, jeśli nie.

*bHighlighted*<br/>
podczas Ma wartość TRUE, jeśli pole wyboru jest wyróżnione lub ma wartość FAŁSZ, jeśli nie.

### <a name="remarks"></a>Uwagi

##  <a name="setaccdata"></a>CMFCRibbonCheckBox::SetACCData

Ustawia dane dostępności dla pola wyboru.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
Okno nadrzędne pola wyboru.

*Data*<br/>
Dane dostępności dla pola wyboru.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda ustawia dane dostępności dla pola wyboru i zawsze zwraca wartość TRUE. Zastąp tę metodę, aby ustawić dane dostępności i zwrócić wartość wskazującą powodzenie lub niepowodzenie.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)
