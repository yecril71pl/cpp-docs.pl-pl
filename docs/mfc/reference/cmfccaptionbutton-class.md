---
title: Klasa CMFCCaptionButton
ms.date: 11/04/2016
f1_keywords:
- CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetHit
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetIconID
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetRect
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetSize
- AFXCAPTIONBUTTON/CMFCCaptionButton::IsMiniFrameButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::Move
- AFXCAPTIONBUTTON/CMFCCaptionButton::OnDraw
- AFXCAPTIONBUTTON/CMFCCaptionButton::SetMiniFrameButton
helpviewer_keywords:
- CMFCCaptionButton [MFC], CMFCCaptionButton
- CMFCCaptionButton [MFC], GetHit
- CMFCCaptionButton [MFC], GetIconID
- CMFCCaptionButton [MFC], GetRect
- CMFCCaptionButton [MFC], GetSize
- CMFCCaptionButton [MFC], IsMiniFrameButton
- CMFCCaptionButton [MFC], Move
- CMFCCaptionButton [MFC], OnDraw
- CMFCCaptionButton [MFC], SetMiniFrameButton
ms.assetid: c5774b38-c0dd-414a-9ede-3b2f78f233ec
ms.openlocfilehash: 1b0a999f1fd1e3df1b0a971220454397cead02a9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752597"
---
# <a name="cmfccaptionbutton-class"></a>Klasa CMFCCaptionButton

Klasa `CMFCCaptionButton` implementuje przycisk, który jest wyświetlany na pasku podpisu dla okienka dokowania lub okna mini-ramki. Zazwyczaj struktura tworzy przyciski podpisu automatycznie.

## <a name="syntax"></a>Składnia

```
class CMFCCaptionButton : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|Nazwa|Opis|
|----------|-----------------|
|[CMFCCaptionButton::CMFCCaptionButton](#cmfccaptionbutton)|Konstruuje obiekt CMFCCaptionButton.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCCaptionButton::GetHit](#gethit)|Zwraca polecenie reprezentowane przez przycisk.|
|[CMFCCaptionButton::GetIconID](#geticonid)|Zwraca identyfikator obrazu skojarzony z przyciskiem.|
|[CMFCCaptionButton::GetRect](#getrect)|Zwraca prostokąt zajmowany przez przycisk.|
|[CMFCCaptionButton::GetSize](#getsize)|Zwraca szerokość i wysokość przycisku.|
|[CMFCCaptionButton::IsMiniFrameButton](#isminiframebutton)|Wskazuje, czy wysokość paska tytułu jest ustawiona na mini rozmiar.|
|[CMFCCaptionButton::Przenieś](#move)|Ustawia lokalizację rysowania przycisków i stan pokazu okna.|
|[CMFCCaptionButton::OnDraw](#ondraw)|Rysuje przycisk podpisu.|
|[CMFCCaptionButton::SetMiniFrameButton](#setminiframebutton)|Ustawia mini rozmiar paska tytułu.|

## <a name="remarks"></a>Uwagi

Klasę można wyprowadzić z [klasy CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) i użyć `AddButton`metody chronionej , aby dodać przyciski podpisu do okna mini ramki.

CPaneFrameWnd.h definiuje identyfikatory poleceń dla dwóch typów przycisków podpisu:

- AFX_CAPTION_BTN_PIN, który wyświetla przycisk pin, gdy okienko dokowania obsługuje tryb automatycznego ukrywania.

- AFX_CAPTION_BTN_CLOSE, który wyświetla przycisk **Zamknij,** gdy okienko może zostać zamknięte lub ukryte.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak skonstruować `CMFCCaptionButton` obiekt i ustawić mini rozmiar paska tytułu.

[!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CmfcCaptionButton (Przycisk CMFCCaption)](../../mfc/reference/cmfccaptionbutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcaptionbutton.h

## <a name="cmfccaptionbuttoncmfccaptionbutton"></a><a name="cmfccaptionbutton"></a>CMFCCaptionButton::CMFCCaptionButton

Konstruuje `CMFCCaptionButton` obiekt.

```
CMFCCaptionButton();

CMFCCaptionButton(
    UINT nHit,
    BOOL bLeftAlign = FALSE);
```

### <a name="parameters"></a>Parametry

*nHit*<br/>
[w] Polecenie skojarzone z przyciskiem.

*bUchołka*<br/>
[w] Określa, czy przycisk jest wyrównany do lewej.

W poniższej tabeli wymieniono możliwe wartości parametru *nHit.*

|Wartość|Polecenie|
|-----------|-------------|
|AFX_HTCLOSE|Zamknij przycisk.|
|HTMINBUTTON ( HTMINBUTTON )|Przycisk Minimalizuj.|
|HTMAXBUTTON ( HTMAXBUTTON )|Przycisk Maksymalizuj.|
|AFX_HTLEFTBUTTON|Strzałka w lewo.|
|AFX_HTRIGHTBUTTON|Strzałka w prawo.|
|AFX_HTMENU|Przycisk menu strzałki w dół.|
|HTNOWHERE|Wartość domyślna; reprezentuje brak polecenia.|

### <a name="remarks"></a>Uwagi

Domyślnie przyciski podpisu nie są skojarzone z poleceniem.

Przyciski podpisu są wyrównane po prawej lub lewej stronie.

## <a name="cmfccaptionbuttongethit"></a><a name="gethit"></a>CMFCCaptionButton::GetHit

Zwraca polecenie reprezentowane przez przycisk.

```
UINT GetHit() const;
```

### <a name="return-value"></a>Wartość zwracana

Polecenie reprezentowane przez przycisk.

W poniższej tabeli wymieniono możliwe wartości zwracane.

|Wartość|Polecenie|
|-----------|-------------|
|AFX_HTCLOSE|Zamknij przycisk.|
|HTMINBUTTON ( HTMINBUTTON )|Przycisk Minimalizuj.|
|HTMAXBUTTON ( HTMAXBUTTON )|Przycisk Maksymalizuj.|
|AFX_HTLEFTBUTTON|Strzałka w lewo.|
|AFX_HTRIGHTBUTTON|Strzałka w prawo.|
|AFX_HTMENU|Przycisk menu strzałki w dół.|
|HTNOWHERE|Wartość domyślna; reprezentuje brak polecenia.|

## <a name="cmfccaptionbuttongeticonid"></a><a name="geticonid"></a>CMFCCaptionButton::GetIconID

Zwraca identyfikator obrazu skojarzony z przyciskiem.

```
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,
    BOOL bMaximized = FALSE) const;
```

### <a name="parameters"></a>Parametry

*Bhorz*<br/>
[w] PRAWDA dla identyfikatorów obrazów ze strzałką w lewo lub w prawo; FAŁSZ dla identyfikatorów obrazów strzałki w górę lub w dół.

*bMaximized*<br/>
[w] PRAWDA dla maksymalizacji identyfikatora obrazu; FAŁSZ dla zminimalizowania identyfikatora obrazu.

### <a name="return-value"></a>Wartość zwracana

Identyfikator obrazu.

### <a name="remarks"></a>Uwagi

Parametry określają identyfikatory obrazów, aby zminimalizować lub zmaksymalizować przyciski podpisów.

## <a name="cmfccaptionbuttongetrect"></a><a name="getrect"></a>CMFCCaptionButton::GetRect

Zwraca prostokąt zajmowany przez przycisk.

```
virtual CRect GetRect() const;
```

### <a name="return-value"></a>Wartość zwracana

Prostokąt reprezentujący lokalizację przycisku.

### <a name="remarks"></a>Uwagi

Jeśli nie widać przycisku, zwrócony rozmiar wynosi 0.

## <a name="cmfccaptionbuttongetsize"></a><a name="getsize"></a>CMFCCaptionButton::GetSize

Zwraca szerokość i wysokość przycisku.

```
static CSize GetSize();
```

### <a name="return-value"></a>Wartość zwracana

Zewnętrzne wymiary przycisku.

### <a name="remarks"></a>Uwagi

Zwrócony rozmiar zawiera margines przycisku i obramowanie.

## <a name="cmfccaptionbuttonisminiframebutton"></a><a name="isminiframebutton"></a>CMFCCaptionButton::IsMiniFrameButton

Wskazuje, czy wysokość paska tytułu jest ustawiona na mini rozmiar.

```
BOOL IsMiniFrameButton() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli podpis jest ustawiony na mini rozmiar; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfccaptionbuttonmove"></a><a name="move"></a>CMFCCaptionButton::Przenieś

Ustawia lokalizację rysowania przycisków i stan pokazu okna.

```cpp
void Move(
    const CPoint& ptTo,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

*ptTo*<br/>
[w] Nowa lokalizacja.

*bHide (ur.*<br/>
[w] Czy chcesz wyświetlić przycisk.

## <a name="cmfccaptionbuttonondraw"></a><a name="ondraw"></a>CMFCCaptionButton::OnDraw

Rysuje przycisk podpisu.

```
virtual void OnDraw(
    CDC* pDC,
    BOOL bActive,
    BOOL bHorz = TRUE,
    BOOL bMaximized = TRUE,
    BOOL bDisabled = FALSE);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia dla przycisku.

*bAktywny*<br/>
[w] Czy narysować aktywny obraz przycisku.

*Bhorz*<br/>
[w] Zarezerwowane do użycia w klasie pochodnej.

*bMaximized*<br/>
[w] Czy narysować zmaksymalizowany obraz przycisku.

*bWydaj*<br/>
[w] Czy narysować włączony obraz przycisku.

### <a name="remarks"></a>Uwagi

*BMaximized* parametr jest używany, gdy przycisk jest przycisk maksymalizacji lub zminimalizowania.

## <a name="cmfccaptionbuttonsetminiframebutton"></a><a name="setminiframebutton"></a>CMFCCaptionButton::SetMiniFrameButton

Ustawia mini rozmiar paska tytułu.

```cpp
void SetMiniFramebutton(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parametry

*bStaw*<br/>
[w] PRAWDA dla wysokości mini paska tytułu; FAŁSZ dla domyślnej wysokości paska tytułu.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)<br/>
[Klasa CDockablePane](../../mfc/reference/cdockablepane-class.md)
