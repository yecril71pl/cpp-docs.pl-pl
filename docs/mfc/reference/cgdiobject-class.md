---
title: Klasa CGdiObject
ms.date: 11/04/2016
f1_keywords:
- CGdiObject
- AFXWIN/CGdiObject
- AFXWIN/CGdiObject::CGdiObject
- AFXWIN/CGdiObject::Attach
- AFXWIN/CGdiObject::CreateStockObject
- AFXWIN/CGdiObject::DeleteObject
- AFXWIN/CGdiObject::DeleteTempMap
- AFXWIN/CGdiObject::Detach
- AFXWIN/CGdiObject::FromHandle
- AFXWIN/CGdiObject::GetObject
- AFXWIN/CGdiObject::GetObjectType
- AFXWIN/CGdiObject::GetSafeHandle
- AFXWIN/CGdiObject::UnrealizeObject
- AFXWIN/CGdiObject::m_hObject
helpviewer_keywords:
- CGdiObject [MFC], CGdiObject
- CGdiObject [MFC], Attach
- CGdiObject [MFC], CreateStockObject
- CGdiObject [MFC], DeleteObject
- CGdiObject [MFC], DeleteTempMap
- CGdiObject [MFC], Detach
- CGdiObject [MFC], FromHandle
- CGdiObject [MFC], GetObject
- CGdiObject [MFC], GetObjectType
- CGdiObject [MFC], GetSafeHandle
- CGdiObject [MFC], UnrealizeObject
- CGdiObject [MFC], m_hObject
ms.assetid: 1cba3ba5-3d49-4e43-8293-209299f2f6f4
ms.openlocfilehash: 87545d67addb6a1f0931007d8912989968f7a74a
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53177852"
---
# <a name="cgdiobject-class"></a>Klasa CGdiObject

Udostępnia klasę bazową dla różnych rodzajów grafiki Windows obiekty interface (GDI) urządzenia, takie jak mapy bitowe, regiony, pędzle, pióra, palety i czcionki.

## <a name="syntax"></a>Składnia

```
class CGdiObject : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGdiObject::CGdiObject](#cgdiobject)|Konstruuje `CGdiObject` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGdiObject::Attach](#attach)|Dołącza obiekt Windows GDI, aby `CGdiObject` obiektu.|
|[CGdiObject::CreateStockObject](#createstockobject)|Pobiera uchwyt do Windows wstępnie zdefiniowanych standardowych pióra, Pędzle lub czcionki.|
|[CGdiObject::DeleteObject](#deleteobject)|Usuwa obiekt Windows GDI dołączony do `CGdiObject` obiekt z pamięci przez zwolnienie wszystkich magazynów systemu skojarzony z obiektem.|
|[CGdiObject::DeleteTempMap](#deletetempmap)|Usuwa wszystkie tymczasowe `CGdiObject` obiekty utworzone przez `FromHandle`.|
|[CGdiObject::Detach](#detach)|Odłącza obiekt Windows GDI, od `CGdiObject` obiektu i zwraca uchwyt do obiektu Windows GDI.|
|[CGdiObject::FromHandle](#fromhandle)|Zwraca wskaźnik do `CGdiObject` obiektu, biorąc pod uwagę uchwyt do obiektu Windows GDI.|
|[CGdiObject::GetObject](#getobject)|Wypełnia buforów z danymi, opisujący obiekt Windows GDI dołączonych do `CGdiObject` obiektu.|
|[CGdiObject::GetObjectType](#getobjecttype)|Pobiera typ obiektu interfejsu GDI.|
|[CGdiObject::GetSafeHandle](#getsafehandle)|Zwraca `m_hObject` chyba że **to** ma wartość NULL, w której jest zwracana wartość case NULL.|
|[CGdiObject::UnrealizeObject](#unrealizeobject)|Resetuje pochodzenia pędzla lub resetuje palety logiczne.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGdiObject::operator! =](#operator_neq)|Określa, czy dwa obiekty GDI logicznie nie są równe.|
|[CGdiObject::operator ==](#operator_eq_eq)|Określa, czy dwa obiekty GDI są logicznie równe.|
|[CGdiObject::operator HGDIOBJ](#operator_hgdiobj)|Pobiera UCHWYT do obiektu Windows GDI dołączone.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CGdiObject::m_hObject](#m_hobject)|UCHWYT zawierający HBITMAP, HPALETTE, hrgn — HBRUSH, hpen — lub HFONT dołączony do tego obiektu.|

## <a name="remarks"></a>Uwagi

Nigdy nie twórz `CGdiObject` bezpośrednio. Zamiast tworzenia obiektu z jednego z jej klas pochodnych, takich jak `CPen` lub `CBrush`.

Aby uzyskać więcej informacji na temat `CGdiObject`, zobacz [obiektów graficznych](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CGdiObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="attach"></a>  CGdiObject::Attach

Dołącza obiekt Windows GDI, aby `CGdiObject` obiektu.

```
BOOL Attach(HGDIOBJ hObject);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
DOJŚCIE do obiektu Windows GDI (na przykład hpen — lub HBRUSH).

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli kończy się pomyślnie; załącznika w przeciwnym razie 0.

##  <a name="cgdiobject"></a>  CGdiObject::CGdiObject

Konstruuje `CGdiObject` obiektu.

```
CGdiObject();
```

### <a name="remarks"></a>Uwagi

Nigdy nie twórz `CGdiObject` bezpośrednio. Zamiast tworzenia obiektu z jednego z jej klas pochodnych, takich jak `CPen` lub `Cbrush`.

##  <a name="createstockobject"></a>  CGdiObject::CreateStockObject

Pobiera dojścia do jednego z wstępnie zdefiniowanych standardowych pióra Windows GDI, Pędzle lub czcionek i dołącza obiektu GDI `CGdiObject` obiektu.

```
BOOL CreateStockObject(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określanie typu podstawowego obiektu żądanego stała. Zobacz parametr *fnObject* dla [GetStockObject](/windows/desktop/api/wingdi/nf-wingdi-getstockobject) w zestawie Windows SDK opis odpowiednie wartości.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji przy użyciu jednego z pochodnej klasy, która odnosi się do typu obiektu interfejsu GDI Windows, takich jak `CPen` podstawowe pióra.

##  <a name="deleteobject"></a>  CGdiObject::DeleteObject

Usuwa przyłączonego obiektu Windows GDI z pamięci, zwalniając cały magazyn systemu skojarzony z obiektem Windows GDI.

```
BOOL DeleteObject();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli obiekt GDI został pomyślnie usunięty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Magazyn skojarzony z `CGdiObject` obiektu nie dotyczy to wywołanie. Aplikacja nie powinien wywoływać `DeleteObject` na `CGdiObject` obiektu, który jest aktualnie wybrany do kontekstu urządzenia.

Po usunięciu pędzla wzoru mapy bitowej skojarzone z pędzel nie zostanie usunięty. Mapy bitowej muszą zostać usunięte niezależnie.

##  <a name="deletetempmap"></a>  CGdiObject::DeleteTempMap

Wywoływana automatycznie przez `CWinApp` obsługi czasu bezczynności `DeleteTempMap` usuwa wszystkie tymczasowe `CGdiObject` obiekty utworzone przez `FromHandle`.

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Uwagi

`DeleteTempMap` Odłącza obiekt Windows GDI dołączona do tymczasowej `CGdiObject` obiekt przed usunięciem `CGdiObject` obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]

##  <a name="detach"></a>  CGdiObject::Detach

Odłącza obiekt Windows GDI, od `CGdiObject` obiektu i zwraca uchwyt do obiektu Windows GDI.

```
HGDIOBJ Detach();
```

### <a name="return-value"></a>Wartość zwracana

A `HANDLE` do Windows GDI obiekt o odłączony; w przeciwnym razie wartość NULL, jeśli żaden obiekt interfejsu GDI nie jest dołączony.

##  <a name="fromhandle"></a>  CGdiObject::FromHandle

Zwraca wskaźnik do `CGdiObject` obiektu, biorąc pod uwagę uchwyt do obiektu Windows GDI.

```
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
DOJŚCIE do obiektu Windows GDI.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CGdiObject` może to być tymczasowy lub stały.

### <a name="remarks"></a>Uwagi

Jeśli `CGdiObject` obiekt nie jest już dołączony do obiektu Windows GDI tymczasowego `CGdiObject` obiekt zostanie utworzony i dołączony.

Ten tymczasowy `CGdiObject` obiektu jest prawidłowa tylko dopóki aplikacja ma czas bezczynności w jego pętlę zdarzeń, które zostaną usunięte wszystkie tymczasowe obiekty graficzne. Innymi słowy to to, że tymczasowy obiekt jest prawidłowy tylko podczas przetwarzania komunikatu w jednym oknie.

##  <a name="getobject"></a>  CGdiObject::GetObject

Wypełnia bufor danych, który definiuje określonego obiektu.

```
int GetObject(
    int nCount,
    LPVOID lpObject) const;
```

### <a name="parameters"></a>Parametry

*nCount*<br/>
Określa liczbę bajtów do skopiowania do *lpObject* buforu.

*lpObject*<br/>
Wskazuje buforu dostarczone przez użytkownika, który ma otrzymać informacje.

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów pobrane; w przeciwnym razie 0, jeśli błąd występuje.

### <a name="remarks"></a>Uwagi

Funkcja pobiera strukturę danych, którego typ zależy od typu obiektu graficznego pokazany na poniższej liście:

|Obiekt|Typ buforu|
|------------|-----------------|
|`CPen`|[LOGPEN](/windows/desktop/api/Wingdi/ns-wingdi-taglogpen)|
|`CBrush`|[LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush)|
|`CFont`|[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)|
|`CBitmap`|[MAPY BITOWEJ](/windows/desktop/api/wingdi/ns-wingdi-tagbitmap)|
|`CPalette`|WORD|
|`CRgn`|Nieobsługiwane|

Jeśli obiekt jest `CBitmap` obiektu `GetObject` zwraca tylko szerokość, wysokość i informacji o formacie kolorów mapy bitowej. Liczbę bitów mogą być pobierane przy użyciu [CBitmap::GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits).

Jeśli obiekt jest `CPalette` obiektu `GetObject` pobiera słowo, które określa liczbę wpisów z palety. Funkcja nie pobiera pożądanych [LOGPALETTE](/windows/desktop/api/wingdi/ns-wingdi-taglogpalette) strukturę, która definiuje palety. Aplikację można uzyskać informacji na temat wpisy palety, wywołując [CPalette::GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries).

##  <a name="getobjecttype"></a>  CGdiObject::GetObjectType

Pobiera typ obiektu interfejsu GDI.

```
UINT GetObjectType() const;
```

### <a name="return-value"></a>Wartość zwracana

Typ obiektu, jeśli to się powiedzie; w przeciwnym razie 0. Wartość może być jedną z następujących czynności:

- OBJ_BITMAP mapy bitowej

- OBJ_BRUSH pędzla

- Czcionka OBJ_FONT

- OBJ_PAL palety

- OBJ_PEN pióra

- Rozszerzony OBJ_EXTPEN pióra

- OBJ_REGION Region

- Kontekst urządzenia OBJ_DC

- Kontekst urządzenia OBJ_MEMDC pamięci

- OBJ_METAFILE metaplik

- Kontekście urządzenia metaplików OBJ_METADC

- OBJ_ENHMETAFILE rozszerzonych metaplików

- Kontekst urządzenia rozszerzony metaplik OBJ_ENHMETADC

##  <a name="getsafehandle"></a>  CGdiObject::GetSafeHandle

Zwraca `m_hObject` chyba że **to** ma wartość NULL, w której jest zwracana wartość case NULL.

```
HGDIOBJ GetSafeHandle() const;
```

### <a name="return-value"></a>Wartość zwracana

DOJŚCIE do przyłączonego obiektu Windows GDI; w przeciwnym razie wartość NULL, jeśli żaden obiekt nie jest dołączony.

### <a name="remarks"></a>Uwagi

To jest częścią modelu interfejsu ogólnego dojścia i jest przydatne, gdy wartość NULL jest nieprawidłowa lub specjalne wartość dojścia.

### <a name="example"></a>Przykład

  Zobacz przykład [CWnd::IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled).

##  <a name="m_hobject"></a>  CGdiObject::m_hObject

UCHWYT zawierający HBITMAP, hrgn —, HBRUSH hpen —, HPALETTE lub HFONT dołączony do tego obiektu.

```
HGDIOBJ m_hObject;
```

##  <a name="operator_neq"></a>  CGdiObject::operator! =

Określa, czy dwa obiekty GDI logicznie nie są równe.

```
BOOL operator!=(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Parametry

*obj*<br/>
Wskaźnik do istniejącego `CGdiObject`.

### <a name="remarks"></a>Uwagi

Określa, jeśli obiekt GDI po lewej stronie nie jest równy obiektowi GDI po prawej stronie.

##  <a name="operator_eq_eq"></a>  CGdiObject::operator ==

Określa, czy dwa obiekty GDI są logicznie równe.

```
BOOL operator==(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Parametry

*obj*<br/>
Odwołanie do istniejącego `CGdiObject`.

### <a name="remarks"></a>Uwagi

Określa, czy obiekt GDI po lewej stronie równy obiektowi GDI po prawej stronie.

##  <a name="operator_hgdiobj"></a>  CGdiObject::operator HGDIOBJ

Pobiera UCHWYT do obiektu dołączonego Windows GDI; w przeciwnym razie wartość NULL, jeśli żaden obiekt nie jest dołączony.

```
operator HGDIOBJ() const;
```

##  <a name="unrealizeobject"></a>  CGdiObject::UnrealizeObject

Resetuje pochodzenia pędzla lub resetuje palety logiczne.

```
BOOL UnrealizeObject();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Gdy `UnrealizeObject` jest funkcją składową z `CGdiObject` klasy, jego powinny być używane tylko na `CBrush` lub `CPalette` obiektów.

Aby uzyskać `CBrush` obiektów, `UnrealizeObject` instruuje system, aby zresetować pochodzenia danego pędzla następnym razem, jest ono zaznaczone do kontekstu urządzenia. Jeśli obiekt jest `CPalette` obiektu `UnrealizeObject` poleca systemowi sobie sprawę z palety, tak, jakby nie było wcześniej zrealizowane. Przy następnym aplikacja wywołuje [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette) funkcji na palecie określony system całkowicie ponownie mapuje logiczną paletę do palety systemu.

`UnrealizeObject` Nie należy używać funkcji przy użyciu standardowych obiektów. `UnrealizeObject` Zawsze wtedy, gdy ustawiono nowe źródła pędzla należy wywołać funkcję (przez [CDC::SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg) funkcji). `UnrealizeObject` Funkcji nie może być wywoływana dla aktualnie wybrany pędzel lub aktualnie wybranego paletę wszystkich kontekstach wyświetlania.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CBitmap](../../mfc/reference/cbitmap-class.md)<br/>
[Klasa CBrush](../../mfc/reference/cbrush-class.md)<br/>
[Klasa CFont](../../mfc/reference/cfont-class.md)<br/>
[Klasa CPalette](../../mfc/reference/cpalette-class.md)<br/>
[Klasa CPen](../../mfc/reference/cpen-class.md)<br/>
[Klasa CRgn](../../mfc/reference/crgn-class.md)
