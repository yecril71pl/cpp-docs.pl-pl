---
title: Klasa CMapStringToOb
ms.date: 11/04/2016
f1_keywords:
- CMapStringToOb
- AFXCOLL/CMapStringToOb
- AFXCOLL/CMapStringToOb::CMapStringToOb
- AFXCOLL/CMapStringToOb::GetCount
- AFXCOLL/CMapStringToOb::GetHashTableSize
- AFXCOLL/CMapStringToOb::GetNextAssoc
- AFXCOLL/CMapStringToOb::GetSize
- AFXCOLL/CMapStringToOb::GetStartPosition
- AFXCOLL/CMapStringToOb::HashKey
- AFXCOLL/CMapStringToOb::InitHashTable
- AFXCOLL/CMapStringToOb::IsEmpty
- AFXCOLL/CMapStringToOb::Lookup
- AFXCOLL/CMapStringToOb::LookupKey
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
helpviewer_keywords:
- CMapStringToOb [MFC], CMapStringToOb
- CMapStringToOb [MFC], GetCount
- CMapStringToOb [MFC], GetHashTableSize
- CMapStringToOb [MFC], GetNextAssoc
- CMapStringToOb [MFC], GetSize
- CMapStringToOb [MFC], GetStartPosition
- CMapStringToOb [MFC], HashKey
- CMapStringToOb [MFC], InitHashTable
- CMapStringToOb [MFC], IsEmpty
- CMapStringToOb [MFC], Lookup
- CMapStringToOb [MFC], LookupKey
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: 09653980-b885-4f3a-8594-0aeb7f94c601
ms.openlocfilehash: 6520d1c38701647ae51450b9b9800a7cd2701b7a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754583"
---
# <a name="cmapstringtoob-class"></a>Klasa CMapStringToOb

Klasa kolekcji słownika, `CString` która `CObject` mapuje unikatowe obiekty do wskaźników.

## <a name="syntax"></a>Składnia

```
class CMapStringToOb : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMapStringToOb::CMapStringToOb](#cmapstringtoob)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMapStringToOb::GetCount](#getcount)|Zwraca liczbę elementów na tej mapie.|
|[CMapStringToOb::GetHashTableSize](#gethashtablesize)|Określa bieżącą liczbę elementów w tabeli mieszania.|
|[CMapStringToOb::GetNextAssoc](#getnextassoc)|Pobiera następny element do iteracji.|
|[CMapStringToOb::Rozmiar](#getsize)|Zwraca liczbę elementów na tej mapie.|
|[CMapStringToOb::GetStartPosition](#getstartposition)|Zwraca położenie pierwszego elementu.|
|[CMapStringToOb::HashKey](#hashkey)|Oblicza wartość mieszania określonego klucza.|
|[CMapStringToOb::InitHashTable](#inithashtable)|Inicjuje tabelę mieszania.|
|[CMapStringToOb::IsEmpty](#isempty)|Testy stanu pustej mapy (bez elementów).|
|[CMapStringToOb::Odnośnik](#lookup)|Wyszukuje wskaźnik void na podstawie klucza wskaźnika void. Wartość wskaźnika, a nie encja, na której wskazuje, jest używana do porównywania kluczy.|
|[CMapStringToOb::Klucz odnośnika](#lookupkey)|Zwraca odwołanie do klucza skojarzonego z określoną wartością klucza.|
|[CMapStringToOb::UsuńWszystki](#removeall)|Usuwa wszystkie elementy z tej mapy.|
|[CMapStringToOb::Usuń przycisk](#removekey)|Usuwa element określony przez klucz.|
|[CMapStringToOb::SetAt](#setat)|Wstawia element do mapy; zastępuje istniejący element, jeśli zostanie znaleziony pasujący klucz.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMapStringToOb::operator \[\]](#operator_at)|Wstawia element do mapy — `SetAt`zastępowanie operatora dla .|

## <a name="remarks"></a>Uwagi

Po wstawieniu `CString` -  `CObject*` pary (elementu) do mapy można skutecznie pobrać lub usunąć parę `CString` przy użyciu ciągu lub wartości jako klucza. Można również iterować na wszystkich elementów na mapie.

Zmienna typu POSITION jest używana do alternatywnego dostępu do wejścia we wszystkich odmianach mapy. Możesz użyć pozycji, aby "zapamiętać" wpis i iterować przez mapę. Można by pomyśleć, że ta iteracja jest sekwencyjna według wartości klucza; tak nie jest. Sekwencja pobranych elementów jest nieokreślona.

`CMapStringToOb`zawiera makro `IMPLEMENT_SERIAL` w celu wspierania serializacji i dumpingu jego elementów. Każdy element jest serializowany po kolei, jeśli mapa jest przechowywana w **<<** archiwum, za `Serialize` pomocą przeciążonego operatora wstawiania ( ) lub z funkcją elementu członkowskiego.

Jeśli potrzebujesz zrzutu diagnostycznego poszczególnych elementów `CString` na `CObject` mapie (wartość i zawartość), należy ustawić głębokość kontekstu zrzutu na 1 lub większą.

Po `CMapStringToOb` usunięciu obiektu lub usunięciu jego elementów `CString` obiekty `CObject` i wskaźniki zostaną usunięte. Obiekty, do których `CObject` odwołują się wskaźniki, nie są niszczone.

Wyprowadzenie klasy mapy jest podobne do wyprowadzania listy. Zobacz artykuł [Kolekcje](../../mfc/collections.md) na ilustrację wyprowadzenia klasy listy specjalnego przeznaczenia.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CMapStringToOb`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll.h

## <a name="cmapstringtoobcmapstringtoob"></a><a name="cmapstringtoob"></a>CMapStringToOb::CMapStringToOb

Konstruuje `CString`pustą `CObject*` mapę -to-.

```
CMapStringToOb(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parametry

*nBlockSize (Rozmiar)*<br/>
Określa szczegółowość alokacji pamięci w celu rozszerzenia mapy.

### <a name="remarks"></a>Uwagi

Wraz z rozwojem mapy pamięć jest przydzielana w jednostkach wpisów *nBlockSize.*

W poniższej tabeli przedstawiono `CMapStringToOb:: CMapStringToOb`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord( INT_PTR** `nBlockSize` **= 10 );**|
|[PmapstringToptr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapStringToString (CMapStringToString)](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb( INT_PTR** `nBlockSize` **= 10 );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr( INT_PTR** `nBlockSize` **= 10 );**|

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

## <a name="cmapstringtoobgetcount"></a><a name="getcount"></a>CMapStringToOb::GetCount

Określa, ile elementów znajduje się na mapie.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów na tej mapie.

### <a name="remarks"></a>Uwagi

W poniższej tabeli przedstawiono `CMapStringToOb::GetCount`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetCount( ) const;**|
|[PmapstringToptr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapStringToString (CMapStringToString)](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetCount( ) const;**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]

## <a name="cmapstringtoobgethashtablesize"></a><a name="gethashtablesize"></a>CMapStringToOb::GetHashTableSize

Określa bieżącą liczbę elementów w tabeli mieszania.

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę elementów w tabeli mieszania.

### <a name="remarks"></a>Uwagi

W poniższej tabeli przedstawiono `CMapStringToOb::GetHashTableSize`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT GetHashTableSize( ) const;**|
|[PmapstringToptr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapStringToString (CMapStringToString)](../../mfc/reference/cmapstringtostring-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT GetHashTableSize( ) const;**|

## <a name="cmapstringtoobgetnextassoc"></a><a name="getnextassoc"></a>CMapStringToOb::GetNextAssoc

Pobiera element mapy w *rNextPosition*, a następnie aktualizuje *rNextPosition* odwoływać się do następnego elementu na mapie.

```cpp
void GetNextAssoc(
    POSITION& rNextPosition,
    CString& rKey,
    CObject*& rValue) const;
```

### <a name="parameters"></a>Parametry

*rNastępna pozycja*<br/>
Określa odwołanie do wartości POSITION zwróconej `GetNextAssoc` `GetStartPosition` przez poprzedni lub wywołanie.

*rKey (Klawisz)*<br/>
Określa zwracany klucz pobranego elementu (ciąg).

*rWartość*<br/>
Określa zwracaną wartość pobranego elementu `CObject` (wskaźnika). Zobacz Uwagi, aby uzyskać więcej informacji na temat tego parametru.

### <a name="remarks"></a>Uwagi

Ta funkcja jest najbardziej przydatna do iteracji przez wszystkie elementy na mapie. Należy zauważyć, że sekwencja pozycji nie musi być taka sama jak sekwencja wartości klucza.

Jeśli pobrany element jest ostatnim na mapie, nowa wartość *rNextPosition* jest ustawiona na WARTOŚĆ NULL.

Dla *rValue* parametr, należy rzutować typ obiektu do **CObject\***, który jest to, co wymaga kompilator, jak pokazano w poniższym przykładzie:

[!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]

Nie dotyczy to `GetNextAssoc` map opartych na szablonach.

W poniższej tabeli przedstawiono `CMapStringToOb::GetNextAssoc`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void GetNextAssoc( POZYCJA&** *rNextPosition* **, void\* ** *rKey* **, void\* ** *rValue* **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void GetNextAssoc( POZYCJA&** *rNextPosition* **, void\* ** *rKey* **, WORD&** *rValue* **) const;**|
|[PmapstringToptr](../../mfc/reference/cmapstringtoptr-class.md)|**void GetNextAssoc( POZYCJA&** *rNextPosition* **, CString&** *rKey* **, void\* ** *rValue* **) const;**|
|[CMapStringToString (CMapStringToString)](../../mfc/reference/cmapstringtostring-class.md)|**void GetNextAssoc( POZYCJA&** *rNextPosition* **, CString&** *rKey* **, CString&** *rValue* **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void GetNextAssoc( POZYCJA&** *rNextPosition* **, WORD&** *rKey* **,\* CObject** *rValue* **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void GetNextAssoc( POZYCJA&** *rNextPosition* **, WORD&** *rKey* **, void\* ** *rValue* **) const;**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]

Wyniki tego programu są następujące:

```Output
Lisa : a CAge at $4724 11
Marge : a CAge at $47A8 35
Homer : a CAge at $4766 36
Bart : a CAge at $45D4 13
```

## <a name="cmapstringtoobgetsize"></a><a name="getsize"></a>CMapStringToOb::Rozmiar

Zwraca liczbę elementów mapy.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów na mapie.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby pobrać liczbę elementów na mapie.

W poniższej tabeli przedstawiono `CMapStringToOb::GetSize`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetSize( ) const;**|
|[PmapstringToptr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapStringToString (CMapStringToString)](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetSize( ) const;**|

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]

## <a name="cmapstringtoobgetstartposition"></a><a name="getstartposition"></a>CMapStringToOb::GetStartPosition

Rozpoczyna iterację mapy, zwracając wartość POSITION, która może `GetNextAssoc` zostać przekazana do wywołania.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość POSITION wskazująca pozycję początkową dla iteracji mapy; lub NULL, jeśli mapa jest pusta.

### <a name="remarks"></a>Uwagi

Sekwencja iteracji nie jest przewidywalna; w związku z tym "pierwszy element na mapie" nie ma szczególnego znaczenia.

W poniższej tabeli przedstawiono `CMapStringToOb::GetStartPosition`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**POZYCJA GetStartPosition( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**POZYCJA GetStartPosition( ) const;**|
|[PmapstringToptr](../../mfc/reference/cmapstringtoptr-class.md)|**POZYCJA GetStartPosition( ) const;**|
|[CMapStringToString (CMapStringToString)](../../mfc/reference/cmapstringtostring-class.md)|**POZYCJA GetStartPosition( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**POZYCJA GetStartPosition( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**POZYCJA GetStartPosition( ) const;**|

### <a name="example"></a>Przykład

Zobacz przykład [CMapStringToOb::GetNextAssoc](#getnextassoc).

## <a name="cmapstringtoobhashkey"></a><a name="hashkey"></a>CMapStringToOb::HashKey

Oblicza wartość mieszania określonego klucza.

```
UINT HashKey(LPCTSTR key) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klucz, którego wartość mieszania ma być obliczona.

### <a name="return-value"></a>Wartość zwracana

Wartość skrótu klucza

### <a name="remarks"></a>Uwagi

W poniższej tabeli przedstawiono `CMapStringToOb::HashKey`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT HashKey( void)** <strong>\*</strong> `key` **const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT HashKey( void)** <strong>\*</strong> `key` **const;**|
|[CMapStringToString (CMapStringToString)](../../mfc/reference/cmapstringtostring-class.md)|**UINT HashKey( LPCTSTR** `key` **) const;**|
|[PmapstringToptr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT HashKey( LPCTSTR** `key` **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT HashKey( WORD** `key` **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT HashKey( WORD** `key` **) const;**|

## <a name="cmapstringtoobinithashtable"></a><a name="inithashtable"></a>CMapStringToOb::InitHashTable

Inicjuje tabelę mieszania.

```cpp
void InitHashTable(
    UINT hashSize,
    BOOL bAllocNow = TRUE);
```

### <a name="parameters"></a>Parametry

*rozmiar hashSize*<br/>
Liczba wpisów w tabeli mieszania.

*bLokalnyTeraz*<br/>
Jeśli true, przydziela tabelę mieszania podczas inicjowania; w przeciwnym razie tabela jest przydzielana w razie potrzeby.

### <a name="remarks"></a>Uwagi

Aby uzyskać najlepszą wydajność, rozmiar tabeli mieszania powinien być liczbą pierwszą. Aby zminimalizować kolizje, rozmiar powinien być o około 20 procent większy niż największy przewidywany zestaw danych.

W poniższej tabeli przedstawiono `CMapStringToOb::InitHashTable`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|
|[CMapStringToString (CMapStringToString)](../../mfc/reference/cmapstringtostring-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|
|[PmapstringToptr](../../mfc/reference/cmapstringtoptr-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|

## <a name="cmapstringtoobisempty"></a><a name="isempty"></a>CMapStringToOb::IsEmpty

Określa, czy mapa jest pusta.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli ta mapa nie zawiera żadnych elementów; w przeciwnym razie 0.

### <a name="example"></a>Przykład

Zobacz przykład [RemoveAll](#removeall).

### <a name="remarks"></a>Uwagi

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do **CMapStringToOb:: IsEmpty**.

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL IsEmpty( ) const;**|
|[PmapstringToptr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapStringToString (CMapStringToString)](../../mfc/reference/cmapstringtostring-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL IsEmpty( ) const;**|

## <a name="cmapstringtooblookup"></a><a name="lookup"></a>CMapStringToOb::Odnośnik

Zwraca `CObject` wskaźnik na `CString` podstawie wartości.

```
BOOL Lookup(
    LPCTSTR key,
    CObject*& rValue) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Określa klucz ciągu identyfikujący element, który ma być wyszukany.

*rWartość*<br/>
Określa zwracaną wartość z elementu spojrzał w górę.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli element został znaleziony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`Lookup`używa algorytmu mieszania, aby szybko znaleźć element mapy z `CString` kluczem, który dokładnie odpowiada (wartość).

W poniższej tabeli przedstawiono `CMapStringToOb::LookUp`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL Lookup( void** <strong>\*</strong> `key` **, void\* ** `rValue` ) **const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL Lookup( void** <strong>\*</strong> `key` **, WORD&** `rValue` **) const;**|
|[PmapstringToptr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL Lookup( LPCTSTR** `key` **, void\* ** `rValue` ) **const;**|
|[CMapStringToString (CMapStringToString)](../../mfc/reference/cmapstringtostring-class.md)|**BOOL Lookup( LPCTSTR** `key` **, CString&** `rValue` **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL Lookup( WORD** `key` **,\* CObject** `rValue` **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL Lookup( WORD** `key` **, void\* ** `rValue` ) **const;**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]

## <a name="cmapstringtooblookupkey"></a><a name="lookupkey"></a>CMapStringToOb::Klucz odnośnika

Zwraca odwołanie do klucza skojarzonego z określoną wartością klucza.

```
BOOL LookupKey(
    LPCTSTR key,
    LPCTSTR& rKey) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Określa klucz ciągu identyfikujący element, który ma być wyszukany.

*rKey (Klawisz)*<br/>
Odwołanie do skojarzonego klucza.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli klucz został znaleziony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użycie odwołania do klucza jest niebezpieczne, jeśli jest używane po usunięciu skojarzonego elementu z mapy lub po zniszczeniu mapy.

W poniższej tabeli przedstawiono `CMapStringToOb:: LookupKey`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[PmapstringToptr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL LookupKey( LPCTSTR** `key` **, LPCTSTR&** `rKey` **) const;**|
|[CMapStringToString (CMapStringToString)](../../mfc/reference/cmapstringtostring-class.md)|**BOOL LookupKey( LPCTSTR** `key` **, LPCTSTR&** `rKey` **) const;**|

## <a name="cmapstringtooboperator--"></a><a name="operator_at"></a>CMapStringToOb::operator [ ]

Wygodny substytut funkcji `SetAt` elementu członkowskiego.

```
CObject*& operator[ ](lpctstr key);
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do wskaźnika `CObject` do obiektu; lub NULL, jeśli mapa jest pusta lub *klucz* jest poza zakresem.

### <a name="remarks"></a>Uwagi

W ten sposób może być używany tylko po lewej stronie instrukcji przypisania (wartość l). Jeśli nie ma żadnego elementu mapy z określonym kluczem, tworzony jest nowy element.

Nie ma "prawej strony" (r-value) równoważne tego operatora, ponieważ istnieje możliwość, że klucz nie można znaleźć na mapie. Użyj `Lookup` funkcji elementu członkowskiego do pobierania elementu.

W poniższej tabeli przedstawiono `CMapStringToOb::operator []`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|<strong>nieważne\*& operatora\[ \* ](nieważne</strong> `key` ** \);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**operator\[word& ](nieważny** <strong>\*</strong> `key` ** \);**|
|[PmapstringToptr](../../mfc/reference/cmapstringtoptr-class.md)|**nieważny\* operator\[& ](lpctstr** `key` ** \);**|
|[CMapStringToString (CMapStringToString)](../../mfc/reference/cmapstringtostring-class.md)|**CString\[& operator ](lpctstr** `key` ** \);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*& operator\[](słowo** `key` ** \);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**nieważny\*& operatora\[](słowo** `key` ** \);**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]

Wyniki tego programu są następujące:

```Output
Operator [] example: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $4A02 11
[Bart] = a CAge at $497E 13
```

## <a name="cmapstringtoobremoveall"></a><a name="removeall"></a>CMapStringToOb::UsuńWszystki

Usuwa wszystkie elementy z tej mapy `CString` i niszczy kluczowe obiekty.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Uwagi

Obiekty, `CObject` do których odwołuje się każdy klucz, nie są niszczone. Funkcja `RemoveAll` może powodować przecieki pamięci, jeśli nie `CObject` upewnij się, że obiekty, do których istnieje odwołanie, są niszczone.

Funkcja działa poprawnie, jeśli mapa jest już pusta.

W poniższej tabeli przedstawiono `CMapStringToOb::RemoveAll`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void RemoveAll( );**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void RemoveAll( );**|
|[PmapstringToptr](../../mfc/reference/cmapstringtoptr-class.md)|**void RemoveAll( );**|
|[CMapStringToString (CMapStringToString)](../../mfc/reference/cmapstringtostring-class.md)|**void RemoveAll( );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void RemoveAll( );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void RemoveAll( );**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]

## <a name="cmapstringtoobremovekey"></a><a name="removekey"></a>CMapStringToOb::Usuń przycisk

Wyszukuje wpis mapy odpowiadający dostarczonemu kluczowi; następnie, jeśli zostanie znaleziony klucz, usuwa wpis.

```
BOOL RemoveKey(LPCTSTR key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Określa ciąg używany do wyszukiwania mapy.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wpis został znaleziony i pomyślnie usunięte; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Może to spowodować przecieki `CObject` pamięci, jeśli obiekt nie zostanie usunięty w innym miejscu.

W poniższej tabeli przedstawiono `CMapStringToOb::RemoveKey`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL RemoveKey( void** <strong>\*</strong> `key` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL RemoveKey( void** <strong>\*</strong> `key` **);**|
|[PmapstringToptr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL RemoveKey( LPCTSTR** `key` **);**|
|[CMapStringToString (CMapStringToString)](../../mfc/reference/cmapstringtostring-class.md)|**BOOL RemoveKey( LPCTSTR** `key` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL RemoveKey( WORD** `key` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL RemoveKey( WORD** `key` **);**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]

Wyniki tego programu są następujące:

```Output
RemoveKey example: A CMapStringToOb with 3 elements
[Marge] = a CAge at $49A0 35
[Homer] = a CAge at $495E 36
[Bart] = a CAge at $4634 13
```

## <a name="cmapstringtoobsetat"></a><a name="setat"></a>CMapStringToOb::SetAt

Podstawowy oznacza wstawienie elementu do mapy.

```cpp
void SetAt(
    LPCTSTR key,
    CObject* newValue);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Określa ciąg, który jest kluczem nowego elementu.

*Newvalue*<br/>
Określa `CObject` wskaźnik, który jest wartością nowego elementu.

### <a name="remarks"></a>Uwagi

Po pierwsze, klucz jest spojrzał w górę. Jeśli zostanie znaleziony klucz, odpowiednia wartość zostanie zmieniona; w przeciwnym razie zostanie utworzony nowy element klucz-wartość.

W poniższej tabeli przedstawiono `CMapStringToOb::SetAt`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void SetAt( void** <strong>\*</strong> `key` **, void** <strong>\*</strong> `newValue` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void SetAt( void** <strong>\*</strong> `key` **, WORD** `newValue` **);**|
|[PmapstringToptr](../../mfc/reference/cmapstringtoptr-class.md)|**void SetAt( LPCTSTR** `key` **, void** <strong>\*</strong> `newValue` **);**|
|[CMapStringToString (CMapStringToString)](../../mfc/reference/cmapstringtostring-class.md)|**void SetAt( LPCTSTR** `key` **, LPCTSTR** `newValue` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void SetAt( WORD** `key` **, CObject** <strong>\*</strong> `newValue` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void SetAt( WORD** `key` **, void** <strong>\*</strong> `newValue` **);**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]

Wyniki tego programu są następujące:

```Output
before Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $493C 11
[Bart] = a CAge at $4654 13
after Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $49C0 12
[Bart] = a CAge at $4654 13
```

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[Klasa CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)<br/>
[Klasa CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)<br/>
[Klasa CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)<br/>
[Klasa CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)<br/>
[Klasa CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)
