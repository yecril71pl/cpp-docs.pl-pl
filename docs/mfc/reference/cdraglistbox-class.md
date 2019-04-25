---
title: Klasa CDragListBox
ms.date: 11/04/2016
f1_keywords:
- CDragListBox
- AFXCMN/CDragListBox
- AFXCMN/CDragListBox::CDragListBox
- AFXCMN/CDragListBox::BeginDrag
- AFXCMN/CDragListBox::CancelDrag
- AFXCMN/CDragListBox::Dragging
- AFXCMN/CDragListBox::DrawInsert
- AFXCMN/CDragListBox::Dropped
- AFXCMN/CDragListBox::ItemFromPt
helpviewer_keywords:
- CDragListBox [MFC], CDragListBox
- CDragListBox [MFC], BeginDrag
- CDragListBox [MFC], CancelDrag
- CDragListBox [MFC], Dragging
- CDragListBox [MFC], DrawInsert
- CDragListBox [MFC], Dropped
- CDragListBox [MFC], ItemFromPt
ms.assetid: fee20b42-60ae-4aa9-83f9-5a3d9b96e33b
ms.openlocfilehash: d8afc5b14f5f52ca7a4d28a3d3c3c5440b7c819f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164049"
---
# <a name="cdraglistbox-class"></a>Klasa CDragListBox

Ponadto, aby zapewnić funkcjonalność pola listy Windows `CDragListBox` klasy umożliwia użytkownikowi przenoszenie elementów pola listy, takich jak nazwy plików, w polu listy.

## <a name="syntax"></a>Składnia

```
class CDragListBox : public CListBox
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDragListBox::CDragListBox](#cdraglistbox)|Konstruuje `CDragListBox` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDragListBox::BeginDrag](#begindrag)|Wywoływane przez platformę, gdy rozpoczyna się operacja przeciągania.|
|[CDragListBox::CancelDrag](#canceldrag)|Wywoływane przez platformę, gdy Anulowano operację przeciągania.|
|[CDragListBox::Dragging](#dragging)|Wywoływane przez platformę w czasie trwania operacji przeciągania.|
|[CDragListBox::DrawInsert](#drawinsert)|Rysuje prowadnicę wstawiania, przeciągnij pola listy.|
|[CDragListBox::Dropped](#dropped)|Wywoływane przez platformę po upuszczeniu elementu.|
|[CDragListBox::ItemFromPt](#itemfrompt)|Zwraca współrzędne elementu przeciągania.|

## <a name="remarks"></a>Uwagi

Pola list z tej możliwości użytkownicy kolejność elementów na liście w jakikolwiek sposób najbardziej przydaje się do nich. Domyślnie pole listy będzie przenieść element do nowej lokalizacji na liście. Jednak `CDragListBox` obiekty można dostosować tak, aby skopiować elementy zamiast przenoszenia ich.

Skojarzony formant pola listy `CDragListBox` klasy nie może mieć LBS_SORT lub stylu LBS_MULTIPLESELECT. Aby uzyskać opis style pola listy, zobacz [style pola listy](../../mfc/reference/styles-used-by-mfc.md#list-box-styles).

Aby użyć przeciągania pola listy w oknie dialogowym istniejących aplikacji, Dodaj pole listy do szablonu okna dialogowego za pomocą edytora okien dialogowych, a następnie przypisz zmienną członkowską (kategorii `Control` i typ zmiennej `CDragListBox`) odpowiadający pole listy kontrolowanie w szablonie okna dialogowego.

Aby uzyskać więcej informacji na temat przypisywania formanty do zmiennych składowych, zobacz [skrót do definiowania zmiennych Członkowskich dla formantów okna dialogowego](../../windows/defining-member-variables-for-dialog-controls.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CDragListBox`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

##  <a name="begindrag"></a>  CDragListBox::BeginDrag

Wywoływane przez platformę, gdy wystąpi zdarzenie, które można rozpocząć operacji przeciągania, takich jak naciśnięcie klawisza lewego przycisku myszy.

```
virtual BOOL BeginDrag(CPoint pt);
```

### <a name="parameters"></a>Parametry

*(czas pacyficzny)*<br/>
A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) obiekt, który zawiera współrzędne elementu przeciągania.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli przeciąganie może, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę funkcję, jeśli chcesz kontrolować, co się dzieje po rozpoczęciu operacji przeciągania. Domyślna implementacja przechwytuje mysz i pozostaje w trybie przeciągnij, dopóki użytkownik kliknie przycisk myszy w lewo lub w prawo lub naciśnie klawisz ESC, w tym czasie operacji przeciągania zostanie anulowane.

##  <a name="canceldrag"></a>  CDragListBox::CancelDrag

Wywoływane przez platformę, gdy Anulowano operację przeciągania.

```
virtual void CancelDrag(CPoint pt);
```

### <a name="parameters"></a>Parametry

*(czas pacyficzny)*<br/>
A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) obiekt, który zawiera współrzędne elementu przeciągania.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę funkcję, aby obsługiwać żadnych specjalnych przetwarzania dla kontrolki pola listy.

##  <a name="cdraglistbox"></a>  CDragListBox::CDragListBox

Konstruuje `CDragListBox` obiektu.

```
CDragListBox();
```

##  <a name="dragging"></a>  CDragListBox::Dragging

Wywoływane przez platformę podczas przeciągania elementu pola listy w ramach `CDragListBox` obiektu.

```
virtual UINT Dragging(CPoint pt);
```

### <a name="parameters"></a>Parametry

*(czas pacyficzny)*<br/>
A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) obiekt, który zawiera x i y ekran współrzędne kursora.

### <a name="return-value"></a>Wartość zwracana

Identyfikator zasobu kursora do wyświetlenia. Możliwe są następujące wartości:

- DL_COPYCURSOR wskazuje, że zostanie skopiowany element.

- DL_MOVECURSOR wskazuje, że będzie można przenieść elementu.

- DL_STOPCURSOR wskazuje, czy bieżący element docelowy nie jest dopuszczalna.

### <a name="remarks"></a>Uwagi

Domyślne zachowanie zwraca DL_MOVECURSOR. Należy przesłonić tę funkcję, aby zapewnić dodatkowe funkcje.

##  <a name="drawinsert"></a>  CDragListBox::DrawInsert

Metoda wywoływana przez platformę, by narysować prowadnicę wstawiania przed elementem o wskazanym indeksie.

```
virtual void DrawInsert(int nItem);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Liczony od zera indeks punktu wstawiania.

### <a name="remarks"></a>Uwagi

Wartość - 1 powoduje wyczyszczenie prowadnicę wstawiania. Należy przesłonić tę funkcję, aby zmodyfikować wygląd i zachowanie prowadnicę wstawiania.

##  <a name="dropped"></a>  CDragListBox::Dropped

Wywoływane przez platformę, gdy element zostanie porzucony w ramach `CDragListBox` obiektu.

```
virtual void Dropped(
    int nSrcIndex,
    CPoint pt);
```

### <a name="parameters"></a>Parametry

*nSrcIndex*<br/>
Określa liczony od zera indeks porzuconych ciągu.

*(czas pacyficzny)*<br/>
A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) obiekt, który zawiera współrzędne lokacji docelowej.

### <a name="remarks"></a>Uwagi

Domyślne zachowanie kopiuje elementu pola listy i jego danych do nowej lokalizacji, a następnie usuwa oryginalnego elementu. Należy przesłonić tę funkcję, aby dostosować zachowanie domyślne, takich jak umożliwianie kopie elementów pola listy, można przeciągać do innych lokalizacji w obrębie listy.

##  <a name="itemfrompt"></a>  CDragListBox::ItemFromPt

Wywołanie tej funkcji można pobrać liczony od zera indeks elementu pola listy znajdującym się w *pt*.

```
int ItemFromPt(
    CPoint pt,
    BOOL bAutoScroll = TRUE) const;
```

### <a name="parameters"></a>Parametry

*(czas pacyficzny)*<br/>
A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) obiekt, który zawiera współrzędne punktu, w polu listy.

*bAutoScroll*<br/>
Różna od zera, jeśli przewijania może, w przeciwnym razie 0.

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks elementu pola listy przeciągania.

## <a name="see-also"></a>Zobacz także

[MFC Sample TSTCON](../../overview/visual-cpp-samples.md)<br/>
[Klasa CListBox](../../mfc/reference/clistbox-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CListBox](../../mfc/reference/clistbox-class.md)
