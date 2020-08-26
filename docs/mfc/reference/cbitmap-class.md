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
ms.openlocfilehash: adb2a461de5e82fa76ce0ed9961d970f46dbe26a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834989"
---
# <a name="cbitmap-class"></a>Klasa CBitmap

Hermetyzuje mapę bitową interfejsu urządzenia graficznego (GDI) systemu Windows i udostępnia funkcje elementów członkowskich do manipulowania mapą bitową.

## <a name="syntax"></a>Składnia

```
class CBitmap : public CGdiObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBitmap:: CBitmap](#cbitmap)|Konstruuje `CBitmap` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBitmap:: ismap](#createbitmap)|Inicjuje obiekt z mapą bitową pamięci zależnej od urządzenia, która ma określoną szerokość, Wysokość i wzorzec bitowy.|
|[CBitmap:: CreateBitmapIndirect](#createbitmapindirect)|Inicjuje obiekt za pomocą mapy bitowej z wzorcem Width, Height i bit (jeśli został określony) podany w `BITMAP` strukturze.|
|[CBitmap:: CreateCompatibleBitmap](#createcompatiblebitmap)|Inicjuje obiekt z mapą bitową, tak aby był zgodny z określonym urządzeniem.|
|[CBitmap:: CreateDiscardableBitmap](#creatediscardablebitmap)|Inicjuje obiekt z odciskiem mapy bitowej, która jest zgodna z określonym urządzeniem.|
|[CBitmap:: FromHandle](#fromhandle)|Zwraca wskaźnik do obiektu, `CBitmap` gdy ma dojść do mapy bitowej systemu Windows `HBITMAP` .|
|[CBitmap:: getmap](#getbitmap)|Wypełnia `BITMAP` strukturę informacjami o mapie bitowej.|
|[CBitmap:: GetBitmapBits](#getbitmapbits)|Kopiuje bity określonej mapy bitowej do określonego buforu.|
|[CBitmap:: GetBitmapDimension](#getbitmapdimension)|Zwraca szerokość i wysokość mapy bitowej. Przyjęto, że wysokość i szerokość są ustawione wcześniej przez funkcję elementu członkowskiego [SetBitmapDimension](#setbitmapdimension) .|
|[CBitmap:: LoadBitmap](#loadbitmap)|Inicjuje obiekt przez załadowanie nazwanego zasobu mapy bitowej z pliku wykonywalnego aplikacji i dołączenie mapy bitowej do obiektu.|
|[CBitmap:: LoadMappedBitmap](#loadmappedbitmap)|Ładuje mapę bitową i mapuje kolory na bieżące kolory systemowe.|
|[CBitmap:: LoadOEMBitmap](#loadoembitmap)|Inicjuje obiekt przez załadowanie wstępnie zdefiniowanej mapy bitowej systemu Windows i dołączenie mapy bitowej do obiektu.|
|[CBitmap:: SetBitmapBits](#setbitmapbits)|Ustawia bity mapy bitowej na określone wartości bitowe.|
|[CBitmap:: SetBitmapDimension](#setbitmapdimension)|Przypisuje szerokość i wysokość do mapy bitowej w jednostkach 0,1 milimetrów.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBitmap:: operator HBITMAP](#operator_hbitmap)|Zwraca dojście systemu Windows dołączone do `CBitmap` obiektu.|

## <a name="remarks"></a>Uwagi

Aby użyć `CBitmap` obiektu, konstrukcja obiektu, Dołącz do niego uchwyt mapy bitowej z jedną z funkcji Członkowskich inicjujących, a następnie Wywołaj funkcje składowe obiektu.

Aby uzyskać więcej informacji na temat używania obiektów graficznych, takich jak `CBitmap` , zobacz [obiektów graficznych](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBitmap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

## <a name="cbitmapcbitmap"></a><a name="cbitmap"></a> CBitmap:: CBitmap

Konstruuje `CBitmap` obiekt.

```
CBitmap();
```

### <a name="remarks"></a>Uwagi

Obiekt wyników musi być zainicjowany przy użyciu jednej z funkcji inicjujących elementów członkowskich.

## <a name="cbitmapcreatebitmap"></a><a name="createbitmap"></a> CBitmap:: ismap

Inicjuje mapę bitową pamięci zależną od urządzenia, która ma określoną szerokość, Wysokość i wzorzec bitowy.

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
Określa szerokość (w pikselach) mapy bitowej.

*nHeight*<br/>
Określa wysokość (w pikselach) mapy bitowej.

*nPlanes*<br/>
Określa liczbę płaszczyzn kolorów w mapie bitowej.

*nBitcount*<br/>
Określa liczbę bitów koloru na piksel wyświetlania.

*lpBits*<br/>
Wskazuje tablicę bajtów zawierającą początkowe wartości bitowe mapy bitowej. Jeśli ma wartość NULL, Nowa mapa bitowa nie zostanie zainicjowana.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

W przypadku mapy bitowej koloru parametr *nPlanes* lub *nBitcount* powinien mieć wartość 1. Jeśli oba te parametry są ustawione na 1, program `CreateBitmap` tworzy czarną mapę bitową.

Mimo że nie można bezpośrednio wybrać mapy bitowej dla urządzenia wyświetlającego, można ją wybrać jako bieżącą mapę bitową dla kontekstu urządzenia pamięci, używając funkcji [przechwytywania:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) i skopiowanej do dowolnego zgodnego kontekstu urządzenia przy użyciu funkcję [przechwytywania:: BitBlt](../../mfc/reference/cdc-class.md#bitblt) .

Po zakończeniu pracy z `CBitmap` obiektem utworzonym przez `CreateBitmap` funkcję, najpierw wybierz mapę bitową z kontekstu urządzenia, a następnie usuń `CBitmap` obiekt.

Aby uzyskać więcej informacji, zobacz Opis `bmBits` pola w `BITMAP` strukturze. Struktura [mapy bitowej](/windows/win32/api/wingdi/ns-wingdi-bitmap) jest opisana w funkcji składowej [CBitmap:: CreateBitmapIndirect](#createbitmapindirect) .

## <a name="cbitmapcreatebitmapindirect"></a><a name="createbitmapindirect"></a> CBitmap:: CreateBitmapIndirect

Inicjuje mapę bitową, która ma wzorzec Width, Height i bit (jeśli został określony) podany w strukturze wskazywanej przez *lpBitmap*.

```
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```

### <a name="parameters"></a>Parametry

*lpBitmap*<br/>
Wskazuje strukturę [mapy bitowej](/windows/win32/api/wingdi/ns-wingdi-bitmap) , która zawiera informacje o mapie bitowej.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Mimo że nie można bezpośrednio wybrać mapy bitowej dla urządzenia wyświetlającego, można ją wybrać jako bieżącą mapę bitową kontekstu urządzenia pamięci przy użyciu funkcji [przechwytywania:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) i skopiować do dowolnego zgodnego kontekstu urządzenia za pomocą polecenia przestaw: [: BitBlt](../../mfc/reference/cdc-class.md#bitblt) lub funkcja [przechwytywania:: StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) . (Funkcja [przechwytywania::P atblt](../../mfc/reference/cdc-class.md#patblt) może skopiować mapę bitową bieżącego pędzla bezpośrednio do kontekstu wyświetlania urządzenia).

Jeśli `BITMAP` Struktura wskazywana przez parametr *lpBitmap* został wypełniony przy użyciu `GetObject` funkcji, bity mapy bitowej nie są określone, a Mapa bitowa nie została zainicjowana. Aby zainicjować mapę bitową, aplikacja może użyć funkcji, takiej jak funkcja [przechwytywania:: BitBlt](../../mfc/reference/cdc-class.md#bitblt) lub [SetDIBits](/windows/win32/api/wingdi/nf-wingdi-setdibits) , aby skopiować bity z mapy bitowej identyfikowanej przez pierwszy parametr `CGdiObject::GetObject` do mapy bitowej utworzonej przez `CreateBitmapIndirect` .

Po zakończeniu pracy z `CBitmap` obiektem utworzonym za pomocą `CreateBitmapIndirect` funkcji, najpierw wybierz mapę bitową z kontekstu urządzenia, a następnie usuń `CBitmap` obiekt.

## <a name="cbitmapcreatecompatiblebitmap"></a><a name="createcompatiblebitmap"></a> CBitmap:: CreateCompatibleBitmap

Inicjuje mapę bitową zgodną z urządzeniem określonym przez *kontroler PDC*.

```
BOOL CreateCompatibleBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
Określa kontekst urządzenia.

*nWidth*<br/>
Określa szerokość (w pikselach) mapy bitowej.

*nHeight*<br/>
Określa wysokość (w pikselach) mapy bitowej.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Mapa bitowa ma taką samą liczbę płaszczyzn kolorów lub ten sam format bitów na piksel co określony kontekst urządzenia. Można ją wybrać jako bieżącą mapę bitową dla każdego urządzenia pamięci, które jest zgodne z określonym przez *kontroler PDC*.

Jeśli *kontroler PDC* jest kontekstem urządzenia pamięci, zwracana Mapa bitowa ma taki sam format jak aktualnie wybrana Mapa bitowa w tym kontekście urządzenia. "Kontekst urządzenia pamięci" to blok pamięci reprezentujący powierzchnię wyświetlaną. Można go użyć do przygotowania obrazów w pamięci przed skopiowaniem ich do rzeczywistej powierzchni ekranu zgodnego urządzenia.

Po utworzeniu kontekstu urządzenia pamięci GDI automatycznie wybiera czarną mapę bitową.

Ponieważ kontekst urządzenia pamięci kolorowej może mieć wybrane kolory lub mapy bitowe, format mapy bitowej zwracanej przez `CreateCompatibleBitmap` funkcję nie zawsze jest taki sam, ale format zgodnej mapy bitowej dla kontekstu urządzenia niezwiązanego z pamięcią zawsze jest w formacie urządzenia.

Po zakończeniu pracy z `CBitmap` obiektem utworzonym za pomocą `CreateCompatibleBitmap` funkcji, najpierw wybierz mapę bitową z kontekstu urządzenia, a następnie usuń `CBitmap` obiekt.

## <a name="cbitmapcreatediscardablebitmap"></a><a name="creatediscardablebitmap"></a> CBitmap:: CreateDiscardableBitmap

Inicjuje mapę bitową, która jest zgodna z kontekstem urządzenia identyfikowanym przez *PDC*.

```
BOOL CreateDiscardableBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
Określa kontekst urządzenia.

*nWidth*<br/>
Określa szerokość mapy bitowej (w bitach).

*nHeight*<br/>
Określa wysokość (w bitach) mapy bitowej.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Mapa bitowa ma taką samą liczbę płaszczyzn kolorów lub ten sam format bitów na piksel co określony kontekst urządzenia. Aplikacja może wybrać tę mapę bitową jako bieżącą mapę bitową dla urządzenia pamięci, która jest zgodna z określonym przez *PDC*.

System Windows może odrzucić mapę bitową utworzoną przez tę funkcję tylko wtedy, gdy aplikacja nie została wybrana w kontekście wyświetlania. Jeśli system Windows odrzuci mapę bitową, gdy nie jest zaznaczona, a aplikacja później podejmie próbę jej zaznaczenia, funkcja [przechwytywania:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) zwróci wartość null.

Po zakończeniu pracy z `CBitmap` obiektem utworzonym za pomocą `CreateDiscardableBitmap` funkcji, najpierw wybierz mapę bitową z kontekstu urządzenia, a następnie usuń `CBitmap` obiekt.

## <a name="cbitmapfromhandle"></a><a name="fromhandle"></a> CBitmap:: FromHandle

Zwraca wskaźnik do obiektu, `CBitmap` gdy ma dojść do mapy bitowej interfejsu GDI systemu Windows.

```
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
Określa mapę bitową interfejsu GDI systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CBitmap` obiektu, jeśli się powiedzie; w przeciwnym razie wartość null.

### <a name="remarks"></a>Uwagi

Jeśli `CBitmap` obiekt nie jest jeszcze dołączony do dojścia, `CBitmap` tworzony jest obiekt tymczasowy i jest on dołączony. Ten `CBitmap` obiekt tymczasowy jest prawidłowy tylko do następnego czasu, gdy aplikacja ma czas bezczynności w pętli zdarzeń, podczas gdy wszystkie tymczasowe obiekty graficzne są usuwane. Innym sposobem wymawiania tego jest to, że obiekt tymczasowy jest prawidłowy tylko podczas przetwarzania jednego komunikatu w oknie.

## <a name="cbitmapgetbitmap"></a><a name="getbitmap"></a> CBitmap:: getmap

Pobiera właściwości obrazu dla dołączonej mapy bitowej.

```
int GetBitmap(BITMAP* pBitMap);
```

### <a name="parameters"></a>Parametry

*pBitMap*<br/>
Wskaźnik do struktury [mapy bitowej](/windows/win32/api/wingdi/ns-wingdi-bitmap) , która będzie odbierać właściwości obrazu. Ten parametr nie może mieć wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

## <a name="cbitmapgetbitmapbits"></a><a name="getbitmapbits"></a> CBitmap:: GetBitmapBits

Kopiuje wzorzec bitowy dołączonej mapy bitowej do określonego buforu.

```
DWORD GetBitmapBits(
    DWORD dwCount,
    LPVOID lpBits) const;
```

### <a name="parameters"></a>Parametry

*dwCount*<br/>
Liczba bajtów do skopiowania do buforu.

*lpBits*<br/>
Wskaźnik do buforu, który otrzyma mapę bitową.

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów skopiowanych do buforu, jeśli metoda zakończyła się pomyślnie. w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby określić wymagany rozmiar buforu, użyj [CBitmap:: Getmap bitowych](#getbitmap) .

## <a name="cbitmapgetbitmapdimension"></a><a name="getbitmapdimension"></a> CBitmap:: GetBitmapDimension

Zwraca szerokość i wysokość mapy bitowej.

```
CSize GetBitmapDimension() const;
```

### <a name="return-value"></a>Wartość zwracana

Szerokość i wysokość mapy bitowej mierzona w jednostkach 0,1 milimetrów. Wysokość znajduje się w `cy` elemencie członkowskim `CSize` obiektu, a szerokość znajduje się w `cx` elemencie członkowskim. Jeśli szerokość i wysokość mapy bitowej nie została ustawiona przy użyciu `SetBitmapDimension` , wartość zwracana wynosi 0.

### <a name="remarks"></a>Uwagi

Przyjęto, że wysokość i szerokość zostały ustawione wcześniej przy użyciu funkcji składowej [SetBitmapDimension](#setbitmapdimension) .

## <a name="cbitmaploadbitmap"></a><a name="loadbitmap"></a> CBitmap:: LoadBitmap

Ładuje zasób mapy bitowej o nazwie *lpszResourceName* lub identyfikowany przez numer identyfikacyjny w *nIDResource* pliku wykonywalnego aplikacji.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera nazwę zasobu mapy bitowej.

*nIDResource*<br/>
Określa numer identyfikatora zasobu mapy bitowej.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Załadowana Mapa bitowa jest dołączona do `CBitmap` obiektu.

Jeśli mapa bitowa identyfikowana przez *lpszResourceName* nie istnieje lub w przypadku niewystarczającej ilości pamięci do załadowania mapy bitowej, funkcja zwróci wartość 0.

Można użyć funkcji [CGdiObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) , aby usunąć mapę bitową załadowana przez `LoadBitmap` funkcję lub `CBitmap` destruktor usunie obiekt.

> [!CAUTION]
> Przed usunięciem obiektu upewnij się, że nie jest on zaznaczony w kontekście urządzenia.

Następujące mapy bitowe zostały dodane do systemu Windows w wersji 3,1 i nowszych:

OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI

Te mapy bitowe nie są dostępne w sterownikach urządzeń dla systemu Windows w wersji 3,0 i starszych. Aby uzyskać pełną listę map bitowych i wyświetlić ich wygląd, zobacz Windows SDK.

## <a name="cbitmaploadmappedbitmap"></a><a name="loadmappedbitmap"></a> CBitmap:: LoadMappedBitmap

Wywołaj tę funkcję elementu członkowskiego, aby załadować mapę bitową i zamapować kolory na bieżące kolory systemowe.

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
Flaga dla mapy bitowej. Może być równa zero lub CMB_MASKED.

*lpColorMap*<br/>
Wskaźnik do `COLORMAP` struktury zawierającej informacje o kolorach, które są konieczne do mapowania map bitowych. Jeśli ten parametr ma wartość NULL, funkcja używa domyślnej mapy kolorów.

*nMapSize*<br/>
Liczba map kolorów wskazywanych przez *lpColorMap*.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślnie program `LoadMappedBitmap` będzie mapować kolory często używane w glifach przycisków.

Aby uzyskać informacje na temat tworzenia mapowanej mapy bitowej, zobacz funkcję systemu Windows [CreateMappedBitmap](https://go.microsoft.com/fwlink/p/?linkid=230562) i strukturę [COLORMAP](/windows/win32/api/commctrl/ns-commctrl-colormap) w Windows SDK.

## <a name="cbitmaploadoembitmap"></a><a name="loadoembitmap"></a> CBitmap:: LoadOEMBitmap

Ładuje wstępnie zdefiniowaną mapę bitową używaną przez system Windows.

```
BOOL LoadOEMBitmap(UINT nIDBitmap);
```

### <a name="parameters"></a>Parametry

*nIDBitmap*<br/>
Numer IDENTYFIKACYJNy wstępnie zdefiniowanej mapy bitowej systemu Windows. Możliwe wartości są wymienione poniżej w systemie WINDOWS. C

:::row:::
   :::column span="":::
      OBM_BTNCORNERS \
      OBM_BTSIZE \
      OBM_CHECK \
      OBM_CHECKBOXES \
      OBM_CLOSE \
      OBM_COMBO \
      OBM_DNARROW \
      OBM_DNARROWD \
      OBM_DNARROWI \
      OBM_LFARROW \
      OBM_LFARROWD \
      OBM_LFARROWI
   :::column-end:::
   :::column span="":::
      OBM_MNARROW \
      OBM_OLD_CLOSE \
      OBM_OLD_DNARROW \
      OBM_OLD_LFARROW \
      OBM_OLD_REDUCE \
      OBM_OLD_RESTORE \
      OBM_OLD_RGARROW \
      OBM_OLD_UPARROW \
      OBM_OLD_ZOOM \
      OBM_REDUCE \
      OBM_REDUCED
   :::column-end:::
   :::column span="":::
      OBM_RESTORE \
      OBM_RESTORED \
      OBM_RGARROW \
      OBM_RGARROWD \
      OBM_RGARROWI \
      OBM_SIZE \
      OBM_UPARROW \
      OBM_UPARROW \
      OBM_UPARROWD \
      OBM_ZOOM \
      OBM_ZOOMD
   :::column-end:::
:::row-end:::

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Nazwy map bitowych zaczynające się od OBM_OLD reprezentują mapy bitowe używane przez wersje systemu Windows przed 3,0.

Należy pamiętać, że stała OEMRESOURCE musi być zdefiniowana przed dołączeniem systemu WINDOWS. H, aby użyć dowolnych stałych **OBM_** .

## <a name="cbitmapoperator-hbitmap"></a><a name="operator_hbitmap"></a> CBitmap:: operator HBITMAP

Użyj tego operatora, aby uzyskać dojście do dołączonego interfejsu GDI systemu Windows `CBitmap` .

```
operator HBITMAP() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, dojście do obiektu GDI systemu Windows reprezentowane przez `CBitmap` obiekt; w przeciwnym razie wartość null.

### <a name="remarks"></a>Uwagi

Ten operator jest operatorem rzutowania, który obsługuje bezpośrednie użycie `HBITMAP` obiektu.

Aby uzyskać więcej informacji na temat używania obiektów graficznych, zobacz temat [obiekty graficzne](/windows/win32/gdi/graphic-objects) w Windows SDK.

## <a name="cbitmapsetbitmapbits"></a><a name="setbitmapbits"></a> CBitmap:: SetBitmapBits

Ustawia bity mapy bitowej na wartości bitowe podane przez *lpBits*.

```
DWORD SetBitmapBits(
    DWORD dwCount,
    const void* lpBits);
```

### <a name="parameters"></a>Parametry

*dwCount*<br/>
Określa liczbę bajtów wskazywanych przez *lpBits*.

*lpBits*<br/>
Wskazuje tablicę bajtów zawierającą wartości pikseli, które mają zostać skopiowane do `CBitmap` obiektu. Aby Mapa bitowa mogła prawidłowo renderować swój obraz, wartości powinny być sformatowane tak, aby były zgodne z wartościami głębokości, szerokości i koloru, które zostały określone podczas tworzenia wystąpienia CBitmap. Aby uzyskać więcej informacji, zobacz [CBitmap:: ismap](#createbitmap).

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów używanych podczas ustawiania bitów mapy bitowej; 0, jeśli funkcja nie powiedzie się.

## <a name="cbitmapsetbitmapdimension"></a><a name="setbitmapdimension"></a> CBitmap:: SetBitmapDimension

Przypisuje szerokość i wysokość do mapy bitowej w jednostkach 0,1 milimetrów.

```
CSize SetBitmapDimension(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
Określa szerokość mapy bitowej (w jednostkach 0,1 milimetrów).

*nHeight*<br/>
Określa wysokość mapy bitowej (w jednostkach 0,1 milimetrów).

### <a name="return-value"></a>Wartość zwracana

Poprzednie wymiary mapy bitowej. Wysokość znajduje się w `cy` zmiennej składowej `CSize` obiektu, a szerokość znajduje się w `cx` zmiennej składowej.

### <a name="remarks"></a>Uwagi

Interfejs GDI nie używa tych wartości z wyjątkiem powrotu, gdy aplikacja wywołuje funkcję członkowską [GetBitmapDimension](#getbitmapdimension) .

## <a name="see-also"></a>Zobacz też

[Przykładowy interfejs MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CGdiObject](../../mfc/reference/cgdiobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
