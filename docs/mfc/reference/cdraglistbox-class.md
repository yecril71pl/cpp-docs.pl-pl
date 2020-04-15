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
ms.openlocfilehash: 0d1ae94948e1143a5bac17985423c4bd1bfbaf65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374032"
---
# <a name="cdraglistbox-class"></a>Klasa CDragListBox

Oprócz zapewnienia funkcjonalności pola listy systemu `CDragListBox` Windows, klasa umożliwia użytkownikowi przenoszenie elementów pola listy, takich jak nazwy plików, w polu listy.

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
|[CDragListBox::BeginDrag](#begindrag)|Wywoływana przez platformę po rozpoczęciu operacji przeciągania.|
|[CDragListBox::CancelDrag](#canceldrag)|Wywoływana przez platformę, gdy operacja przeciągania została anulowana.|
|[CDragListBox: :Dragging](#dragging)|Wywoływana przez strukturę podczas operacji przeciągania.|
|[CDragListBox::DrawInsert](#drawinsert)|Rysuje prowadnicę wstawiania pola listy przeciągania.|
|[CDragListBox::Dropped](#dropped)|Wywoływana przez platformę po upuszczeniu elementu.|
|[CDragListBox::ItemFromPt](#itemfrompt)|Zwraca współrzędne przeciąganego elementu.|

## <a name="remarks"></a>Uwagi

Pola listy z tą możliwością umożliwiają użytkownikom uporządkowanie elementów na liście w dowolny sposób, niezależnie od tego, co jest dla nich najbardziej przydatne. Domyślnie pole listy spowoduje przeniesienie elementu do nowej lokalizacji na liście. Jednak `CDragListBox` obiekty można dostosować do kopiowania elementów zamiast przenoszenia ich.

Formant pola listy skojarzony z klasą `CDragListBox` nie może mieć LBS_SORT lub stylu LBS_MULTIPLESELECT. Aby uzyskać opis stylów pól listy, zobacz [Style pola listy](../../mfc/reference/styles-used-by-mfc.md#list-box-styles).

Aby użyć pola listy przeciągania w istniejącym oknie dialogowym aplikacji, dodaj kontrolkę pola listy do szablonu okna dialogowego za pomocą edytora dialogów, a następnie przypisz zmienną członkową (kategorii `Control` i typu `CDragListBox`zmiennej) odpowiadającą formancie pola listy w szablonie okna dialogowego.

Aby uzyskać więcej informacji na temat przypisywania formantów do zmiennych członkowskich, zobacz [Skrót do definiowania zmiennych członkowskich dla kontrolek dialogowych](../../windows/defining-member-variables-for-dialog-controls.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Clistbox](../../mfc/reference/clistbox-class.md)

`CDragListBox`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

## <a name="cdraglistboxbegindrag"></a><a name="begindrag"></a>CDragListBox::BeginDrag

Wywoływane przez platformę, gdy wystąpi zdarzenie, które może rozpocząć operację przeciągania, takie jak naciśnięcie lewego przycisku myszy.

```
virtual BOOL BeginDrag(CPoint pt);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
Obiekt [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) zawierający współrzędne przeciąganego elementu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli przeciąganie jest dozwolone, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zastąd w tej funkcji należy zastąpić, jeśli chcesz kontrolować, co się dzieje po rozpoczęciu operacji przeciągania. Domyślna implementacja przechwytuje myszy i pozostaje w trybie przeciągania, dopóki użytkownik nie kliknie lewego lub prawego przycisku myszy lub naciśnie ESC, w którym to czasie operacja przeciągania jest anulowana.

## <a name="cdraglistboxcanceldrag"></a><a name="canceldrag"></a>CDragListBox::CancelDrag

Wywoływana przez platformę, gdy operacja przeciągania została anulowana.

```
virtual void CancelDrag(CPoint pt);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
Obiekt [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) zawierający współrzędne przeciąganego elementu.

### <a name="remarks"></a>Uwagi

Zastąpaj tę funkcję, aby obsłużyć wszelkie specjalne przetwarzanie dla formantu pola listy.

## <a name="cdraglistboxcdraglistbox"></a><a name="cdraglistbox"></a>CDragListBox::CDragListBox

Konstruuje `CDragListBox` obiekt.

```
CDragListBox();
```

## <a name="cdraglistboxdragging"></a><a name="dragging"></a>CDragListBox: :Dragging

Wywoływane przez strukturę, gdy element pola `CDragListBox` listy jest przeciągany wewnątrz obiektu.

```
virtual UINT Dragging(CPoint pt);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
Obiekt [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) zawierający współrzędne ekranu x i y kursora.

### <a name="return-value"></a>Wartość zwracana

Identyfikator zasobu kursora, który ma być wyświetlany. Możliwe są następujące wartości:

- DL_COPYCURSOR Wskazuje, że element zostanie skopiowany.

- DL_MOVECURSOR Wskazuje, że element zostanie przeniesiony.

- DL_STOPCURSOR Wskazuje, że bieżący obiekt docelowy upuszczania jest nie do przyjęcia.

### <a name="remarks"></a>Uwagi

Domyślne zachowanie zwraca DL_MOVECURSOR. Zastąd w tej funkcji należy zastąpić, jeśli chcesz zapewnić dodatkowe funkcje.

## <a name="cdraglistboxdrawinsert"></a><a name="drawinsert"></a>CDragListBox::DrawInsert

Wywoływana przez strukturę, aby narysować przewodnik wstawiania przed elementem ze wskazanym indeksem.

```
virtual void DrawInsert(int nItem);
```

### <a name="parameters"></a>Parametry

*nJejsza*<br/>
Indeks od zera punktu wstawiania.

### <a name="remarks"></a>Uwagi

Wartość - 1 czyści prowadnicę wstawiania. Zastąrpnąć tę funkcję, aby zmodyfikować wygląd lub zachowanie prowadnicy wstawiania.

## <a name="cdraglistboxdropped"></a><a name="dropped"></a>CDragListBox::Dropped

Wywoływane przez platformę, gdy `CDragListBox` element jest upuszczany w obrębie obiektu.

```
virtual void Dropped(
    int nSrcIndex,
    CPoint pt);
```

### <a name="parameters"></a>Parametry

*nSrcIndex*<br/>
Określa indeks od zera upuszczonego ciągu.

*Pt*<br/>
Obiekt [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) zawierający współrzędne witryny upuszczania.

### <a name="remarks"></a>Uwagi

Domyślne zachowanie kopiuje element pola listy i jego dane do nowej lokalizacji, a następnie usuwa oryginalny element. Zastąp tę funkcję, aby dostosować domyślne zachowanie, takie jak włączanie przeciągania kopii elementów pola listy do innych lokalizacji na liście.

## <a name="cdraglistboxitemfrompt"></a><a name="itemfrompt"></a>CDragListBox::ItemFromPt

Wywołanie tej funkcji, aby pobrać indeks od zera elementu pola listy znajdującego się w *pt*.

```
int ItemFromPt(
    CPoint pt,
    BOOL bAutoScroll = TRUE) const;
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
Obiekt [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) zawierający współrzędne punktu w polu listy.

*bAutoScroll*<br/>
Nonzero, jeśli przewijanie jest dozwolone, w przeciwnym razie 0.

### <a name="return-value"></a>Wartość zwracana

Indeks pola listy przeciągania oparty na wartości zerowej.

## <a name="see-also"></a>Zobacz też

[Próbka MFC TSTCON](../../overview/visual-cpp-samples.md)<br/>
[Klasa CListBox](../../mfc/reference/clistbox-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CListBox](../../mfc/reference/clistbox-class.md)
