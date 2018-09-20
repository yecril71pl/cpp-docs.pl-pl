---
title: Klasa CBitmap | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBitmap
- AFXWIN/CBitmap
- AFXWIN/CBitmap::CBitmap
- AFXWIN/CBitmap::CreateBitmap
- AFXWIN/CBitmap::CreateBitmapIndirect
- AFXWIN/CBitmap::CreateCompatibleBitmap
- AFXWIN/CBitmap::CreateDiscardableBitmap
- AFXWIN/CBitmap::FromHandle
- AFXWIN/CBitmap::GetBitmap
- AFXWIN/CBitmap::GetBitmapBits
- AFXWIN/CBitmap::GetBitmapDimension
- AFXWIN/CBitmap::LoadBitmap
- AFXWIN/CBitmap::LoadMappedBitmap
- AFXWIN/CBitmap::LoadOEMBitmap
- AFXWIN/CBitmap::SetBitmapBits
- AFXWIN/CBitmap::SetBitmapDimension
dev_langs:
- C++
helpviewer_keywords:
- CBitmap [MFC], CBitmap
- CBitmap [MFC], CreateBitmap
- CBitmap [MFC], CreateBitmapIndirect
- CBitmap [MFC], CreateCompatibleBitmap
- CBitmap [MFC], CreateDiscardableBitmap
- CBitmap [MFC], FromHandle
- CBitmap [MFC], GetBitmap
- CBitmap [MFC], GetBitmapBits
- CBitmap [MFC], GetBitmapDimension
- CBitmap [MFC], LoadBitmap
- CBitmap [MFC], LoadMappedBitmap
- CBitmap [MFC], LoadOEMBitmap
- CBitmap [MFC], SetBitmapBits
- CBitmap [MFC], SetBitmapDimension
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 322b13ee62e61a836d6b0c66ab619a11348adeae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375644"
---
# <a name="cbitmap-class"></a>Klasa CBitmap

Hermetyzuje mapę bitową Windows graphics urządzenia interface (GDI) i dostarcza funkcji elementów członkowskich do manipulowania mapy bitowej.

## <a name="syntax"></a>Składnia

```
class CBitmap : public CGdiObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBitmap::CBitmap](#cbitmap)|Konstruuje `CBitmap` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBitmap::CreateBitmap](#createbitmap)|Inicjuje obiekt z mapą bitową pamięci zależne od urządzenia, która ma określoną szerokość, wysokość i wzorca bitowego.|
|[CBitmap::CreateBitmapIndirect](#createbitmapindirect)|Inicjuje obiekt z mapy bitowej przy użyciu szerokości, wysokości i wzorca bitowego (jeśli jest określony) podany w `BITMAP` struktury.|
|[CBitmap::CreateCompatibleBitmap](#createcompatiblebitmap)|Inicjuje obiekt z mapy bitowej, tak aby była ona zgodna z określonym urządzeniem.|
|[CBitmap::CreateDiscardableBitmap](#creatediscardablebitmap)|Inicjuje obiekt discardable mapą bitową, która jest zgodna z określonym urządzeniem.|
|[CBitmap::FromHandle](#fromhandle)|Zwraca wskaźnik do `CBitmap` obiektu, kiedy podane dojście do Windows `HBITMAP` mapy bitowej.|
|[CBitmap::GetBitmap](#getbitmap)|Wypełnia `BITMAP` strukturę z informacjami o mapy bitowej.|
|[CBitmap::GetBitmapBits](#getbitmapbits)|Liczba bitów Podana mapa bitowa są kopiowane do określonego bufora.|
|[CBitmap::GetBitmapDimension](#getbitmapdimension)|Zwraca szerokość i wysokość mapy bitowej. Wysokość i szerokość są zakłada się, że zostały ustawione wcześniej [SetBitmapDimension](#setbitmapdimension) funkcja elementu członkowskiego.|
|[CBitmap::LoadBitmap](#loadbitmap)|Inicjuje obiekt przez ładowanie zasobów o nazwie mapę bitową z pliku wykonywalnego aplikacji i dołączanie mapę bitową do obiektu.|
|[CBitmap::LoadMappedBitmap](#loadmappedbitmap)|Ładuje mapę bitową i mapuje kolory do bieżącego kolory systemowe.|
|[CBitmap::LoadOEMBitmap](#loadoembitmap)|Inicjuje obiekt Ładowanie wstępnie zdefiniowanych mapę bitową Windows i dołączanie mapę bitową do obiektu.|
|[CBitmap::SetBitmapBits](#setbitmapbits)|Ustawia bity mapy bitowej wartości bitowe określony.|
|[CBitmap::SetBitmapDimension](#setbitmapdimension)|Przypisuje szerokość i wysokość mapy bitowej w milimetra 0,1 jednostki.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[HBITMAP CBitmap::operator](#operator_hbitmap)|Zwraca uchwyt Windows dołączonych do `CBitmap` obiektu.|

## <a name="remarks"></a>Uwagi

Aby użyć `CBitmap` obiektu, konstruowania obiektu, dołączyć uchwyt mapy bitowej do niej przy użyciu jednego z inicjowanie funkcji Członkowskich, a następnie wywołaj element członkowski obiektu funkcji.

Aby uzyskać więcej informacji na temat korzystania z obiektów graficznych, takich jak `CBitmap`, zobacz [obiektów grafiki](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBitmap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="cbitmap"></a>  CBitmap::CBitmap

Konstruuje `CBitmap` obiektu.

```
CBitmap();
```

### <a name="remarks"></a>Uwagi

Wynikowy obiekt musi zostać zainicjowany z jednej z funkcji elementu członkowskiego inicjowania.

##  <a name="createbitmap"></a>  CBitmap::CreateBitmap

Inicjuje mapę bitową zależne od urządzenia pamięci, która ma określoną szerokość, wysokość i wzorca bitowego.

```
BOOL CreateBitmap(
    int nWidth,
    int nHeight,
    UINT nPlanes,
    UINT nBitcount,
    const void* lpBits);
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
Określa szerokość mapy bitowej (w pikselach).

*nHeight*<br/>
Określa wysokość mapy bitowej (w pikselach).

*nPlanes*<br/>
Określa liczbę płaszczyzn kolorów w mapie bitowej.

*nBitcount*<br/>
Określa liczbę kolorów bitów na piksel wyświetlania.

*lpBits*<br/>
Wskazuje na tablicę bajtów, które zawiera wartości bitowe mapy bitowej początkowej. Jeśli ma wartość NULL, pozostanie nowej mapy bitowej niezainicjowany.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Dla mapy bitowej koloru albo *nPlanes* lub *nBitcount* parametru powinna być równa 1. Jeśli oba te parametry są ustawione na 1, `CreateBitmap` tworzy monochromatyczną mapę bitową.

Mimo że nie można bezpośrednio wybrać mapę bitową do wyświetlania na urządzeniach, można go ustawić jako bieżący mapy bitowej "pamięci urządzenia kontekstu" przy użyciu [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) i skopiowane do wszystkich kontekstach urządzenia za pomocą [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) funkcji.

Po zakończeniu pracy z `CBitmap` obiekt utworzony przez `CreateBitmap` funkcji, najpierw wybierz mapę bitową z kontekstu urządzenia, a następnie usuń `CBitmap` obiektu.

Aby uzyskać więcej informacji, zobacz opis `bmBits` pole `BITMAP` struktury. [Mapy BITOWEJ](../../mfc/reference/bitmap-structure.md) struktura została opisana w sekcji [CBitmap::CreateBitmapIndirect](#createbitmapindirect) funkcja elementu członkowskiego.

##  <a name="createbitmapindirect"></a>  CBitmap::CreateBitmapIndirect

Inicjuje mapę bitową, która ma szerokość, wysokość i wzorca bitowego (jeśli jest określony) podany w strukturze wskazywany przez *lpBitmap*.

```
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```

### <a name="parameters"></a>Parametry

*lpBitmap*<br/>
Wskazuje [mapy BITOWEJ](../../mfc/reference/bitmap-structure.md) strukturę, która zawiera informacje o mapy bitowej.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Mimo że nie można bezpośrednio wybrać mapę bitową do wyświetlania na urządzeniach, można go ustawić jako bieżący mapy bitowej dla kontekstu urządzenia pamięci za pomocą [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) i skopiowane do wszystkich kontekstach urządzenia za pomocą [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) lub [CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) funkcji. ( [CDC::PatBlt](../../mfc/reference/cdc-class.md#patblt) funkcji można skopiować mapy bitowej dla aktualny pędzel bezpośrednio do kontekstu urządzenia wyświetlaną.)

Jeśli `BITMAP` wskazywanej przez *lpBitmap* parametru zostało wypełnione przy użyciu `GetObject` funkcji, bity mapy bitowej nie są określone i mapy bitowej nie został zainicjowany. Aby zainicjować mapy bitowej, aplikacja może użyć funkcji takich jak [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) lub [SetDIBits](/windows/desktop/api/wingdi/nf-wingdi-setdibits) do skopiowania bity mapy bitowej identyfikowane przez pierwszy parametr `CGdiObject::GetObject` do mapy bitowej utworzone przez `CreateBitmapIndirect`.

Po zakończeniu pracy z `CBitmap` obiekt utworzony za pomocą `CreateBitmapIndirect` funkcji, najpierw wybierz mapę bitową z kontekstu urządzenia, a następnie usuń `CBitmap` obiektu.

##  <a name="createcompatiblebitmap"></a>  CBitmap::CreateCompatibleBitmap

Inicjuje mapy bitowej, zgodny z urządzenia określone przez *kontrolera pDC*.

```
BOOL CreateCompatibleBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
Określa kontekst urządzenia.

*nWidth*<br/>
Określa szerokość mapy bitowej (w pikselach).

*nHeight*<br/>
Określa wysokość mapy bitowej (w pikselach).

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Mapa bitowa ma taką samą liczbę płaszczyzn kolorów lub tego samego formatu bitów na piksel jako kontekst określonego urządzenia. Można wybrać jako bieżący mapy bitowej dla dowolnych urządzeń pamięci, która jest zgodna z ten, który został określony przez *kontrolera pDC*.

Jeśli *kontrolera pDC* jest kontekstu urządzenia pamięci mapy bitowej zwracana ma taki sam format, jako aktualnie wybranej mapy bitowej w kontekście tego urządzenia. "Pamięci urządzenia kontekstu" jest blok pamięci, który reprezentuje powierzchni ekranu. Może służyć do przygotowania obrazów w pamięci przed skopiowaniem ich do powierzchni rzeczywiste wyświetlania zgodnych urządzeń.

Podczas tworzenia kontekstu urządzenia pamięci GDI automatycznie wybiera monochromatycznych map bitowych podstawowe dla niego.

Ponieważ kolor kontekstu urządzenia pamięci może mieć kolor lub monochromatyczne wybrane, format mapy bitowej zwracany przez `CreateCompatibleBitmap` funkcja nie jest zawsze taki sam; jednak format zgodny mapy bitowej dla kontekstu urządzenia nonmemory zawsze znajduje się w Format urządzenia.

Po zakończeniu pracy z `CBitmap` obiekt utworzony za pomocą `CreateCompatibleBitmap` funkcji, najpierw wybierz mapę bitową z kontekstu urządzenia, a następnie usuń `CBitmap` obiektu.

##  <a name="creatediscardablebitmap"></a>  CBitmap::CreateDiscardableBitmap

Inicjuje discardable mapy bitowej, zgodny z kontekstu urządzenia identyfikowane przez *kontrolera pDC*.

```
BOOL CreateDiscardableBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
Określa kontekst urządzenia.

*nWidth*<br/>
Określa szerokość (w bitach) mapy bitowej.

*nHeight*<br/>
Określa wysokość mapy bitowej (w bitach).

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Mapa bitowa ma taką samą liczbę płaszczyzn kolorów lub tego samego formatu bitów na piksel jako kontekst określonego urządzenia. Aplikację można wybrać tej mapy bitowej jako bieżący mapy bitowej dla urządzenia pamięci, która jest zgodna z ten, który został określony przez *kontrolera pDC*.

Windows można odrzucić utworzone przez tę funkcję tylko wtedy, gdy aplikacja nie została wybrana go w kontekście wyświetlania mapy bitowej. Jeśli Windows odrzuca mapy bitowej, gdy nie jest zaznaczone i aplikację później spróbuje ją zaznaczyć, [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) funkcja zwróci wartość NULL.

Po zakończeniu pracy z `CBitmap` obiekt utworzony za pomocą `CreateDiscardableBitmap` funkcji, najpierw wybierz mapę bitową z kontekstu urządzenia, a następnie usuń `CBitmap` obiektu.

##  <a name="fromhandle"></a>  CBitmap::FromHandle

Zwraca wskaźnik do `CBitmap` obiektu, kiedy podane dojście do mapy bitowej Windows GDI.

```
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
Określa mapę bitową Windows GDI.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CBitmap` obiektu, jeśli operacja się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Jeśli `CBitmap` obiektu nie jest już dołączony do uchwyt tymczasowego `CBitmap` obiekt zostanie utworzony i dołączony. Ten tymczasowy `CBitmap` obiekt jest prawidłowy tylko do momentu przy następnym aplikacji ma czas bezczynności, po jego pętlę zdarzeń, w której czas wszystkich tymczasowych grafiki obiekty zostaną usunięte. Innymi słowy to to, że tymczasowy obiekt jest prawidłowy tylko podczas przetwarzania komunikatu w jednym oknie.

##  <a name="getbitmap"></a>  CBitmap::GetBitmap

Pobiera właściwości obrazu dołączonego mapy bitowej.

```
int GetBitmap(BITMAP* pBitMap);
```

### <a name="parameters"></a>Parametry

*pBitMap*<br/>
Wskaźnik do [struktury map BITOWYCH](../../mfc/reference/bitmap-structure.md) struktury, który będzie otrzymywał właściwości obrazu. Ten parametr nie może być równa NULL.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

##  <a name="getbitmapbits"></a>  CBitmap::GetBitmapBits

Kopiuje wzorca bitowego lustrzany mapy bitowej, dołączonych do określonego bufora.

```
DWORD GetBitmapBits(
    DWORD dwCount,
    LPVOID lpBits) const;
```

### <a name="parameters"></a>Parametry

*dwCount*<br/>
Liczba bajtów do skopiowania do buforu.

*lpBits*<br/>
Wskaźnik do buforu, który będzie otrzymywał mapy bitowej.

### <a name="return-value"></a>Wartość zwracana

Liczbą bajtów skopiowanych w buforze, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj [CBitmap::GetBitmap](#getbitmap) ustalenie wymagany rozmiar buforu.

##  <a name="getbitmapdimension"></a>  CBitmap::GetBitmapDimension

Zwraca szerokość i wysokość mapy bitowej.

```
CSize GetBitmapDimension() const;
```

### <a name="return-value"></a>Wartość zwracana

Szerokość i wysokość mapy bitowej, mierzone w jednostkach milimetra 0,1. Wysokość znajduje się w `cy` członkiem `CSize` obiektu i szerokość znajduje się w `cx` elementu członkowskiego. Jeśli wysokość i szerokość bitmapy nie została ustawiona za pomocą `SetBitmapDimension`, wartość zwracana to 0.

### <a name="remarks"></a>Uwagi

Wysokość i szerokość są zakłada się, że zostały ustawione wcześniej przy użyciu [SetBitmapDimension](#setbitmapdimension) funkcja elementu członkowskiego.

##  <a name="loadbitmap"></a>  CBitmap::LoadBitmap

Ładuje zasób mapy bitowej o nazwie określonej przez *lpszResourceName* lub identyfikowany przez numer identyfikacyjny w *nIDResource* z pliku wykonywalnego aplikacji.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera nazwę zasobu mapy bitowej.

*nIDResource*<br/>
Określa identyfikator zasobu zasób mapy bitowej.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Załadować mapy bitowej jest dołączony do `CBitmap` obiektu.

Jeśli mapa bitowa oznaczona *lpszResourceName* nie istnieje lub ma za mało pamięci, aby załadować mapy bitowej, funkcja zwraca 0.

Możesz użyć [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) funkcję, aby usunąć mapy bitowej ładowane przez `LoadBitmap` funkcji, lub `CBitmap` destruktor spowoduje usunięcie obiektu dla Ciebie.

> [!CAUTION]
>  Przed usunięciem obiektu, upewnij się, że nie jest zaznaczone do kontekstu urządzenia.

Poniższe mapy bitowe zostały dodane do wersji Windows 3.1 lub nowszy:

OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI

Te mapy bitowe nie znajdują się w sterowniki urządzeń dla wersji Windows 3.0 i wcześniejszych. Aby uzyskać pełną listę mapy bitowe i wyświetlania ich występowania zobacz zestaw Windows SDK.

##  <a name="loadmappedbitmap"></a>  CBitmap::LoadMappedBitmap

Wywołaj tę funkcję elementu członkowskiego, aby załadować mapy bitowej i mapowanie kolorów do bieżącego kolory systemowe.

```
BOOL LoadMappedBitmap(
    UINT nIDBitmap,
    UINT nFlags = 0,
    LPCOLORMAP lpColorMap = NULL,
    int nMapSize = 0);
```

### <a name="parameters"></a>Parametry

*nIDBitmap*<br/>
Identyfikator zasobu mapy bitowej.

*nFlags*<br/>
Flaga mapy bitowej. Może mieć zero lub CMB_MASKED.

*lpColorMap*<br/>
Wskaźnik do `COLORMAP` strukturę, która zawiera kolor potrzebnych do mapy bitowe. Jeśli ten parametr ma wartość NULL, funkcja używa mapy kolor domyślny.

*nMapSize*<br/>
Liczba kolorów mapy, wskazywana przez *lpColorMap*.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślnie `LoadMappedBitmap` zmapuje kolory często używane w symbole przycisku.

Dla informacji o tworzeniu zamapowanego mapy bitowej, zobacz opis funkcji Windows [CreateMappedBitmap](http://go.microsoft.com/fwlink/p/?linkid=230562) i [COLORMAP](/windows/desktop/api/commctrl/ns-commctrl-_colormap) struktury w zestawie Windows SDK.

##  <a name="loadoembitmap"></a>  CBitmap::LoadOEMBitmap

Ładuje mapę bitową wstępnie zdefiniowane, używana przez Windows.

```
BOOL LoadOEMBitmap(UINT nIDBitmap);
```

### <a name="parameters"></a>Parametry

*nIDBitmap*<br/>
Numer identyfikacyjny wstępnie zdefiniowanych mapę bitową Windows. Poniżej przedstawiono możliwe wartości z systemu WINDOWS. GODZ.:

|||
|-|-|
|OBM_BTNCORNERS|OBM_OLD_RESTORE|
|OBM_BTSIZE|OBM_OLD_RGARROW|
|OBM_CHECK|OBM_OLD_UPARROW|
|OBM_CHECKBOXES|OBM_OLD_ZOOM|
|OBM_CLOSE|OBM_REDUCE|
|OBM_COMBO|OBM_REDUCED|
|OBM_DNARROW|OBM_RESTORE|
|OBM_DNARROWD|OBM_RESTORED|
|OBM_DNARROWI|OBM_RGARROW|
|OBM_LFARROW|OBM_RGARROWD|
|OBM_LFARROWD|OBM_RGARROWI|
|OBM_LFARROWI|OBM_SIZE|
|OBM_MNARROW|OBM_UPARROW|
|OBM_OLD_CLOSE|OBM_UPARROWD|
|OBM_OLD_DNARROW|OBM_UPARROW|
|OBM_OLD_LFARROW|OBM_ZOOM|
|OBM_OLD_REDUCE|OBM_ZOOMD|

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Nazwy mapy bitowej, które zaczynają się od OBM_OLD reprezentują mapy bitowe używane przez Windows wersjach wcześniejszych niż 3.0.

Należy pamiętać, że stałe OEMRESOURCE muszą być zdefiniowane przed dołączeniem systemu WINDOWS. H, aby można było użyć dowolnego z **OBM_** stałe.

##  <a name="operator_hbitmap"></a>  HBITMAP CBitmap::operator

Użyj tego operatora, aby uzyskać dojście Windows GDI dołączonych `CBitmap` obiektu.

```
operator HBITMAP() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli operacja się powiedzie, dojścia do obiektu Windows GDI reprezentowany przez `CBitmap` obiektu; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Ten operator jest operatora rzutowania, który obsługuje bezpośredniemu wykorzystaniu `HBITMAP` obiektu.

Aby uzyskać więcej informacji o korzystaniu z obiektów graficznych, zobacz [obiektów grafiki](/windows/desktop/gdi/graphic-objects) w zestawie Windows SDK.

##  <a name="setbitmapbits"></a>  CBitmap::SetBitmapBits

Ustawia bity mapy bitowej wartości bitowe dane *lpBits*.

```
DWORD SetBitmapBits(
    DWORD dwCount,
    const void* lpBits);
```

### <a name="parameters"></a>Parametry

*dwCount*<br/>
Określa liczbę bajtów wskazywany przez *lpBits*.

*lpBits*<br/>
Wskazuje na tablicę BAJTÓW, która zawiera wartości pikseli, które mają być kopiowane do `CBitmap` obiektu. Aby mapy bitowej można było prawidłowo renderować obraz należy sformatować wartości odpowiadają wartości głębokości wysokość, szerokość i kolor, które zostały określone podczas tworzenia wystąpienia CBitmap. Aby uzyskać więcej informacji, zobacz [CBitmap::CreateBitmap](#createbitmap).

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów używanych podczas ustawiania bity mapy bitowej; 0, jeśli funkcja kończy się niepowodzeniem.

##  <a name="setbitmapdimension"></a>  CBitmap::SetBitmapDimension

Przypisuje szerokość i wysokość mapy bitowej w milimetra 0,1 jednostki.

```
CSize SetBitmapDimension(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
Określa szerokość mapy bitowej (w jednostkach 0,1 milimetra).

*nHeight*<br/>
Określa wysokość mapy bitowej (w jednostkach 0,1 milimetra).

### <a name="return-value"></a>Wartość zwracana

Poprzednie wymiary mapy bitowej. Wysokość znajduje się w `cy` zmienną elementu członkowskiego `CSize` obiektu i szerokości znajduje się w `cx` zmiennej składowej.

### <a name="remarks"></a>Uwagi

Interfejs GDI nie używa tych wartości, z wyjątkiem sytuacji, aby przywrócić je po uruchomieniu [GetBitmapDimension](#getbitmapdimension) funkcja elementu członkowskiego.

## <a name="see-also"></a>Zobacz też

[Próbki MFC MDI](../../visual-cpp-samples.md)<br/>
[Klasa CGdiObject](../../mfc/reference/cgdiobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)

