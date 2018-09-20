---
title: Klasa CStatic | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStatic
- AFXWIN/CStatic
- AFXWIN/CStatic::CStatic
- AFXWIN/CStatic::Create
- AFXWIN/CStatic::DrawItem
- AFXWIN/CStatic::GetBitmap
- AFXWIN/CStatic::GetCursor
- AFXWIN/CStatic::GetEnhMetaFile
- AFXWIN/CStatic::GetIcon
- AFXWIN/CStatic::SetBitmap
- AFXWIN/CStatic::SetCursor
- AFXWIN/CStatic::SetEnhMetaFile
- AFXWIN/CStatic::SetIcon
dev_langs:
- C++
helpviewer_keywords:
- CStatic [MFC], CStatic
- CStatic [MFC], Create
- CStatic [MFC], DrawItem
- CStatic [MFC], GetBitmap
- CStatic [MFC], GetCursor
- CStatic [MFC], GetEnhMetaFile
- CStatic [MFC], GetIcon
- CStatic [MFC], SetBitmap
- CStatic [MFC], SetCursor
- CStatic [MFC], SetEnhMetaFile
- CStatic [MFC], SetIcon
ms.assetid: e7c94cd9-5ebd-428a-aa30-b3e51f8efb95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 084a3101b7415ae4b77ed11070c893a7bc44ac37
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439669"
---
# <a name="cstatic-class"></a>Klasa CStatic

Oferuje funkcje formantu statycznego Windows.

## <a name="syntax"></a>Składnia

```
class CStatic : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStatic::CStatic](#cstatic)|Konstruuje `CStatic` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStatic::Create](#create)|Tworzy formant statyczny Windows i dołącza je do `CStatic` obiektu.|
|[CStatic::DrawItem](#drawitem)|Należy przesłonić, aby narysować statyczną kontrolkę rysowanych przez właściciela.|
|[CStatic::GetBitmap](#getbitmap)|Pobiera uchwyt mapy bitowej ustawione wcześniej przy użyciu [SetBitmap](#setbitmap).|
|[CStatic::GetCursor](#getcursor)|Pobiera uchwyt obraz kursora ustawione wcześniej przy użyciu [SetCursor](#setcursor).|
|[CStatic::GetEnhMetaFile](#getenhmetafile)|Pobiera uchwyt rozszerzony metaplik ustawione wcześniej przy użyciu [SetEnhMetaFile](#setenhmetafile).|
|[CStatic::GetIcon](#geticon)|Pobiera uchwyt ikony ustawione wcześniej przy użyciu [SetIcon](#seticon).|
|[CStatic::SetBitmap](#setbitmap)|Określa mapy bitowej do wyświetlenia w kontrolce statyczne.|
|[CStatic::SetCursor](#setcursor)|Określa obraz kursora, mają być wyświetlane w kontrolki statycznej.|
|[CStatic::SetEnhMetaFile](#setenhmetafile)|Określa rozszerzony metaplik mają być wyświetlane w kontrolki statycznej.|
|[CStatic::SetIcon](#seticon)|Określa ikonę do wyświetlenia w kontrolce statyczne.|

## <a name="remarks"></a>Uwagi

Formant statyczny wyświetla ciąg tekstowy, pole, prostokąt, ikona, kursor, mapa bitowa lub rozszerzony metaplik. Może służyć do etykiety, pole lub rozdzielić innych kontrolek. Formant statyczny zwykle nie wymaga danych wejściowych i zawiera żadnych danych wyjściowych; jednak go powiadamiać swój element nadrzędny, kliknięć myszą, jeśli jest tworzona przy użyciu stylu wywołania SS_NOTIFY.

Utwórz formant statyczny w dwóch krokach. Po pierwsze wywołanie konstruktora do konstruowania `CStatic` obiektu, a następnie wywołaj [Utwórz](#create) funkcja elementu członkowskiego, aby utworzyć statyczny formantu i dołączyć go do `CStatic` obiektu.

Jeśli tworzysz `CStatic` obiektu w oknie dialogowym (za pośrednictwem zasobu okna dialogowego), `CStatic` obiektu automatycznie jest niszczony, kiedy użytkownik zamknie okno dialogowe.

Jeśli tworzysz `CStatic` obiekt w tym oknie, konieczne może zniszczyć ją. A `CStatic` automatycznie niszczony jest obiekt utworzony w stosie, w tym oknie. Jeśli tworzysz `CStatic` obiektów na stosie przy użyciu **nowe** funkcji, należy wywołać **Usuń** obiektu zniszczyć ją, gdy są z nią zrobić.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="create"></a>  CStatic::Create

Tworzy formant statyczny Windows i dołącza je do `CStatic` obiektu.

```
virtual BOOL Create(
    LPCTSTR lpszText,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID = 0xffff);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Określa tekst, który można umieścić w formancie. Jeśli ma wartość NULL, tekst nie będą widoczne.

*dwStyle*<br/>
Określa styl okna kontrolki statycznej. Zastosuj dowolną kombinację [style kontrolki statycznej](../../mfc/reference/styles-used-by-mfc.md#static-styles) do formantu.

*Rect*<br/>
Określa położenie i rozmiar kontrolki statycznej. Może być albo `RECT` struktury lub `CRect` obiektu.

*pParentWnd*<br/>
Określa `CStatic` okno nadrzędne, zwykle `CDialog` obiektu. Nie może być równa NULL.

*nID*<br/>
Określa identyfikator kontrolki statycznej kontrolki.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruowania `CStatic` obiektu w dwóch krokach. Najpierw wywołaj Konstruktor `CStatic`, a następnie wywołaj `Create`, która tworzy formant statyczny Windows i dołącza go do `CStatic` obiektu.

Zastosuj następujące [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles) do kontrolki statycznej:

- WS_CHILD zawsze

- WS_VISIBLE zwykle

- WS_DISABLED rzadko

Jeśli wiesz, że do wyświetlania mapy bitowej, kursorem, ikonę lub metaplik w statyczną kontrolkę, należy zastosować jedną z następujących [style statyczne](../../mfc/reference/styles-used-by-mfc.md#static-styles):

- SS_BITMAP na użytek ten styl map bitowych.

- SS_ICON na użytek ten styl ikon i kursorów.

- SS_ENHMETAFILE na użytek ten styl rozszerzonych metaplików.

Kursory, mapy bitowe lub ikony można także użyć następujących stylu:

- Użycie SS_CENTERIMAGE Aby wyśrodkować obraz w kontrolce statyczne.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]

##  <a name="cstatic"></a>  CStatic::CStatic

Konstruuje `CStatic` obiektu.

```
CStatic();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]

##  <a name="drawitem"></a>  CStatic::DrawItem

Metoda wywoływana przez platformę, by narysować statyczną kontrolkę rysowanych przez właściciela.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Wskaźnik do [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) struktury. Struktura zawiera informacje dotyczące elementu do rysowania i typ rysunku, wymagane.

### <a name="remarks"></a>Uwagi

Przesłonić tę funkcję, aby zaimplementować rysunku rysowanych przez właściciela `CStatic` obiektu (kontrolka ma styl SS_OWNERDRAW).

##  <a name="getbitmap"></a>  CStatic::GetBitmap

Pobiera uchwyt mapy bitowej ustawione wcześniej przy użyciu [SetBitmap](#setbitmap), która jest skojarzony z `CStatic`.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do mapy bitowej w bieżącej lub wartość NULL, jeśli nie bitmapy została ustawiona.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="getcursor"></a>  CStatic::GetCursor

Pobiera uchwyt kursora ustawione wcześniej przy użyciu [SetCursor](#setcursor), która jest skojarzony z `CStatic`.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do bieżący kursor lub wartość NULL, jeśli został ustawiony żaden kursor.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="getenhmetafile"></a>  CStatic::GetEnhMetaFile

Pobiera uchwyt rozszerzony metaplik, ustawione wcześniej przy użyciu [SetEnhMetafile](#setenhmetafile), która jest skojarzony z `CStatic`.

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do bieżącego rozszerzony metaplik lub wartość NULL, jeśli został ustawiony nie rozszerzony metaplik.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="geticon"></a>  CStatic::GetIcon

Pobiera uchwyt ikony ustawione wcześniej przy użyciu [SetIcon](#seticon), która jest skojarzony z `CStatic`.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do bieżącego ikony, lub wartość NULL, jeśli ustawiono żadnej ikony.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

##  <a name="setbitmap"></a>  CStatic::SetBitmap

Kojarzy nowej mapy bitowej przy użyciu kontrolki statycznej.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
Dojście do mapy bitowej do rysowania w kontrolki statycznej.

### <a name="return-value"></a>Wartość zwracana

Uchwyt mapy bitowej, który był wcześniej skojarzony z statyczną kontrolkę, lub wartość NULL, jeśli nie bitmapy został skojarzony z kontrolki statycznej.

### <a name="remarks"></a>Uwagi

Mapa bitowa zostanie automatycznie narysowana kontrolki statycznej. Domyślnie będą rysowane w lewym górnym rogu, a rozmiar mapy bitowej będzie można zmienić jego rozmiaru kontrolki statycznej.

Można użyć różnych okna i statyczną kontrolkę stylów, w tym następujące:

- SS_BITMAP zawsze używały tego stylu dla map bitowych.

- Użycie SS_CENTERIMAGE Aby wyśrodkować obraz w kontrolce statyczne. Obraz, który jest większy niż kontrolki statycznej, zostaną przycięte. Jeśli jest mniejszy niż kontrolki statycznej, pustego miejsca wokół obrazu zostanie wypełnione przez kolor piksela w lewym górnym rogu mapy bitowej.

- Biblioteka MFC zawiera klasę `CBitmap`, którego można użyć, jeśli masz więcej przy użyciu obrazu mapy bitowej niż po prostu Wywołaj Win32 funkcji `LoadBitmap`. `CBitmap`, który zawiera jeden rodzaj obiektu interfejsu GDI, jest często używana we współpracy z `CStatic`, czyli `CWnd` klasę, która jest używana do wyświetlania obiektu graficznego jako formant statyczny.

`CImage` jest klasą ATL/MFC, która pozwala łatwo pracować z map bitowych niezależnych urządzenia (DIB). Aby uzyskać więcej informacji, zobacz [CImage, klasa](../../atl-mfc-shared/reference/cimage-class.md).

- Typowy jest zapewnienie `CStatic::SetBitmap` obiektu interfejsu GDI, który jest zwracany przez HBITMAP operator `CBitmap` lub `CImage` obiektu. Kod, aby to zrobić przypomina następujący wiersz.

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```
Poniższy przykład tworzy dwie `CStatic` obiekty na stosie. Następnie ładuje go za pomocą mapy bitowej systemu `CBitmap::LoadOEMBitmap` , a druga z pliku za pomocą `CImage::Load`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="setcursor"></a>  CStatic::SetCursor

Kojarzy nowy obraz kursora z kontrolki statycznej.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Parametry

*hCursor*<br/>
Uchwyt kursora do rysowania w kontrolki statycznej.

### <a name="return-value"></a>Wartość zwracana

Uchwyt kursora była poprzednio skojarzona z statyczną kontrolkę, lub wartość NULL, jeśli kursor nie został skojarzony z kontrolki statycznej.

### <a name="remarks"></a>Uwagi

Kursor zostanie automatycznie narysowana kontrolki statycznej. Domyślnie będą rysowane w lewym górnym rogu, a kontrolki statycznej rozmiar zostanie zmieniony na rozmiar kursora.

Można użyć różnych okna i statyczną kontrolkę style, m.in:

- SS_ICON na użytek ten styl zawsze ikon i kursorów.

- Użycie SS_CENTERIMAGE Aby wyśrodkować w kontrolki statycznej. Obraz, który jest większy niż kontrolki statycznej, zostaną przycięte. Jeśli jest mniejszy niż kontrolki statycznej, pustego miejsca wokół obrazu zostanie wypełnione kolorem tła kontrolki statycznej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="setenhmetafile"></a>  CStatic::SetEnhMetaFile

Kojarzy nowy obraz rozszerzony metaplik z kontrolki statycznej.

```
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```

### <a name="parameters"></a>Parametry

*hMetaFile*<br/>
Dojście rozszerzony metaplik do rysowania w kontrolki statycznej.

### <a name="return-value"></a>Wartość zwracana

Uchwyt rozszerzony metaplik była poprzednio skojarzona z statyczną kontrolkę, lub wartość NULL, jeśli nie rozszerzony metaplik został skojarzony z kontrolki statycznej.

### <a name="remarks"></a>Uwagi

Rozszerzony metaplik zostanie automatycznie narysowana kontrolki statycznej. Rozszerzony metaplik jest skalowana w celu dopasowania do rozmiaru kontrolki statycznej.

Można użyć różnych okna i statyczną kontrolkę style, m.in:

- Użyj SS_ENHMETAFILE zawsze ten styl dla rozszerzonych metaplików.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="seticon"></a>  CStatic::SetIcon

Kojarzy nowy obraz ikony z kontrolki statycznej.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Parametry

*hIcon*<br/>
Uchwyt ikony do rysowania w kontrolki statycznej.

### <a name="return-value"></a>Wartość zwracana

Uchwyt ikony była poprzednio skojarzona z statyczną kontrolkę, lub wartość NULL, jeśli ikony nie został skojarzony z kontrolki statycznej.

### <a name="remarks"></a>Uwagi

Ikona zostanie automatycznie narysowana kontrolki statycznej. Domyślnie będą rysowane w lewym górnym rogu, a kontrolki statycznej rozmiar zostanie zmieniony na rozmiar ikony.

Można użyć różnych okna i statyczną kontrolkę style, m.in:

- SS_ICON na użytek ten styl zawsze ikon i kursorów.

- Użycie SS_CENTERIMAGE Aby wyśrodkować w kontrolki statycznej. Obraz, który jest większy niż kontrolki statycznej, zostaną przycięte. Jeśli jest mniejszy niż kontrolki statycznej, pustego miejsca wokół obrazu zostanie wypełnione kolorem tła kontrolki statycznej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CButton](../../mfc/reference/cbutton-class.md)<br/>
[Klasa CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[Klasa CEdit](../../mfc/reference/cedit-class.md)<br/>
[Klasa CListBox](../../mfc/reference/clistbox-class.md)<br/>
[Klasa CScrollBar](../../mfc/reference/cscrollbar-class.md)<br/>
[Klasa CDialog](../../mfc/reference/cdialog-class.md)
