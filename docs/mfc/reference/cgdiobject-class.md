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
ms.openlocfilehash: 0cd7a0e0ed500ee9394b00e8906640e9f950163b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373738"
---
# <a name="cgdiobject-class"></a>Klasa CGdiObject

Zapewnia klasę podstawową dla różnych rodzajów obiektów interfejsu urządzenia graficznego systemu Windows (GDI), takich jak mapy bitowe, regiony, pędzle, pióra, palety i czcionki.

## <a name="syntax"></a>Składnia

```
class CGdiObject : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGdiObject::CGdiObject](#cgdiobject)|Konstruuje `CGdiObject` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGdiObject::Dołącz](#attach)|Dołącza obiekt GDI systemu `CGdiObject` Windows do obiektu.|
|[CGdiObject::CreateStockObject](#createstockobject)|Pobiera uchwyt do jednego ze wstępnie zdefiniowanych piór, pędzli lub czcionek systemu Windows.|
|[CGdiObject::DeleteObject](#deleteobject)|Usuwa obiekt GDI systemu Windows `CGdiObject` dołączony do obiektu z pamięci, zwalniając całą pamięć systemową skojarzoną z obiektem.|
|[CGdiObject::DeleteTempMap](#deletetempmap)|Usuwa wszystkie `CGdiObject` obiekty tymczasowe `FromHandle`utworzone przez plik .|
|[CGdiObject::Detach](#detach)|Odłącza obiekt GDI systemu `CGdiObject` Windows od obiektu i zwraca dojście do obiektu GDI systemu Windows.|
|[CGdiObject::OdHandle](#fromhandle)|Zwraca wskaźnik do `CGdiObject` obiektu, do który doz.|
|[CGdiObject::GetObject](#getobject)|Wypełnia bufor danymi opisującymi obiekt GDI systemu Windows `CGdiObject` dołączony do obiektu.|
|[CGdiObject::GetObjectType](#getobjecttype)|Pobiera typ obiektu GDI.|
|[CGdiObject::GetSafeHandle](#getsafehandle)|Zwraca, `m_hObject` chyba że jest to null, w którym **to** przypadku null jest zwracany.|
|[CGdiObject::UnrealizeObject](#unrealizeobject)|Resetuje początek pędzla lub resetuje paletę logiczną.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGdiObject::operator !=](#operator_neq)|Określa, czy dwa obiekty GDI logicznie nie są równe.|
|[CGdiObject::operator ==](#operator_eq_eq)|Określa, czy dwa obiekty GDI są logicznie równe.|
|[CGdiObject::operator HGDIOBJ](#operator_hgdiobj)|Pobiera handle do dołączonego obiektu GDI systemu Windows.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CGdiObject::m_hObject](#m_hobject)|Uchwyt zawierający HBITMAP, HPALETTE, HRGN, HBRUSH, HPEN lub HFONT dołączony do tego obiektu.|

## <a name="remarks"></a>Uwagi

Nigdy nie `CGdiObject` tworzysz bezpośrednio. Zamiast tego można utworzyć obiekt z jednej z `CPen` jego `CBrush`klas pochodnych, takich jak lub .

Aby uzyskać `CGdiObject`więcej informacji na temat , zobacz [Obiekty graficzne](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CGdiObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cgdiobjectattach"></a><a name="attach"></a>CGdiObject::Dołącz

Dołącza obiekt GDI systemu `CGdiObject` Windows do obiektu.

```
BOOL Attach(HGDIOBJ hObject);
```

### <a name="parameters"></a>Parametry

*hObiekt*<br/>
Dojem do obiektu GDI systemu Windows (na przykład HPEN lub HBRUSH).

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli przywiązanie zakończy się powodzeniem; w przeciwnym razie 0.

## <a name="cgdiobjectcgdiobject"></a><a name="cgdiobject"></a>CGdiObject::CGdiObject

Konstruuje `CGdiObject` obiekt.

```
CGdiObject();
```

### <a name="remarks"></a>Uwagi

Nigdy nie `CGdiObject` tworzysz bezpośrednio. Zamiast tego można utworzyć obiekt z jednej z `CPen` jego `Cbrush`klas pochodnych, takich jak lub .

## <a name="cgdiobjectcreatestockobject"></a><a name="createstockobject"></a>CGdiObject::CreateStockObject

Pobiera dojście do jednego ze wstępnie zdefiniowanych czasowych piór, pędzli lub czcionek GDI `CGdiObject` systemu Windows i dołącza obiekt GDI do obiektu.

```
BOOL CreateStockObject(int nIndex);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Stała określająca typ żądanego obiektu giełdowego. Opis odpowiednich wartości można znaleźć w parametrze *fnObject* for [GetStockObject](/windows/win32/api/wingdi/nf-wingdi-getstockobject) w usłudze Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji z jedną z klas pochodnych, która odpowiada typowi obiektu GDI systemu Windows, na przykład `CPen` dla pióra giełdowego.

## <a name="cgdiobjectdeleteobject"></a><a name="deleteobject"></a>CGdiObject::DeleteObject

Usuwa dołączony obiekt GDI systemu Windows z pamięci, zwalniając całą pamięć systemową skojarzoną z obiektem GDI systemu Windows.

```
BOOL DeleteObject();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli obiekt GDI został pomyślnie usunięty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ten wywołanie nie `CGdiObject` ma wpływu na magazyn skojarzony z obiektem. Aplikacja nie powinna `DeleteObject` wywoływać `CGdiObject` obiektu, który jest aktualnie wybrany w kontekście urządzenia.

Po usunięciu pędzla wzorka mapa bitowa skojarzona z pędzlem nie jest usuwana. Mapa bitowa musi zostać usunięta niezależnie.

## <a name="cgdiobjectdeletetempmap"></a><a name="deletetempmap"></a>CGdiObject::DeleteTempMap

Wywoływane automatycznie `CWinApp` przez program obsługi czasu `DeleteTempMap` bezczynności, `CGdiObject` usuwa `FromHandle`wszystkie obiekty tymczasowe utworzone przez program .

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Uwagi

`DeleteTempMap`Odłącza obiekt GDI systemu Windows `CGdiObject` dołączony do obiektu `CGdiObject` tymczasowego przed usunięciem obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]

## <a name="cgdiobjectdetach"></a><a name="detach"></a>CGdiObject::Detach

Odłącza obiekt GDI systemu `CGdiObject` Windows od obiektu i zwraca dojście do obiektu GDI systemu Windows.

```
HGDIOBJ Detach();
```

### <a name="return-value"></a>Wartość zwracana

A `HANDLE` do obiektu GDI systemu Windows odłączony; w przeciwnym razie NULL, jeśli nie jest dołączony żaden obiekt GDI.

## <a name="cgdiobjectfromhandle"></a><a name="fromhandle"></a>CGdiObject::OdHandle

Zwraca wskaźnik do `CGdiObject` obiektu, do który doz.

```
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```

### <a name="parameters"></a>Parametry

*hObiekt*<br/>
Dojem do obiektu GDI systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CGdiObject` a, który może być tymczasowy lub stały.

### <a name="remarks"></a>Uwagi

Jeśli `CGdiObject` obiekt nie jest jeszcze dołączony do obiektu GDI systemu Windows, tworzony i dołączany jest obiekt tymczasowy. `CGdiObject`

Ten `CGdiObject` obiekt tymczasowy jest prawidłowy tylko do następnego czasu, gdy aplikacja ma czas bezczynny w pętli zdarzeń, w którym to czasie wszystkie tymczasowe obiekty graficzne są usuwane. Innym sposobem mówienia jest to, że obiekt tymczasowy jest prawidłowy tylko podczas przetwarzania komunikatu okna.

## <a name="cgdiobjectgetobject"></a><a name="getobject"></a>CGdiObject::GetObject

Wypełnia bufor danymi definiuucyja określony obiekt.

```
int GetObject(
    int nCount,
    LPVOID lpObject) const;
```

### <a name="parameters"></a>Parametry

*Ncount*<br/>
Określa liczbę bajtów do skopiowania do buforu *lpObject.*

*lpObject*<br/>
Wskazuje bufor dostarczony przez użytkownika, który ma odbierać informacje.

### <a name="return-value"></a>Wartość zwracana

Liczba pobranych bajtów; w przeciwnym razie 0, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Funkcja pobiera strukturę danych, której typ zależy od typu obiektu graficznego, jak pokazano na poniższej liście:

|Obiekt|Typ buforu|
|------------|-----------------|
|`CPen`|[ODTWÓR Z REJESTRATORA](/windows/win32/api/Wingdi/ns-wingdi-logpen)|
|`CBrush`|[LOGBRUSH (LOGBRUSH)](/windows/win32/api/wingdi/ns-wingdi-logbrush)|
|`CFont`|[Logfont](/windows/win32/api/wingdi/ns-wingdi-logfontw)|
|`CBitmap`|[Bitmapy](/windows/win32/api/wingdi/ns-wingdi-bitmap)|
|`CPalette`|WORD|
|`CRgn`|Nieobsługiwane|

Jeśli obiekt jest `CBitmap` obiektem, `GetObject` zwraca tylko informacje o szerokości, wysokości i formacie kolorów mapy bitowej. Rzeczywiste bity można pobrać za pomocą [CBitmap::GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits).

Jeśli obiekt jest `CPalette` obiektem, `GetObject` pobiera program WORD określający liczbę wpisów w palecie. Funkcja nie pobiera struktury [LOGPALETTE,](/windows/win32/api/wingdi/ns-wingdi-logpalette) która definiuje paletę. Aplikacja może uzyskać informacje na temat wpisów palety, dzwoniąc [CPalette::GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries).

## <a name="cgdiobjectgetobjecttype"></a><a name="getobjecttype"></a>CGdiObject::GetObjectType

Pobiera typ obiektu GDI.

```
UINT GetObjectType() const;
```

### <a name="return-value"></a>Wartość zwracana

Typ obiektu, jeśli zakończy się pomyślnie; w przeciwnym razie 0. Może to być jedna z następujących wartości:

- OBJ_BITMAP bitmapa

- Pędzel OBJ_BRUSH

- Czcionka OBJ_FONT

- Paleta OBJ_PAL

- Pióro OBJ_PEN

- OBJ_EXTPEN Długopis rozszerzony

- OBJ_REGION Region

- Kontekst OBJ_DC urządzenia

- OBJ_MEMDC kontekście urządzenia pamięci

- OBJ_METAFILE Metafile

- kontekst urządzenia OBJ_METADC Metafile

- OBJ_ENHMETAFILE Ulepszony metaplik

- OBJ_ENHMETADC kontekst urządzenia z ulepszoną metapliką

## <a name="cgdiobjectgetsafehandle"></a><a name="getsafehandle"></a>CGdiObject::GetSafeHandle

Zwraca, `m_hObject` chyba że jest to null, w którym **to** przypadku null jest zwracany.

```
HGDIOBJ GetSafeHandle() const;
```

### <a name="return-value"></a>Wartość zwracana

A HANDLE do dołączonego obiektu GDI systemu Windows; w przeciwnym razie NULL, jeśli żaden obiekt nie jest dołączony.

### <a name="remarks"></a>Uwagi

Jest to część ogólnego paradygmatu interfejsu dojścia i jest przydatne, gdy NULL jest prawidłową lub specjalną wartością dla dojścia.

### <a name="example"></a>Przykład

  Zobacz przykład [CWnd::IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled).

## <a name="cgdiobjectm_hobject"></a><a name="m_hobject"></a>CGdiObject::m_hObject

Uchwyt zawierający HBITMAP, HRGN, HBRUSH, HPEN, HPALETTE lub HFONT dołączony do tego obiektu.

```
HGDIOBJ m_hObject;
```

## <a name="cgdiobjectoperator-"></a><a name="operator_neq"></a>CGdiObject::operator !=

Określa, czy dwa obiekty GDI logicznie nie są równe.

```
BOOL operator!=(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Parametry

*Obj*<br/>
Wskaźnik do istniejącego `CGdiObject`pliku .

### <a name="remarks"></a>Uwagi

Określa, czy obiekt GDI po lewej stronie nie jest równy obiektowi GDI po prawej stronie.

## <a name="cgdiobjectoperator-"></a><a name="operator_eq_eq"></a>CGdiObject::operator ==

Określa, czy dwa obiekty GDI są logicznie równe.

```
BOOL operator==(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Parametry

*Obj*<br/>
Odwołanie do istniejącego `CGdiObject`pliku .

### <a name="remarks"></a>Uwagi

Określa, czy obiekt GDI po lewej stronie jest równy obiektowi GDI po prawej stronie.

## <a name="cgdiobjectoperator-hgdiobj"></a><a name="operator_hgdiobj"></a>CGdiObject::operator HGDIOBJ

Pobiera handle do dołączonego obiektu GDI systemu Windows; w przeciwnym razie NULL, jeśli żaden obiekt nie jest dołączony.

```
operator HGDIOBJ() const;
```

## <a name="cgdiobjectunrealizeobject"></a><a name="unrealizeobject"></a>CGdiObject::UnrealizeObject

Resetuje początek pędzla lub resetuje paletę logiczną.

```
BOOL UnrealizeObject();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Chociaż `UnrealizeObject` jest funkcją `CGdiObject` elementu członkowskiego klasy, należy `CBrush` wywołać tylko na lub `CPalette` obiektów.

W `CBrush` przypadku `UnrealizeObject` obiektów kieruje system do resetowania początku danego pędzla przy następnym wybraniu go w kontekście urządzenia. Jeśli obiekt jest `CPalette` obiektem, `UnrealizeObject` kieruje system do realizacji palety tak, jakby nie została wcześniej zrealizowana. Następnym razem, gdy aplikacja wywołuje [cdc::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette) funkcji dla określonej palety, system całkowicie ponownie mapuje paletę logiczną do palety systemu.

Funkcja `UnrealizeObject` nie powinna być używana z obiektami giełdowymi. Funkcja `UnrealizeObject` musi być wywoływana za każdym razem, gdy ustawiono nowe pochodzenie pędzla (za pomocą funkcji [CDC::SetBrushOrg).](../../mfc/reference/cdc-class.md#setbrushorg) Nie `UnrealizeObject` można wywołać funkcji dla aktualnie wybranego pędzla lub aktualnie wybranej palety dowolnego kontekstu wyświetlania.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CBitmap](../../mfc/reference/cbitmap-class.md)<br/>
[Klasa CBrush](../../mfc/reference/cbrush-class.md)<br/>
[Klasa CFont](../../mfc/reference/cfont-class.md)<br/>
[Klasa CPalette](../../mfc/reference/cpalette-class.md)<br/>
[Klasa CPen](../../mfc/reference/cpen-class.md)<br/>
[Klasa CRgn](../../mfc/reference/crgn-class.md)
