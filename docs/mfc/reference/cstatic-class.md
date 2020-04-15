---
title: Klasa CStatic
ms.date: 11/04/2016
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
ms.openlocfilehash: e5c3705c0aa2fd90e73cb54ba5a97c252ed2cf83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371642"
---
# <a name="cstatic-class"></a>Klasa CStatic

Zapewnia funkcjonalność formantu statycznego systemu Windows.

## <a name="syntax"></a>Składnia

```
class CStatic : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStatic::CStatic](#cstatic)|Konstruuje `CStatic` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStatic::Tworzenie](#create)|Tworzy formant statyczny systemu Windows `CStatic` i dołącza go do obiektu.|
|[CStatic::DrawItem](#drawitem)|Zastąd, aby narysować formant statyczny narysowany przez właściciela.|
|[CStatic::GetBitmap](#getbitmap)|Pobiera uchwyt mapy bitowej ustawionej wcześniej za pomocą [SetBitmap](#setbitmap).|
|[CStatic::GetCursor](#getcursor)|Pobiera uchwyt obrazu kursora wcześniej ustawionego za pomocą [setcursor](#setcursor).|
|[CStatic::GetEnhMetaFile](#getenhmetafile)|Pobiera uchwyt ulepszonego metapliku wcześniej ustawionego za pomocą [Pliku SetEnhMetaFile](#setenhmetafile).|
|[CStatic::Geticon](#geticon)|Pobiera uchwyt ikony ustawionej wcześniej za pomocą [SetIcon](#seticon).|
|[CStatic::SetBitmap](#setbitmap)|Określa mapę bitową, która ma być wyświetlana w formancie statycznym.|
|[CStatic::SetCursor](#setcursor)|Określa obraz kursora, który ma być wyświetlany w formancie statycznym.|
|[CStatic::SetEnhMetaFile](#setenhmetafile)|Określa ulepszony metaplik, który ma być wyświetlany w formancie statycznym.|
|[CStatic::SetIcon](#seticon)|Określa ikonę, która ma być wyświetlana w formancie statycznym.|

## <a name="remarks"></a>Uwagi

Formant statyczny wyświetla ciąg tekstowy, pole, prostokąt, ikonę, kursor, bitmapę lub ulepszony metaplik. Może być używany do etykietowania, skrzynki lub oddzielania innych formantów. Sterowanie statyczne zwykle nie pobiera danych wejściowych i nie zapewnia wyjścia; jednak może powiadomić rodzica o kliknięciach myszy, jeśli jest tworzony przy SS_NOTIFY stylu.

Utwórz formant statyczny w dwóch krokach. Najpierw wywołać konstruktora `CStatic` do konstruowania obiektu, a następnie [wywołać Create](#create) `CStatic` funkcji elementu członkowskiego, aby utworzyć formant statyczny i dołączyć go do obiektu.

Jeśli obiekt `CStatic` zostanie utworzony w oknie dialogowym (za pośrednictwem zasobu okna dialogowego), `CStatic` obiekt zostanie automatycznie zniszczony po zamknięciu okna dialogowego przez użytkownika.

Jeśli utworzysz `CStatic` obiekt w oknie, może być również konieczne jego zniszczenie. Obiekt `CStatic` utworzony na stosie w oknie jest automatycznie niszczony. Jeśli `CStatic` tworzysz obiekt na stosie przy użyciu **nowej** funkcji, należy **wywołać delete** na obiekcie, aby go zniszczyć, gdy skończysz z nim.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cstaticcreate"></a><a name="create"></a>CStatic::Tworzenie

Tworzy formant statyczny systemu Windows `CStatic` i dołącza go do obiektu.

```
virtual BOOL Create(
    LPCTSTR lpszText,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID = 0xffff);
```

### <a name="parameters"></a>Parametry

*lpszText (tekst)*<br/>
Określa tekst, który ma być umieszczany w formancie. Jeśli null, żaden tekst nie będzie widoczny.

*Dwstyle*<br/>
Określa styl okna formantu statycznego. Zastosuj dowolną kombinację [stylów sterowania statycznego](../../mfc/reference/styles-used-by-mfc.md#static-styles) do formantu.

*Rect*<br/>
Określa położenie i rozmiar formantu statycznego. Może to być `RECT` struktura lub `CRect` obiekt.

*pParentWnd*<br/>
Określa okno `CStatic` nadrzędne, `CDialog` zwykle obiekt. Nie może być null.

*Nid*<br/>
Określa identyfikator formantu statycznego.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruuj `CStatic` obiekt w dwóch krokach. Najpierw wywołaj konstruktora `CStatic` `Create`, a następnie wywołaj , który tworzy `CStatic` formant statyczny systemu Windows i dołącza go do obiektu.

Zastosuj następujące [style okien](../../mfc/reference/styles-used-by-mfc.md#window-styles) do formantu statycznego:

- WS_CHILD zawsze

- WS_VISIBLE zwykle

- WS_DISABLED rzadko

Jeśli zamierzasz wyświetlić w formancie statycznym mapę bitową, kursor, ikonę lub metaplik, musisz zastosować jeden z następujących [stylów statycznych:](../../mfc/reference/styles-used-by-mfc.md#static-styles)

- SS_BITMAP Użyj tego stylu dla map bitowych.

- SS_ICON Użyj tego stylu dla kursorów i ikon.

- SS_ENHMETAFILE Użyj tego stylu, aby uzyskać ulepszone metapliki.

W przypadku kursorów, map bitowych lub ikon można również użyć następującego stylu:

- SS_CENTERIMAGE Służy do wyśrodkowywać obraz w formancie statycznym.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]

## <a name="cstaticcstatic"></a><a name="cstatic"></a>CStatic::CStatic

Konstruuje `CStatic` obiekt.

```
CStatic();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]

## <a name="cstaticdrawitem"></a><a name="drawitem"></a>CStatic::DrawItem

Wywoływana przez strukturę do rysowania formantu statycznego rysowanego przez właściciela.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Wskaźnik do struktury [DRAWITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-drawitemstruct) Struktura zawiera informacje o elemencie, który ma zostać narysowany i o typie wymaganego rysunku.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby zaimplementować rysunek dla obiektu rysowanego przez `CStatic` właściciela (formant ma styl SS_OWNERDRAW).

## <a name="cstaticgetbitmap"></a><a name="getbitmap"></a>CStatic::GetBitmap

Pobiera uchwyt mapy bitowej, wcześniej ustawiony z [SetBitmap](#setbitmap), `CStatic`który jest skojarzony z .

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do bieżącej mapy bitowej lub NULL, jeśli nie ustawiono mapy bitowej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

## <a name="cstaticgetcursor"></a><a name="getcursor"></a>CStatic::GetCursor

Pobiera uchwyt kursora, wcześniej ustawiony z [SetCursor](#setcursor), który `CStatic`jest skojarzony z .

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do bieżącego kursora lub NULL, jeśli nie ustawiono żadnego kursora.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

## <a name="cstaticgetenhmetafile"></a><a name="getenhmetafile"></a>CStatic::GetEnhMetaFile

Pobiera uchwyt rozszerzonego metapliku, wcześniej ustawionego za pomocą [SetEnhMetafile](#setenhmetafile), który jest skojarzony z `CStatic`.

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do bieżącego rozszerzonego metapliku lub NULL, jeśli nie ustawiono rozszerzonego metapliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

## <a name="cstaticgeticon"></a><a name="geticon"></a>CStatic::Geticon

Pobiera uchwyt ikony, wcześniej ustawiona z [SetIcon](#seticon), `CStatic`który jest skojarzony z .

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do bieżącej ikony lub NULL, jeśli nie ustawiono żadnej ikony.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="cstaticsetbitmap"></a><a name="setbitmap"></a>CStatic::SetBitmap

Kojarzy nową mapę bitową z formantem statycznym.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parametry

*hBitmapa*<br/>
Uchwyt mapy bitowej, która ma zostać narysowana w formancie statycznym.

### <a name="return-value"></a>Wartość zwracana

Dojście mapy bitowej, która była wcześniej skojarzona z formantem statycznym, lub NULL, jeśli z formantu statycznego nie została skojarzona żadna mapa bitowa.

### <a name="remarks"></a>Uwagi

Mapa bitowa zostanie automatycznie narysowana w formancie statycznym. Domyślnie zostanie narysowany w lewym górnym rogu, a formant statyczny zostanie przesunięty na rozmiar mapy bitowej.

Można użyć różnych stylów sterowania okien i statycznych, w tym:

- SS_BITMAP Użyj tego stylu zawsze dla map bitowych.

- SS_CENTERIMAGE Służy do wyśrodkowywać obraz w formancie statycznym. Jeśli obraz jest większy niż formant statyczny, zostanie przycięty. Jeśli jest mniejszy niż formant statyczny, puste miejsce wokół obrazu zostanie wypełnione kolorem piksela w lewym górnym rogu mapy bitowej.

- MFC zapewnia `CBitmap`klasę , której można użyć, gdy trzeba zrobić więcej z obrazem `LoadBitmap`mapy bitowej niż tylko wywołać funkcję Win32 . `CBitmap`, który zawiera jeden rodzaj obiektu GDI, `CStatic`jest często `CWnd` używany we współpracy z , który jest klasą, która jest używana do wyświetlania obiektu graficznego jako formantu statycznego.

`CImage`to klasa ATL/MFC, która umożliwia łatwiejszą pracę z niezależnymi mapami bitowymi (DIB) niezależnie od urządzenia. Aby uzyskać więcej informacji, zobacz [CImage Class](../../atl-mfc-shared/reference/cimage-class.md).

- Typowym zastosowaniem `CStatic::SetBitmap` jest nadanie obiektu GDI, który jest `CBitmap` `CImage` zwracany przez operatora HBITMAP lub obiektu. Kod w tym celu przypomina następujący wiersz.

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```

Poniższy przykład `CStatic` tworzy dwa obiekty na stosie. Następnie ładuje jeden z systemową `CBitmap::LoadOEMBitmap` mapą bitową, `CImage::Load`a drugą z pliku za pomocą pliku .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

## <a name="cstaticsetcursor"></a><a name="setcursor"></a>CStatic::SetCursor

Kojarzy nowy obraz kursora z formantem statycznym.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Parametry

*hCursor (własno)-do*<br/>
Uchwyt kursora, który ma zostać narysowany w formancie statycznym.

### <a name="return-value"></a>Wartość zwracana

Dojście kursora wcześniej skojarzone z formantu statycznego lub NULL, jeśli żaden kursor nie został skojarzony z formantu statycznego.

### <a name="remarks"></a>Uwagi

Kursor zostanie automatycznie narysowany w formancie statycznym. Domyślnie zostanie on narysowany w lewym górnym rogu, a formant statyczny zostanie przesunięty na rozmiar kursora.

Można używać różnych stylów sterowania okien i statycznych, w tym następujących:

- SS_ICON Użyj tego stylu zawsze dla kursorów i ikon.

- SS_CENTERIMAGE Użyj do wyśrodkować w formancie statycznym. Jeśli obraz jest większy niż formant statyczny, zostanie przycięty. Jeśli jest mniejszy niż formant statyczny, puste miejsce wokół obrazu zostanie wypełnione kolorem tła formantu statycznego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

## <a name="cstaticsetenhmetafile"></a><a name="setenhmetafile"></a>CStatic::SetEnhMetaFile

Kojarzy nowy ulepszony obraz metapliku z formantem statycznym.

```
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```

### <a name="parameters"></a>Parametry

*hMetaFile*<br/>
Uchwyt ulepszonego metapliku, który ma być narysowany w formancie statycznym.

### <a name="return-value"></a>Wartość zwracana

Uchwyt ulepszonego metapliku wcześniej skojarzonego z kontrolą statyczną lub NULL, jeśli z kontrolą statyczną nie skojarzono się z ulepszonym metaplikem.

### <a name="remarks"></a>Uwagi

Ulepszony metaplik zostanie automatycznie narysowany w formancie statycznym. Ulepszony metaplik jest skalowany w celu dopasowania do rozmiaru sterowania statycznego.

Można używać różnych stylów sterowania okien i statycznych, w tym następujących:

- SS_ENHMETAFILE Użyj tego stylu zawsze do ulepszonych metaplików.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

## <a name="cstaticseticon"></a><a name="seticon"></a>CStatic::SetIcon

Kojarzy nowy obraz ikony z formantem statycznym.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Parametry

*hIcon (własówce)*<br/>
Uchwyt ikony, która ma zostać narysowana w formancie statycznym.

### <a name="return-value"></a>Wartość zwracana

Uchwyt ikony wcześniej skojarzony z formantem statycznym lub NULL, jeśli żadna ikona nie została skojarzona z formantem statycznym.

### <a name="remarks"></a>Uwagi

Ikona zostanie automatycznie narysowana w formancie statycznym. Domyślnie zostanie on narysowany w lewym górnym rogu, a formant statyczny zostanie przesunięty na rozmiar ikony.

Można używać różnych stylów sterowania okien i statycznych, w tym następujących:

- SS_ICON Użyj tego stylu zawsze dla kursorów i ikon.

- SS_CENTERIMAGE Użyj do wyśrodkować w formancie statycznym. Jeśli obraz jest większy niż formant statyczny, zostanie przycięty. Jeśli jest mniejszy niż formant statyczny, puste miejsce wokół obrazu zostanie wypełnione kolorem tła formantu statycznego.

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
