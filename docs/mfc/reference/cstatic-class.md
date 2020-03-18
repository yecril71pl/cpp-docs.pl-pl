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
ms.openlocfilehash: fc0164b2d0046ca2d36291696dd6137a9fcef069
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447428"
---
# <a name="cstatic-class"></a>Klasa CStatic

Oferuje funkcje kontrolki statycznej systemu Windows.

## <a name="syntax"></a>Składnia

```
class CStatic : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CStatic::CStatic](#cstatic)|Konstruuje obiekt `CStatic`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CStatic:: Create](#create)|Tworzy formant statyczny systemu Windows i dołącza go do obiektu `CStatic`.|
|[CStatic::D rawItem](#drawitem)|Przesłoń, aby narysować formant statyczny rysowany przez właściciela.|
|[CStatic:: getmap](#getbitmap)|Pobiera uchwyt mapy bitowej poprzednio ustawiony za pomocą [Setmap bitowych](#setbitmap).|
|[CStatic:: GetCursor](#getcursor)|Pobiera uchwyt obrazu kursora wcześniej ustawionego za pomocą elementu [SetCursor](#setcursor).|
|[CStatic::GetEnhMetaFile](#getenhmetafile)|Pobiera uchwyt rozszerzonego metapliku ustawionego wcześniej za pomocą [SetEnhMetaFile](#setenhmetafile).|
|[CStatic:: GetIcon](#geticon)|Pobiera uchwyt ikony wcześniej ustawionej za pomocą [SetIcon](#seticon).|
|[CStatic:: setmap](#setbitmap)|Określa mapę bitową, która ma być wyświetlana w formancie statycznym.|
|[CStatic:: SetCursor](#setcursor)|Określa obraz kursora, który ma być wyświetlany w kontrolce statycznej.|
|[CStatic::SetEnhMetaFile](#setenhmetafile)|Określa rozszerzony metaplik, który ma być wyświetlany w kontrolce statycznej.|
|[CStatic:: SetIcon](#seticon)|Określa ikonę, która ma być wyświetlana w formancie statycznym.|

## <a name="remarks"></a>Uwagi

Kontrolka statyczna wyświetla ciąg tekstowy, pole, prostokąt, ikonę, kursor, mapę bitową lub ulepszony metaplik. Może służyć do etykietowania, pola lub oddzielania innych kontrolek. Statyczna kontrolka zwykle nie przyjmuje danych wejściowych i nie udostępnia danych wyjściowych. może jednak powiadomić swój element nadrzędny kliknięcia myszą, jeśli zostanie on utworzony z stylem SS_NOTIFY.

Utwórz kontrolkę statyczną w dwóch krokach. Najpierw Wywołaj konstruktora w celu skonstruowania obiektu `CStatic`, a następnie wywołaj funkcję [Create](#create) member, aby utworzyć statyczny formant i dołączyć go do obiektu `CStatic`.

Jeśli utworzysz obiekt `CStatic` w oknie dialogowym (za pomocą zasobu okna dialogowego), obiekt `CStatic` zostanie automatycznie zniszczony, gdy użytkownik zamknie okno dialogowe.

Jeśli utworzysz obiekt `CStatic` w oknie, może być również konieczne jego zniszczenie. Obiekt `CStatic` utworzony na stosie w oknie jest automatycznie niszczony. Jeśli utworzysz obiekt `CStatic` na stercie przy użyciu **nowej** funkcji, musisz wywołać metodę **delete** dla obiektu, aby zniszczyć go po zakończeniu pracy z nim.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="create"></a>CStatic:: Create

Tworzy formant statyczny systemu Windows i dołącza go do obiektu `CStatic`.

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
Określa tekst, który ma zostać umieszczony w kontrolce. Jeśli wartość jest równa NULL, tekst nie będzie widoczny.

*dwStyle*<br/>
Określa styl okna kontrolki statycznej. Zastosuj dowolną kombinację [statycznych stylów kontroli](../../mfc/reference/styles-used-by-mfc.md#static-styles) do kontrolki.

*cinania*<br/>
Określa położenie i rozmiar kontrolki statycznej. Może to być struktura `RECT` lub `CRect` obiektu.

*pParentWnd*<br/>
Określa `CStatic` okno nadrzędne, zazwyczaj jest obiektem `CDialog`. Nie może mieć wartości NULL.

*nID*<br/>
Określa identyfikator kontrolki statycznej kontrolki.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Utwórz obiekt `CStatic` w dwóch krokach. Najpierw Wywołaj konstruktora `CStatic`, a następnie Wywołaj `Create`, który tworzy formant statyczny systemu Windows i dołącza go do obiektu `CStatic`.

Zastosuj następujące [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) do kontrolki statycznej:

- WS_CHILD zawsze

- WS_VISIBLE zwykle

- WS_DISABLED rzadko

Jeśli w kontrolce statycznej ma być wyświetlana mapa bitowa, kursor, ikona lub metaplik, należy zastosować jeden z następujących [stylów statycznych](../../mfc/reference/styles-used-by-mfc.md#static-styles):

- SS_BITMAP Użyj tego stylu dla map bitowych.

- SS_ICON użyć tego stylu dla kursorów i ikon.

- SS_ENHMETAFILE użyć tego stylu dla ulepszonych plików.

W przypadku kursorów, map bitowych lub ikon warto również użyć następującego stylu:

- SS_CENTERIMAGE użyć do wyśrodkowania obrazu w kontrolce statycznej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]

##  <a name="cstatic"></a>CStatic::CStatic

Konstruuje obiekt `CStatic`.

```
CStatic();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]

##  <a name="drawitem"></a>CStatic::D rawItem

Wywoływane przez platformę, by narysować formant statyczny rysowany przez właściciela.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Wskaźnik do struktury [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) . Struktura zawiera informacje na temat elementu, który ma być rysowany, i wymagany typ rysunku.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby zaimplementować rysowanie dla obiektu `CStatic` rysowanego przez właściciela (kontrolka ma styl SS_OWNERDRAW).

##  <a name="getbitmap"></a>CStatic:: getmap

Pobiera uchwyt mapy bitowej, wcześniej ustawiony za pomocą [Setmap bitowych](#setbitmap), która jest skojarzona z `CStatic`.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do bieżącej mapy bitowej lub wartość NULL, jeśli nie została ustawiona żadna mapa bitowa.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="getcursor"></a>CStatic:: GetCursor

Pobiera uchwyt kursora wcześniej ustawiony za pomocą elementu [SetCursor](#setcursor), który jest skojarzony z `CStatic`.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do bieżącego kursora lub wartość NULL, jeśli nie ustawiono kursora.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="getenhmetafile"></a>CStatic::GetEnhMetaFile

Pobiera uchwyt rozszerzonego metapliku, wcześniej ustawiony za pomocą [SetEnhMetafile](#setenhmetafile), który jest skojarzony z `CStatic`.

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do bieżącego rozszerzonego metapliku lub wartość NULL, jeśli nie ustawiono rozszerzonego metapliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="geticon"></a>CStatic:: GetIcon

Pobiera uchwyt ikony wcześniej ustawionej za pomocą [SetIcon](#seticon), która jest skojarzona z `CStatic`.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do bieżącej ikony lub wartość NULL, jeśli nie ustawiono żadnej ikony.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

##  <a name="setbitmap"></a>CStatic:: setmap

Kojarzy nową mapę bitową z kontrolką statyczną.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
Uchwyt mapy bitowej, który ma być rysowany w kontrolce statycznej.

### <a name="return-value"></a>Wartość zwracana

Uchwyt mapy bitowej, która była poprzednio skojarzona z kontrolką statyczną lub wartość NULL, jeśli żadna mapa bitowa nie została skojarzona z kontrolką statyczną.

### <a name="remarks"></a>Uwagi

Mapa bitowa zostanie automatycznie narysowana w kontrolce statycznej. Domyślnie zostanie narysowana w lewym górnym rogu, a rozmiar kontrolki statycznej zostanie zmieniony na rozmiar mapy bitowej.

Można użyć różnych stylów okna i statycznych kontrolek, w tym:

- SS_BITMAP używać tego stylu zawsze dla map bitowych.

- SS_CENTERIMAGE użyć do wyśrodkowania obrazu w kontrolce statycznej. Jeśli obraz jest większy niż kontrolka statyczna, zostanie przycięty. Jeśli jest mniejsza niż kontrolka statyczna, puste miejsce wokół obrazu zostanie wypełnione kolorem piksela w lewym górnym rogu mapy bitowej.

- MFC udostępnia klasę `CBitmap`, której można użyć, gdy trzeba wykonać więcej za pomocą obrazu mapy bitowej niż tylko wywołać funkcję Win32 `LoadBitmap`. `CBitmap`, który zawiera jeden rodzaj obiektu GDI, jest często używany w współpracy z `CStatic`, która jest klasą `CWnd`, która jest używana do wyświetlania obiektu graficznego jako kontrolki statycznej.

`CImage` jest klasą ATL/MFC, która umożliwia łatwiejsze współdziałanie z niezależnymi mapami bitowymi urządzeń (DIB). Aby uzyskać więcej informacji, zobacz [Klasa funkcji CImage](../../atl-mfc-shared/reference/cimage-class.md).

- Typowym zastosowaniem jest nadanie `CStatic::SetBitmap` obiektu GDI zwracanego przez operator HBITMAP obiektu `CBitmap` lub `CImage`. Kod, aby to zrobić, jest podobny do następującego wiersza.

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```

Poniższy przykład tworzy dwa `CStatic` obiekty na stercie. Następnie ładuje je za pomocą mapy bitowej systemu przy użyciu `CBitmap::LoadOEMBitmap`, a drugi z pliku przy użyciu `CImage::Load`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="setcursor"></a>CStatic:: SetCursor

Kojarzy nowy obraz kursora z kontrolką statyczną.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Parametry

*hCursor*<br/>
Uchwyt kursora do rysowania w kontrolce statycznej.

### <a name="return-value"></a>Wartość zwracana

Uchwyt kursora wcześniej skojarzony z kontrolką statyczną lub wartość NULL, jeśli żaden kursor nie został skojarzony z kontrolką statyczną.

### <a name="remarks"></a>Uwagi

Kursor zostanie automatycznie narysowany w kontrolce statycznej. Domyślnie zostanie narysowana w lewym górnym rogu, a rozmiar kontrolki statycznej zmieni się na rozmiar kursora.

Można użyć różnych stylów okna i statycznych kontrolek, w tym następujących:

- SS_ICON używać tego stylu zawsze dla kursorów i ikon.

- SS_CENTERIMAGE użyć do wyśrodkowania w kontrolce statycznej. Jeśli obraz jest większy niż kontrolka statyczna, zostanie przycięty. Jeśli jest mniejsza niż kontrolka statyczna, puste miejsce wokół obrazu zostanie wypełnione kolorem tła kontrolki statycznej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="setenhmetafile"></a>CStatic::SetEnhMetaFile

Kojarzy nowy obraz rozszerzonego metapliku z kontrolką statyczną.

```
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```

### <a name="parameters"></a>Parametry

*hMetaFile*<br/>
Uchwyt rozszerzonego metapliku do rysowania w kontrolce statycznej.

### <a name="return-value"></a>Wartość zwracana

Dojście rozszerzonego metapliku poprzednio skojarzone z kontrolką statyczną lub wartość NULL, jeśli nie został skojarzony żaden rozszerzony metaplik z kontrolką statyczną.

### <a name="remarks"></a>Uwagi

Rozszerzony metaplik zostanie automatycznie narysowany w kontrolce statycznej. Ulepszony metaplik jest skalowany w celu dopasowania do rozmiaru kontrolki statycznej.

Można użyć różnych stylów okna i statycznych kontrolek, w tym następujących:

- SS_ENHMETAFILE używać tego stylu zawsze dla ulepszonych plików.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="seticon"></a>CStatic:: SetIcon

Kojarzy nowy obraz ikony z kontrolką statyczną.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Parametry

*hIcon*<br/>
Uchwyt ikony, która ma zostać narysowana w kontrolce statycznej.

### <a name="return-value"></a>Wartość zwracana

Uchwyt ikony wcześniej skojarzonej z kontrolką statyczną lub wartość NULL, jeśli żadna ikona nie została skojarzona z kontrolką statyczną.

### <a name="remarks"></a>Uwagi

Ikona zostanie automatycznie narysowana w kontrolce statycznej. Domyślnie zostanie narysowana w lewym górnym rogu, a rozmiar kontrolki statycznej zostanie zmieniony na rozmiar ikony.

Można użyć różnych stylów okna i statycznych kontrolek, w tym następujących:

- SS_ICON używać tego stylu zawsze dla kursorów i ikon.

- SS_CENTERIMAGE użyć do wyśrodkowania w kontrolce statycznej. Jeśli obraz jest większy niż kontrolka statyczna, zostanie przycięty. Jeśli jest mniejsza niż kontrolka statyczna, puste miejsce wokół obrazu zostanie wypełnione kolorem tła kontrolki statycznej.

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
