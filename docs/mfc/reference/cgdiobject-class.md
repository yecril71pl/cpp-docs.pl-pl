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
ms.openlocfilehash: ea82e2c667dcbd476d22ed23085d409b448b27ed
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506257"
---
# <a name="cgdiobject-class"></a>Klasa CGdiObject

Udostępnia klasę bazową dla różnych rodzajów obiektów interfejsu urządzenia graficznego (GDI) systemu Windows, takich jak mapy bitowe, regiony, pędzle, pióra, palety i czcionki.

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
|[CGdiObject:: Attach](#attach)|Dołącza obiekt GDI systemu Windows do `CGdiObject` obiektu.|
|[CGdiObject::](#createstockobject)|Pobiera dojście do jednego z wstępnie zdefiniowanych piór, pędzli lub czcionek systemu Windows.|
|[CGdiObject::D eleteObject](#deleteobject)|Usuwa obiekt GDI systemu Windows dołączony do `CGdiObject` obiektu z pamięci, zwalniając wszystkie magazyny systemowe skojarzone z obiektem.|
|[CGdiObject::DeleteTempMap](#deletetempmap)|Usuwa wszystkie obiekty `CGdiObject` tymczasowe utworzone przez `FromHandle`.|
|[CGdiObject::Detach](#detach)|Odłącza obiekt interfejsu GDI systemu Windows z `CGdiObject` obiektu i zwraca dojście do obiektu GDI systemu Windows.|
|[CGdiObject::FromHandle](#fromhandle)|Zwraca wskaźnik do `CGdiObject` obiektu, który ma dojście do obiektu GDI systemu Windows.|
|[CGdiObject:: GetObject](#getobject)|Wypełnia bufor danymi opisującymi obiekt GDI systemu Windows dołączony do `CGdiObject` obiektu.|
|[CGdiObject:: GetObjectType](#getobjecttype)|Pobiera typ obiektu GDI.|
|[CGdiObject:: GetSafeHandle](#getsafehandle)|Zwraca `m_hObject` wartość, chyba że jest **to** wartość null, a w tym przypadku zwracana jest wartość null.|
|[CGdiObject:: unzrozumieobject](#unrealizeobject)|Resetuje początek pędzla lub resetuje paletę logiczną.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGdiObject:: operator! =](#operator_neq)|Określa, czy dwa obiekty GDI są logicznie nierówne.|
|[CGdiObject:: operator = =](#operator_eq_eq)|Określa, czy dwa obiekty GDI są logicznie równe.|
|[CGdiObject:: operator HGDIOBJ](#operator_hgdiobj)|Pobiera dojście do dołączonego obiektu GDI systemu Windows.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CGdiObject::m_hObject](#m_hobject)|Dojście zawierające elementy HBITMAP, HPALETTE, HRGN, HBRUSH, HPEN lub HFONT dołączone do tego obiektu.|

## <a name="remarks"></a>Uwagi

Nigdy nie utworzysz `CGdiObject` bezpośredniego. Zamiast tego należy utworzyć obiekt z jednej z klas pochodnych, takich jak `CPen` lub. `CBrush`

Aby uzyskać więcej informacji `CGdiObject`na temat, zobacz [grafika Objects](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CGdiObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="attach"></a>CGdiObject:: Attach

Dołącza obiekt GDI systemu Windows do `CGdiObject` obiektu.

```
BOOL Attach(HGDIOBJ hObject);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
Dojście do obiektu GDI systemu Windows (na przykład HPEN lub HBRUSH).

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli załącznik zakończył się pomyślnie; w przeciwnym razie 0.

##  <a name="cgdiobject"></a>CGdiObject::CGdiObject

Konstruuje `CGdiObject` obiekt.

```
CGdiObject();
```

### <a name="remarks"></a>Uwagi

Nigdy nie utworzysz `CGdiObject` bezpośredniego. Zamiast tego należy utworzyć obiekt z jednej z klas pochodnych, takich jak `CPen` lub. `Cbrush`

##  <a name="createstockobject"></a>CGdiObject::

Pobiera dojście do jednego ze wstępnie zdefiniowanych piór, pędzli lub czcionek systemu Windows, a także dołącza obiekt GDI do `CGdiObject` obiektu.

```
BOOL CreateStockObject(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Stała określająca żądany typ obiektu giełdowego. Zapoznaj się z parametrem *fnObject* dla elementu GetStockObject w Windows SDK, aby uzyskać opis odpowiednich wartości. [](/windows/win32/api/wingdi/nf-wingdi-getstockobject)

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję z jedną z klas pochodnych, która odpowiada typowi obiektu GDI systemu Windows, `CPen` na przykład dla pióra podstawowego.

##  <a name="deleteobject"></a>CGdiObject::D eleteObject

Usuwa dołączony obiekt GDI systemu Windows z pamięci, zwalniając wszystkie magazyny systemowe skojarzone z obiektem GDI systemu Windows.

```
BOOL DeleteObject();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli obiekt GDI został pomyślnie usunięty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

To wywołanie nie ma wpływ `CGdiObject` na magazyn skojarzony z obiektem. Aplikacja nie powinna wywoływać `DeleteObject` `CGdiObject` obiektu, który jest aktualnie wybrany w kontekście urządzenia.

Po usunięciu pędzla wzorca Mapa bitowa skojarzona z pędzlem nie zostanie usunięta. Mapa bitowa musi zostać usunięta niezależnie.

##  <a name="deletetempmap"></a>CGdiObject::D eleteTempMap

Wywoływana automatycznie przez `CWinApp` program obsługi czasu bezczynności, `DeleteTempMap` usuwa wszystkie obiekty `CGdiObject` tymczasowe utworzone przez `FromHandle`.

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Uwagi

`DeleteTempMap`odłącza obiekt GDI systemu Windows dołączony do obiektu tymczasowego `CGdiObject` przed `CGdiObject` usunięciem obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]

##  <a name="detach"></a>CGdiObject::D etach

Odłącza obiekt interfejsu GDI systemu Windows z `CGdiObject` obiektu i zwraca dojście do obiektu GDI systemu Windows.

```
HGDIOBJ Detach();
```

### <a name="return-value"></a>Wartość zwracana

`HANDLE` Do obiektu GDI systemu Windows odłączono; w przeciwnym razie wartość null, jeśli nie dołączono żadnego obiektu GDI.

##  <a name="fromhandle"></a>CGdiObject::FromHandle

Zwraca wskaźnik do `CGdiObject` obiektu, który ma dojście do obiektu GDI systemu Windows.

```
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
UCHWYT do obiektu GDI systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu `CGdiObject` , który może być tymczasowy lub trwały.

### <a name="remarks"></a>Uwagi

Jeśli obiekt nie jest jeszcze dołączony do obiektu GDI systemu Windows, tworzony jest obiekt `CGdiObject` tymczasowy i jest on dołączony. `CGdiObject`

Ten obiekt `CGdiObject` tymczasowy jest prawidłowy tylko do następnego momentu, gdy aplikacja ma czas bezczynności w pętli zdarzeń, podczas gdy wszystkie tymczasowe obiekty graficzne są usuwane. Innym sposobem wymawiania tego jest to, że obiekt tymczasowy jest prawidłowy tylko podczas przetwarzania jednego komunikatu w oknie.

##  <a name="getobject"></a>CGdiObject:: GetObject

Wypełnia bufor danymi, które definiują określony obiekt.

```
int GetObject(
    int nCount,
    LPVOID lpObject) const;
```

### <a name="parameters"></a>Parametry

*nCount*<br/>
Określa liczbę bajtów, które mają być skopiowane do buforu *lpObject* .

*lpObject*<br/>
Wskazuje bufor dostarczony przez użytkownika, który ma otrzymywać informacje.

### <a name="return-value"></a>Wartość zwracana

Liczba pobranych bajtów; w przeciwnym razie, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Funkcja pobiera strukturę danych, której typ zależy od typu obiektu graficznego, jak pokazano na poniższej liście:

|Obiekt|Typ bufora|
|------------|-----------------|
|`CPen`|[LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen)|
|`CBrush`|[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)|
|`CFont`|[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)|
|`CBitmap`|[BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap)|
|`CPalette`|WORD|
|`CRgn`|Nieobsługiwane|

Jeśli obiekt jest `CBitmap` obiektem, `GetObject` zwraca tylko informacje o szerokości, wysokości i formacie koloru mapy bitowej. Rzeczywiste bity można pobrać przy użyciu [CBitmap:: GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits).

Jeśli obiekt jest `CPalette` obiektem, `GetObject` program pobiera słowo, które określa liczbę wpisów w palecie. Funkcja nie pobiera struktury [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) , która definiuje paletę. Aplikacja może uzyskać informacje dotyczące wpisów palety, wywołując [CPalette:: GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries).

##  <a name="getobjecttype"></a>CGdiObject:: GetObjectType

Pobiera typ obiektu GDI.

```
UINT GetObjectType() const;
```

### <a name="return-value"></a>Wartość zwracana

Typ obiektu, jeśli powodzenie; w przeciwnym razie 0. Może to być jedna z następujących wartości:

- Mapa bitowa OBJ_BITMAP

- Pędzel OBJ_BRUSH

- Czcionka OBJ_FONT

- Paleta OBJ_PAL

- OBJ_PEN pióro

- Pióro rozszerzone OBJ_EXTPEN

- Region OBJ_REGION

- Kontekst urządzenia OBJ_DC

- Kontekst urządzenia pamięci OBJ_MEMDC

- Metaplik OBJ_METAFILE

- Kontekst urządzenia metapliku OBJ_METADC

- Rozszerzony metaplik OBJ_ENHMETAFILE

- Kontekst urządzenia OBJ_ENHMETADC Enhanced-metaplik

##  <a name="getsafehandle"></a>CGdiObject:: GetSafeHandle

Zwraca `m_hObject` wartość, chyba że jest **to** wartość null, a w tym przypadku zwracana jest wartość null.

```
HGDIOBJ GetSafeHandle() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do dołączonego obiektu GDI systemu Windows; w przeciwnym razie wartość NULL, jeśli żaden obiekt nie jest dołączony.

### <a name="remarks"></a>Uwagi

Jest to część ogólnego modelu interfejsu uchwytu i jest przydatna, gdy wartość NULL jest prawidłowa lub specjalna dla dojścia.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CWnd:: IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled).

##  <a name="m_hobject"></a>  CGdiObject::m_hObject

Dojście zawierające elementy HBITMAP, HRGN, HBRUSH, HPEN, HPALETTE lub HFONT dołączone do tego obiektu.

```
HGDIOBJ m_hObject;
```

##  <a name="operator_neq"></a>CGdiObject:: operator! =

Określa, czy dwa obiekty GDI są logicznie nierówne.

```
BOOL operator!=(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Parametry

*obj*<br/>
Wskaźnik do istniejącego `CGdiObject`.

### <a name="remarks"></a>Uwagi

Określa, czy obiekt GDI po lewej stronie nie jest równy obiektowi GDI po prawej stronie.

##  <a name="operator_eq_eq"></a>CGdiObject:: operator = =

Określa, czy dwa obiekty GDI są logicznie równe.

```
BOOL operator==(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Parametry

*obj*<br/>
Odwołanie do istniejącej `CGdiObject`.

### <a name="remarks"></a>Uwagi

Określa, czy obiekt GDI po lewej stronie jest równy obiektowi GDI po prawej stronie.

##  <a name="operator_hgdiobj"></a>CGdiObject:: operator HGDIOBJ

Pobiera dojście do dołączonego obiektu GDI systemu Windows; w przeciwnym razie wartość NULL, jeśli żaden obiekt nie jest dołączony.

```
operator HGDIOBJ() const;
```

##  <a name="unrealizeobject"></a>CGdiObject:: unzrozumieobject

Resetuje początek pędzla lub resetuje paletę logiczną.

```
BOOL UnrealizeObject();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Chociaż `UnrealizeObject` jest funkcją `CGdiObject` członkowską klasy, należy ją wywołać tylko dla `CBrush` obiektów lub `CPalette` .

W `CBrush` przypadku obiektów `UnrealizeObject` program kieruje system do zresetowania źródła danego pędzla przy następnym zaznaczeniu w kontekście urządzenia. Jeśli obiekt jest `CPalette` obiektem, `UnrealizeObject` Nakazuje systemowi zaimplementowanie palety, tak jakby nie była wcześniej prawdziwa. Następnym razem, gdy aplikacja wywoła funkcję [przechwytywania:: RealizePalette](../../mfc/reference/cdc-class.md#realizepalette) dla określonej palety, system całkowicie ponownie mapuje paletę logiczną na paletę systemową.

`UnrealizeObject` Funkcja nie powinna być używana z obiektami podstawowymi. Funkcja musi być wywoływana za każdym razem, gdy jest ustawiony nowy punkt początkowy pędzla (za pomocą funkcji [przechwytywania zmian:: SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg) ). `UnrealizeObject` `UnrealizeObject` Funkcja nie może być wywoływana dla aktualnie wybranego pędzla lub aktualnie wybranej palety dowolnego kontekstu wyświetlania.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CBitmap](../../mfc/reference/cbitmap-class.md)<br/>
[Klasa CBrush](../../mfc/reference/cbrush-class.md)<br/>
[Klasa CFont](../../mfc/reference/cfont-class.md)<br/>
[Klasa CPalette](../../mfc/reference/cpalette-class.md)<br/>
[Klasa CPen](../../mfc/reference/cpen-class.md)<br/>
[Klasa CRgn](../../mfc/reference/crgn-class.md)
