---
title: Klasa CObArray
ms.date: 11/04/2016
f1_keywords:
- CObArray
- AFXCOLL/CObArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 27894efd-2370-4776-9ed9-24a98492af17
ms.openlocfilehash: 7b923fd9231d3652d8d2f1750a8024d15287811e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360447"
---
# <a name="cobarray-class"></a>Klasa CObArray

Obsługuje tablice `CObject` wskaźników.

## <a name="syntax"></a>Składnia

```
class CObArray : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CObArray::CObArray](#cobarray)|Konstruuje pustą `CObject` tablicę dla wskaźników.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CObArray::Dodaj](#add)|Dodaje element na końcu tablicy; w razie potrzeby zwiększa tablicę.|
|[CObArray::Dołącz](#append)|Dołącza inną tablicę do tablicy; w razie potrzeby zwiększa tablicę.|
|[CObArray::Kopiowanie](#copy)|Kopiuje inną tablicę do tablicy; w razie potrzeby zwiększa tablicę.|
|[CObArray::ElementAt](#elementat)|Zwraca tymczasowe odwołanie do wskaźnika elementu w tablicy.|
|[CObArray::FreeExtra](#freeextra)|Zwalnia całą nieużytą pamięć powyżej bieżącej górnej granicy.|
|[CObArray::GetAt](#getat)|Zwraca wartość w danym indeksie.|
|[CObArray::GetCount](#getcount)|Pobiera liczbę elementów w tej tablicy.|
|[CObArray::GetData](#getdata)|Umożliwia dostęp do elementów w tablicy. Może mieć wartość NULL.|
|[CObArray::GetSize](#getsize)|Pobiera liczbę elementów w tej tablicy.|
|[CObArray::GetUpperBound](#getupperbound)|Zwraca największy prawidłowy indeks.|
|[CObArray::Wstawianie](#insertat)|Wstawia element (lub wszystkie elementy w innej tablicy) w określonym indeksie.|
|[CObArray::IsEmpty](#isempty)|Określa, czy tablica jest pusta.|
|[CObArray::UsuńWszystki](#removeall)|Usuwa wszystkie elementy z tej tablicy.|
|[CObArray::Usuń](#removeat)|Usuwa element w określonym indeksie.|
|[CObArray::SetAt](#setat)|Ustawia wartość dla danego indeksu; tablicy nie może rosnąć.|
|[CObArray::SetAtGrow](#setatgrow)|Ustawia wartość dla danego indeksu; w razie potrzeby zwiększa tablicę.|
|[CObArray::SetSize](#setsize)|Ustawia liczbę elementów, które mają być zawarte w tej tablicy.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CObArray::operator \[\]](#operator_at)|Ustawia lub pobiera element w określonym indeksie.|

## <a name="remarks"></a>Uwagi

Te tablice obiektów są podobne do tablic C, ale mogą dynamicznie zmniejszać i rosnąć w razie potrzeby.

Indeksy tablicy zawsze zaczynają się od pozycji 0. Można zdecydować, czy naprawić górną granicę lub zezwolić tablicy rozwinąć po dodaniu elementów poza bieżącą powiązaną. Pamięć jest przydzielana w sposób ciągły do górnej granicy, nawet jeśli niektóre elementy są null.

W obszarze Win32 rozmiar `CObArray` obiektu jest ograniczony tylko do dostępnej pamięci.

Podobnie jak w przypadku tablicy `CObArray` C, czas dostępu dla elementu indeksowanego jest stały i jest niezależny od rozmiaru tablicy.

`CObArray`zawiera makro IMPLEMENT_SERIAL w celu wspierania serializacji i dumpingu jego elementów. Jeśli tablica `CObject` wskaźników jest przechowywana w archiwum, za pomocą przeciążonego operatora wstawiania lub funkcji `Serialize` elementu członkowskiego, każdy `CObject` element jest z kolei szeregowy wraz z jego indeksem tablicy.

Jeśli potrzebujesz zrzutu `CObject` poszczególnych elementów w tablicy, `CDumpContext` należy ustawić głębokość obiektu na 1 lub większą.

Po `CObArray` usunięciu obiektu lub usunięciu jego elementów `CObject` usuwane są tylko wskaźniki, a nie obiekty, do których się odwołują.

> [!NOTE]
> Przed użyciem tablicy należy użyć `SetSize` do ustalenia jego rozmiaru i przydzielić dla niej pamięć. Jeśli nie używasz `SetSize`, dodawanie elementów do tablicy powoduje, że często są ponownie przydzielane i kopiowane. Częste ponowne przydzielanie i kopiowanie są nieefektywne i mogą fragmentować pamięć.

Wyprowadzanie klasy tablicy jest podobne do wyprowadzania listy. Szczegółowe informacje na temat wyprowadzania klasy listy specjalnego przeznaczenia można znaleźć w [artykule Kolekcje](../../mfc/collections.md).

> [!NOTE]
> W przypadku zamiaru serializacji tablicy należy użyć makra IMPLEMENT_SERIAL w implementacji klasy pochodnej.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CObArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll.h

## <a name="cobarrayadd"></a><a name="add"></a>CObArray::Dodaj

Dodaje nowy element na końcu tablicy, powiększając tablicę o 1.

```
INT_PTR Add(CObject* newElement);
```

### <a name="parameters"></a>Parametry

*nowyElement*<br/>
Wskaźnik, `CObject` który ma zostać dodany do tej tablicy.

### <a name="return-value"></a>Wartość zwracana

Indeks dodanego elementu.

### <a name="remarks"></a>Uwagi

Jeśli [SetSize](#setsize) został użyty z *nGrowBy* wartość większą niż 1, a następnie dodatkowe pamięci mogą być przydzielane. Jednak górna granica wzrośnie tylko o 1.

W poniższej tabeli przedstawiono `CObArray::Add`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**INT_PTR Add( BYTE** `newElement` **);**<br /><br /> **rzut( CMemoryException\* );**|
|[CdWordArray (CdWordArray)](../../mfc/reference/cdwordarray-class.md)|**INT_PTR Dodaj( DWORD** `newElement` **);**<br /><br /> **rzut( CMemoryException\* );**|
|[Cptrarray](../../mfc/reference/cptrarray-class.md)|**INT_PTR Dodaj( void** <strong>\*</strong> `newElement` **);**<br /><br /> **rzut( CMemoryException\* );**|
|[CStringArray (Polski)](../../mfc/reference/cstringarray-class.md)|**INT_PTR Add( LPCTSTR);** `newElement` **rzut( CMemoryException\* );**<br /><br /> **INT_PTR Add (const CString** `newElement` **&);**|
|[CUIntArray (CuIntArray)](../../mfc/reference/cuintarray-class.md)|**INT_PTR Dodaj( UINT** `newElement` **);**<br /><br /> **rzut( CMemoryException\* );**|
|[CWordArray (Polski)](../../mfc/reference/cwordarray-class.md)|**INT_PTR Dodaj( WORD** `newElement` **);**<br /><br /> **rzut( CMemoryException\* );**|

### <a name="example"></a>Przykład

  Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]

Wyniki tego programu są następujące:

```Output
Add example: A CObArray with 2 elements
[0] = a CAge at $442A 21
[1] = a CAge at $4468 40
```

## <a name="cobarrayappend"></a><a name="append"></a>CObArray::Dołącz

Wywołanie tej funkcji elementu członkowskiego, aby dodać zawartość innej tablicy na końcu danej tablicy.

```
INT_PTR Append(const CObArray& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
Źródło elementów, które mają być dołączone do tablicy.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszego dołączonego elementu.

### <a name="remarks"></a>Uwagi

Tablice muszą być tego samego typu.

W razie `Append` potrzeby może przydzielić dodatkową pamięć, aby pomieścić elementy dołączone do tablicy.

W poniższej tabeli przedstawiono `CObArray::Append`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**INT_PTR Append( const CByteArray&** *src* **);**|
|[CdWordArray (CdWordArray)](../../mfc/reference/cdwordarray-class.md)|**INT_PTR Append( const CDWordArray&** *src* **);**|
|[Cptrarray](../../mfc/reference/cptrarray-class.md)|**INT_PTR Append( const CPtrArray&** *src* **);**|
|[CStringArray (Polski)](../../mfc/reference/cstringarray-class.md)|**INT_PTR Append( const CStringArray&** *src* **);**|
|[CUIntArray (CuIntArray)](../../mfc/reference/cuintarray-class.md)|**INT_PTR Append( const CUIntArray&** *src* **);**|
|[CWordArray (Polski)](../../mfc/reference/cwordarray-class.md)|**INT_PTR Append( const CWordArray&** *src* **);**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]

## <a name="cobarraycopy"></a><a name="copy"></a>CObArray::Kopiowanie

Wywołanie tej funkcji elementu członkowskiego, aby zastąpić elementy danej tablicy z elementami innej tablicy tego samego typu.

```
void Copy(const CObArray& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
Źródło elementów, które mają zostać skopiowane do tablicy.

### <a name="remarks"></a>Uwagi

`Copy`nie zwalnia pamięci; jednak w razie `Copy` potrzeby może przydzielić dodatkową pamięć, aby pomieścić elementy skopiowane do tablicy.

W poniższej tabeli przedstawiono `CObArray::Copy`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**void Copy( const CByteArray&** *src* **);**|
|[CdWordArray (CdWordArray)](../../mfc/reference/cdwordarray-class.md)|**void Copy( const CDWordArray&** *src* **);**|
|[Cptrarray](../../mfc/reference/cptrarray-class.md)|**void Copy( const CPtrArray&** *src* **);**|
|[CStringArray (Polski)](../../mfc/reference/cstringarray-class.md)|**void Copy( const CStringArray&** *src* **);**|
|[CUIntArray (CuIntArray)](../../mfc/reference/cuintarray-class.md)|**void Copy( const CUIntArray&** *src* **);**|
|[CWordArray (Polski)](../../mfc/reference/cwordarray-class.md)|**void Copy( const CWordArray&** *src* **);**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]

## <a name="cobarraycobarray"></a><a name="cobarray"></a>CObArray::CObArray

Konstruuje `CObject` pustą tablicę wskaźnika.

```
CObArray();
```

### <a name="remarks"></a>Uwagi

Tablica rośnie jeden element naraz.

W poniższej tabeli przedstawiono `CObArray::CObArray`inne konstruktory, które są podobne do .

|Klasa|Konstruktor|
|-----------|-----------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**CByteArray( );**|
|[CdWordArray (CdWordArray)](../../mfc/reference/cdwordarray-class.md)|**CDWordArray( );**|
|[Cptrarray](../../mfc/reference/cptrarray-class.md)|**CPtrArray( );**|
|[CStringArray (Polski)](../../mfc/reference/cstringarray-class.md)|**CStringArray( );**|
|[CUIntArray (CuIntArray)](../../mfc/reference/cuintarray-class.md)|**CUIntArray( );**|
|[CWordArray (Polski)](../../mfc/reference/cwordarray-class.md)|**CWordArray( );**|

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]

## <a name="cobarrayelementat"></a><a name="elementat"></a>CObArray::ElementAt

Zwraca tymczasowe odwołanie do wskaźnika elementu w tablicy.

```
CObject*& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0 i `GetUpperBound`mniejszy lub równy wartości zwracanej przez program .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `CObject` wskaźnika.

### <a name="remarks"></a>Uwagi

Służy do implementowania operatora przypisania po lewej stronie dla tablic. Należy zauważyć, że jest to funkcja zaawansowana, która powinna być używana tylko do implementacji operatorów tablic specjalnych.

W poniższej tabeli przedstawiono `CObArray::ElementAt`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**BYTE& ElementAt( INT_PTR** `nIndex` **);**|
|[CdWordArray (CdWordArray)](../../mfc/reference/cdwordarray-class.md)|**DWORD& ElementAt( INT_PTR** `nIndex` **);**|
|[Cptrarray](../../mfc/reference/cptrarray-class.md)|**void\*& ElementAt( INT_PTR** `nIndex` **);**|
|[CStringArray (Polski)](../../mfc/reference/cstringarray-class.md)|**CString& ElementAt( INT_PTR** `nIndex` **);**|
|[CUIntArray (CuIntArray)](../../mfc/reference/cuintarray-class.md)|**UINT& ElementAt( INT_PTR** `nIndex` **);**|
|[CWordArray (Polski)](../../mfc/reference/cwordarray-class.md)|**WORD& ElementAt( INT_PTR** `nIndex` **);**|

### <a name="example"></a>Przykład

  Zobacz przykład [CObArray::GetSize](#getsize).

## <a name="cobarrayfreeextra"></a><a name="freeextra"></a>CObArray::FreeExtra

Zwalnia wszelkie dodatkowe pamięci, która została przydzielona, gdy tablica została wyhodowana.

```
void FreeExtra();
```

### <a name="remarks"></a>Uwagi

Ta funkcja nie ma wpływu na rozmiar lub górną granicę tablicy.

W poniższej tabeli przedstawiono `CObArray::FreeExtra`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**void FreeExtra( );**|
|[CdWordArray (CdWordArray)](../../mfc/reference/cdwordarray-class.md)|**void FreeExtra( );**|
|[Cptrarray](../../mfc/reference/cptrarray-class.md)|**void FreeExtra( );**|
|[CStringArray (Polski)](../../mfc/reference/cstringarray-class.md)|**void FreeExtra( );**|
|[CUIntArray (CuIntArray)](../../mfc/reference/cuintarray-class.md)|**void FreeExtra( );**|
|[CWordArray (Polski)](../../mfc/reference/cwordarray-class.md)|**void FreeExtra( );**|

### <a name="example"></a>Przykład

  Zobacz przykład [CObArray::GetData](#getdata).

## <a name="cobarraygetat"></a><a name="getat"></a>CObArray::GetAt

Zwraca element tablicy w określonym indeksie.

```
CObject* GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0 i `GetUpperBound`mniejszy lub równy wartości zwracanej przez program .

### <a name="return-value"></a>Wartość zwracana

Element `CObject` wskaźnika aktualnie w tym indeksie.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Przekazywanie wartości ujemnej lub wartości większej `GetUpperBound` niż wartość zwrócona przez spowoduje niepowodzenie potwierdzenia.

W poniższej tabeli przedstawiono `CObArray::GetAt`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**BYTE GetAt( INT_PTR** `nIndex` **) const;**|
|[CdWordArray (CdWordArray)](../../mfc/reference/cdwordarray-class.md)|**DWORD GetAt( INT_PTR** `nIndex` **) const;**|
|[Cptrarray](../../mfc/reference/cptrarray-class.md)|**void\* GetAt( INT_PTR** `nIndex` **) const;**|
|[CStringArray (Polski)](../../mfc/reference/cstringarray-class.md)|**CString GetAt( INT_PTR** `nIndex` **) const;**|
|[CUIntArray (CuIntArray)](../../mfc/reference/cuintarray-class.md)|**UINT GetAt( INT_PTR** `nIndex` **) const;**|
|[CWordArray (Polski)](../../mfc/reference/cwordarray-class.md)|**WORD GetAt( INT_PTR** `nIndex` **) const;**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]

## <a name="cobarraygetcount"></a><a name="getcount"></a>CObArray::GetCount

Zwraca liczbę elementów tablicy.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w tablicy.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby pobrać liczbę elementów w tablicy. Ponieważ indeksy są oparte na wartościach zerowych, rozmiar jest o 1 większy niż największy indeks.

W poniższej tabeli przedstawiono `CObArray::GetCount`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetCount( ) const;**|
|[CdWordArray (CdWordArray)](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetCount( ) const;**|
|[Cptrarray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetCount( ) const;**|
|[CStringArray (Polski)](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetCount( ) const;**|
|[CUIntArray (CuIntArray)](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetCount( ) const;**|
|[CWordArray (Polski)](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetCount( ) const;**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]

## <a name="cobarraygetdata"></a><a name="getdata"></a>CObArray::GetData

Ta funkcja elementu członkowskiego służy do uzyskiwania bezpośredniego dostępu do elementów w tablicy.

```
const CObject** GetData() const;

CObject** GetData();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do tablicy `CObject` wskaźników.

### <a name="remarks"></a>Uwagi

Jeśli żadne elementy `GetData` nie są dostępne, zwraca wartość null.

Podczas gdy bezpośredni dostęp do elementów tablicy może pomóc `GetData`w ciężej pracy, należy zachować ostrożność podczas wywoływania; wszelkie błędy, które można wprowadzić bezpośrednio wpływają na elementy tablicy.

W poniższej tabeli przedstawiono `CObArray::GetData`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**const BYTE\* GetData( ) const; BYTE\* GetData( );**|
|[CdWordArray (CdWordArray)](../../mfc/reference/cdwordarray-class.md)|**const DWORD\* GetData( ) const;DWORD\* GetData( );**|
|[Cptrarray](../../mfc/reference/cptrarray-class.md)|**const\* \* void GetData( )\* \* const;void GetData( );**|
|[CStringArray (Polski)](../../mfc/reference/cstringarray-class.md)|**const CString\* GetData( ) const; CString\* GetData( );**|
|[CUIntArray (CuIntArray)](../../mfc/reference/cuintarray-class.md)|**const UINT\* GetData( ) const; UINT\* GetData( );**|
|[CWordArray (Polski)](../../mfc/reference/cwordarray-class.md)|**const\* WORD GetData( ) const; WORD\* GetData( );**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]

## <a name="cobarraygetsize"></a><a name="getsize"></a>CObArray::GetSize

Zwraca rozmiar tablicy.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Uwagi

Ponieważ indeksy są oparte na wartościach zerowych, rozmiar jest o 1 większy niż największy indeks.

W poniższej tabeli przedstawiono `CObArray::GetSize`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetSize( ) const;**|
|[CdWordArray (CdWordArray)](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetSize( ) const;**|
|[Cptrarray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetSize( ) const;**|
|[CStringArray (Polski)](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetSize( ) const;**|
|[CUIntArray (CuIntArray)](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetSize( ) const;**|
|[CWordArray (Polski)](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetSize( ) const;**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]

## <a name="cobarraygetupperbound"></a><a name="getupperbound"></a>CObArray::GetUpperBound

Zwraca bieżącą górną granicę tej tablicy.

```
INT_PTR GetUpperBound() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks górnej granicy (zero-based).

### <a name="remarks"></a>Uwagi

Ponieważ indeksy tablicowe są oparte na wartości zero, `GetSize`ta funkcja zwraca wartość o 1 mniejszą niż .

Warunek `GetUpperBound( )` = -1 wskazuje, że tablica nie zawiera żadnych elementów.

W poniższej tabeli przedstawiono `CObArray::GetUpperBound`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[CdWordArray (CdWordArray)](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[Cptrarray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[CStringArray (Polski)](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[CUIntArray (CuIntArray)](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[CWordArray (Polski)](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetUpperBound( ) const;**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]

## <a name="cobarrayinsertat"></a><a name="insertat"></a>CObArray::Wstawianie

Wstawia element (lub wszystkie elementy w innej tablicy) w określonym indeksie.

```
void InsertAt(
    INT_PTR nIndex,
    CObject* newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CObArray* pNewArray);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks liczby całkowitej, który może być `GetUpperBound`większy niż wartość zwracana przez .

*nowyElement*<br/>
Wskaźnik, `CObject` który ma zostać umieszczony w tej tablicy. *NewElement* wartości NULL jest dozwolone.

*Ncount*<br/>
Liczba wstawienia tego elementu (wartość domyślna to 1).

*nStartIndex*<br/>
Indeks liczby całkowitej, który może być `GetUpperBound`większy niż wartość zwracana przez .

*pNewArray (Nienawisłość)*<br/>
Inna tablica, która zawiera elementy, które mają zostać dodane do tej tablicy.

### <a name="remarks"></a>Uwagi

Pierwsza wersja `InsertAt` wstawia jeden element (lub wiele kopii elementu) w określonym indeksie w tablicy. W procesie przesuwa się w górę (przez zwiększanie indeksu) istniejący element w tym indeksie i przesuwa się w górę wszystkie elementy nad nim.

Druga wersja wstawia wszystkie `CObArray` elementy z innej kolekcji, począwszy od pozycji *nStartIndex.*

Funkcja `SetAt` natomiast zastępuje jeden określony element tablicy i nie przesuwa żadnych elementów.

W poniższej tabeli przedstawiono `CObArray::InsertAt`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, BYTE** `newElement` **, int** `nCount` = **1 );**<br /><br /> **rzut( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CByteArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **rzut( CMemoryException\* );**|
|[CdWordArray (CdWordArray)](../../mfc/reference/cdwordarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, DWORD** `newElement` **, int** `nCount` = **1 );**<br /><br /> **rzut( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CDWordArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **rzut( CMemoryException\* );**|
|[Cptrarray](../../mfc/reference/cptrarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **, int** `nCount` = **1 );**<br /><br /> **rzut( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CPtrArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **rzut( CMemoryException\* );**|
|[CStringArray (Polski)](../../mfc/reference/cstringarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, LPCTSTR** `newElement` **, int** `nCount` **= 1 );**<br /><br /> **rzut( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CStringArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **rzut( CMemoryException\* );**|
|[CUIntArray (CuIntArray)](../../mfc/reference/cuintarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, UINT** `newElement` **, int** `nCount` = **1 );**<br /><br /> **rzut( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CUIntArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **rzut( CMemoryException\* );**|
|[CWordArray (Polski)](../../mfc/reference/cwordarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, WORD** `newElement` **, int** `nCount` = **1 );**<br /><br /> **rzut( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CWordArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **rzut( CMemoryException\* );**|

### <a name="example"></a>Przykład

  Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]

Wyniki tego programu są następujące:

```Output
InsertAt example: A CObArray with 3 elements
[0] = a CAge at $45C8 21
[1] = a CAge at $4646 30
[2] = a CAge at $4606 40
```

## <a name="cobarrayisempty"></a><a name="isempty"></a>CObArray::IsEmpty

Określa, czy tablica jest pusta.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli tablica jest pusta; w przeciwnym razie 0.

## <a name="cobarrayoperator--"></a><a name="operator_at"></a>CObArray::operator [ ]

Te operatory indeksu dolnego `SetAt` `GetAt` są wygodnym substytutem i funkcji.

```
CObject*& operator[](int_ptr nindex);
CObject* operator[](int_ptr nindex) const;
```

### <a name="remarks"></a>Uwagi

Pierwszy operator, wywoływany dla tablic, które nie są **const,** mogą być używane po prawej stronie (r-value) lub po lewej stronie (l-value) instrukcji przypisania. Drugi, wywoływany dla **const** tablice, mogą być używane tylko po prawej stronie.

Wersja debugowania biblioteki potwierdza, jeśli indeks dolny (po lewej lub prawej stronie instrukcji przypisania) jest poza granicami.

W poniższej tabeli przedstawiono `CObArray::operator []`inne operatory, które są podobne do .

|Klasa|Operator|
|-----------|--------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**BYTE& operator** `nindex` ** \)** [](int_ptr;<br /><br /> **Operator BYTE [](int_ptr** `nindex` ** \) const;**|
|[CdWordArray (CdWordArray)](../../mfc/reference/cdwordarray-class.md)|**OPERATOR& DWORD [](int_ptr** `nindex` ** \);**<br /><br /> **OPERATOR DWORD [](int_ptr** `nindex` ** \) const;**|
|[Cptrarray](../../mfc/reference/cptrarray-class.md)|**nieważne\*& operatora [](int_ptr** `nindex` ** \);**<br /><br /> **void\* operator [](int_ptr** `nindex` ** \) const;**|
|[CStringArray (Polski)](../../mfc/reference/cstringarray-class.md)|**Operator& sznurkowego [](int_ptr** `nindex` ** \);**<br /><br /> **Operator CString [](int_ptr** `nindex` ** \) const;**|
|[CUIntArray (CuIntArray)](../../mfc/reference/cuintarray-class.md)|**Operator& UINT [](int_ptr** `nindex` ** \);**<br /><br /> **Operator UINT [](int_ptr** `nindex` ** \) const;**|
|[CWordArray (Polski)](../../mfc/reference/cwordarray-class.md)|**OPERATOR WORD& [](int_ptr** `nindex` ** \);**<br /><br /> **operator WORD [](int_ptr** `nindex` ** \) const;**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]

## <a name="cobarrayremoveall"></a><a name="removeall"></a>CObArray::UsuńWszystki

Usuwa wszystkie wskaźniki z tej tablicy, ale `CObject` w rzeczywistości nie usuwa obiektów.

```
void RemoveAll();
```

### <a name="remarks"></a>Uwagi

Jeśli tablica jest już pusta, funkcja nadal działa.

Funkcja `RemoveAll` zwalnia całą pamięć używaną do przechowywania wskaźnika.

W poniższej tabeli przedstawiono `CObArray::RemoveAll`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**void RemoveAll( );**|
|[CdWordArray (CdWordArray)](../../mfc/reference/cdwordarray-class.md)|**void RemoveAll( );**|
|[Cptrarray](../../mfc/reference/cptrarray-class.md)|**void RemoveAll( );**|
|[CStringArray (Polski)](../../mfc/reference/cstringarray-class.md)|**void RemoveAll( );**|
|[CUIntArray (CuIntArray)](../../mfc/reference/cuintarray-class.md)|**void RemoveAll( );**|
|[CWordArray (Polski)](../../mfc/reference/cwordarray-class.md)|**void RemoveAll( );**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]

## <a name="cobarrayremoveat"></a><a name="removeat"></a>CObArray::Usuń

Usuwa jeden lub więcej elementów, począwszy od określonego indeksu w tablicy.

```
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0 i `GetUpperBound`mniejszy lub równy wartości zwracanej przez program .

*Ncount*<br/>
Liczba elementów do usunięcia.

### <a name="remarks"></a>Uwagi

W procesie przesuwa się w dół wszystkie elementy powyżej usuniętego elementu(-ów). Zmniejsza górną granicę tablicy, ale nie zwalnia pamięci.

Jeśli spróbujesz usunąć więcej elementów niż są zawarte w tablicy powyżej punktu usuwania, a następnie debugowania wersji biblioteki potwierdza.

Funkcja `RemoveAt` usuwa `CObject` wskaźnik z tablicy, ale nie usuwa samego obiektu.

W poniższej tabeli przedstawiono `CObArray::RemoveAt`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[CdWordArray (CdWordArray)](../../mfc/reference/cdwordarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[Cptrarray](../../mfc/reference/cptrarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[CStringArray (Polski)](../../mfc/reference/cstringarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[CUIntArray (CuIntArray)](../../mfc/reference/cuintarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[CWordArray (Polski)](../../mfc/reference/cwordarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** *nCount* = **1 );**|

### <a name="example"></a>Przykład

  Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]

Wyniki tego programu są następujące:

```Output
RemoveAt example: A CObArray with 1 elements
[0] = a CAge at $4606 40
```

## <a name="cobarraysetat"></a><a name="setat"></a>CObArray::SetAt

Ustawia element tablicy w określonym indeksie.

```
void SetAt(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0 i `GetUpperBound`mniejszy lub równy wartości zwracanej przez program .

*nowyElement*<br/>
Wskaźnik obiektu, który ma zostać wstawiony do tej tablicy. Wartość NULL jest dozwolona.

### <a name="remarks"></a>Uwagi

`SetAt`nie spowoduje, że tablica wzrośnie. Użyj, `SetAtGrow` jeśli ma być automatycznie powiększana tablica.

Należy upewnić się, że wartość indeksu reprezentuje prawidłową pozycję w tablicy. Jeśli jest poza granicami, a następnie debugowania wersji biblioteki potwierdza.

W poniższej tabeli przedstawiono `CObArray::SetAt`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**void SetAt( INT_PTR** `nIndex` **, BYTE** `newElement` **);**|
|[CdWordArray (CdWordArray)](../../mfc/reference/cdwordarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, DWORD** `newElement` **);**|
|[Cptrarray](../../mfc/reference/cptrarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **);**|
|[CStringArray (Polski)](../../mfc/reference/cstringarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**|
|[CUIntArray (CuIntArray)](../../mfc/reference/cuintarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, UINT** `newElement` **);**|
|[CWordArray (Polski)](../../mfc/reference/cwordarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, WORD** `newElement` **);**|

### <a name="example"></a>Przykład

  Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]

Wyniki tego programu są następujące:

```Output
SetAt example: A CObArray with 2 elements
[0] = a CAge at $47E0 30
[1] = a CAge at $47A0 40
```

## <a name="cobarraysetatgrow"></a><a name="setatgrow"></a>CObArray::SetAtGrow

Ustawia element tablicy w określonym indeksie.

```
void SetAtGrow(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0.

*nowyElement*<br/>
Wskaźnik obiektu, który ma zostać dodany do tej tablicy. Wartość NULL jest dozwolona.

### <a name="remarks"></a>Uwagi

Tablica rośnie automatycznie, jeśli to konieczne (oznacza to, że górna granica jest dostosowana do nowego elementu).

W poniższej tabeli przedstawiono `CObArray::SetAtGrow`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, BYTE** `newElement` **);**<br /><br /> **rzut( CMemoryException\* );**|
|[CdWordArray (CdWordArray)](../../mfc/reference/cdwordarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, DWORD** `newElement` **);**<br /><br /> **rzut( CMemoryException\* );**|
|[Cptrarray](../../mfc/reference/cptrarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **);**<br /><br /> **rzut( CMemoryException\* );**|
|[CStringArray (Polski)](../../mfc/reference/cstringarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**<br /><br /> **rzut( CMemoryException\* );**|
|[CUIntArray (CuIntArray)](../../mfc/reference/cuintarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, UINT** `newElement` **);**<br /><br /> **rzut( CMemoryException\* );**|
|[CWordArray (Polski)](../../mfc/reference/cwordarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, WORD** `newElement` **);**<br /><br /> **rzut( CMemoryException\* );**|

### <a name="example"></a>Przykład

  Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]

Wyniki tego programu są następujące:

```Output
SetAtGrow example: A CObArray with 4 elements
[0] = a CAge at $47C0 21
[1] = a CAge at $4800 40
[2] = NULL
[3] = a CAge at $4840 65
```

## <a name="cobarraysetsize"></a><a name="setsize"></a>CObArray::SetSize

Ustanawia rozmiar pustej lub istniejącej tablicy; przydziela pamięć, jeśli to konieczne.

```
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Parametry

*nNowy Rozmiar*<br/>
Nowy rozmiar tablicy (liczba elementów). Musi być równa 0 lub większa.

*nGrowBy ( nGrowBy )*<br/>
Minimalna liczba slotów elementu do przydzielenia, jeśli konieczne jest zwiększenie rozmiaru.

### <a name="remarks"></a>Uwagi

Jeśli nowy rozmiar jest mniejszy niż stary rozmiar, tablica jest obcinana i zwalniana jest cała nieużywana pamięć. Aby zwiększyć wydajność, wywołanie, `SetSize` aby ustawić rozmiar tablicy przed użyciem go. Zapobiega to konieczności ponownego przydzielenia i kopiowania tablicy za każdym razem, gdy element jest dodawany.

Parametr *nGrowBy* wpływa na alokację pamięci wewnętrznej, gdy tablica rośnie. Jego użycie nigdy nie wpływa na `GetSize` `GetUpperBound`rozmiar tablicy zgłoszony przez i .

Jeśli rozmiar tablicy wzrosła, wszystkie nowo przydzielone **wskaźniki CObject** <strong>\*</strong> są ustawione na NULL.

W poniższej tabeli przedstawiono `CObArray::SetSize`inne funkcje członkowskie, które są podobne do .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[Cbytearray](../../mfc/reference/cbytearray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1 );**<br /><br /> **rzut( CMemoryException\* );**|
|[CdWordArray (CdWordArray)](../../mfc/reference/cdwordarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1 );**<br /><br /> **rzut( CMemoryException\* );**|
|[Cptrarray](../../mfc/reference/cptrarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1 );**<br /><br /> **rzut( CMemoryException\* );**|
|[CStringArray (Polski)](../../mfc/reference/cstringarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1 );**<br /><br /> **rzut( CMemoryException\* );**|
|[CUIntArray (CuIntArray)](../../mfc/reference/cuintarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1 );**<br /><br /> **rzut( CMemoryException\* );**|
|[CWordArray (Polski)](../../mfc/reference/cwordarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1 );**<br /><br /> **rzut( CMemoryException\* );**|

### <a name="example"></a>Przykład

  Zobacz przykład [CObArray::GetData](#getdata).

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CStringArray](../../mfc/reference/cstringarray-class.md)<br/>
[Klasa CPtrArray](../../mfc/reference/cptrarray-class.md)<br/>
[Klasa CByteArray](../../mfc/reference/cbytearray-class.md)<br/>
[Klasa CWordArray](../../mfc/reference/cwordarray-class.md)<br/>
[Klasa CDWordArray](../../mfc/reference/cdwordarray-class.md)
