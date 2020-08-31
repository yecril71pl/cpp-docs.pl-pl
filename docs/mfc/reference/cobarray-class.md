---
title: Klasa CObArray
description: Dokumentacja interfejsu API dla `CObArray` `MFC` klasy, która przechowuje `CObject` wskaźniki w tablicy.
ms.date: 08/27/2020
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
ms.openlocfilehash: cbc1799a9634b3d8c09077b755b8a097289460fd
ms.sourcegitcommit: c8f1605354724a13566bc3b0fac3c5d98265f1d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2020
ms.locfileid: "89062150"
---
# <a name="cobarray-class"></a>Klasa CObArray

Obsługuje tablice `CObject` wskaźników.

## <a name="syntax"></a>Składnia

```cpp
class CObArray : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CObArray::CObArray](#cobarray)|Konstruuje pustą tablicę dla `CObject` wskaźników.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CObArray:: Add](#add)|Dodaje element na końcu tablicy; w razie potrzeby powiększa tablicę.|
|[CObArray:: Append](#append)|Dołącza kolejną tablicę do tablicy; w razie potrzeby powiększa tablicę.|
|[CObArray:: Copy](#copy)|Kopiuje kolejną tablicę do tablicy; w razie potrzeby powiększa tablicę.|
|[CObArray::ElementAt](#elementat)|Zwraca tymczasowe odwołanie do wskaźnika elementu w tablicy.|
|[CObArray::FreeExtra](#freeextra)|Zwalnia wszystkie nieużywane pamięci powyżej bieżącej górnej granicy.|
|[CObArray::GetAt](#getat)|Zwraca wartość w danym indeksie.|
|[CObArray:: GetCount](#getcount)|Pobiera liczbę elementów w tej tablicy.|
|[CObArray:: GetData](#getdata)|Umożliwia dostęp do elementów w tablicy. Może być `NULL` .|
|[CObArray:: GetSize](#getsize)|Pobiera liczbę elementów w tej tablicy.|
|[CObArray::GetUpperBound](#getupperbound)|Zwraca największy prawidłowy indeks.|
|[CObArray::InsertAt](#insertat)|Wstawia element (lub wszystkie elementy w innej tablicy) o określonym indeksie.|
|[CObArray:: IsEmpty](#isempty)|Określa, czy tablica jest pusta.|
|[CObArray::](#removeall)|Usuwa wszystkie elementy z tej tablicy.|
|[CObArray::RemoveAt](#removeat)|Usuwa element z określonym indeksem.|
|[CObArray::SetAt](#setat)|Ustawia wartość dla danego indeksu; Tablica nie może być większa.|
|[CObArray::SetAtGrow](#setatgrow)|Ustawia wartość dla danego indeksu; w razie potrzeby powiększa tablicę.|
|[CObArray:: setSize](#setsize)|Ustawia liczbę elementów, które mają być zawarte w tej tablicy.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CObArray:: operator \[\]](#operator_at)|Ustawia lub pobiera element pod określonym indeksem.|

## <a name="remarks"></a>Uwagi

Te tablice obiektów są podobne do tablic C, ale mogą być dynamicznie zmniejszane i zwiększane w razie potrzeby.

Indeksy tablicy zawsze zaczynają się na pozycji 0. Możesz zdecydować, czy chcesz naprawić górną granicę, czy zezwolić, aby tablica została rozwinięta, gdy dodasz elementy poza bieżącą granicą. Pamięć jest przydzielono w sposób ciągły do górnej granicy, nawet jeśli niektóre elementy są `NULL` .

W obszarze Win32 rozmiar `CObArray` obiektu jest ograniczony tylko do dostępnej pamięci.

Podobnie jak w przypadku tablicy języka C, czas dostępu dla `CObArray` indeksowanego elementu jest stały i jest niezależny od rozmiaru tablicy.

`CObArray` obejmuje IMPLEMENT_SERIAL makro do obsługi serializacji i dumpingu jego elementów. Jeśli tablica `CObject` wskaźników jest przechowywana w archiwum, z przeciążonym operatorem wstawiania lub `Serialize` funkcją składową, każdy `CObject` element jest z kolei serializowany wraz z jego indeksem tablicy.

Jeśli potrzebujesz zrzutu poszczególnych `CObject` elementów w tablicy, musisz ustawić głębokość `CDumpContext` obiektu na 1 lub większą.

Po `CObArray` usunięciu obiektu lub po usunięciu jego elementów `CObject` są usuwane tylko te wskaźniki, a nie obiekty, do których się odwołują.

> [!NOTE]
> Przed użyciem tablicy należy użyć, `SetSize` Aby określić jej rozmiar i przydzielić pamięć. Jeśli nie używasz `SetSize` , dodawanie elementów do tablicy powoduje, że jest on często ponownie alokowany i kopiowany. Częste ponowne przydzielanie i kopiowanie są niewydajne i mogą fragmentację pamięci.

Klasa pochodna klasy Array jest podobna do pochodnej listy. Aby uzyskać szczegółowe informacje na temat wyprowadzania klasy listy specjalnego przeznaczenia, zobacz [kolekcje](../../mfc/collections.md)artykułów.

> [!NOTE]
> Aby serializować tablicę, należy użyć makra IMPLEMENT_SERIAL w implementacji klasy pochodnej.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CObArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll. h

## <a name="cobarrayadd"></a><a name="add"></a> CObArray:: Add

Dodaje nowy element na końcu tablicy, zwiększając tablicę o 1.

```cpp
INT_PTR Add(CObject* newElement);
```

### <a name="parameters"></a>Parametry

*newElement*\
`CObject`Wskaźnik, który ma zostać dodany do tej tablicy.

### <a name="return-value"></a>Wartość zwracana

Indeks dodanego elementu.

### <a name="remarks"></a>Uwagi

Jeśli wartość [SetSize](#setsize) została użyta z wartością *nGrowBy* większą niż 1, może zostać przypisana dodatkowa pamięć. Górna granica zostanie jednak zwiększona o 1.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObArray::Add` .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`INT_PTR Add(BYTE newElement);`<br /><br />`throw(CMemoryException*);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`INT_PTR Add(DWORD newElement);`<br /><br />`throw(CMemoryException*);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`INT_PTR Add(void* newElement);`<br /><br />`throw(CMemoryException*);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`INT_PTR Add(LPCTSTR newElement); throw(CMemoryException*);`<br /><br />`INT_PTR Add(const CString& newElement);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`INT_PTR Add(UINT newElement);`<br /><br />`throw(CMemoryException*);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`INT_PTR Add(WORD newElement);`<br /><br />`throw(CMemoryException*);`|

### <a name="example"></a>Przykład

  Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą `CAge` klasy używanej we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]

Wyniki z tego programu są następujące:

```Output
Add example: A CObArray with 2 elements
[0] = a CAge at $442A 21
[1] = a CAge at $4468 40
```

## <a name="cobarrayappend"></a><a name="append"></a> CObArray:: Append

Wywołaj tę funkcję elementu członkowskiego, aby dodać zawartość innej tablicy na końcu danej tablicy.

```cpp
INT_PTR Append(const CObArray& src);
```

### <a name="parameters"></a>Parametry

*SRC*\
Źródło elementów do dołączenia do tablicy.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszego dołączonego elementu.

### <a name="remarks"></a>Uwagi

Tablice muszą być tego samego typu.

W razie potrzeby `Append` może przydzielić dodatkową pamięć, aby pomieścić elementy dołączone do tablicy.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObArray::Append` .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`INT_PTR Append(const CByteArray& src);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`INT_PTR Append(const CDWordArray& src);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`INT_PTR Append(const CPtrArray& src);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`INT_PTR Append(const CStringArray& src);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`INT_PTR Append(const CUIntArray& src);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`INT_PTR Append(const CWordArray& src);`|

### <a name="example"></a>Przykład

Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą `CAge` klasy używanej we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]

## <a name="cobarraycopy"></a><a name="copy"></a> CObArray:: Copy

Wywołaj tę funkcję elementu członkowskiego, aby zastąpić elementy danej tablicy elementami innej tablicy tego samego typu.

```cpp
void Copy(const CObArray& src);
```

### <a name="parameters"></a>Parametry

*SRC*\
Źródło elementów, które mają zostać skopiowane do tablicy.

### <a name="remarks"></a>Uwagi

`Copy` brak wolnej pamięci. W razie potrzeby `Copy` może przydzielić dodatkową pamięć, aby pomieścić elementy skopiowane do tablicy.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObArray::Copy` .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void Copy(const CByteArray& src);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void Copy(const CDWordArray& src);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void Copy(const CPtrArray& src);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void Copy(const CStringArray& src);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void Copy(const CUIntArray& src);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void Copy(const CWordArray& src);`|

### <a name="example"></a>Przykład

Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą `CAge` klasy używanej we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]

## <a name="cobarraycobarray"></a><a name="cobarray"></a> CObArray::CObArray

Konstruuje pustą `CObject` tablicę wskaźników.

```cpp
CObArray();
```

### <a name="remarks"></a>Uwagi

Tablica powiększa jeden element jednocześnie.

W poniższej tabeli przedstawiono inne konstruktory podobne do programu `CObArray::CObArray` .

|Klasa|Konstruktor|
|-----------|-----------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`CByteArray();`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`CDWordArray();`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`CPtrArray();`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`CStringArray();`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`CUIntArray();`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`CWordArray();`|

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]

## <a name="cobarrayelementat"></a><a name="elementat"></a> CObArray::ElementAt

Zwraca tymczasowe odwołanie do wskaźnika elementu w tablicy.

```cpp
CObject*& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*\
Indeks liczby całkowitej, który jest większy lub równy 0 i mniejszy lub równy wartości zwracanej przez `GetUpperBound` .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `CObject` wskaźnika.

### <a name="remarks"></a>Uwagi

Służy do implementacji operatora przypisania lewej strony dla tablic. Jest to funkcja zaawansowana, która powinna być używana tylko do implementowania specjalnych operatorów tablicowych.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObArray::ElementAt` .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`BYTE& ElementAt(INT_PTR nIndex);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`DWORD& ElementAt(INT_PTR nIndex);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void*& ElementAt(INT_PTR nIndex);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`CString& ElementAt(INT_PTR nIndex);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`UINT& ElementAt(INT_PTR nIndex);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`WORD& ElementAt(INT_PTR nIndex);`|

### <a name="example"></a>Przykład

Zobacz przykład dla [CObArray:: GetSize](#getsize).

## <a name="cobarrayfreeextra"></a><a name="freeextra"></a> CObArray::FreeExtra

Zwalnia wszelkie dodatkowe pamięci, które zostały przydzieloną podczas uprawy tablicy.

```cpp
void FreeExtra();
```

### <a name="remarks"></a>Uwagi

Ta funkcja nie ma wpływu na rozmiar ani górną granicę tablicy.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObArray::FreeExtra` .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void FreeExtra();`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void FreeExtra();`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void FreeExtra();`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void FreeExtra();`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void FreeExtra();`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void FreeExtra();`|

### <a name="example"></a>Przykład

  Zobacz przykład dla [CObArray:: GetData](#getdata).

## <a name="cobarraygetat"></a><a name="getat"></a> CObArray::GetAt

Zwraca element array o określonym indeksie.

```cpp
CObject* GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*\
Indeks liczby całkowitej, który jest większy lub równy 0 i mniejszy lub równy wartości zwracanej przez `GetUpperBound` .

### <a name="return-value"></a>Wartość zwracana

`CObject`Element wskaźnika aktualnie na tym indeksie.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Przekazanie wartości ujemnej lub wartości większej niż wartość zwrócona przez `GetUpperBound` spowoduje niepowodzenie potwierdzenia.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObArray::GetAt` .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`BYTE GetAt(INT_PTR nIndex) const;`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`DWORD GetAt(INT_PTR nIndex) const;`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void* GetAt(INT_PTR nIndex) const;`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`CString GetAt(INT_PTR nIndex) const;`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`UINT GetAt(INT_PTR nIndex) const;`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`WORD GetAt(INT_PTR nIndex) const;`|

### <a name="example"></a>Przykład

Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą `CAge` klasy używanej we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]

## <a name="cobarraygetcount"></a><a name="getcount"></a> CObArray:: GetCount

Zwraca liczbę elementów tablicy.

```cpp
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w tablicy.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby pobrać liczbę elementów w tablicy. Ponieważ indeksy są oparte na zero, rozmiar jest większy niż największy indeks.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObArray::GetCount` .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`INT_PTR GetCount() const;`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`INT_PTR GetCount() const;`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`INT_PTR GetCount() const;`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`INT_PTR GetCount() const;`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`INT_PTR GetCount() const;`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`INT_PTR GetCount() const;`|

### <a name="example"></a>Przykład

Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą `CAge` klasy używanej we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]

## <a name="cobarraygetdata"></a><a name="getdata"></a> CObArray:: GetData

Użyj tej funkcji elementu członkowskiego, aby uzyskać bezpośredni dostęp do elementów w tablicy.

```cpp
const CObject** GetData() const;

CObject** GetData();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do tablicy `CObject` wskaźników.

### <a name="remarks"></a>Uwagi

Jeśli żadne elementy nie są dostępne, `GetData` Funkcja zwraca `NULL` wartość.

Mimo że bezpośredni dostęp do elementów tablicy może ułatwić pracę szybciej, należy zachować ostrożność podczas wywoływania `GetData` ; wszelkie błędy wprowadzane bezpośrednio mają wpływ na elementy tablicy.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObArray::GetData` .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`const BYTE* GetData() const; BYTE* GetData();`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`const DWORD* GetData() const; DWORD* GetData();`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`const void** GetData() const; void** GetData();`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`const CString* GetData() const; CString* GetData();`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`const UINT* GetData() const; UINT* GetData();`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`const WORD* GetData() const; WORD* GetData();`|

### <a name="example"></a>Przykład

Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą `CAge` klasy używanej we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]

## <a name="cobarraygetsize"></a><a name="getsize"></a> CObArray:: GetSize

Zwraca rozmiar tablicy.

```cpp
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Uwagi

Ponieważ indeksy są oparte na zero, rozmiar jest większy niż największy indeks.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObArray::GetSize` .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`INT_PTR GetSize() const;`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`INT_PTR GetSize() const;`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`INT_PTR GetSize() const;`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`INT_PTR GetSize() const;`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`INT_PTR GetSize() const;`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`INT_PTR GetSize() const;`|

### <a name="example"></a>Przykład

Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą `CAge` klasy używanej we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]

## <a name="cobarraygetupperbound"></a><a name="getupperbound"></a> CObArray::GetUpperBound

Zwraca bieżącą górną granicę tej tablicy.

```cpp
INT_PTR GetUpperBound() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks górnej granicy (liczony od zera).

### <a name="remarks"></a>Uwagi

Ponieważ indeksy tablicy są oparte na zero, ta funkcja zwraca wartość 1 mniejszą niż `GetSize` .

Warunek `GetUpperBound() = -1` wskazuje, że tablica nie zawiera żadnych elementów.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObArray::GetUpperBound` .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`INT_PTR GetUpperBound() const;`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`INT_PTR GetUpperBound() const;`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`INT_PTR GetUpperBound() const;`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`INT_PTR GetUpperBound() const;`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`INT_PTR GetUpperBound() const;`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`INT_PTR GetUpperBound() const;`|

### <a name="example"></a>Przykład

Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą `CAge` klasy używanej we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]

## <a name="cobarrayinsertat"></a><a name="insertat"></a> CObArray::InsertAt

Wstawia element (lub wszystkie elementy w innej tablicy) o określonym indeksie.

```cpp
void InsertAt(
    INT_PTR nIndex,
    CObject* newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CObArray* pNewArray);
```

### <a name="parameters"></a>Parametry

*nIndex*\
Indeks liczby całkowitej, który może być większy niż wartość zwrócona przez `GetUpperBound` .

*newElement*\
`CObject`Wskaźnik, który ma zostać umieszczony w tej tablicy. *NewElement* wartości `NULL` jest dozwolony.

*nCount*\
Liczba przypadków wstawienia tego elementu (wartość domyślna to 1).

*nStartIndex*\
Indeks liczby całkowitej, który może być większy niż wartość zwrócona przez `GetUpperBound` .

*pNewArray*\
Inna tablica zawierająca elementy, które mają zostać dodane do tej tablicy.

### <a name="remarks"></a>Uwagi

Pierwsza wersja `InsertAt` wstawia jeden element (lub wiele kopii elementu) o określonym indeksie w tablicy. W procesie zostaje on przesunięty w górę (przez zwiększenie indeksu) istniejący element w tym indeksie i przesunie wszystkie elementy znajdujące się powyżej.

Druga wersja wstawia wszystkie elementy z innej `CObArray` kolekcji, rozpoczynając od pozycji *nStartIndex* .

`SetAt`Funkcja, w przeciwieństwie, zastępuje jeden określony element tablicy i nie przesuwa żadnych elementów.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObArray::InsertAt` .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void InsertAt(INT_PTR nIndex, BYTE newElement, int nCount = 1);`<br /><br />`throw(CMemoryException*);`<br /><br />`void InsertAt(INT_PTR nStartIndex, CByteArray* pNewArray);`<br /><br />`throw(CMemoryException*);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void InsertAt(INT_PTR nIndex, DWORD newElement, int nCount = 1);`<br /><br />`throw(CMemoryException*);`<br /><br />`void InsertAt(INT_PTR nStartIndex, CDWordArray* pNewArray);`<br /><br />`throw(CMemoryException*);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void InsertAt(INT_PTR nIndex, void* newElement, int nCount = 1);`<br /><br />`throw(CMemoryException*);`<br /><br />`void InsertAt(INT_PTR nStartIndex, CPtrArray* pNewArray);`<br /><br />`throw(CMemoryException*);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void InsertAt(INT_PTR nIndex, LPCTSTR newElement, int nCount = 1);`<br /><br />`throw(CMemoryException*);`<br /><br />`void InsertAt(INT_PTR nStartIndex, CStringArray* pNewArray);`<br /><br />`throw(CMemoryException*);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void InsertAt(INT_PTR nIndex, UINT newElement, int nCount = 1);`<br /><br />`throw(CMemoryException*);`<br /><br />`void InsertAt(INT_PTR nStartIndex, CUIntArray* pNewArray);`<br /><br />`throw(CMemoryException*);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void InsertAt(INT_PTR nIndex, WORD newElement, int nCount = 1);`<br /><br />`throw(CMemoryException*);`<br /><br />`void InsertAt(INT_PTR nStartIndex, CWordArray* pNewArray);`<br /><br />`throw(CMemoryException*);`|

### <a name="example"></a>Przykład

  Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą `CAge` klasy używanej we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]

Wyniki z tego programu są następujące:

```Output
InsertAt example: A CObArray with 3 elements
[0] = a CAge at $45C8 21
[1] = a CAge at $4646 30
[2] = a CAge at $4606 40
```

## <a name="cobarrayisempty"></a><a name="isempty"></a> CObArray:: IsEmpty

Określa, czy tablica jest pusta.

```cpp
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli tablica jest pusta; w przeciwnym razie 0.

## <a name="cobarrayoperator--"></a><a name="operator_at"></a> CObArray:: operator []

Te operatory indeksów dolnych są wygodnym substytutem `SetAt` dla `GetAt` funkcji i.

```cpp
CObject*& operator[](int_ptr nindex);
CObject* operator[](int_ptr nindex) const;
```

### <a name="remarks"></a>Uwagi

Pierwszy operator, wywoływany dla tablic, które nie **`const`** jest, może być używany po prawej stronie (r-Value) lub lewej (l-wartości) instrukcji przypisania. Sekunda, wywołana dla **`const`** tablic, może być używana tylko po prawej stronie.

Wersja debugowania biblioteki potwierdza, czy indeks dolny (w lewej lub prawej stronie instrukcji przypisania) znajduje się poza zakresem.

W poniższej tabeli przedstawiono inne operatory podobne do programu `CObArray::operator []` .

|Klasa|Operator|
|-----------|--------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`BYTE& operator [](INT_PTR nindex);`<br /><br />`BYTE operator [](INT_PTR nindex) const;`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`DWORD& operator [](INT_PTR nindex);`<br /><br />`DWORD operator [](INT_PTR nindex) const;`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void*& operator [](INT_PTR nindex);`<br /><br />`void* operator [](INT_PTR nindex) const;`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`CString& operator [](INT_PTR nindex);`<br /><br />`CString operator [](INT_PTR nindex) const;`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`UINT& operator [](INT_PTR nindex);`<br /><br />`UINT operator [](INT_PTR nindex) const;`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`WORD& operator [](INT_PTR nindex);`<br /><br />`WORD operator [](INT_PTR nindex) const;`|

### <a name="example"></a>Przykład

Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą `CAge` klasy używanej we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]

## <a name="cobarrayremoveall"></a><a name="removeall"></a> CObArray::

Usuwa wszystkie wskaźniki z tej tablicy, ale w rzeczywistości nie usuwa `CObject` obiektów.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Uwagi

Jeśli tablica jest już pusta, funkcja nadal działa.

`RemoveAll`Funkcja zwalnia wszystkie pamięci używane do przechowywania wskaźnika.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObArray::RemoveAll` .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void RemoveAll();`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void RemoveAll();`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void RemoveAll();`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void RemoveAll();`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void RemoveAll();`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void RemoveAll();`|

### <a name="example"></a>Przykład

Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą `CAge` klasy używanej we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]

## <a name="cobarrayremoveat"></a><a name="removeat"></a> CObArray::RemoveAt

Usuwa jeden lub więcej elementów, zaczynając od określonego indeksu w tablicy.

```cpp
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Parametry

*nIndex*\
Indeks liczby całkowitej, który jest większy lub równy 0 i mniejszy lub równy wartości zwracanej przez `GetUpperBound` .

*nCount*\
Liczba elementów do usunięcia.

### <a name="remarks"></a>Uwagi

W procesie przesunie wszystkie elementy powyżej usuniętych elementów. Zmniejsza górną granicę tablicy, ale nie zwalnia pamięci.

Jeśli spróbujesz usunąć więcej elementów niż znajduje się w tablicy powyżej punktu usuwania, wówczas wersja do debugowania zostanie przeszukana w bibliotece.

`RemoveAt`Funkcja usuwa `CObject` wskaźnik z tablicy, ale nie usuwa samego obiektu.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObArray::RemoveAt` .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void RemoveAt(INT_PTR nIndex, INT_PTR nCount = 1);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void RemoveAt(INT_PTR nIndex, INT_PTR nCount = 1);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void RemoveAt(INT_PTR nIndex, INT_PTR nCount = 1);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void RemoveAt(INT_PTR nIndex, INT_PTR nCount = 1);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void RemoveAt(INT_PTR nIndex, INT_PTR nCount = 1);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void RemoveAt(INT_PTR nIndex, INT_PTR nCount = 1);`|

### <a name="example"></a>Przykład

  Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą `CAge` klasy używanej we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]

Wyniki z tego programu są następujące:

```Output
RemoveAt example: A CObArray with 1 elements
[0] = a CAge at $4606 40
```

## <a name="cobarraysetat"></a><a name="setat"></a> CObArray::SetAt

Ustawia element Array pod określonym indeksem.

```cpp
void SetAt(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*\
Indeks liczby całkowitej, który jest większy lub równy 0 i mniejszy lub równy wartości zwracanej przez `GetUpperBound` .

*newElement*\
Wskaźnik obiektu, który ma zostać wstawiony do tej tablicy. `NULL`Dozwolona jest wartość.

### <a name="remarks"></a>Uwagi

`SetAt` nie spowoduje wzrostu rozmiaru tablicy. Użyj `SetAtGrow` , jeśli chcesz, aby tablica była powiększana automatycznie.

Upewnij się, że wartość indeksu reprezentuje prawidłową pozycję w tablicy. Jeśli jest poza zakresem, wówczas wersja do debugowania zostanie przeprowadzona.

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObArray::SetAt` .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void SetAt(INT_PTR nIndex, BYTE newElement);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void SetAt(INT_PTR nIndex, DWORD newElement);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void SetAt(INT_PTR nIndex, void* newElement);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void SetAt(INT_PTR nIndex, LPCTSTR newElement);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void SetAt(INT_PTR nIndex, UINT newElement);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void SetAt(INT_PTR nIndex, WORD newElement);`|

### <a name="example"></a>Przykład

  Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą `CAge` klasy używanej we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]

Wyniki z tego programu są następujące:

```Output
SetAt example: A CObArray with 2 elements
[0] = a CAge at $47E0 30
[1] = a CAge at $47A0 40
```

## <a name="cobarraysetatgrow"></a><a name="setatgrow"></a> CObArray::SetAtGrow

Ustawia element Array pod określonym indeksem.

```cpp
void SetAtGrow(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*\
Indeks liczby całkowitej, który jest większy lub równy 0.

*newElement*\
Wskaźnik obiektu, który ma zostać dodany do tej tablicy. `NULL`Dozwolona jest wartość.

### <a name="remarks"></a>Uwagi

Tablica powiększa się automatycznie w razie potrzeby (to znaczy górną granicę dostosowuje się w celu uwzględnienia nowego elementu).

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObArray::SetAtGrow` .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void SetAtGrow(INT_PTR nIndex, BYTE newElement);`<br /><br />`throw(CMemoryException*);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void SetAtGrow(INT_PTR nIndex, DWORD newElement);`<br /><br />`throw(CMemoryException*);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void SetAtGrow(INT_PTR nIndex, void* newElement);`<br /><br />`throw( CMemoryException*);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void SetAtGrow(INT_PTR nIndex, LPCTSTR newElement);`<br /><br />`throw(CMemoryException*);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void SetAtGrow(INT_PTR nIndex, UINT newElement);`<br /><br />`throw(CMemoryException*);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void SetAtGrow(INT_PTR nIndex, WORD newElement);`<br /><br />`throw(CMemoryException*);`|

### <a name="example"></a>Przykład

  Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą `CAge` klasy używanej we wszystkich przykładach kolekcji.

[!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]

Wyniki z tego programu są następujące:

```Output
SetAtGrow example: A CObArray with 4 elements
[0] = a CAge at $47C0 21
[1] = a CAge at $4800 40
[2] = NULL
[3] = a CAge at $4840 65
```

## <a name="cobarraysetsize"></a><a name="setsize"></a> CObArray:: setSize

Ustala rozmiar pustej lub istniejącej tablicy; przydziela pamięć w razie potrzeby.

```cpp
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Parametry

*nNewSize*\
Nowy rozmiar tablicy (liczba elementów). Musi być równa 0 lub większa.

*nGrowBy*\
Minimalna liczba gniazd elementów do przydzielenia w przypadku konieczności zwiększenia rozmiaru.

### <a name="remarks"></a>Uwagi

Jeśli nowy rozmiar jest mniejszy niż stary rozmiar, tablica zostanie obcięta, a cała niewykorzystana pamięć zostanie wydzielona. W celu uzyskania sprawności należy wywołać `SetSize` ustawienie rozmiaru tablicy przed jej użyciem. Zapobiega to konieczności ponownej alokacji i kopiowania tablicy za każdym razem, gdy element zostanie dodany.

Parametr *nGrowBy* ma wpływ na alokację pamięci wewnętrznej podczas wzrostu tablicy. Jego użycie nigdy nie wpływa na rozmiar tablicy raportowany przez `GetSize` i `GetUpperBound` .

Jeśli rozmiar tablicy wzrosną, wszystkie nowo przyłączone `CObject *` wskaźniki są ustawione na `NULL` .

W poniższej tabeli przedstawiono inne funkcje członkowskie, które są podobne do `CObArray::SetSize` .

|Klasa|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void SetSize(INT_PTR nNewSize, int nGrowBy = -1);`<br /><br /> `throw(CMemoryException*);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void SetSize(INT_PTR nNewSize, int nGrowBy = -1);`<br /><br /> `throw(CMemoryException*);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void SetSize(INT_PTR nNewSize, int nGrowBy = -1);`<br /><br /> `throw(CMemoryException*);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void SetSize(INT_PTR nNewSize, int nGrowBy = -1);`<br /><br /> `throw(CMemoryException*);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void SetSize(INT_PTR nNewSize, int nGrowBy = -1);`<br /><br /> `throw(CMemoryException*);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void SetSize(INT_PTR nNewSize, int nGrowBy = -1);`<br /><br /> `throw(CMemoryException*);`|

### <a name="example"></a>Przykład

  Zobacz przykład dla [CObArray:: GetData](#getdata).

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)\
[Wykres hierarchii](../../mfc/hierarchy-chart.md)\
[Klasa CStringArray](../../mfc/reference/cstringarray-class.md)\
[Klasa CPtrArray](../../mfc/reference/cptrarray-class.md)\
[Klasa CByteArray](../../mfc/reference/cbytearray-class.md)\
[Klasa CWordArray](../../mfc/reference/cwordarray-class.md)\
[Klasa CDWordArray](../../mfc/reference/cdwordarray-class.md)
