---
title: Klasa CBitmap
ms.date: 11/04/2016
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
ms.openlocfilehash: 9a33a6e1bea601422e043d7f2a80029c72d97e50
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352742"
---
# <a name="cbitmap-class"></a>Klasa CBitmap

Hermetyzuje mapę bitową interfejsu urządzenia graficznego systemu Windows (GDI) i udostępnia funkcje członkowskie do manipulowania bitmapą.

## <a name="syntax"></a>Składnia

```
class CBitmap : public CGdiObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBitmap::CBitmap](#cbitmap)|Konstruuje `CBitmap` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBitmap::CreateBitmap](#createbitmap)|Inicjuje obiekt za pomocą mapy bitowej pamięci zależnej od urządzenia, która ma określoną szerokość, wysokość i wzorzec bitowy.|
|[CBitmap::CreateBitmapIndirect](#createbitmapindirect)|Inicjuje obiekt z bitmapą z szerokością, wysokością i wzorcem `BITMAP` bitowym (jeśli jest określony) podanym w strukturze.|
|[CBitmap::CreateCompatibleBitmap](#createcompatiblebitmap)|Inicjuje obiekt za pomocą mapy bitowej, tak aby był zgodny z określonym urządzeniem.|
|[CBitmap::CreateDiscardableBitmap](#creatediscardablebitmap)|Inicjuje obiekt za pomocą odrzucanej mapy bitowej, która jest zgodna z określonym urządzeniem.|
|[CBitmap::OdRążej](#fromhandle)|Zwraca wskaźnik do `CBitmap` obiektu po podaniu `HBITMAP` dojścia do mapy bitowej systemu Windows.|
|[CBitmap::GetBitmap](#getbitmap)|Wypełnia strukturę `BITMAP` informacjami o mapie bitowej.|
|[CBitmap::GetBitmapBits](#getbitmapbits)|Kopiuje bity określonej mapy bitowej do określonego buforu.|
|[CBitmap::GetBitmapDimension](#getbitmapdimension)|Zwraca szerokość i wysokość mapy bitowej. Zakłada się, że wysokość i szerokość zostały ustawione wcześniej przez funkcję elementu członkowskiego [SetBitmapDimension.](#setbitmapdimension)|
|[CBitmap::LoadBitmap](#loadbitmap)|Inicjuje obiekt, ładując nazwany zasób mapy bitowej z pliku wykonywalnego aplikacji i dołączając mapę bitową do obiektu.|
|[CBitmap::LoadMappedBitmap](#loadmappedbitmap)|Ładuje mapę bitową i mapuje kolory do bieżących kolorów systemowych.|
|[CBitmap::LoadOEMBitmap](#loadoembitmap)|Inicjuje obiekt, ładując wstępnie zdefiniowaną mapę bitową systemu Windows i dołączając mapę bitową do obiektu.|
|[CBitmap::SetBitmapBits](#setbitmapbits)|Ustawia bity mapy bitowej na określone wartości bitowe.|
|[CBitmap::SetBitmapDimension](#setbitmapdimension)|Przypisuje szerokość i wysokość do mapy bitowej w jednostkach 0,1 milimetra.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBitmap::operator HBITMAP](#operator_hbitmap)|Zwraca uchwyt systemu Windows `CBitmap` dołączony do obiektu.|

## <a name="remarks"></a>Uwagi

Aby użyć `CBitmap` obiektu, skonstruuj obiekt, dołącz do niego uchwyt mapy bitowej z jedną z funkcji elementu członkowskiego inicjowania, a następnie wywołaj funkcje członkowskie obiektu.

Aby uzyskać więcej informacji `CBitmap`na temat używania obiektów graficznych, takich jak , zobacz [Obiekty graficzne](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cgdiobject](../../mfc/reference/cgdiobject-class.md)

`CBitmap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cbitmapcbitmap"></a><a name="cbitmap"></a>CBitmap::CBitmap

Konstruuje `CBitmap` obiekt.

```
CBitmap();
```

### <a name="remarks"></a>Uwagi

Wynikowy obiekt musi zostać zainicjowany przy jednej z funkcji elementu członkowskiego inicjowania.

## <a name="cbitmapcreatebitmap"></a><a name="createbitmap"></a>CBitmap::CreateBitmap

Inicjuje mapę bitową pamięci zależną od urządzenia, która ma określoną szerokość, wysokość i wzorzec bitowy.

```
BOOL CreateBitmap(
    int nWidth,
    int nHeight,
    UINT nPlanes,
    UINT nBitcount,
    const void* lpBits);
```

### <a name="parameters"></a>Parametry

*nWidth (ww.*<br/>
Określa szerokość (w pikselach) mapy bitowej.

*nFeksja*<br/>
Określa wysokość (w pikselach) mapy bitowej.

*nPlanes (Samoloty)*<br/>
Określa liczbę płaszczyzn kolorów w mapie bitowej.

*nWyliczaj*<br/>
Określa liczbę bitów kolorów na piksel ekranu.

*lpBits (lpBits)*<br/>
Wskazuje tablicę bajtów zawierającą początkowe wartości bitowe mapy bitowej. Jeśli jest null, nowa mapa bitowa pozostaje niezainicjowana.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

W przypadku kolorowej mapy bitowej parametr *nPlanes* lub *nBitcount* powinien być ustawiony na 1. Jeśli oba te parametry są ustawione `CreateBitmap` na 1, tworzy monochromatycznej mapy bitowej.

Chociaż mapy bitowej nie można wybrać bezpośrednio dla urządzenia wyświetlającego, można ją wybrać jako bieżącą mapę bitową dla "kontekstu urządzenia pamięci" przy użyciu [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) i skopiować do dowolnego zgodnego kontekstu urządzenia przy użyciu funkcji [CDC::BitBlt.](../../mfc/reference/cdc-class.md#bitblt)

Po zakończeniu z `CBitmap` obiektem `CreateBitmap` utworzonym przez funkcję najpierw zaznacz mapę bitową `CBitmap` z kontekstu urządzenia, a następnie usuń obiekt.

Aby uzyskać więcej informacji, `bmBits` zobacz opis `BITMAP` pola w strukturze. Struktura [BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap) jest opisana w funkcji elementu członkowskiego [CBitmap::CreateBitmapIndirect.](#createbitmapindirect)

## <a name="cbitmapcreatebitmapindirect"></a><a name="createbitmapindirect"></a>CBitmap::CreateBitmapIndirect

Inicjuje mapę bitową, która ma szerokość, wysokość i wzorzec bitowy (jeśli jest określony) podany w strukturze wskazanej przez *lpBitmap*.

```
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```

### <a name="parameters"></a>Parametry

*lpBitmap (mapa bitowa)*<br/>
Wskazuje strukturę [BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap) zawierającą informacje o mapie bitowej.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Chociaż mapy bitowej nie można wybrać bezpośrednio dla urządzenia wyświetlającego, można ją wybrać jako bieżącą mapę bitową dla kontekstu urządzenia pamięci przy użyciu [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) i skopiować do dowolnego zgodnego kontekstu urządzenia za pomocą funkcji [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) lub [CDC::StretchBlt.](../../mfc/reference/cdc-class.md#stretchblt) (Funkcja [CDC::PatBlt](../../mfc/reference/cdc-class.md#patblt) może skopiować mapę bitową bieżącego pędzla bezpośrednio do kontekstu urządzenia wyświetlającego).

Jeśli `BITMAP` struktura wskazywiona przez parametr *lpBitmap* została wypełniona za pomocą `GetObject` funkcji, bity mapy bitowej nie są określone, a mapa bitowa jest niezainicjowana. Aby zainicjować mapę bitową, aplikacja może użyć funkcji, takiej jak [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) lub [SetDIBits,](/windows/win32/api/wingdi/nf-wingdi-setdibits) aby `CGdiObject::GetObject` skopiować bity `CreateBitmapIndirect`z mapy bitowej identyfikowanej przez pierwszy parametr mapy bitowej utworzonej przez program .

Po zakończeniu z `CBitmap` obiektem `CreateBitmapIndirect` utworzonym za pomocą funkcji najpierw zaznacz mapę `CBitmap` bitową z kontekstu urządzenia, a następnie usuń obiekt.

## <a name="cbitmapcreatecompatiblebitmap"></a><a name="createcompatiblebitmap"></a>CBitmap::CreateCompatibleBitmap

Inicjuje mapę bitową, która jest zgodna z urządzeniem określonym przez *pDC*.

```
BOOL CreateCompatibleBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Określa kontekst urządzenia.

*nWidth (ww.*<br/>
Określa szerokość (w pikselach) mapy bitowej.

*nFeksja*<br/>
Określa wysokość (w pikselach) mapy bitowej.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Mapa bitowa ma taką samą liczbę płaszczyzn kolorów lub format bitów na piksel, jak określony kontekst urządzenia. Można go wybrać jako bieżącą mapę bitową dla dowolnego urządzenia pamięci zgodnego z urządzeniem określonym przez *pDC*.

Jeśli *pDC* jest kontekstem urządzenia pamięci, zwrócona mapa bitowa ma ten sam format co aktualnie wybrana mapa bitowa w tym kontekście urządzenia. "Kontekst urządzenia pamięci" jest blokiem pamięci reprezentującym powierzchnię wyświetlania. Może być używany do przygotowania obrazów w pamięci przed skopiowaniem ich do rzeczywistej powierzchni wyświetlacza zgodnego urządzenia.

Po utworzeniu kontekstu urządzenia pamięci GDI automatycznie wybiera dla niego monochromatyczny bitmapę zapasową.

Ponieważ kontekst urządzenia pamięci kolorów może mieć zaznaczone kolorowe lub monochromatyczne mapy bitowe, format mapy bitowej zwracanej przez `CreateCompatibleBitmap` funkcję nie zawsze jest taki sam; jednak format zgodnej mapy bitowej dla kontekstu urządzenia niememorowego jest zawsze w formacie urządzenia.

Po zakończeniu z `CBitmap` obiektem `CreateCompatibleBitmap` utworzonym za pomocą funkcji najpierw zaznacz mapę `CBitmap` bitową z kontekstu urządzenia, a następnie usuń obiekt.

## <a name="cbitmapcreatediscardablebitmap"></a><a name="creatediscardablebitmap"></a>CBitmap::CreateDiscardableBitmap

Inicjuje odrzucaną mapę bitową, która jest zgodna z kontekstem urządzenia identyfikowanym przez *pDC*.

```
BOOL CreateDiscardableBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Określa kontekst urządzenia.

*nWidth (ww.*<br/>
Określa szerokość (w bitach) mapy bitowej.

*nFeksja*<br/>
Określa wysokość (w bitach) mapy bitowej.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Mapa bitowa ma taką samą liczbę płaszczyzn kolorów lub format bitów na piksel, jak określony kontekst urządzenia. Aplikacja może wybrać tę mapę bitową jako bieżącą mapę bitową dla urządzenia pamięci zgodnego z urządzeniem określonym przez *pDC*.

System Windows może odrzucić mapę bitową utworzoną przez tę funkcję tylko wtedy, gdy aplikacja nie wybrała jej w kontekście wyświetlania. Jeśli system Windows odrzuci mapę bitową, gdy nie jest zaznaczona, a aplikacja później spróbuje ją zaznaczyć, funkcja [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) zwróci wartość NULL.

Po zakończeniu z `CBitmap` obiektem `CreateDiscardableBitmap` utworzonym za pomocą funkcji najpierw zaznacz mapę `CBitmap` bitową z kontekstu urządzenia, a następnie usuń obiekt.

## <a name="cbitmapfromhandle"></a><a name="fromhandle"></a>CBitmap::OdRążej

Zwraca wskaźnik do `CBitmap` obiektu po podaniu dojścia do mapy bitowej interfejsu GDI systemu Windows.

```
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parametry

*hBitmapa*<br/>
Określa mapę bitową interfejsu GDI systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CBitmap` obiektu, jeśli zakończy się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Jeśli `CBitmap` obiekt nie jest jeszcze dołączony do `CBitmap` uchwytu, tworzony i dołączany jest obiekt tymczasowy. Ten `CBitmap` obiekt tymczasowy jest prawidłowy tylko do następnego czasu, gdy aplikacja ma czas bezczynny w pętli zdarzeń, w którym to czasie wszystkie tymczasowe obiekty graficzne są usuwane. Innym sposobem mówienia jest to, że obiekt tymczasowy jest prawidłowy tylko podczas przetwarzania komunikatu okna.

## <a name="cbitmapgetbitmap"></a><a name="getbitmap"></a>CBitmap::GetBitmap

Pobiera właściwości obrazu dołączonej mapy bitowej.

```
int GetBitmap(BITMAP* pBitMap);
```

### <a name="parameters"></a>Parametry

*pBitMap (mapa bitów)*<br/>
Wskaźnik do struktury [BITMAP,](/windows/win32/api/wingdi/ns-wingdi-bitmap) która otrzyma właściwości obrazu. Ten parametr nie może być null.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

## <a name="cbitmapgetbitmapbits"></a><a name="getbitmapbits"></a>CBitmap::GetBitmapBits

Kopiuje wzorzec bitowy dołączonej mapy bitowej do określonego buforu.

```
DWORD GetBitmapBits(
    DWORD dwCount,
    LPVOID lpBits) const;
```

### <a name="parameters"></a>Parametry

*dwCount (licz)*<br/>
Liczba bajtów do skopiowania do buforu.

*lpBits (lpBits)*<br/>
Wskaźnik do buforu, który otrzyma mapę bitową.

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów skopiowanych do buforu, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj [CBitmap::GetBitmap,](#getbitmap) aby określić wymagany rozmiar buforu.

## <a name="cbitmapgetbitmapdimension"></a><a name="getbitmapdimension"></a>CBitmap::GetBitmapDimension

Zwraca szerokość i wysokość mapy bitowej.

```
CSize GetBitmapDimension() const;
```

### <a name="return-value"></a>Wartość zwracana

Szerokość i wysokość mapy bitowej mierzona w jednostkach 0,1 milimetra. Wysokość znajduje się `cy` w `CSize` części członkowskiej obiektu, `cx` a szerokość znajduje się w człowianych. Jeśli szerokość i wysokość mapy bitowej `SetBitmapDimension`nie zostały ustawione przy użyciu , zwracana wartość wynosi 0.

### <a name="remarks"></a>Uwagi

Zakłada się, że wysokość i szerokość zostały ustawione wcześniej przy użyciu funkcji elementu członkowskiego [SetBitmapDimension.](#setbitmapdimension)

## <a name="cbitmaploadbitmap"></a><a name="loadbitmap"></a>CBitmap::LoadBitmap

Ładuje zasób mapy bitowej nazwany przez *lpszResourceName* lub identyfikowany przez numer identyfikacyjny w *nIDResource* z pliku wykonywalnego aplikacji.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Wskazuje ciąg zakończony z wartością null, który zawiera nazwę zasobu mapy bitowej.

*nIDSerwród*<br/>
Określa numer identyfikatora zasobu mapy bitowej.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Załadowana mapa bitowa jest `CBitmap` dołączona do obiektu.

Jeśli bitmapa zidentyfikowana przez *lpszResourceName* nie istnieje lub jeśli nie ma wystarczającej ilości pamięci do załadowania mapy bitowej, funkcja zwraca wartość 0.

Za pomocą funkcji [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) można usunąć bitmapę `LoadBitmap` załadowaną przez `CBitmap` tę funkcję lub destruktor usunie obiekt.

> [!CAUTION]
> Przed usunięciem obiektu upewnij się, że nie jest on zaznaczony w kontekście urządzenia.

Następujące mapy bitowe zostały dodane do systemu Windows w wersji 3.1 lub nowszej:

OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI

Te mapy bitowe nie znajdują się w sterownikach urządzeń dla systemu Windows w wersji 3.0 lub wcześniejszych. Aby uzyskać pełną listę map bitowych i wyświetlanie ich wyglądu, zobacz SDK systemu Windows.

## <a name="cbitmaploadmappedbitmap"></a><a name="loadmappedbitmap"></a>CBitmap::LoadMappedBitmap

Wywołanie tej funkcji elementu członkowskiego, aby załadować mapę bitową i zamapować kolory na bieżące kolory systemowe.

```
BOOL LoadMappedBitmap(
    UINT nIDBitmap,
    UINT nFlags = 0,
    LPCOLORMAP lpColorMap = NULL,
    int nMapSize = 0);
```

### <a name="parameters"></a>Parametry

*nIDBitmapa*<br/>
Identyfikator zasobu mapy bitowej.

*nPłgi*<br/>
Flaga mapy bitowej. Może być zero lub CMB_MASKED.

*lpColorMap*<br/>
Wskaźnik do `COLORMAP` struktury zawierającej informacje o kolorze potrzebne do mapowania map bitowych. Jeśli ten parametr ma wartość NULL, funkcja używa domyślnej mapy kolorów.

*rozmiar nMapSize*<br/>
Liczba kolorowych map wskazanych przez *lpColorMap*.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślnie `LoadMappedBitmap` będzie mapować kolory często używane w glifach przycisków.

Aby uzyskać informacje dotyczące tworzenia mapowania bitmapy, zobacz funkcję Windows [CreateMappedBitmap](https://go.microsoft.com/fwlink/p/?linkid=230562) i strukturę [COLORMAP](/windows/win32/api/commctrl/ns-commctrl-colormap) w zestaw windows SDK.

## <a name="cbitmaploadoembitmap"></a><a name="loadoembitmap"></a>CBitmap::LoadOEMBitmap

Ładuje wstępnie zdefiniowaną mapę bitową używaną przez system Windows.

```
BOOL LoadOEMBitmap(UINT nIDBitmap);
```

### <a name="parameters"></a>Parametry

*nIDBitmapa*<br/>
Numer identyfikatora wstępnie zdefiniowanej mapy bitowej systemu Windows. Możliwe wartości są wymienione poniżej z systemu WINDOWS. H:

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

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Nazwy bitmap, które zaczynają się od OBM_OLD reprezentują mapy bitowe używane przez wersje systemu Windows przed wersją 3.0.

Należy zauważyć, że stała OEMRESOURCE musi być zdefiniowana przed dołączeniem systemu WINDOWS. H w celu użycia któregokolwiek ze **stałych OBM_.**

## <a name="cbitmapoperator-hbitmap"></a><a name="operator_hbitmap"></a>CBitmap::operator HBITMAP

Użyj tego operatora, aby uzyskać dołączony uchwyt `CBitmap` GDI systemu Windows obiektu.

```
operator HBITMAP() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, dojście do obiektu `CBitmap` GDI systemu Windows reprezentowanego przez obiekt; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Ten operator jest operatorem odlewania, `HBITMAP` który obsługuje bezpośrednie użycie obiektu.

Aby uzyskać więcej informacji na temat używania obiektów [graficznych,](/windows/win32/gdi/graphic-objects) zobacz Obiekty graficzne w sdk systemu Windows.

## <a name="cbitmapsetbitmapbits"></a><a name="setbitmapbits"></a>CBitmap::SetBitmapBits

Ustawia bity mapy bitowej na wartości bitowe podane przez *lpBits*.

```
DWORD SetBitmapBits(
    DWORD dwCount,
    const void* lpBits);
```

### <a name="parameters"></a>Parametry

*dwCount (licz)*<br/>
Określa liczbę bajtów wskazywali przez *lpBits*.

*lpBits (lpBits)*<br/>
Wskazuje tablicę BYTE zawierającą wartości pikseli, `CBitmap` które mają zostać skopiowane do obiektu. Aby mapa bitowa mogła poprawnie renderować swój obraz, wartości powinny być sformatowane w taki sposób, aby były zgodne z wartościami głębokości wysokości, szerokości i koloru, które zostały określone podczas tworzenia instancji CBitmap. Aby uzyskać więcej informacji, zobacz [CBitmap::CreateBitmap](#createbitmap).

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów używanych do ustawiania bitów bitmapy; 0, jeśli funkcja nie powiedzie się.

## <a name="cbitmapsetbitmapdimension"></a><a name="setbitmapdimension"></a>CBitmap::SetBitmapDimension

Przypisuje szerokość i wysokość do mapy bitowej w jednostkach 0,1 milimetra.

```
CSize SetBitmapDimension(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*nWidth (ww.*<br/>
Określa szerokość mapy bitowej (w jednostkach 0,1 milimetra).

*nFeksja*<br/>
Określa wysokość mapy bitowej (w jednostkach 0,1 milimetra).

### <a name="return-value"></a>Wartość zwracana

Poprzednie wymiary mapy bitowej. Wysokość znajduje `cy` się w `CSize` zmiennej prętowej obiektu, a szerokość w zmiennej prętowej. `cx`

### <a name="remarks"></a>Uwagi

GDI nie używa tych wartości, z wyjątkiem do zwrócenia ich, gdy aplikacja wywołuje [GetBitmapDimension](#getbitmapdimension) funkcji elementu członkowskiego.

## <a name="see-also"></a>Zobacz też

[Przykładowy MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CGdiObject](../../mfc/reference/cgdiobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
