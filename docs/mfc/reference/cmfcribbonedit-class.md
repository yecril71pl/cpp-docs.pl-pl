---
title: Klasa CMFCRibbonEdit
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CanBeStretched
- AFXRIBBONEDIT/CMFCRibbonEdit::CopyFrom
- AFXRIBBONEDIT/CMFCRibbonEdit::CreateEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::DestroyCtrl
- AFXRIBBONEDIT/CMFCRibbonEdit::DropDownList
- AFXRIBBONEDIT/CMFCRibbonEdit::EnableSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::GetCompactSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::GetIntermediateSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::GetWidth
- AFXRIBBONEDIT/CMFCRibbonEdit::HasCompactMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasFocus
- AFXRIBBONEDIT/CMFCRibbonEdit::HasLargeMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::IsHighlighted
- AFXRIBBONEDIT/CMFCRibbonEdit::OnAfterChangeRect
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDraw
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawLabelAndImage
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawOnList
- AFXRIBBONEDIT/CMFCRibbonEdit::OnEnable
- AFXRIBBONEDIT/CMFCRibbonEdit::OnHighlight
- AFXRIBBONEDIT/CMFCRibbonEdit::OnKey
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonDown
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonUp
- AFXRIBBONEDIT/CMFCRibbonEdit::OnRTLChanged
- AFXRIBBONEDIT/CMFCRibbonEdit::OnShow
- AFXRIBBONEDIT/CMFCRibbonEdit::Redraw
- AFXRIBBONEDIT/CMFCRibbonEdit::SetACCData
- AFXRIBBONEDIT/CMFCRibbonEdit::SetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::SetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::SetWidth
helpviewer_keywords:
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CanBeStretched
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CopyFrom
- CMFCRibbonEdit [MFC], CreateEdit
- CMFCRibbonEdit [MFC], DestroyCtrl
- CMFCRibbonEdit [MFC], DropDownList
- CMFCRibbonEdit [MFC], EnableSpinButtons
- CMFCRibbonEdit [MFC], GetCompactSize
- CMFCRibbonEdit [MFC], GetEditText
- CMFCRibbonEdit [MFC], GetIntermediateSize
- CMFCRibbonEdit [MFC], GetTextAlign
- CMFCRibbonEdit [MFC], GetWidth
- CMFCRibbonEdit [MFC], HasCompactMode
- CMFCRibbonEdit [MFC], HasFocus
- CMFCRibbonEdit [MFC], HasLargeMode
- CMFCRibbonEdit [MFC], HasSpinButtons
- CMFCRibbonEdit [MFC], IsHighlighted
- CMFCRibbonEdit [MFC], OnAfterChangeRect
- CMFCRibbonEdit [MFC], OnDraw
- CMFCRibbonEdit [MFC], OnDrawLabelAndImage
- CMFCRibbonEdit [MFC], OnDrawOnList
- CMFCRibbonEdit [MFC], OnEnable
- CMFCRibbonEdit [MFC], OnHighlight
- CMFCRibbonEdit [MFC], OnKey
- CMFCRibbonEdit [MFC], OnLButtonDown
- CMFCRibbonEdit [MFC], OnLButtonUp
- CMFCRibbonEdit [MFC], OnRTLChanged
- CMFCRibbonEdit [MFC], OnShow
- CMFCRibbonEdit [MFC], Redraw
- CMFCRibbonEdit [MFC], SetACCData
- CMFCRibbonEdit [MFC], SetEditText
- CMFCRibbonEdit [MFC], SetTextAlign
- CMFCRibbonEdit [MFC], SetWidth
ms.assetid: 9b85f1f2-446b-454e-9af9-104fdad8a897
ms.openlocfilehash: 4f973074fbec3d04b1c1a74852b02ff2564217c1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504948"
---
# <a name="cmfcribbonedit-class"></a>Klasa CMFCRibbonEdit

Implementuje kontrolkę edycji, która znajduje się na pasku wstążki.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonEdit : public CMFCRibbonButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Konstruuje `CMFCRibbonEdit` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonEdit::CanBeStretched](#canbestretched)|Wskazuje, czy wysokość `CMFCRibbonEdit` kontrolki może wzrosnąć w pionie do wysokości wiersza wstążki.|
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Konstruuje `CMFCRibbonEdit` obiekt.|
|[CMFCRibbonEdit::CopyFrom](#copyfrom)|Kopiuje stan określonego `CMFCRibbonEdit` obiektu do bieżącego `CMFCRibbonEdit` obiektu.|
|[CMFCRibbonEdit:: SetEdit](#createedit)|Tworzy nowe pole tekstowe dla `CMFCRibbonEdit` obiektu.|
|[CMFCRibbonEdit::DestroyCtrl](#destroyctrl)|`CMFCRibbonEdit` Niszczy obiekt.|
|[CMFCRibbonEdit::DropDownList](#dropdownlist)|Odrzuca pole listy.|
|[CMFCRibbonEdit::EnableSpinButtons](#enablespinbuttons)|Włącza i ustawia zakres przycisku pokrętła dla pola tekstowego.|
|[CMFCRibbonEdit::GetCompactSize](#getcompactsize)|Pobiera rozmiar `CFMCRibbonEdit` kompaktowy obiektu.|
|[CMFCRibbonEdit::GetEditText](#getedittext)|Pobiera tekst w polu tekstowym.|
|[CMFCRibbonEdit::GetIntermediateSize](#getintermediatesize)|Pobiera pośredni rozmiar `CMFCRibbonEdit` obiektu.|
|[CMFCRibbonEdit:: TextAlign](#gettextalign)|Pobiera wyrównanie tekstu w polu tekstowym.|
|[CMFCRibbonEdit:: getwidth](#getwidth)|Pobiera szerokość `CMFCRibbonEdit` formantu (w pikselach).|
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|Wskazuje, czy rozmiar `CMFCRibbonEdit` wyświetlanego formantu może być kompaktowy.|
|[CMFCRibbonEdit::HasFocus](#hasfocus)|Wskazuje, czy `CMFCRIbbonEdit` kontrolka ma fokus.|
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|Wskazuje, czy rozmiar `CMFCRibbonEdit` wyświetlanego formantu może być duży.|
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|Wskazuje, czy pole tekstowe ma przycisk pokrętło.|
|[CMFCRibbonEdit:: ispodświetlacz](#ishighlighted)|Wskazuje, `CMFCRibbonEdit` czy formant jest wyróżniony.|
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|Wywoływane przez platformę, gdy wymiary prostokąta wyświetlania dla `CMFCRibbonEdit` kontrolki zmienią się.|
|[CMFCRibbonEdit:: OnDraw](#ondraw)|Wywoływane przez platformę, by narysować `CMFCRibbonEdit` kontrolkę.|
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|Wywoływane przez platformę, by narysować etykietę i obraz dla `CMFCRibbonEdit` kontrolki.|
|[CMFCRibbonEdit::OnDrawOnList](#ondrawonlist)|Wywoływane przez platformę, by narysować `CMFCRibbonEdit` kontrolkę w polu listy poleceń.|
|[CMFCRibbonEdit:: onenable](#onenable)|Wywoływane przez platformę, aby włączyć lub wyłączyć `CMFCRibbonEdit` formant.|
|[CMFCRibbonEdit:: onpodświetl](#onhighlight)|Wywoływane przez platformę, gdy wskaźnik przechodzi lub opuszcza granice `CMFCRibbonEdit` formantu.|
|[CMFCRibbonEdit::OnKey](#onkey)|Wywoływane przez platformę, gdy użytkownik naciśnie element poradę dotyczącą klawiszy, a `CMFCRibbonEdit` kontrolka ma fokus.|
|[CMFCRibbonEdit::OnLButtonDown](#onlbuttondown)|Wywoływane przez platformę, by zaktualizować `CMFCRibbonEdit` kontrolkę, gdy użytkownik naciśnie lewym przyciskiem myszy na kontrolce.|
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|Wywoływane przez platformę, gdy użytkownik zwolni lewy przycisk myszy.|
|[CMFCRibbonEdit::OnRTLChanged](#onrtlchanged)|Wywoływane przez platformę, by zaktualizować `CMFCRibbonEdit` kontrolkę, gdy zmieni się kierunek układu.|
|[CMFCRibbonEdit:: OnShow](#onshow)|Wywoływane przez platformę, by pokazać lub ukryć `CMFCRibbonEdit` formant.|
|[CMFCRibbonEdit:: redraw](#redraw)|Aktualizuje wyświetlaną `CMFCRibbonEdit` kontrolkę.|
|[CMFCRibbonEdit::SetACCData](#setaccdata)|Ustawia dane ułatwień dostępu dla `CMFCRibbonEdit` obiektu.|
|[CMFCRibbonEdit::SetEditText](#setedittext)|Ustawia tekst w polu tekstowym.|
|[CMFCRibbonEdit::SetTextAlign](#settextalign)|Ustawia wyrównanie tekstu pola tekstowego.|
|[CMFCRibbonEdit:: setwidth](#setwidth)|Ustawia szerokość pola tekstowego dla `CMFCRibbonEdit` kontrolki.|

## <a name="remarks"></a>Uwagi

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób konstruowania `CMFCRibbonEdit` obiektu, wyświetlania przycisków pokrętła obok kontrolki Edycja i ustawiania tekstu kontrolki edycji. Ten fragment kodu jest częścią [przykładu demonstracyjnego pakietu MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxRibbonEdit. h

##  <a name="canbestretched"></a>CMFCRibbonEdit::CanBeStretched

Wskazuje, czy wysokość formantu [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) może wzrosnąć w pionie do wysokości wiersza wstążki.

```
virtual BOOL CanBeStretched();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="cmfcribbonedit"></a>CMFCRibbonEdit::CMFCRibbonEdit

Konstruuje obiekt [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
CMFCRibbonEdit(
    UINT nID,
    int nWidth,
    LPCTSTR lpszLabel = NULL,
    int nImage = -1);

CMFCRibbonEdit();
```

### <a name="parameters"></a>Parametry

*nID*<br/>
podczas Identyfikator polecenia dla `CMFCRibbonEdit` kontrolki.

*nWidth*<br/>
podczas Szerokość pola `CMFCRibbonEdit` tekstowego formantu w pikselach.

*lpszLabel*<br/>
podczas Etykieta `CMFCRibbonEdit` kontrolki.

*Nokreślono*<br/>
podczas Indeks małego obrazu do użycia w `CMFCRibbonEdit` formancie. Kolekcja małych obrazów jest obsługiwana przez nadrzędną kategorię wstążki.

### <a name="remarks"></a>Uwagi

`CMFCRibbonEdit` Formant nie używa dużego obrazu.

##  <a name="copyfrom"></a>CMFCRibbonEdit::CopyFrom

Kopiuje stan określonego obiektu [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) do bieżącego obiektu [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parametry

*SRC*<br/>
podczas Obiekt źródłowy `CMFCRibbonEdit` .

### <a name="remarks"></a>Uwagi

Parametr *src* musi być typu `CMFCRibbonEdit`.

##  <a name="createedit"></a>CMFCRibbonEdit:: SetEdit

Tworzy nowe pole tekstowe dla obiektu [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
podczas Wskaźnik do okna `CMFCRibbonEdit` nadrzędnego obiektu.

*dwEditStyle*<br/>
podczas Określa styl pola tekstowego. Możesz połączyć style okna wymienione w sekcji uwagi za pomocą [stylów kontrolki edycji](/windows/win32/Controls/edit-control-styles) , które są opisane w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowego pola tekstowego, jeśli metoda zakończyła się pomyślnie. w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę w klasie pochodnej, aby utworzyć niestandardowe pole tekstowe.

Do pola tekstowego można zastosować następujące [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) :

- **WS_CHILD**

- **WS_VISIBLE**

- **WS_DISABLED**

- **WS_GROUP**

- **WS_TABSTOP**

##  <a name="destroyctrl"></a>CMFCRibbonEdit::D estroyCtrl

Niszczy obiekt [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void DestroyCtrl();
```

### <a name="remarks"></a>Uwagi

##  <a name="dropdownlist"></a>CMFCRibbonEdit::D ropDownList

Odrzuca pole listy.

```
virtual void DropDownList();
```

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda nie wykonuje żadnych operacji. Zastąp tę metodę, aby rozwinąć pole listy.

##  <a name="enablespinbuttons"></a>CMFCRibbonEdit::EnableSpinButtons

Włącza i ustawia zakres przycisku pokrętła dla pola tekstowego.

```
void EnableSpinButtons(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
podczas Wartość minimalna przycisku pokrętła.

*Nmaks.*<br/>
podczas Wartość maksymalna przycisku pokrętła.

### <a name="remarks"></a>Uwagi

Przyciski pokrętła wyświetlają strzałkę w górę i w dół oraz umożliwiają użytkownikom przechodzenie przez stały zestaw wartości.

##  <a name="getcompactsize"></a>CMFCRibbonEdit::GetCompactSize

Pobiera rozmiar kompaktowy obiektu [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
podczas Wskaźnik do kontekstu urządzenia dla `CMFCRibbonEdit` obiektu.

### <a name="return-value"></a>Wartość zwracana

Rozmiar `CMFCRibbonEdit` kompaktowy obiektu.

### <a name="remarks"></a>Uwagi

##  <a name="getedittext"></a>CMFCRibbonEdit::GetEditText

Pobiera tekst w polu tekstowym.

```
CString GetEditText() const;
```

### <a name="return-value"></a>Wartość zwracana

Tekst w polu tekstowym.

### <a name="remarks"></a>Uwagi

##  <a name="getintermediatesize"></a>CMFCRibbonEdit::GetIntermediateSize

Pobiera pośredni rozmiar obiektu [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
podczas Wskaźnik do kontekstu urządzenia dla `CMFCRibbonEdit` obiektu.

### <a name="return-value"></a>Wartość zwracana

Rozmiar `CMFCRibbonEdit` pośredni obiektu.

### <a name="remarks"></a>Uwagi

##  <a name="gettextalign"></a>CMFCRibbonEdit:: TextAlign

Pobiera wyrównanie tekstu w polu tekstowym.

```
int GetTextAlign() const;
```

### <a name="return-value"></a>Wartość zwracana

Wyliczona wartość tekstowa. Więcej wartości można znaleźć w sekcji uwagi.

### <a name="remarks"></a>Uwagi

Zwracana wartość jest jednym z następujących stylów kontrolki edycji:

- **ES_LEFT** dla lewego wyrównania

- **ES_CENTER** dla wyrównania Center

- **ES_RIGHT** na wyrównanie do prawej

Aby uzyskać więcej informacji o tych stylach, zobacz [Edycja stylów kontrolek](/windows/win32/Controls/edit-control-styles).

##  <a name="getwidth"></a>CMFCRibbonEdit:: getwidth

Pobiera szerokość kontrolki [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) w pikselach.

```
int GetWidth(BOOL bInFloatyMode = FALSE) const;
```

### <a name="parameters"></a>Parametry

*bInFloatyMode*<br/>
podczas Ma wartość true `CMFCRibbonEdit` , Jeśli kontrolka jest w trybie swobodnym; w przeciwnym razie, FAŁSZ.

### <a name="return-value"></a>Wartość zwracana

Szerokość `CMFCRibbonEdit` formantu (w pikselach).

### <a name="remarks"></a>Uwagi

##  <a name="hascompactmode"></a>CMFCRibbonEdit::HasCompactMode

Wskazuje, czy rozmiar wyświetlania formantu [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) może być zwarty.

```
virtual BOOL HasCompactMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda zawsze zwraca wartość TRUE. Zastąp tę metodę, aby określić, czy rozmiar wyświetlania może być kompaktowy.

##  <a name="hasfocus"></a>CMFCRibbonEdit::HasFocus

Wskazuje, czy formant [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) ma fokus.

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość true `CMFCRibbonEdit` , Jeśli kontrolka ma fokus; w przeciwnym razie wartość false.

### <a name="remarks"></a>Uwagi

##  <a name="haslargemode"></a>CMFCRibbonEdit::HasLargeMode

Wskazuje, czy rozmiar wyświetlania formantu [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) może być duży.

```
virtual BOOL HasLargeMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda zawsze zwraca wartość FALSE. Zastąp tę metodę, aby określić, czy rozmiar wyświetlania może być duży.

##  <a name="hasspinbuttons"></a>CMFCRibbonEdit::HasSpinButtons

Wskazuje, czy pole tekstowe ma przycisk pokrętło.

```
virtual BOOL HasSpinButtons() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli pole tekstowe ma przycisk pokrętła; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="ishighlighted"></a>CMFCRibbonEdit:: ispodświetlacz

Wskazuje, czy formant [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) jest wyróżniony.

```
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość true `CMFCRibbonEdit` , Jeśli kontrolka jest wyróżniona; w przeciwnym razie wartość false.

### <a name="remarks"></a>Uwagi

##  <a name="onafterchangerect"></a>CMFCRibbonEdit::OnAfterChangeRect

Wywoływane przez platformę, gdy wymiary prostokąta wyświetlania dla kontrolki [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) zmienią się.

```
virtual void OnAfterChangeRect(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
podczas Wskaźnik do kontekstu urządzenia dla `CMFCRibbonEdit` kontrolki.

### <a name="remarks"></a>Uwagi

##  <a name="ondraw"></a>CMFCRibbonEdit:: OnDraw

Wywoływane przez platformę, by narysować kontrolkę [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
podczas Wskaźnik do kontekstu urządzenia dla `CMFCRibbonEdit` kontrolki.

### <a name="remarks"></a>Uwagi

##  <a name="ondrawlabelandimage"></a>CMFCRibbonEdit::OnDrawLabelAndImage

Wywoływane przez platformę, by narysować etykietę i obraz dla kontrolki [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnDrawLabelAndImage(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
podczas Wskaźnik do kontekstu urządzenia dla `CMFCRibbonEdit` kontrolki.

### <a name="remarks"></a>Uwagi

##  <a name="ondrawonlist"></a>CMFCRibbonEdit::OnDrawOnList

Wywoływane przez platformę, by narysować kontrolkę [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) w polu listy poleceń.

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

*pDC*<br/>
podczas Wskaźnik do kontekstu urządzenia dla `CMFCRibbonEdit` kontrolki.

*strText*<br/>
podczas Klasa wyświetlania tekstu [ ] (../../mfc/reference/cmfcribbonedit-class.md "CMFCRibbonEdit").

*nTextOffset*<br/>
podczas Odległość w pikselach od lewej strony pola listy do wyświetlanego tekstu.

*cinania*<br/>
podczas Prostokąt `CMFCRibbonEdit` wyświetlania formantu.

*bIsSelected*<br/>
podczas Ten parametr nie jest używany.

*bHighlighted*<br/>
podczas Ten parametr nie jest używany.

### <a name="remarks"></a>Uwagi

Pole listy polecenia wyświetla kontrolki wstążki umożliwiające użytkownikom dostosowywanie paska narzędzi Szybki dostęp.

##  <a name="onenable"></a>CMFCRibbonEdit:: onenable

Wywoływane przez platformę, aby włączyć lub wyłączyć formant [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnEnable(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
podczas Wartość TRUE, aby włączyć kontrolkę; Wartość FALSE, aby wyłączyć formant.

### <a name="remarks"></a>Uwagi

##  <a name="onhighlight"></a>CMFCRibbonEdit:: onpodświetl

Wywoływane przez platformę, gdy wskaźnik przechodzi lub opuszcza granice formantu [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnHighlight(BOOL bHighlight);
```

### <a name="parameters"></a>Parametry

*bHighlight*<br/>
podczas Ma wartość true, jeśli wskaźnik znajduje się w granicach `CMFCRibbonEdit` formantu; w przeciwnym razie, FAŁSZ.

### <a name="remarks"></a>Uwagi

##  <a name="onkey"></a>CMFCRibbonEdit::OnKey

Wywoływane przez platformę, gdy użytkownik naciśnie element poradę dotyczącą klawiszy, a kontrolka [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) ma fokus.

```
virtual BOOL OnKey(BOOL bIsMenuKey);
```

### <a name="parameters"></a>Parametry

*bIsMenuKey*<br/>
podczas Wartość TRUE, jeśli poradę dotyczącą klawiszy wyświetla menu podręczne; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli zdarzenie zostało obsłużone; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="onlbuttondown"></a>CMFCRibbonEdit::OnLButtonDown

Wywoływane przez platformę, by zaktualizować kontrolkę [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) , gdy użytkownik naciśnie lewym przyciskiem myszy na kontrolce.

```
virtual void OnLButtonDown(CPoint point);
```

### <a name="parameters"></a>Parametry

*moment*<br/>
podczas Ten parametr nie jest używany.

### <a name="remarks"></a>Uwagi

##  <a name="onlbuttonup"></a>CMFCRibbonEdit::OnLButtonUp

Wywoływane przez platformę, gdy użytkownik zwolni lewy przycisk myszy.

```
virtual void OnLButtonUp(CPoint point);
```

### <a name="parameters"></a>Parametry

*moment*<br/>
podczas Ten parametr nie jest używany.

### <a name="remarks"></a>Uwagi

##  <a name="onrtlchanged"></a>CMFCRibbonEdit::OnRTLChanged

Wywoływane przez platformę, by zaktualizować kontrolkę [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) , gdy zmieni się kierunek układu.

```
virtual void OnRTLChanged(BOOL bIsRTL);
```

### <a name="parameters"></a>Parametry

*bIsRTL*<br/>
podczas PRAWDA, jeśli układ jest od prawej do lewej; FAŁSZ, jeśli układ jest od lewej do prawej.

### <a name="remarks"></a>Uwagi

##  <a name="onshow"></a>CMFCRibbonEdit:: OnShow

Wywoływane przez platformę, by pokazać lub ukryć formant [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
podczas Wartość TRUE, aby pokazać formant; Wartość FALSE, aby ukryć formant.

### <a name="remarks"></a>Uwagi

##  <a name="redraw"></a>CMFCRibbonEdit:: redraw

Aktualizuje sposób wyświetlania formantu [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void Redraw();
```

### <a name="remarks"></a>Uwagi

Ta metoda odrysuje prostokąt `CMFCRibbonEdit` wyświetlania obiektu przez pośrednie wywołanie [CWnd:: RedrawWindow](/windows/win32/api/winuser/nf-winuser-redrawwindow) z ustawionymi flagami RDW_INVALIDATE, RDW_ERASE i RDW_UPDATENOW.

##  <a name="setaccdata"></a>CMFCRibbonEdit::SetACCData

Ustawia dane ułatwień dostępu dla obiektu [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
Wskaźnik do okna nadrzędnego dla `CMFCRibbonEdit` obiektu.

*Data*<br/>
Dane ułatwień dostępu dla `CMFCRibbonEdit` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

##  <a name="setedittext"></a>CMFCRibbonEdit::SetEditText

Ustawia tekst w polu tekstowym.

```
void SetEditText(CString strText);
```

### <a name="parameters"></a>Parametry

*strText*<br/>
podczas Tekst pola tekstowego.

##  <a name="settextalign"></a>CMFCRibbonEdit:: TextAlign

Ustawia wyrównanie tekstu pola tekstowego.

```
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>Parametry

*nAlign*<br/>
podczas Wyliczona wartość tekstowa. Więcej wartości można znaleźć w sekcji uwagi.

### <a name="remarks"></a>Uwagi

Parametr *nAlign* jest jednym z następujących stylów kontrolki edycji:

- ES_LEFT dla lewego wyrównania

- ES_CENTER dla wyrównania Center

- ES_RIGHT na wyrównanie do prawej

Aby uzyskać więcej informacji o tych stylach, zobacz [Edycja stylów kontrolek](/windows/win32/Controls/edit-control-styles).

##  <a name="setwidth"></a>CMFCRibbonEdit:: setwidth

Ustawia szerokość pola tekstowego dla kontrolki [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
void SetWidth(
    int nWidth,
    BOOL bInFloatyMode = FALSE);
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
podczas Szerokość pola tekstowego w pikselach.

*bInFloatyMode*<br/>
Wartość TRUE powoduje ustawienie szerokości trybu zmiennoprzecinkowego; Wartość FALSE powoduje ustawienie szerokości trybu regularnego.

### <a name="remarks"></a>Uwagi

`CMFCRibbonEdit` Kontrolka ma dwie szerokości w zależności od trybu wyświetlania: tryb zmiennoprzecinkowy i tryb regularny.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[Klasa CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)
