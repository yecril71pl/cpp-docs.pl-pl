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
ms.openlocfilehash: b260d3a88fc8c3f2d341005c1e47cfd9ab668e1e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500360"
---
# <a name="cdraglistbox-class"></a>Klasa CDragListBox

Oprócz udostępniania funkcjonalności pola listy systemu Windows, `CDragListBox` Klasa umożliwia użytkownikowi przenoszenie elementów pola listy, takich jak nazwy plików, w polu listy.

## <a name="syntax"></a>Składnia

```
class CDragListBox : public CListBox
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDragListBox::CDragListBox](#cdraglistbox)|Konstruuje `CDragListBox` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDragListBox::BeginDrag](#begindrag)|Wywoływane przez platformę po rozpoczęciu operacji przeciągania.|
|[CDragListBox::CancelDrag](#canceldrag)|Wywoływane przez platformę, gdy operacja przeciągania została anulowana.|
|[CDragListBox::D ragging](#dragging)|Wywoływane przez platformę w trakcie operacji przeciągania.|
|[CDragListBox::D rawInsert](#drawinsert)|Rysuje prowadnicę wstawiania pola listy przeciągnij.|
|[CDragListBox::D ropped](#dropped)|Wywoływane przez platformę po usunięciu elementu.|
|[CDragListBox::ItemFromPt](#itemfrompt)|Zwraca współrzędne przeciąganego elementu.|

## <a name="remarks"></a>Uwagi

Pola listy z tą możliwością umożliwiają użytkownikom kolejność elementów na liście w dowolny sposób, który jest najbardziej przydatny dla nich. Domyślnie pole listy spowoduje przeniesienie elementu do nowej lokalizacji na liście. Jednak `CDragListBox` obiekty można dostosować w celu kopiowania elementów zamiast ich przesuwania.

Kontrolka pola listy skojarzona z `CDragListBox` klasą nie może mieć stylu LBS_SORT ani LBS_MULTIPLESELECT. Aby uzyskać opis stylów pól listy, zobacz [Style pola listy](../../mfc/reference/styles-used-by-mfc.md#list-box-styles).

Aby użyć przeciąganego pola listy w istniejącym oknie dialogowym aplikacji, Dodaj kontrolkę pole listy do szablonu okna dialogowego przy użyciu edytora okien dialogowych, a następnie przypisz zmienną członkowską (kategorii `Control` i typu zmiennej `CDragListBox` ) odpowiadającą kontrolce pole listy w szablonie okna dialogowego.

Aby uzyskać więcej informacji na temat przypisywania formantów do zmiennych składowych, zobacz [skrót do definiowania zmiennych członkowskich dla formantów okna dialogowego](../../windows/adding-editing-or-deleting-controls.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CDragListBox`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn. h

## <a name="cdraglistboxbegindrag"></a><a name="begindrag"></a> CDragListBox::BeginDrag

Wywoływane przez platformę, gdy wystąpi zdarzenie, które może rozpocząć operację przeciągania, taką jak naciśnięcie lewego przycisku myszy.

```
virtual BOOL BeginDrag(CPoint pt);
```

### <a name="parameters"></a>Parametry

*zmiennoprzecinkow*<br/>
Obiekt [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) , który zawiera współrzędne przeciąganego elementu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli przeciąganie jest dozwolone, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję, jeśli chcesz kontrolować, co się dzieje po rozpoczęciu operacji przeciągania. Domyślna implementacja przechwytuje mysz i pozostaje w trybie przeciągania, dopóki użytkownik kliknie lewy lub prawy przycisk myszy lub naciśnie klawisz ESC, podczas którego operacja przeciągania zostanie anulowana.

## <a name="cdraglistboxcanceldrag"></a><a name="canceldrag"></a> CDragListBox::CancelDrag

Wywoływane przez platformę, gdy operacja przeciągania została anulowana.

```
virtual void CancelDrag(CPoint pt);
```

### <a name="parameters"></a>Parametry

*zmiennoprzecinkow*<br/>
Obiekt [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) , który zawiera współrzędne przeciąganego elementu.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby obsłużyć wszelkie specjalne przetwarzanie dla kontrolki pole listy.

## <a name="cdraglistboxcdraglistbox"></a><a name="cdraglistbox"></a> CDragListBox::CDragListBox

Konstruuje `CDragListBox` obiekt.

```
CDragListBox();
```

## <a name="cdraglistboxdragging"></a><a name="dragging"></a> CDragListBox::D ragging

Wywoływane przez platformę, gdy element pola listy jest przeciągany w obrębie `CDragListBox` obiektu.

```
virtual UINT Dragging(CPoint pt);
```

### <a name="parameters"></a>Parametry

*zmiennoprzecinkow*<br/>
Obiekt [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) , który zawiera współrzędne ekranu x i y kursora.

### <a name="return-value"></a>Wartość zwracana

Identyfikator zasobu kursora, który ma zostać wyświetlony. Możliwe są następujące wartości:

- DL_COPYCURSOR wskazuje, że element zostanie skopiowany.

- DL_MOVECURSOR wskazuje, że element zostanie przeniesiony.

- DL_STOPCURSOR wskazuje, że bieżący element docelowy upuszczania nie jest akceptowalny.

### <a name="remarks"></a>Uwagi

Zachowanie domyślne zwraca DL_MOVECURSOR. Zastąp tę funkcję, jeśli chcesz udostępnić dodatkowe funkcje.

## <a name="cdraglistboxdrawinsert"></a><a name="drawinsert"></a> CDragListBox::D rawInsert

Wywoływane przez platformę, by narysować prowadnicę wstawiania przed elementem o wskazanym indeksie.

```
virtual void DrawInsert(int nItem);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Indeks (liczony od zera) punktu wstawiania.

### <a name="remarks"></a>Uwagi

Wartość-1 czyści prowadnicę wstawiania. Zastąp tę funkcję, aby zmodyfikować wygląd lub zachowanie przewodnika wstawiania.

## <a name="cdraglistboxdropped"></a><a name="dropped"></a> CDragListBox::D ropped

Wywoływane przez platformę, gdy element zostanie porzucony w `CDragListBox` obiekcie.

```
virtual void Dropped(
    int nSrcIndex,
    CPoint pt);
```

### <a name="parameters"></a>Parametry

*nSrcIndex*<br/>
Określa indeks ciągu porzuconego od zera.

*zmiennoprzecinkow*<br/>
Obiekt [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) , który zawiera współrzędne lokacji docelowej.

### <a name="remarks"></a>Uwagi

Zachowanie domyślne kopiuje element pola listy i jego dane do nowej lokalizacji, a następnie usuwa oryginalny element. Przesłoń tę funkcję, aby dostosować zachowanie domyślne, takie jak włączenie kopiowania elementów pola listy do przeciągania do innych lokalizacji na liście.

## <a name="cdraglistboxitemfrompt"></a><a name="itemfrompt"></a> CDragListBox::ItemFromPt

Wywołaj tę funkcję, aby pobrać indeks (liczony od zera) elementu pola listy znajdującego się w *pkt pt*.

```
int ItemFromPt(
    CPoint pt,
    BOOL bAutoScroll = TRUE) const;
```

### <a name="parameters"></a>Parametry

*zmiennoprzecinkow*<br/>
Obiekt [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) zawierający współrzędne punktu w polu listy.

*bAutoScroll*<br/>
Niezerowe, jeśli przewijanie jest dozwolone, w przeciwnym razie 0.

### <a name="return-value"></a>Wartość zwracana

Indeks (liczony od zera) elementu pola listy.

## <a name="see-also"></a>Zobacz też

[Przykład TSTCON MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CListBox](../../mfc/reference/clistbox-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CListBox](../../mfc/reference/clistbox-class.md)
