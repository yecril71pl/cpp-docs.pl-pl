---
title: Klasa CMFCRibbonStatusBarPane
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsExtended
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnDrawBorder
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFillBackground
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAnimationList
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StartAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StopAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFinishAnimation
helpviewer_keywords:
- CMFCRibbonStatusBarPane [MFC], CMFCRibbonStatusBarPane
- CMFCRibbonStatusBarPane [MFC], GetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], GetTextAlign
- CMFCRibbonStatusBarPane [MFC], IsAnimation
- CMFCRibbonStatusBarPane [MFC], IsExtended
- CMFCRibbonStatusBarPane [MFC], OnDrawBorder
- CMFCRibbonStatusBarPane [MFC], OnFillBackground
- CMFCRibbonStatusBarPane [MFC], SetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], SetAnimationList
- CMFCRibbonStatusBarPane [MFC], SetTextAlign
- CMFCRibbonStatusBarPane [MFC], StartAnimation
- CMFCRibbonStatusBarPane [MFC], StopAnimation
- CMFCRibbonStatusBarPane [MFC], OnFinishAnimation
ms.assetid: 5d034c3c-ecca-4267-b88c-0f55a2884dd0
ms.openlocfilehash: 554b9fe364c6a213e038416a605c17cdd4f8e7d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368798"
---
# <a name="cmfcribbonstatusbarpane-class"></a>Klasa CMFCRibbonStatusBarPane

Klasa `CMFCRibbonStatusBarPane` implementuje element wstążki, który można dodać do paska stanu wstążki.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonStatusBarPane : public CMFCRibbonButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane](#cmfcribbonstatusbarpane)|Konstruuje i inicjuje `CMFCRibbonStatusBarPane` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::GetAlmostLargeText](#getalmostlargetext)|Zwraca ciąg definiujący najdłuższy ciąg tekstowy, który może być wyświetlany w okienku bez obcinania.|
|[CMFCRibbonStatusBarPane::GetTextAlign](#gettextalign)|Zwraca bieżące ustawienie wyrównania tekstu.|
|[CMFCRibbonStatusBarPane::IsAnimation](#isanimation)|Określa, czy animacja jest w toku.|
|[CMFCRibbonStatusBarPane::Rozszerzenie](#isextended)|Określa, czy okienko znajduje się w rozszerzonym obszarze paska stanu wstążki.|
|[CMFCRibbonStatusBarPane::OnDrawBorder](#ondrawborder)|(Zastępuje [CMFCRibbonButton::OnDrawBorder](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder).)|
|[CMFCRibbonStatusBarPane::OnFillBackground](#onfillbackground)|(Zastępuje [CMFCRibbonButton::OnFillBackground](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground).)|
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](#setalmostlargetext)|Definiuje najdłuższy ciąg tekstowy, który może być wyświetlany w okienku bez obcinania.|
|[CMFCRibbonStatusBarPane::SetAnimationList](#setanimationlist)|Przypisuje do okienka listę obrazów, która może służyć do animacji.|
|[CMFCRibbonStatusBarPane::SetTextAlign](#settextalign)|Ustawia wyrównanie tekstu.|
|[CMFCRibbonStatusBarPane::StartAnimation](#startanimation)|Uruchamia animację przypisaną do okienka.|
|[CMFCRibbonStatusBarPane::StopAnimation](#stopanimation)|Zatrzymuje animację przypisaną do okienka. .|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::OnFinishAnimation](#onfinishanimation)|Wywoływana przez platformę, gdy animacja, która jest przypisana do okienka zatrzymuje.|

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCRibbonStatusBarPane` używać różnych metod w klasie. W przykładzie pokazano, `CMFCRibbonStatusBarPane` jak skonstruować obiekt, ustawić wyrównanie tekstu etykiety okienka paska stanu, zdefiniować najdłuższy tekst, który może być wyświetlany w okienku paska stanu bez obcinania, dołączyć do paska stanu listę obrazów, które mogą być używane do animacji, i rozpocząć animację.

[!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribbonstatusbarpane.h

## <a name="cmfcribbonstatusbarpanecmfcribbonstatusbarpane"></a><a name="cmfcribbonstatusbarpane"></a>CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane

Konstruuj obiekt okienka na pasku stanu.

```
CMFCRibbonStatusBarPane(
    UINT nCmdID,
    LPCTSTR lpszText,
    BOOL bIsStatic=FALSE,
    HICON hIcon=NULL,
    LPCTSTR lpszAlmostLargeText=NULL);

CMFCRibbonStatusBarPane(
    UINT nCmdID,
    LPCTSTR lpszText,
    HBITMAP hBmpAnimationList,
    int cxAnimation=16,
    COLORREF clrTrnsp=RGB(192,192 1,192) 1,
    HICON hIcon=NULL,
    BOOL bIsStatic=FALSE);

CMFCRibbonStatusBarPane(
    UINT nCmdID,
    LPCTSTR lpszText,
    UINT uiAnimationListResID,
    int cxAnimation=16,
    COLORREF clrTrnsp=RGB(192, 192 1, 192) 1,
    HICON hIcon=NULL,
    BOOL bIsStatic=FALSE);
```

### <a name="parameters"></a>Parametry

*nCmdID (identyfikator nCmdID)*<br/>
[w] Określa identyfikator polecenia okienka.

*lpszText (tekst)*<br/>
[w] Określa ciąg tekstowy, który ma być wyświetlany w okienku.

*bJsStatic*<br/>
[w] Jeśli prawda, nie można wyróżnić ani wybrać okienka stanu, klikając go.

*hIcon (własówce)*<br/>
[w] Określa uchwyt do ikony, która ma być wyświetlana w okienku.

*lpszAlmostLargeText*<br/>
[w] Określa najdłuższy ciąg tekstowy, który może być wyświetlany w okienku.

*lista zwierząt hBmp*<br/>
[w] Określa dojście do listy obrazów, która jest używana do animacji.

*cxAnimacja*<br/>
[w] Określa szerokość w pikselach ikony na liście obrazów używanej do animacji.

*clrTrnsp (clrTrnsp)*<br/>
[w] Określa przezroczysty kolor obrazów na liście obrazów, które są używane do animacji.

*uiAnimationListResID*<br/>
[w] Określa identyfikator zasobu listy obrazów, która jest używana do animacji.

## <a name="cmfcribbonstatusbarpanegetalmostlargetext"></a><a name="getalmostlargetext"></a>CMFCRibbonStatusBarPane::GetAlmostLargeText

Pobiera najdłuższy ciąg tekstowy, który może być wyświetlany w okienku paska stanu.

```
LPCTSTR GetAlmostLargeText() const;
```

### <a name="return-value"></a>Wartość zwracana

Najdłuższy ciąg tekstowy, który może być wyświetlany w okienku paska stanu.

## <a name="cmfcribbonstatusbarpanegettextalign"></a><a name="gettextalign"></a>CMFCRibbonStatusBarPane::GetTextAlign

Pobiera bieżące ustawienie wyrównanie tekstu etykiety okienka paska stanu.

```
int GetTextAlign() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżące wyrównanie tekstu, które może być jedną z następujących czynności:

- TA_LEFT

- TA_CENTER

- TA_RIGHT.

## <a name="cmfcribbonstatusbarpaneisanimation"></a><a name="isanimation"></a>CMFCRibbonStatusBarPane::IsAnimation

Określa, czy animacja jest w toku.

```
BOOL IsAnimation() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli animacja jest w toku; FAŁSZ inaczej.

## <a name="cmfcribbonstatusbarpaneisextended"></a><a name="isextended"></a>CMFCRibbonStatusBarPane::Rozszerzenie

Określ, czy okienko znajduje się w rozszerzonym obszarze paska stanu wstążki.

```
BOOL IsExtended() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okienko znajduje się na pasku stanu rozszerzonym obszarze. FAŁSZ inaczej.

## <a name="cmfcribbonstatusbarpaneondrawborder"></a><a name="ondrawborder"></a>CMFCRibbonStatusBarPane::OnDrawBorder

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
virtual void OnDrawBorder(CDC*);
```

### <a name="parameters"></a>Parametry

[w] *&#42;CDC*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonstatusbarpaneonfillbackground"></a><a name="onfillbackground"></a>CMFCRibbonStatusBarPane::OnFillBackground

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
virtual COLORREF OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[w] *pDC*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonstatusbarpaneonfinishanimation"></a><a name="onfinishanimation"></a>CMFCRibbonStatusBarPane::OnFinishAnimation

Framework wywołuje tę metodę, gdy animacja, która jest przypisana do okienka kończy.

```
virtual void OnFinishAnimation();
```

### <a name="remarks"></a>Uwagi

`StopAnimation`metoda wywołuje `OnFinishAnimation` metodę, której można użyć do oczyszczenia danych po zakończeniu animacji.

## <a name="cmfcribbonstatusbarpanesetalmostlargetext"></a><a name="setalmostlargetext"></a>CMFCRibbonStatusBarPane::SetAlmostLargeText

Zdefiniuj najdłuższy tekst, który może być wyświetlany w okienku paska stanu bez obcinania.

```
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```

### <a name="parameters"></a>Parametry

*lpszAlmostLargeText*<br/>
[w] Określa najdłuższy ciąg, który może być wyświetlany na pasku stanu bez obcinania.

### <a name="remarks"></a>Uwagi

Biblioteka oblicza rozmiar tekstu, który *lpszAlmostLargeText* określa i odpowiednio rozmiary okienka. Tekst zostanie obcięty, jeśli nadal nie mieści się w okienku.

## <a name="cmfcribbonstatusbarpanesetanimationlist"></a><a name="setanimationlist"></a>CMFCRibbonStatusBarPane::SetAnimationList

Dołącza do okienka paska stanu listę obrazów, która może służyć do animacji.

```
void SetAnimationList(
    HBITMAP hBmpAnimationList,
    int cxAnimation=16,
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);

BOOL SetAnimationList(
    UINT uiAnimationListResID,
    int cxAnimation=16,
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);
```

### <a name="parameters"></a>Parametry

*lista zwierząt hBmp*<br/>
[w] Określa dojście do listy obrazów.

*cxAnimacja*<br/>
[w] Określa szerokość ramki na liście obrazów w pikselach.

*clrTransp (tłumaczenie kl./s)*<br/>
[w] Określa przezroczysty kolor listy obrazów.

*uiAnimationListResID*<br/>
[w] Określa identyfikator zasobu listy obrazów.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli lista obrazów została pomyślnie dołączona do okienka paska stanu; FAŁSZ inaczej.

## <a name="cmfcribbonstatusbarpanesettextalign"></a><a name="settextalign"></a>CMFCRibbonStatusBarPane::SetTextAlign

Ustawia wyrównanie tekstu etykiety okienka paska stanu.

```
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>Parametry

*nZłańczyć*<br/>
[w] Określa wyrównanie tekstu.

### <a name="remarks"></a>Uwagi

*nAlign* może mieć jedną z następujących wartości:

- TA_LEFT: wyrównanie w lewo

- TA_CENTER: wyrównanie środka

- TA_RIGHT: wyrównanie w prawo

## <a name="cmfcribbonstatusbarpanestartanimation"></a><a name="startanimation"></a>CMFCRibbonStatusBarPane::StartAnimation

Uruchamia animację przypisaną do okienka.

```
void StartAnimation(
    UINT nFrameDelay=500,
    UINT nDuration=-1);
```

### <a name="parameters"></a>Parametry

*nFrameDelay ( nFrameDelay )*<br/>
[w] Określa liczbę klatek na sekundę animacji w milisekundach.

*nDuration*<br/>
[w] Określa, jak długo animacja ma być odtwarzana w milisekundach. Użyj -1 dla nieskończonej pętli.

### <a name="remarks"></a>Uwagi

Przed wywołaniem `StartAnimation` za pomocą programu `SetAnimationList`.

## <a name="cmfcribbonstatusbarpanestopanimation"></a><a name="stopanimation"></a>CMFCRibbonStatusBarPane::StopAnimation

Zatrzymuje animację przypisaną do okienka paska stanu.

```
void StopAnimation();
```

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[Klasa CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)
