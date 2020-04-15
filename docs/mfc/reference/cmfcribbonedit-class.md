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
ms.openlocfilehash: ab621a05f9b658eee9babb14e257680fa95e0f96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375179"
---
# <a name="cmfcribbonedit-class"></a>Klasa CMFCRibbonEdit

Implementuje formant edycji, który znajduje się na pasku wstążki.

## <a name="syntax"></a>Składnia

```cpp
class CMFCRibbonEdit : public CMFCRibbonButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonEdytuj::CMFCRibbonEdytuj](#cmfcribbonedit)|Konstruuje `CMFCRibbonEdit` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonEdytuj::CanBeStretched](#canbestretched)|Wskazuje, czy wysokość `CMFCRibbonEdit` formantu może wzrosnąć pionowo do wysokości wiersza wstążki.|
|[CMFCRibbonEdytuj::CMFCRibbonEdytuj](#cmfcribbonedit)|Konstruuje `CMFCRibbonEdit` obiekt.|
|[CMFCRibbonEdytuj::CopyFrom](#copyfrom)|Kopiuje stan określonego `CMFCRibbonEdit` obiektu do `CMFCRibbonEdit` bieżącego obiektu.|
|[CMFCRibbonEdytuj::UtwórzEdytuj](#createedit)|Tworzy nowe pole tekstowe `CMFCRibbonEdit` dla obiektu.|
|[CMFCRibbonEdytuj::DestroyCtrl](#destroyctrl)|Niszczy `CMFCRibbonEdit` obiekt.|
|[CMFCRibbonEdytuj::DropDownList](#dropdownlist)|Porzuca pole listy.|
|[CMFCRibbonEdytuj::EnableSpinButtons](#enablespinbuttons)|Włącza i ustawia zakres przycisku pokrętła dla pola tekstowego.|
|[CMFCRibbonEdyt::GetCompactSize](#getcompactsize)|Pobiera kompaktowy rozmiar `CFMCRibbonEdit` obiektu.|
|[CMFCRibbonEdyt::GetEditText](#getedittext)|Pobiera tekst w polu tekstowym.|
|[CMFCRibbonEdyt::GetIntermediateSize](#getintermediatesize)|Pobiera rozmiar pośredni `CMFCRibbonEdit` obiektu.|
|[CMFCRibbonEdyt::GetTextAlign](#gettextalign)|Pobiera wyrównanie tekstu w polu tekstowym.|
|[CMFCRibbonEdytuj::GetWidth](#getwidth)|Pobiera szerokość( w pikselach) `CMFCRibbonEdit` formantu.|
|[CMFCRibbonEdytuj::HasCompactMode](#hascompactmode)|Wskazuje, czy rozmiar wyświetlania `CMFCRibbonEdit` formantu może być kompaktowy.|
|[CMFCRibbonEdyt::HasFocus](#hasfocus)|Wskazuje, `CMFCRIbbonEdit` czy formant ma fokus.|
|[CMFCRibbonEdytuj::HasLargeMode](#haslargemode)|Wskazuje, czy rozmiar wyświetlania `CMFCRibbonEdit` formantu może być duży.|
|[CMFCRibbonEdytuj::HasSpinButtons](#hasspinbuttons)|Wskazuje, czy pole tekstowe ma przycisk pokrętła.|
|[CMFCRibbonEdyt::IsHighlighted](#ishighlighted)|Wskazuje, `CMFCRibbonEdit` czy formant jest wyróżniony.|
|[CMFCRibbonEdytuj::OnAfterChangeRect](#onafterchangerect)|Wywoływane przez strukturę, gdy zmienią się `CMFCRibbonEdit` wymiary prostokąta wyświetlania formantu.|
|[CMFCRibbonEdytuj::OnDraw](#ondraw)|Wywoływana przez ramy `CMFCRibbonEdit` do rysowania formantu.|
|[CMFCRibbonEdytuj::OnDrawLabelAndImage](#ondrawlabelandimage)|Wywoływana przez strukturę do rysowania `CMFCRibbonEdit` etykiety i obrazu dla formantu.|
|[CMFCRibbonEdytuj::OnDrawOnList](#ondrawonlist)|Wywoływane przez strukturę, aby narysować `CMFCRibbonEdit` formant w polu listy poleceń.|
|[CMFCRibbonEdytuj::OnEnable](#onenable)|Wywoływane przez strukturę, `CMFCRibbonEdit` aby włączyć lub wyłączyć formant.|
|[CMFCRibbonEdytuj::OnHighlight](#onhighlight)|Wywoływane przez strukturę, gdy wskaźnik wchodzi lub `CMFCRibbonEdit` opuszcza granice formantu.|
|[CMFCRibbonEdyt::OnKey](#onkey)|Wywoływane przez platformę, gdy użytkownik naciska `CMFCRibbonEdit` etykietkę klucza i formant ma fokus.|
|[CMFCRibbonEdyt::OnLButtonDown](#onlbuttondown)|Wywoływane przez strukturę, aby zaktualizować `CMFCRibbonEdit` formant, gdy użytkownik naciśnie lewy przycisk myszy na formancie.|
|[CMFCRibbonEdyt::OnLButtonUp](#onlbuttonup)|Wywoływane przez strukturę, gdy użytkownik zwalnia lewy przycisk myszy.|
|[CMFCRibbonEdyt::OnRTLZmieniony](#onrtlchanged)|Wywoływane przez strukturę, aby zaktualizować formant, `CMFCRibbonEdit` gdy układ zmienia kierunek.|
|[CMFCRibbonEdytuj::OnShow](#onshow)|Wywoływana przez strukturę, `CMFCRibbonEdit` aby pokazać lub ukryć formant.|
|[CMFCRibbonEdytuj::Przerysuj](#redraw)|Aktualizuje wyświetlanie `CMFCRibbonEdit` formantu.|
|[CMFCRibbonEdytuj::SetACCData](#setaccdata)|Ustawia dane ułatwień `CMFCRibbonEdit` dostępu dla obiektu.|
|[CMFCRibbonEdytuj::SetEditText](#setedittext)|Ustawia tekst w polu tekstowym.|
|[CMFCRibbonEdytuj::SetTextAlign](#settextalign)|Ustawia wyrównanie tekstu pola tekstowego.|
|[CMFCRibbonEdytuj::SetWidth](#setwidth)|Ustawia szerokość pola tekstowego `CMFCRibbonEdit` formantu.|

## <a name="remarks"></a>Uwagi

## <a name="example"></a>Przykład

W poniższym `CMFCRibbonEdit` przykładzie pokazano, jak skonstruować obiekt, wyświetlić przyciski pokrętła obok formantu edycji i ustawić tekst formantu edycji. Ten fragment kodu jest częścią [przykładu demo pakietu MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxRibbonEdit.h

## <a name="cmfcribboneditcanbestretched"></a><a name="canbestretched"></a>CMFCRibbonEdytuj::CanBeStretched

Wskazuje, czy wysokość [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) formantmoże zwiększyć pionowo do wysokości wiersza wstążki.

```cpp
virtual BOOL CanBeStretched();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość FAŁSZ.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboneditcmfcribbonedit"></a><a name="cmfcribbonedit"></a>CMFCRibbonEdytuj::CMFCRibbonEdytuj

Konstruuje [OBIEKT CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
CMFCRibbonEdit(
    UINT nID,
    int nWidth,
    LPCTSTR lpszLabel = NULL,
    int nImage = -1);

CMFCRibbonEdit();
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
[w] Identyfikator polecenia dla `CMFCRibbonEdit` formantu.

*nWidth (ww.*<br/>
[w] Szerokość w pikselach pola tekstowego `CMFCRibbonEdit` formantu.

*lpszLabel (lpszLabel)*<br/>
[w] Etykieta dla `CMFCRibbonEdit` formantu.

*nImage (Obraz)*<br/>
[w] Indeks małego obrazu do użycia `CMFCRibbonEdit` dla formantu. Kolekcja małych obrazów jest obsługiwana przez nadrzędną kategorię wstążki.

### <a name="remarks"></a>Uwagi

Formant `CMFCRibbonEdit` nie używa dużego obrazu.

## <a name="cmfcribboneditcopyfrom"></a><a name="copyfrom"></a>CMFCRibbonEdytuj::CopyFrom

Kopie stan określonego [OBIEKTU CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) do bieżącego [obiektu CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
[w] Obiekt `CMFCRibbonEdit` źródłowy.

### <a name="remarks"></a>Uwagi

Parametr *src* musi być `CMFCRibbonEdit`typu .

## <a name="cmfcribboneditcreateedit"></a><a name="createedit"></a>CMFCRibbonEdytuj::UtwórzEdytuj

Tworzy nowe pole tekstowe dla [obiektu CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Parametry

*pWndRodziciela*<br/>
[w] Wskaźnik do okna nadrzędnego `CMFCRibbonEdit` obiektu.

*dwEdytStyle*<br/>
[w] Określa styl pola tekstowego. Style okien wymienione w sekcji Uwagi można połączyć ze [stylami formantu edycji opisanymi](/windows/win32/Controls/edit-control-styles) w panelu Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowego pola tekstowego, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Zastąpi tę metodę w klasie pochodnej, aby utworzyć niestandardowe pole tekstowe.

Do pola tekstowego można zastosować następujące [style okien:](../../mfc/reference/styles-used-by-mfc.md#window-styles)

- **Ws_child**

- **Ws_visible**

- **WS_DISABLED**

- **WS_GROUP**

- **Ws_tabstop**

## <a name="cmfcribboneditdestroyctrl"></a><a name="destroyctrl"></a>CMFCRibbonEdytuj::DestroyCtrl

Niszczy [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) obiektu.

```cpp
virtual void DestroyCtrl();
```

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboneditdropdownlist"></a><a name="dropdownlist"></a>CMFCRibbonEdytuj::DropDownList

Porzuca pole listy.

```cpp
virtual void DropDownList();
```

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda nic nie robi. Zastąpi tę metodę, aby wyświetlić listę rozwijaną.

## <a name="cmfcribboneditenablespinbuttons"></a><a name="enablespinbuttons"></a>CMFCRibbonEdytuj::EnableSpinButtons

Włącza i ustawia zakres przycisku pokrętła dla pola tekstowego.

```cpp
void EnableSpinButtons(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parametry

*nMin (min.*<br/>
[w] Minimalna wartość przycisku spin.

*Nmax*<br/>
[w] Maksymalna wartość przycisku spin.

### <a name="remarks"></a>Uwagi

Przyciski obrotu wyświetlają strzałkę w górę i w dół oraz umożliwiają użytkownikom przechodzenie przez stały zestaw wartości.

## <a name="cmfcribboneditgetcompactsize"></a><a name="getcompactsize"></a>CMFCRibbonEdyt::GetCompactSize

Pobiera kompaktowy rozmiar [obiektu CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu `CMFCRibbonEdit` urządzenia dla obiektu.

### <a name="return-value"></a>Wartość zwracana

Kompaktowy rozmiar `CMFCRibbonEdit` obiektu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboneditgetedittext"></a><a name="getedittext"></a>CMFCRibbonEdyt::GetEditText

Pobiera tekst w polu tekstowym.

```cpp
CString GetEditText() const;
```

### <a name="return-value"></a>Wartość zwracana

Tekst w polu tekstowym.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboneditgetintermediatesize"></a><a name="getintermediatesize"></a>CMFCRibbonEdyt::GetIntermediateSize

Pobiera rozmiar pośredni [obiektu CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu `CMFCRibbonEdit` urządzenia dla obiektu.

### <a name="return-value"></a>Wartość zwracana

Rozmiar pośredni `CMFCRibbonEdit` obiektu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboneditgettextalign"></a><a name="gettextalign"></a>CMFCRibbonEdyt::GetTextAlign

Pobiera wyrównanie tekstu w polu tekstowym.

```cpp
int GetTextAlign() const;
```

### <a name="return-value"></a>Wartość zwracana

Wyrównanie tekstu wyliczone wartości. Zobacz uwagi sekcji możliwe wartości.

### <a name="remarks"></a>Uwagi

Zwracana wartość jest jednym z następujących stylów kontroli edycji:

- **ES_LEFT** do wyrównania w lewo

- **ES_CENTER** do wyrównania środka

- **ES_RIGHT** do wyrównania prawego

Aby uzyskać więcej informacji na temat tych stylów, zobacz [Edytowanie stylów sterowania](/windows/win32/Controls/edit-control-styles).

## <a name="cmfcribboneditgetwidth"></a><a name="getwidth"></a>CMFCRibbonEdytuj::GetWidth

Pobiera szerokość, w pikselach, [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli.

```cpp
int GetWidth(BOOL bInFloatyMode = FALSE) const;
```

### <a name="parameters"></a>Parametry

*bInFloatyMode*<br/>
[w] PRAWDA, `CMFCRibbonEdit` jeśli formant jest w trybie przestawnym; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

Szerokość `CMFCRibbonEdit` formantu w pikselach.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonedithascompactmode"></a><a name="hascompactmode"></a>CMFCRibbonEdytuj::HasCompactMode

Wskazuje, czy rozmiar wyświetlania dla [cmfcribbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli może być kompaktowy.

```cpp
virtual BOOL HasCompactMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda zawsze zwraca wartość PRAWDA. Zastąd w tej metodzie należy wskazać, czy rozmiar wyświetlania może być kompaktowy.

## <a name="cmfcribbonedithasfocus"></a><a name="hasfocus"></a>CMFCRibbonEdyt::HasFocus

Wskazuje, czy [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) formant ma fokus.

```cpp
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, `CMFCRibbonEdit` jeśli formant ma fokus; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonedithaslargemode"></a><a name="haslargemode"></a>CMFCRibbonEdytuj::HasLargeMode

Wskazuje, czy rozmiar wyświetlania dla [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) formant może być duży.

```cpp
virtual BOOL HasLargeMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość FAŁSZ.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda zawsze zwraca wartość FAŁSZ. Zastąd w tej metodzie należy wskazać, czy rozmiar wyświetlania może być duży.

## <a name="cmfcribbonedithasspinbuttons"></a><a name="hasspinbuttons"></a>CMFCRibbonEdytuj::HasSpinButtons

Wskazuje, czy pole tekstowe ma przycisk pokrętła.

```cpp
virtual BOOL HasSpinButtons() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli pole tekstowe ma przycisk pokrętła; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboneditishighlighted"></a><a name="ishighlighted"></a>CMFCRibbonEdyt::IsHighlighted

Wskazuje, czy [cmfcribbonEdit](../../mfc/reference/cmfcribbonedit-class.md) formant jest wyróżniony.

```cpp
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, `CMFCRibbonEdit` jeśli formant jest wyróżniony; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboneditonafterchangerect"></a><a name="onafterchangerect"></a>CMFCRibbonEdytuj::OnAfterChangeRect

Wywoływane przez strukturę, gdy zmienią się wymiary prostokąta wyświetlania dla formantu [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual void OnAfterChangeRect(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu `CMFCRibbonEdit` urządzenia dla formantu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboneditondraw"></a><a name="ondraw"></a>CMFCRibbonEdytuj::OnDraw

Wywoływana przez ramy do rysowania [cmfcribbonedit](../../mfc/reference/cmfcribbonedit-class.md) kontroli.

```cpp
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu `CMFCRibbonEdit` urządzenia dla formantu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboneditondrawlabelandimage"></a><a name="ondrawlabelandimage"></a>CMFCRibbonEdytuj::OnDrawLabelAndImage

Wywoływana przez strukturę do rysowania etykiety i obrazu dla [cmfcribbonedit](../../mfc/reference/cmfcribbonedit-class.md) kontroli.

```cpp
virtual void OnDrawLabelAndImage(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu `CMFCRibbonEdit` urządzenia dla formantu.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboneditondrawonlist"></a><a name="ondrawonlist"></a>CMFCRibbonEdytuj::OnDrawOnList

Wywoływana przez platformę do rysowania [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli w polu listy poleceń.

```cpp
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu `CMFCRibbonEdit` urządzenia dla formantu.

*strText (tekst)*<br/>
[w] Wyświetlany tekst [ ](../../mfc/reference/cmfcribbonedit-class.md "klasa cmfcribbonedit").

*nTextOffset (Zestaw nTextOffset)*<br/>
[w] Odległość w pikselach od lewej strony pola listy do wyświetlanego tekstu.

*Rect*<br/>
[w] Prostokąt wyświetlania formantu. `CMFCRibbonEdit`

*bWybrany*<br/>
[w] Ten parametr nie jest używany.

*bWyświetlony*<br/>
[w] Ten parametr nie jest używany.

### <a name="remarks"></a>Uwagi

W polu listy poleceń są wyświetlane kontrolki wstążki umożliwiające użytkownikom dostosowanie paska narzędzi szybkiego dostępu.

## <a name="cmfcribboneditonenable"></a><a name="onenable"></a>CMFCRibbonEdytuj::OnEnable

Wywoływane przez platformę, aby włączyć lub wyłączyć [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli.

```cpp
virtual void OnEnable(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
[w] TRUE, aby włączyć formant; FALSE, aby wyłączyć formant.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboneditonhighlight"></a><a name="onhighlight"></a>CMFCRibbonEdytuj::OnHighlight

Wywoływane przez strukturę, gdy wskaźnik wchodzi lub opuszcza granice [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli.

```cpp
virtual void OnHighlight(BOOL bHighlight);
```

### <a name="parameters"></a>Parametry

*bWyświetlenie*<br/>
[w] PRAWDA, jeśli wskaźnik znajduje się `CMFCRibbonEdit` w granicach formantu; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboneditonkey"></a><a name="onkey"></a>CMFCRibbonEdyt::OnKey

Wywoływane przez platformę, gdy użytkownik naciska klawiatury i [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli ma fokus.

```cpp
virtual BOOL OnKey(BOOL bIsMenuKey);
```

### <a name="parameters"></a>Parametry

*bIsMenuKey*<br/>
[w] PRAWDA, jeśli w etykietce klawisza jest wyświetlane wyskakujące menu; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli zdarzenie zostało obsłużony; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboneditonlbuttondown"></a><a name="onlbuttondown"></a>CMFCRibbonEdyt::OnLButtonDown

Wywoływana przez platformę, aby zaktualizować [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli, gdy użytkownik naciska lewy przycisk myszy na formancie.

```cpp
virtual void OnLButtonDown(CPoint point);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
[w] Ten parametr nie jest używany.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboneditonlbuttonup"></a><a name="onlbuttonup"></a>CMFCRibbonEdyt::OnLButtonUp

Wywoływane przez strukturę, gdy użytkownik zwalnia lewy przycisk myszy.

```cpp
virtual void OnLButtonUp(CPoint point);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
[w] Ten parametr nie jest używany.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboneditonrtlchanged"></a><a name="onrtlchanged"></a>CMFCRibbonEdyt::OnRTLZmieniony

Wywoływana przez strukturę, aby zaktualizować [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli, gdy układ zmienia kierunek.

```cpp
virtual void OnRTLChanged(BOOL bIsRTL);
```

### <a name="parameters"></a>Parametry

*bIsRTL*<br/>
[w] PRAWDA, jeśli układ jest od prawej do lewej; FAŁSZ, jeśli układ jest od lewej do prawej.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboneditonshow"></a><a name="onshow"></a>CMFCRibbonEdytuj::OnShow

Wywoływana przez platformę, aby pokazać lub ukryć [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli.

```cpp
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bPokaż*<br/>
[w] TRUE, aby wyświetlić formant; FALSE, aby ukryć formant.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboneditredraw"></a><a name="redraw"></a>CMFCRibbonEdytuj::Przerysuj

Aktualizuje wyświetlanie [cmfcribbonEdit](../../mfc/reference/cmfcribbonedit-class.md) kontroli.

```cpp
virtual void Redraw();
```

### <a name="remarks"></a>Uwagi

Ta metoda ponownie rysuje prostokąt wyświetlania `CMFCRibbonEdit` obiektu, pośrednio wywołując [CWnd::RedrawWindow](/windows/win32/api/winuser/nf-winuser-redrawwindow) z ustawioną RDW_INVALIDATE, RDW_ERASE i RDW_UPDATENOW flagami.

## <a name="cmfcribboneditsetaccdata"></a><a name="setaccdata"></a>CMFCRibbonEdytuj::SetACCData

Ustawia dane ułatwień dostępu dla [obiektu CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pRoczysz*<br/>
Wskaźnik do okna nadrzędnego `CMFCRibbonEdit` obiektu.

*Danych*<br/>
Dane ułatwień `CMFCRibbonEdit` dostępu dla obiektu.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboneditsetedittext"></a><a name="setedittext"></a>CMFCRibbonEdytuj::SetEditText

Ustawia tekst w polu tekstowym.

```cpp
void SetEditText(CString strText);
```

### <a name="parameters"></a>Parametry

*strText (tekst)*<br/>
[w] Tekst pola tekstowego.

## <a name="cmfcribboneditsettextalign"></a><a name="settextalign"></a>CMFCRibbonEdytuj::SetTextAlign

Ustawia wyrównanie tekstu pola tekstowego.

```cpp
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>Parametry

*nZłańczyć*<br/>
[w] Wyrównanie tekstu wyliczone wartości. Zobacz uwagi sekcji możliwe wartości.

### <a name="remarks"></a>Uwagi

Parametr *nAlign* jest jednym z następujących stylów sterowania edycją:

- ES_LEFT do wyrównania w lewo

- ES_CENTER do wyrównania środka

- ES_RIGHT do wyrównania prawego

Aby uzyskać więcej informacji na temat tych stylów, zobacz [Edytowanie stylów sterowania](/windows/win32/Controls/edit-control-styles).

## <a name="cmfcribboneditsetwidth"></a><a name="setwidth"></a>CMFCRibbonEdytuj::SetWidth

Ustawia szerokość pola tekstowego dla [kontrolki CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
void SetWidth(
    int nWidth,
    BOOL bInFloatyMode = FALSE);
```

### <a name="parameters"></a>Parametry

*nWidth (ww.*<br/>
[w] Szerokość pola tekstowego w pikselach.

*bInFloatyMode*<br/>
PRAWDA, aby ustawić szerokość dla trybu przestawnego; FALSE, aby ustawić szerokość dla trybu regularnego.

### <a name="remarks"></a>Uwagi

Formant `CMFCRibbonEdit` ma dwie szerokości w zależności od trybu wyświetlania: tryb przestawny i tryb normalny.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[Klasa CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)
