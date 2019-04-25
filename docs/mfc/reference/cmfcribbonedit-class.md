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
ms.openlocfilehash: 80ee43ae32416f9f62df419c4afbd46a0aa63cc8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237095"
---
# <a name="cmfcribbonedit-class"></a>Klasa CMFCRibbonEdit

Implementuje formant edycji, który znajduje się na pasku wstążki.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonEdit : public CMFCRibbonButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Konstruuje `CMFCRibbonEdit` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonEdit::CanBeStretched](#canbestretched)|Wskazuje, czy wysokość `CMFCRibbonEdit` kontroli może zwiększyć w pionie do wysokości wiersza wstążki.|
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Konstruuje `CMFCRibbonEdit` obiektu.|
|[CMFCRibbonEdit::CopyFrom](#copyfrom)|Kopiuje określony stan `CMFCRibbonEdit` obiekt do bieżącego `CMFCRibbonEdit` obiektu.|
|[CMFCRibbonEdit::CreateEdit](#createedit)|Tworzy nowe pole tekstowe dla `CMFCRibbonEdit` obiektu.|
|[CMFCRibbonEdit::DestroyCtrl](#destroyctrl)|Niszczy `CMFCRibbonEdit` obiektu.|
|[CMFCRibbonEdit::DropDownList](#dropdownlist)|Można otworzyć rozwijane pole listy.|
|[CMFCRibbonEdit::EnableSpinButtons](#enablespinbuttons)|Włącza i ustawia zakres przycisku pokrętła dla pola tekstowego.|
|[CMFCRibbonEdit::GetCompactSize](#getcompactsize)|Pobiera rozmiar compact `CFMCRibbonEdit` obiektu.|
|[CMFCRibbonEdit::GetEditText](#getedittext)|Pobiera tekst w polu tekstowym.|
|[CMFCRibbonEdit::GetIntermediateSize](#getintermediatesize)|Pobiera rozmiar pośrednich `CMFCRibbonEdit` obiektu.|
|[CMFCRibbonEdit::GetTextAlign](#gettextalign)|Pobiera wyrównanie tekstu w polu tekstowym.|
|[CMFCRibbonEdit::GetWidth](#getwidth)|Pobiera szerokość w pikselach, o `CMFCRibbonEdit` kontroli.|
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|Wskazuje, czy rozmiar wyświetlania `CMFCRibbonEdit` formant może być compact.|
|[CMFCRibbonEdit::HasFocus](#hasfocus)|Wskazuje, czy `CMFCRIbbonEdit` kontrolka ma fokus.|
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|Wskazuje, czy rozmiar wyświetlania `CMFCRibbonEdit` kontrolki mogą być duże.|
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|Wskazuje, czy pole ma pokrętła.|
|[CMFCRibbonEdit::IsHighlighted](#ishighlighted)|Wskazuje, czy `CMFCRibbonEdit` formant jest wyróżniony.|
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|Wywoływane przez platformę, gdy wymiary prostokąta wyświetlania `CMFCRibbonEdit` kontrolować zmiany.|
|[CMFCRibbonEdit::OnDraw](#ondraw)|Wywoływane przez platformę, by narysować `CMFCRibbonEdit` kontroli.|
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|Wywoływane przez platformę, by narysować etykiety i obrazów do `CMFCRibbonEdit` kontroli.|
|[CMFCRibbonEdit::OnDrawOnList](#ondrawonlist)|Wywoływane przez platformę, by narysować `CMFCRibbonEdit` kontroli w polu listy poleceń.|
|[CMFCRibbonEdit::OnEnable](#onenable)|Wywoływane przez platformę, aby włączyć lub wyłączyć `CMFCRibbonEdit` kontroli.|
|[CMFCRibbonEdit::OnHighlight](#onhighlight)|Wywoływane przez platformę, gdy wskaźnik wchodzi lub opuszczeniu granic `CMFCRibbonEdit` kontroli.|
|[CMFCRibbonEdit::OnKey](#onkey)|Wywoływane przez platformę, gdy użytkownik naciśnie poradę dotyczącą klawiszy i `CMFCRibbonEdit` kontrolka ma fokus.|
|[CMFCRibbonEdit::OnLButtonDown](#onlbuttondown)|Wywoływane przez platformę, aby zaktualizować `CMFCRibbonEdit` kontroli, gdy użytkownik naciśnie lewego przycisku myszy na kontrolce.|
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|Wywoływane przez platformę, gdy użytkownik zwolni przycisk myszy po lewej stronie.|
|[CMFCRibbonEdit::OnRTLChanged](#onrtlchanged)|Wywoływane przez platformę, aby zaktualizować `CMFCRibbonEdit` kontrolować zmiany kierunku układu.|
|[CMFCRibbonEdit::OnShow](#onshow)|Wywoływane przez platformę, by pokazać lub ukryć `CMFCRibbonEdit` kontroli.|
|[CMFCRibbonEdit::Redraw](#redraw)|Wyświetlanie aktualizacji `CMFCRibbonEdit` kontroli.|
|[CMFCRibbonEdit::SetACCData](#setaccdata)|Ustawia dane ułatwień dostępu dla `CMFCRibbonEdit` obiektu.|
|[CMFCRibbonEdit::SetEditText](#setedittext)|Ustawia tekst w polu tekstowym.|
|[CMFCRibbonEdit::SetTextAlign](#settextalign)|Określa wyrównanie tekstu w polu tekstowym.|
|[CMFCRibbonEdit::SetWidth](#setwidth)|Określa szerokość pola tekstowego dla `CMFCRibbonEdit` kontroli.|

## <a name="remarks"></a>Uwagi

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób tworzenia `CMFCRibbonEdit` obiektu, Pokaż przyciski pokrętła obok kontrolki edycji i Ustaw tekst kontrolki edycji. Ten fragment kodu jest częścią [próbka MS Office 2007 Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxRibbonEdit.h

##  <a name="canbestretched"></a>  CMFCRibbonEdit::CanBeStretched

Wskazuje, czy wysokość [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli może zwiększyć w pionie do wysokości wiersza wstążki.

```
virtual BOOL CanBeStretched();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="cmfcribbonedit"></a>  CMFCRibbonEdit::CMFCRibbonEdit

Konstruuje [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) obiektu.

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
[in] Identyfikator dla polecenia `CMFCRibbonEdit` kontroli.

*nWidth*<br/>
[in] Szerokość w pikselach pole tekstowe `CMFCRibbonEdit` kontroli.

*lpszLabel*<br/>
[in] Etykieta dla `CMFCRibbonEdit` kontroli.

*nImage*<br/>
[in] Indeks małych obrazów do użycia dla `CMFCRibbonEdit` kontroli. Kolekcja małe obrazy są obsługiwane przez kategorii nadrzędnej wstążki.

### <a name="remarks"></a>Uwagi

`CMFCRibbonEdit` Formantu nie korzysta z dużym obrazem.

##  <a name="copyfrom"></a>  CMFCRibbonEdit::CopyFrom

Kopiuje określony stan [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) obiekt do bieżącego [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) obiektu.

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
[in] Źródło `CMFCRibbonEdit` obiektu.

### <a name="remarks"></a>Uwagi

*Src* parametru musi być typu `CMFCRibbonEdit`.

##  <a name="createedit"></a>  CMFCRibbonEdit::CreateEdit

Tworzy nowe pole tekstowe dla [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) obiektu.

```
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[in] Wskaźnik do okna nadrzędnego `CMFCRibbonEdit` obiektu.

*dwEditStyle*<br/>
[in] Określa styl pola tekstowego. Można połączyć Style okna wymienionych w sekcji uwag z [style kontrolki edycji](/windows/desktop/Controls/edit-control-styles) opisano w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowego pola tekstowego, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę metodę w klasie pochodnej, aby utworzyć niestandardowe pole tekstowe.

Można zastosować następujące [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles) do pola tekstowego:

- **WS_CHILD**

- **WS_VISIBLE**

- **WS_DISABLED**

- **WS_GROUP**

- **WS_TABSTOP**

##  <a name="destroyctrl"></a>  CMFCRibbonEdit::DestroyCtrl

Niszczy [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) obiektu.

```
virtual void DestroyCtrl();
```

### <a name="remarks"></a>Uwagi

##  <a name="dropdownlist"></a>  CMFCRibbonEdit::DropDownList

Można otworzyć rozwijane pole listy.

```
virtual void DropDownList();
```

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda nie działa. Zastępuje tę metodę, aby rozwinąć pole listy.

##  <a name="enablespinbuttons"></a>  CMFCRibbonEdit::EnableSpinButtons

Włącza i ustawia zakres przycisku pokrętła dla pola tekstowego.

```
void EnableSpinButtons(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
[in] Wartość minimalna przycisku pokrętła.

*nMax*<br/>
[in] Maksymalna wartość przycisku pokrętła.

### <a name="remarks"></a>Uwagi

Przycisków pokręteł wyświetlania w górę i Strzałka w dół i umożliwić użytkownikom przechodzenie między ustalony zestaw wartości.

##  <a name="getcompactsize"></a>  CMFCRibbonEdit::GetCompactSize

Pobiera rozmiar compact [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) obiektu.

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Wskaźnik do kontekstu urządzenia `CMFCRibbonEdit` obiektu.

### <a name="return-value"></a>Wartość zwracana

Rozmiar compact `CMFCRibbonEdit` obiektu.

### <a name="remarks"></a>Uwagi

##  <a name="getedittext"></a>  CMFCRibbonEdit::GetEditText

Pobiera tekst w polu tekstowym.

```
CString GetEditText() const;
```

### <a name="return-value"></a>Wartość zwracana

Tekst w polu tekstowym.

### <a name="remarks"></a>Uwagi

##  <a name="getintermediatesize"></a>  CMFCRibbonEdit::GetIntermediateSize

Pobiera rozmiar pośrednich [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) obiektu.

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Wskaźnik do kontekstu urządzenia `CMFCRibbonEdit` obiektu.

### <a name="return-value"></a>Wartość zwracana

Pośredni rozmiar `CMFCRibbonEdit` obiektu.

### <a name="remarks"></a>Uwagi

##  <a name="gettextalign"></a>  CMFCRibbonEdit::GetTextAlign

Pobiera wyrównanie tekstu w polu tekstowym.

```
int GetTextAlign() const;
```

### <a name="return-value"></a>Wartość zwracana

Wyrównanie tekstu wyliczany wartości. Zobacz sekcję Spostrzeżenia, aby możliwe wartości.

### <a name="remarks"></a>Uwagi

Zwrócona wartość jest jednym z następujących style kontrolki edycji:

- **ES_LEFT** dla wyrównanie do lewej

- **ES_CENTER** dla wyrównanie do środka

- **ES_RIGHT** dla wyrównanie do prawej

Aby uzyskać więcej informacji na temat tych stylów, zobacz [Edytuj style kontrolki](/windows/desktop/Controls/edit-control-styles).

##  <a name="getwidth"></a>  CMFCRibbonEdit::GetWidth

Pobiera szerokość w pikselach, o [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli.

```
int GetWidth(BOOL bInFloatyMode = FALSE) const;
```

### <a name="parameters"></a>Parametry

*bInFloatyMode*<br/>
[in] Wartość TRUE, jeśli `CMFCRibbonEdit` kontrolka jest w trybie zmiennoprzecinkowych; w przeciwnym razie wartość FALSE.

### <a name="return-value"></a>Wartość zwracana

Szerokość w pikselach, o `CMFCRibbonEdit` kontroli.

### <a name="remarks"></a>Uwagi

##  <a name="hascompactmode"></a>  CMFCRibbonEdit::HasCompactMode

Wskazuje, czy rozmiar wyświetlania [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) formant może być compact.

```
virtual BOOL HasCompactMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda zawsze zwraca wartość TRUE. Zastępuje tę metodę, aby wskazać, czy rozmiar wyświetlania można compact.

##  <a name="hasfocus"></a>  CMFCRibbonEdit::HasFocus

Wskazuje, czy [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontrolka ma fokus.

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli `CMFCRibbonEdit` kontrolka ma fokus; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="haslargemode"></a>  CMFCRibbonEdit::HasLargeMode

Wskazuje, czy rozmiar wyświetlania [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontrolki mogą być duże.

```
virtual BOOL HasLargeMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda zawsze zwraca wartość FALSE. Zastępuje tę metodę, aby wskazać, czy rozmiar wyświetlania mogą być duże.

##  <a name="hasspinbuttons"></a>  CMFCRibbonEdit::HasSpinButtons

Wskazuje, czy pole ma pokrętła.

```
virtual BOOL HasSpinButtons() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli pole tekstowe przycisku pokrętła; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="ishighlighted"></a>  CMFCRibbonEdit::IsHighlighted

Wskazuje, czy [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) formant jest wyróżniony.

```
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli `CMFCRibbonEdit` kontrolka jest wyróżnione; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="onafterchangerect"></a>  CMFCRibbonEdit::OnAfterChangeRect

Wywoływane przez platformę, gdy wymiary prostokąta wyświetlania [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontrolować zmiany.

```
virtual void OnAfterChangeRect(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Wskaźnik do kontekstu urządzenia `CMFCRibbonEdit` kontroli.

### <a name="remarks"></a>Uwagi

##  <a name="ondraw"></a>  CMFCRibbonEdit::OnDraw

Wywoływane przez platformę, by narysować [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Wskaźnik do kontekstu urządzenia `CMFCRibbonEdit` kontroli.

### <a name="remarks"></a>Uwagi

##  <a name="ondrawlabelandimage"></a>  CMFCRibbonEdit::OnDrawLabelAndImage

Wywoływane przez platformę, by narysować etykiety i obrazów do [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli.

```
virtual void OnDrawLabelAndImage(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Wskaźnik do kontekstu urządzenia `CMFCRibbonEdit` kontroli.

### <a name="remarks"></a>Uwagi

##  <a name="ondrawonlist"></a>  CMFCRibbonEdit::OnDrawOnList

Wywoływane przez platformę, by narysować [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli w polu listy poleceń.

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
[in] Wskaźnik do kontekstu urządzenia `CMFCRibbonEdit` kontroli.

*strText*<br/>
[in] Tekst wyświetlany [ ] (../../mfc/reference/cmfcribbonedit-class.md "klasa cmfcribbonedit").

*nTextOffset*<br/>
[in] Odległość w pikselach, po lewej stronie pola listy do wyświetlania tekstu.

*Rect*<br/>
[in] Prostokąt wyświetlania dla `CMFCRibbonEdit` kontroli.

*bIsSelected*<br/>
[in] Ten parametr nie jest używany.

*bHighlighted*<br/>
[in] Ten parametr nie jest używany.

### <a name="remarks"></a>Uwagi

Pole listy poleceń Wyświetla formanty wstążki, aby umożliwić użytkownikom dostosowywanie paska narzędzi Szybki dostęp.

##  <a name="onenable"></a>  CMFCRibbonEdit::OnEnable

Wywoływane przez platformę, aby włączyć lub wyłączyć [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli.

```
virtual void OnEnable(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bWłączenie*<br/>
[in] Wartość TRUE powoduje włączenie kontroli. Wartość FALSE, aby wyłączyć formant.

### <a name="remarks"></a>Uwagi

##  <a name="onhighlight"></a>  CMFCRibbonEdit::OnHighlight

Wywoływane przez platformę, gdy wskaźnik wchodzi lub opuszczeniu granic [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli.

```
virtual void OnHighlight(BOOL bHighlight);
```

### <a name="parameters"></a>Parametry

*bHighlight*<br/>
[in] Wartość TRUE, jeśli kursor znajduje się w granicach `CMFCRibbonEdit` sterowania; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="onkey"></a>  CMFCRibbonEdit::OnKey

Wywoływane przez platformę, gdy użytkownik naciśnie poradę dotyczącą klawiszy i [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontrolka ma fokus.

```
virtual BOOL OnKey(BOOL bIsMenuKey);
```

### <a name="parameters"></a>Parametry

*bIsMenuKey*<br/>
[in] Wartość TRUE, jeśli poradę dotyczącą klawiszy wyświetla wyskakujące menu; w przeciwnym razie wartość FALSE.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli zdarzenie został obsłużony; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="onlbuttondown"></a>  CMFCRibbonEdit::OnLButtonDown

Wywoływane przez platformę, aby zaktualizować [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli, gdy użytkownik naciśnie lewego przycisku myszy na kontrolce.

```
virtual void OnLButtonDown(CPoint point);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
[in] Ten parametr nie jest używany.

### <a name="remarks"></a>Uwagi

##  <a name="onlbuttonup"></a>  CMFCRibbonEdit::OnLButtonUp

Wywoływane przez platformę, gdy użytkownik zwolni przycisk myszy po lewej stronie.

```
virtual void OnLButtonUp(CPoint point);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
[in] Ten parametr nie jest używany.

### <a name="remarks"></a>Uwagi

##  <a name="onrtlchanged"></a>  CMFCRibbonEdit::OnRTLChanged

Wywoływane przez platformę, aby zaktualizować [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontrolować zmiany kierunku układu.

```
virtual void OnRTLChanged(BOOL bIsRTL);
```

### <a name="parameters"></a>Parametry

*bIsRTL*<br/>
[in] Wartość TRUE, jeśli układ od prawej do lewej; Wartość FALSE, jeśli układ od lewej do prawej.

### <a name="remarks"></a>Uwagi

##  <a name="onshow"></a>  CMFCRibbonEdit::OnShow

Wywoływane przez platformę, by pokazać lub ukryć [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
[in] Wartość TRUE, aby pokazać kontroli. Wartość FALSE, aby ukryć formant.

### <a name="remarks"></a>Uwagi

##  <a name="redraw"></a>  CMFCRibbonEdit::Redraw

Wyświetlanie aktualizacji [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli.

```
virtual void Redraw();
```

### <a name="remarks"></a>Uwagi

Ta metoda ponownie rysuje prostokąt wyświetlania dla `CMFCRibbonEdit` obiektu przez wywołanie pośrednio [CWnd::RedrawWindow](/windows/desktop/api/winuser/nf-winuser-redrawwindow) przy użyciu flag RDW_INVALIDATE RDW_ERASE i RDW_UPDATENOW zestawu.

##  <a name="setaccdata"></a>  CMFCRibbonEdit::SetACCData

Ustawia dane ułatwień dostępu dla [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) obiektu.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
Wskaźnik do okna nadrzędnego `CMFCRibbonEdit` obiektu.

*data*<br/>
Dane dostępności `CMFCRibbonEdit` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

##  <a name="setedittext"></a>  CMFCRibbonEdit::SetEditText

Ustawia tekst w polu tekstowym.

```
void SetEditText(CString strText);
```

### <a name="parameters"></a>Parametry

*strText*<br/>
[in] Tekst dla pola tekstowego.

##  <a name="settextalign"></a>  CMFCRibbonEdit::SetTextAlign

Określa wyrównanie tekstu w polu tekstowym.

```
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>Parametry

*nAlign*<br/>
[in] Wyrównanie tekstu wyliczany wartości. Zobacz sekcję Spostrzeżenia, aby możliwe wartości.

### <a name="remarks"></a>Uwagi

Parametr *nAlign* jest jednym z następujących Edytuj style kontrolki:

- ES_LEFT dla wyrównanie do lewej

- ES_CENTER dla wyrównanie do środka

- ES_RIGHT dla wyrównanie do prawej

Aby uzyskać więcej informacji na temat tych stylów, zobacz [Edytuj style kontrolki](/windows/desktop/Controls/edit-control-styles).

##  <a name="setwidth"></a>  CMFCRibbonEdit::SetWidth

Określa szerokość pola tekstowego dla [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli.

```
void SetWidth(
    int nWidth,
    BOOL bInFloatyMode = FALSE);
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
[in] Szerokość w pikselach, pola tekstowego.

*bInFloatyMode*<br/>
Wartość TRUE, aby ustawić szerokość tryb przestawny Wartość FALSE, aby ustawić szerokość do trybu normalnego.

### <a name="remarks"></a>Uwagi

`CMFCRibbonEdit` Kontrolka ma dwa szerokości, w zależności od jego trybu wyświetlania: liczb zmiennoprzecinkowych tryb i do trybu normalnego.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[Klasa CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)
