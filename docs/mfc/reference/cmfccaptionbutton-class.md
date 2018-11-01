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
ms.openlocfilehash: 4fa9d6a57cb2ee70e9da7853954241955d724a5c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604305"
---
# <a name="cmfccaptionbutton-class"></a>Klasa CMFCCaptionButton

`CMFCCaptionButton` Klasa implementuje przycisk, który jest wyświetlany na pasku podpisu dla okienka dokowania lub okna mini ramki. Typowo szablon tworzy przyciski podpisu automatycznie.

## <a name="syntax"></a>Składnia

```
class CMFCCaptionButton : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|Nazwa|Opis|
|----------|-----------------|
|[CMFCCaptionButton::CMFCCaptionButton](#cmfccaptionbutton)|Tworzy obiekt CMFCCaptionButton.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCCaptionButton::GetHit](#gethit)|Zwraca polecenie reprezentowane przez przycisk.|
|[CMFCCaptionButton::GetIconID](#geticonid)|Zwraca identyfikator obrazu skojarzonego z przyciskiem.|
|[CMFCCaptionButton::GetRect](#getrect)|Zwraca prostokąt zajmowane przez przycisk.|
|[CMFCCaptionButton::GetSize](#getsize)|Zwraca szerokość i wysokość przycisku.|
|[CMFCCaptionButton::IsMiniFrameButton](#isminiframebutton)|Wskazuje, czy rozmiar mini jest równa wysokość paska tytułu.|
|[CMFCCaptionButton::Move](#move)|Określa przycisk rysowania lokalizacji i okno Pokaż stan.|
|[CMFCCaptionButton::OnDraw](#ondraw)|Rysuje przycisk paska tytułowego.|
|[CMFCCaptionButton::SetMiniFrameButton](#setminiframebutton)|Określa rozmiar podręczny pasek tytułu.|

## <a name="remarks"></a>Uwagi

Można wyprowadzić klasę z [klasa CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) i użyć metody chronionej `AddButton`, aby dodać przyciski podpisu do okna mini ramki.

CPaneFrameWnd.h definiuje identyfikatory poleceń dla dwóch typów przyciski podpisu:

- AFX_CAPTION_BTN_PIN, zawierające przycisk przypinania, gdy okienko dokowania obsługuje trybie autoukrywania.

- AFX_CAPTION_BTN_CLOSE, który wyświetla **Zamknij** przycisku w okienku można zamknąć lub ukryte.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób tworzenia `CMFCCaptionButton` obiektu oraz ustawić wielkość mini paska tytułu.

[!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcaptionbutton.h

##  <a name="cmfccaptionbutton"></a>  CMFCCaptionButton::CMFCCaptionButton

Konstruuje `CMFCCaptionButton` obiektu.

```
CMFCCaptionButton();

CMFCCaptionButton(
    UINT nHit,
    BOOL bLeftAlign = FALSE);
```

### <a name="parameters"></a>Parametry

*nHit*<br/>
[in] Polecenie skojarzone z nim.

*bLeftAlign*<br/>
[in] Określa, czy przycisk jest wyrównany do lewej.

Poniższa tabela zawiera listę możliwych wartości dla *nHit* parametru.

|Wartość|Polecenie|
|-----------|-------------|
|AFX_HTCLOSE|Przycisk Zamknij.|
|HTMINBUTTON|Minimize — przycisk.|
|HTMAXBUTTON|Przycisk maksymalizacji.|
|AFX_HTLEFTBUTTON|Przycisk strzałki w lewo.|
|AFX_HTRIGHTBUTTON|Przycisk strzałki w prawo.|
|AFX_HTMENU|Naciśnięty przycisk strzałki w menu.|
|HTNOWHERE|Wartością domyślną; reprezentuje żadne polecenie.|

### <a name="remarks"></a>Uwagi

Domyślnie przyciski podpisu nie są skojarzone z poleceniem.

Przyciski podpisu są wyrównane w prawo lub lewo.

##  <a name="gethit"></a>  CMFCCaptionButton::GetHit

Zwraca polecenie reprezentowane przez przycisk.

```
UINT GetHit() const;
```

### <a name="return-value"></a>Wartość zwracana

Polecenie reprezentowane przez przycisk.

Poniższa tabela zawiera listę możliwych wartości zwracanych.

|Wartość|Polecenie|
|-----------|-------------|
|AFX_HTCLOSE|Przycisk Zamknij.|
|HTMINBUTTON|Minimize — przycisk.|
|HTMAXBUTTON|Przycisk maksymalizacji.|
|AFX_HTLEFTBUTTON|Przycisk strzałki w lewo.|
|AFX_HTRIGHTBUTTON|Przycisk strzałki w prawo.|
|AFX_HTMENU|Naciśnięty przycisk strzałki w menu.|
|HTNOWHERE|Wartością domyślną; reprezentuje żadne polecenie.|

##  <a name="geticonid"></a>  CMFCCaptionButton::GetIconID

Zwraca identyfikator obrazu skojarzonego z przyciskiem.

```
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,
    BOOL bMaximized = FALSE) const;
```

### <a name="parameters"></a>Parametry

*bHorz*<br/>
[in] Wartość TRUE dla obrazu Strzałka w lewo lub w prawo identyfikatory; Wartość FALSE dla w górę lub dół obrazu strzałkę identyfikatorów.

*bMaximized*<br/>
[in] Wartość TRUE dla Identyfikatora obrazu Maksymalizuj; Wartość FALSE dla identyfikatora Minimalizuj obrazu.

### <a name="return-value"></a>Wartość zwracana

Identyfikator obrazu.

### <a name="remarks"></a>Uwagi

Parametry określ identyfikatory obrazu dla minimalizacji lub zmaksymalizować przyciski podpisu.

##  <a name="getrect"></a>  CMFCCaptionButton::GetRect

Zwraca prostokąt zajmowane przez przycisk.

```
virtual CRect GetRect() const;
```

### <a name="return-value"></a>Wartość zwracana

Prostokąt, który reprezentuje lokalizację przycisku.

### <a name="remarks"></a>Uwagi

Jeśli nie widzisz przycisku, rozmiar zwrócony to 0.

##  <a name="getsize"></a>  CMFCCaptionButton::GetSize

Zwraca szerokość i wysokość przycisku.

```
static CSize GetSize();
```

### <a name="return-value"></a>Wartość zwracana

Zewnętrzne wymiary przycisku.

### <a name="remarks"></a>Uwagi

Rozmiar zwrócony obejmuje margines przycisku i obramowanie.

##  <a name="isminiframebutton"></a>  CMFCCaptionButton::IsMiniFrameButton

Wskazuje, czy rozmiar mini jest równa wysokość paska tytułu.

```
BOOL IsMiniFrameButton() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli podpis jest równa mini rozmiaru. w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="move"></a>  CMFCCaptionButton::Move

Określa przycisk rysowania lokalizacji i okno Pokaż stan.

```
void Move(
    const CPoint& ptTo,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

*ptTo*<br/>
[in] Nowa lokalizacja.

*bHide*<br/>
[in] Określa, czy wyświetlać przycisk.

##  <a name="ondraw"></a>  CMFCCaptionButton::OnDraw

Rysuje przycisk paska tytułowego.

```
virtual void OnDraw(
    CDC* pDC,
    BOOL bActive,
    BOOL bHorz = TRUE,
    BOOL bMaximized = TRUE,
    BOOL bDisabled = FALSE);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do kontekstu urządzenia dla przycisku.

*bWykonywanie aktywnych*<br/>
[in] Określa, czy rysować obraz z aktywnego przycisku.

*bHorz*<br/>
[in] Zarezerwowany do użytku w klasie pochodnej.

*bMaximized*<br/>
[in] Określa, czy rysować obraz przycisku w trybie zmaksymalizowanym.

*bWyłączone*<br/>
[in] Określa, czy rysować obraz z aktywny przycisk.

### <a name="remarks"></a>Uwagi

*BMaximized* parametr jest używany, gdy przycisk ma Maksymalizuj lub minimize — przycisk.

##  <a name="setminiframebutton"></a>  CMFCCaptionButton::SetMiniFrameButton

Określa rozmiar podręczny pasek tytułu.

```
void SetMiniFramebutton(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parametry

*bUstawienie*<br/>
[in] Wartość TRUE dla wysokość paska tytułu mini; Wartość FALSE dla domyślna wysokość paska tytułu.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)<br/>
[Klasa CDockablePane](../../mfc/reference/cdockablepane-class.md)
