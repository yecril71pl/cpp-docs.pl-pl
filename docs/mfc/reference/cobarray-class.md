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
ms.openlocfilehash: 78d736b53a2febe4f4a026e3aaf9db14dd7f9c0b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392495"
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
|[CObArray::CObArray](#cobarray)|Tworzy się pusta tablica `CObject` wskaźników.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CObArray::Add](#add)|Dodaje element do końca tablicy; zwiększa rozmiar tablicy, jeśli to konieczne.|
|[CObArray::Append](#append)|Dołącza innej tablicy do tablicy; zwiększa rozmiar tablicy, jeśli to konieczne.|
|[CObArray::Copy](#copy)|Kopiuje innej tablicy do tablicy; zwiększa rozmiar tablicy, jeśli to konieczne.|
|[CObArray::ElementAt](#elementat)|Zwraca tymczasowe odwołanie do wskaźnika elementu w tablicy.|
|[CObArray::FreeExtra](#freeextra)|Zwalnia wszystkie nieużywanej pamięci powyżej bieżącego górną granicę.|
|[CObArray::GetAt](#getat)|Zwraca wartość pod danym indeksem.|
|[CObArray::GetCount](#getcount)|Pobiera liczbę elementów w tej tablicy.|
|[CObArray::GetData](#getdata)|Umożliwia dostęp do elementów w tablicy. Może mieć wartości NULL.|
|[CObArray::GetSize](#getsize)|Pobiera liczbę elementów w tej tablicy.|
|[CObArray::GetUpperBound](#getupperbound)|Zwraca największy nieprawidłowy indeks.|
|[CObArray::InsertAt](#insertat)|Wstawia element (lub wszystkie elementy w innej tablicy) z określonym indeksem.|
|[CObArray::IsEmpty](#isempty)|Określa, czy tablica jest pusta.|
|[CObArray::RemoveAll](#removeall)|Usuwa wszystkie elementy z tej tablicy.|
|[CObArray::RemoveAt](#removeat)|Usuwa element pod określonym indeksem.|
|[CObArray::SetAt](#setat)|Ustawia wartość dla podanego indeksu; Tablica nie może wzrosnąć.|
|[CObArray::SetAtGrow](#setatgrow)|Ustawia wartość dla podanego indeksu; zwiększa rozmiar tablicy, jeśli to konieczne.|
|[CObArray::SetSize](#setsize)|Ustawia liczbę elementów, które mają być zawarte w tej tablicy.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CObArray::operator \[ \]](#operator_at)|Ustawia lub pobiera element pod określonym indeksem.|

## <a name="remarks"></a>Uwagi

Te macierze obiektu przypominają tablice języka C, ale można dynamicznie zmniejszać i powiększać w razie.

Indeksy tablicy zawsze rozpoczynają się od pozycji 0. Możesz zdecydować, czy rozwiązać górną granicę lub zezwalać na tablicy rozwinąć po dodaniu elementów poza bieżącą granicą. Pamięć jest alokowana ciągłym górnej granicy, nawet jeśli niektóre elementy mają wartość null.

W obszarze Win32, rozmiar `CObArray` obiektu jest ograniczona tylko do dostępnej pamięci.

Podobnie jak w przypadku tablicy C, czas dostępu dla `CObArray` indeksowanego elementu jest stała i nie zależy od rozmiaru tablicy.

`CObArray` dołącza IMPLEMENT_SERIAL — makro do obsługi serializacji i zrzucanie z jego elementów. Jeśli tablica `CObject` wskaźniki są przechowywane do archiwum, za pomocą operatora przeciążona wstawiania lub za pomocą `Serialize` funkcję członkowską, każdy `CObject` elementu z kolei serializacji wraz z jego indeks tablicy.

Jeśli potrzebujesz zrzutu indywidualnego `CObject` elementów w tablicy, należy ustawić głębokość `CDumpContext` obiekt do 1 lub większą.

Gdy `CObArray` obiekt zostanie usunięty lub gdy jego elementy są usuwane, tylko `CObject` wskaźniki są usuwane i obiekty nie mogą odwoływać się.

> [!NOTE]
>  Przed rozpoczęciem korzystania z tablicy, należy użyć `SetSize` jej rozmiaru i przydzielanie pamięci dla niego. Jeśli nie używasz `SetSize`, dodawanie elementów do tablicy powoduje, że często ponownie przydzielane i skopiować. Częste ponowne przydzielenie kopiowania są nieefektywne i może fragmentu pamięci.

Wyprowadzanie klasy tablicy jest podobny do wyprowadzania listy. Aby uzyskać szczegółowe informacje dotyczące tworzenia elementów pochodnych klasy listy specjalnych, zobacz artykuł [kolekcje](../../mfc/collections.md).

> [!NOTE]
>  Jeśli zamierzasz serializacji tablicy, należy użyć IMPLEMENT_SERIAL — makro w implementacji klasy pochodnej.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CObArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll.h

##  <a name="add"></a>  CObArray::Add

Dodaje nowy element do końca tablicy, rośnie tablicy o 1.

```
INT_PTR Add(CObject* newElement);
```

### <a name="parameters"></a>Parametry

*newElement*<br/>
`CObject` Wskaźnika, które mają zostać dodane do tej tablicy.

### <a name="return-value"></a>Wartość zwracana

Indeks dodanego elementu.

### <a name="remarks"></a>Uwagi

Jeśli [SetSize](#setsize) został użyty z *nGrowBy* wartość większą niż 1, a następnie dodatkową pamięć, które mogą być przydzielone. Jednakże górna granica wzrosną tylko 1.

W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::Add`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Dodaj INT_PTR (BAJTÓW** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR Add( DWORD** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Dodaj INT_PTR (void** <strong>\*</strong> `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Dodaj INT_PTR (LPCTSTR** `newElement` **); throw (CMemoryException\* );**<br /><br /> **INT_PTR Add(const CString&** `newElement` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR Add( UINT** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Dodaj INT_PTR (program WORD** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|

### <a name="example"></a>Przykład

  Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.

[!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]

Wyniki z tego programu są następujące:

```Output
Add example: A CObArray with 2 elements
[0] = a CAge at $442A 21
[1] = a CAge at $4468 40
```

##  <a name="append"></a>  CObArray::Append

Wywołaj tę funkcję elementu członkowskiego, aby dodać zawartość innej tablicy na końcu danej tablicy.

```
INT_PTR Append(const CObArray& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
Źródło elementów do dołączenia do macierzy.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszy dołączony element.

### <a name="remarks"></a>Uwagi

Tablice muszą być tego samego typu.

Jeśli to konieczne, `Append` może przydzielić dodatkową pamięć, aby pomieścić elementów do tablicy.

W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::Append`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Dołącz INT_PTR (const CByteArray &** *src* **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Dołącz INT_PTR (const CDWordArray &** *src* **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Dołącz INT_PTR (const CPtrArray &** *src* **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Dołącz INT_PTR (const CStringArray &** *src* **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Dołącz INT_PTR (const CUIntArray &** *src* **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Dołącz INT_PTR (const CWordArray &** *src* **);**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.

[!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]

##  <a name="copy"></a>  CObArray::Copy

Wywołaj tę funkcję elementu członkowskiego w celu zastąpienia elementy danej tablicy elementów innej tablicy tego samego typu.

```
void Copy(const CObArray& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
Źródło elementów, które mają być kopiowane do tablicy.

### <a name="remarks"></a>Uwagi

`Copy` nie spowoduje zwolnienia pamięci. Jednakże, jeśli to konieczne, `Copy` może przydzielić dodatkową pamięć, aby pomieścić elementów kopiowanych z tablicą.

W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::Copy`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void Copy( const CByteArray&** *src* **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void kopiowania (const CDWordArray &** *src* **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void Copy( const CPtrArray&** *src* **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void kopiowania (const CStringArray &** *src* **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void kopiowania (const CUIntArray &** *src* **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void kopiowania (const CWordArray &** *src* **);**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.

[!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]

##  <a name="cobarray"></a>  CObArray::CObArray

Tworzy pustą `CObject` wskaźnika tablicy.

```
CObArray();
```

### <a name="remarks"></a>Uwagi

Tablica rośnie jeden element w danym momencie.

W poniższej tabeli przedstawiono inne konstruktory, które są podobne do `CObArray::CObArray`.

|Class|Konstruktor|
|-----------|-----------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**CByteArray( );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**CDWordArray( );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**CPtrArray( );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CStringArray ();**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**CUIntArray( );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**CWordArray( );**|

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]

##  <a name="elementat"></a>  CObArray::ElementAt

Zwraca tymczasowe odwołanie do wskaźnika elementu w tablicy.

```
CObject*& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez obiekt `GetUpperBound`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `CObject` wskaźnika.

### <a name="remarks"></a>Uwagi

Służy do implementowania operatora przypisania po lewej stronie macierzy. Należy zauważyć, że to zaawansowanych funkcji, które mają być używane tylko w celu wykonania operatory specjalne tablicy.

W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::ElementAt`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE& ElementAt( INT_PTR** `nIndex` **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD & ElementAt (INT_PTR** `nIndex` **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\*& ElementAt( INT_PTR** `nIndex` **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Cstring — & ElementAt (INT_PTR** `nIndex` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT & ElementAt (INT_PTR** `nIndex` **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Dla & ElementAt (INT_PTR** `nIndex` **);**|

### <a name="example"></a>Przykład

  Zobacz przykład [CObArray::GetSize](#getsize).

##  <a name="freeextra"></a>  CObArray::FreeExtra

Zwalnia dodatkową pamięć, która została przydzielona podczas został wzrosła tablicy.

```
void FreeExtra();
```

### <a name="remarks"></a>Uwagi

Ta funkcja nie ma wpływu na rozmiar lub górna granica tablicy.

W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::FreeExtra`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void FreeExtra( );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void FreeExtra( );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void FreeExtra( );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void FreeExtra( );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void FreeExtra( );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void FreeExtra( );**|

### <a name="example"></a>Przykład

  Zobacz przykład [CObArray::GetData](#getdata).

##  <a name="getat"></a>  CObArray::GetAt

Zwraca element tablicy o określonym indeksie.

```
CObject* GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez obiekt `GetUpperBound`.

### <a name="return-value"></a>Wartość zwracana

`CObject` Wskaźnika elementu obecnie pod tym indeksem.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Przekazywanie wartości ujemnej lub wartość większa niż wartość zwrócona przez obiekt `GetUpperBound` spowoduje niepowodzenie asercji.

W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::GetAt`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**GetAt BAJTÓW (INT_PTR** `nIndex` **) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD GetAt (INT_PTR** `nIndex` **) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\* GetAt (INT_PTR** `nIndex` **) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Cstring — GetAt (INT_PTR** `nIndex` **) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT GetAt (INT_PTR** `nIndex` **) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**GetAt programu WORD (INT_PTR** `nIndex` **) const;**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.

[!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]

##  <a name="getcount"></a>  CObArray::GetCount

Zwraca liczbę elementów tablicy.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w tablicy.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby pobrać liczbę elementów w tablicy. Ponieważ indeksy są od zera, rozmiar jest większy od największego indeksu 1.

W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::GetCount`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetCount () const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetCount () const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetCount () const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetCount () const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetCount () const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetCount () const;**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.

[!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]

##  <a name="getdata"></a>  CObArray::GetData

Użyj tej funkcji elementu członkowskiego do uzyskania bezpośredniego dostępu do elementów w tablicy.

```
const CObject** GetData() const;

CObject** GetData();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do tablicy `CObject` wskaźników.

### <a name="remarks"></a>Uwagi

Jeśli żadne elementy są dostępne, `GetData` zwraca wartość null.

Gdy bezpośredni dostęp do elementów tablicy pomoże szybciej, należy zachować ostrożność podczas wywoływania `GetData`; wszelkie błędy wprowadzone bezpośrednio wpływają na elementy tablicy.

W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::GetData`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Const BAJTÓW\* (const;) na GetData BAJT\* GetData ();**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Const DWORD\* GetData const (); DWORD\* GetData ();**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Stała wartość void\* \* (GetData) const; void\* \* GetData ();**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Const CString\* (const;) na GetData Cstring —\* GetData ();**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Const UINT\* (const;) na GetData UINT\* GetData ();**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Const WORD\* (const;) na GetData WORD\* GetData ();**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.

[!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]

##  <a name="getsize"></a>  CObArray::GetSize

Zwraca rozmiar tablicy.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Uwagi

Ponieważ indeksy są od zera, rozmiar jest większy od największego indeksu 1.

W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::GetSize`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR getsize — () const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR getsize — () const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR getsize — () const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR getsize — () const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR getsize — () const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR getsize — () const;**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.

[!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]

##  <a name="getupperbound"></a>  CObArray::GetUpperBound

Zwraca bieżący górną granicę tej tablicy.

```
INT_PTR GetUpperBound() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks (liczony od zera) górną granicę.

### <a name="remarks"></a>Uwagi

Ponieważ indeksy tablicy zaczynają się od zera, ta funkcja zwraca wartość 1 poniżej `GetSize`.

Warunek `GetUpperBound( )` = -1 oznacza, że tablica nie zawiera żadnych elementów.

W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::GetUpperBound`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetUpperBound () const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetUpperBound () const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetUpperBound () const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetUpperBound () const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetUpperBound () const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetUpperBound () const;**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.

[!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]

##  <a name="insertat"></a>  CObArray::InsertAt

Wstawia element (lub wszystkie elementy w innej tablicy) z określonym indeksem.

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

*nIndex*<br/>
Liczba całkowita indeksu, który może być większa niż wartość zwrócona przez obiekt `GetUpperBound`.

*newElement*<br/>
`CObject` Wskaźnika, które mają być umieszczone w tej tablicy. A *newElement* o wartości NULL jest dozwolona.

*nCount*<br/>
Liczba przypadków, gdy ten element powinien być wstawiany (wartość domyślna to 1).

*nStartIndex*<br/>
Liczba całkowita indeksu, który może być większa niż wartość zwrócona przez obiekt `GetUpperBound`.

*pNewArray*<br/>
Innej tablicy, która zawiera elementy, które mają zostać dodane do tej tablicy.

### <a name="remarks"></a>Uwagi

Pierwsza wersja `InsertAt` wstawia jednego elementu (lub wiele kopii elementu) od określonego indeksu tablicy. W procesie przenosi (przez zwiększanie indeks) istniejącego elementu w ten indeks, a przewiduje się wszystkie elementy, nad nim.

Druga wersja wstawia wszystkie elementy z innego `CObArray` kolekcji, zaczynając od *nStartIndex* pozycji.

`SetAt` Funkcji, z kolei zastępuje jeden element określonej tablicy i nie przesunięcia żadnych elementów.

W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::InsertAt`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, BAJT** `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CByteArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, DWORD** `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CDWordArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CPtrArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, LPCTSTR** `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CStringArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, UINT** `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CUIntArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, WORD** `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CWordArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|

### <a name="example"></a>Przykład

  Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.

[!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]

Wyniki z tego programu są następujące:

```Output
InsertAt example: A CObArray with 3 elements
[0] = a CAge at $45C8 21
[1] = a CAge at $4646 30
[2] = a CAge at $4606 40
```

##  <a name="isempty"></a>  CObArray::IsEmpty

Określa, czy tablica jest pusta.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli tablica jest pusta. w przeciwnym razie 0.

##  <a name="operator_at"></a>  [] CObArray::operator

Tych operatorów indeksu dolnego są wygodnym zastępuje `SetAt` i `GetAt` funkcji.

```
CObject*& operator[](int_ptr nindex);
CObject* operator[](int_ptr nindex) const;
```

### <a name="remarks"></a>Uwagi

Pierwszy operator wywoływane dla tablic, które nie są **const**, mogą być używane w prawo (r) lub (l wartość) po lewej stronie instrukcji przypisania. Druga Strona, wywołana dla **const** tablic, mogą być używane tylko po prawej stronie.

Wersja do debugowania biblioteki potwierdza, jeśli indeksu dolnego (albo po lewej lub prawej stronie instrukcji przypisania) jest poza zakresem.

W poniższej tabeli przedstawiono inne operatory, które są podobne do `CObArray::operator []`.

|Class|Operator|
|-----------|--------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE & — operator [] (int_ptr** `nindex`  **\);**<br /><br /> **BYTE — operator [] (int_ptr** `nindex`  **\) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD & — operator [] (int_ptr** `nindex`  **\);**<br /><br /> **DWORD operator [] (int_ptr** `nindex`  **\) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\*& — operator [] (int_ptr** `nindex`  **\);**<br /><br /> **void\* — operator [] (int_ptr** `nindex`  **\) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Cstring — & — operator [] (int_ptr** `nindex`  **\);**<br /><br /> **Cstring — operator [] (int_ptr** `nindex`  **\) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT & — operator [] (int_ptr** `nindex`  **\);**<br /><br /> **UINT operator [] (int_ptr** `nindex`  **\) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD & — operator [] (int_ptr** `nindex`  **\);**<br /><br /> **WORD operator [] (int_ptr** `nindex`  **\) const;**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.

[!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]

##  <a name="removeall"></a>  CObArray::RemoveAll

Usuwa wszystkie wskaźniki z tej tablicy, ale faktycznie nie usuwa `CObject` obiektów.

```
void RemoveAll();
```

### <a name="remarks"></a>Uwagi

Jeśli tablica jest pusty, funkcja jest nadal działa.

`RemoveAll` Funkcja zwalnia całą pamięć używana na potrzeby magazynu wskaźnika.

W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::RemoveAll`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAll( );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAll( );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAll( );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAll( );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAll( );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAll( );**|

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.

[!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]

##  <a name="removeat"></a>  CObArray::RemoveAt

Usuwa jeden lub więcej elementów, zaczynając od określonego indeksu tablicy.

```
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez obiekt `GetUpperBound`.

*nCount*<br/>
Liczba elementów do usunięcia.

### <a name="remarks"></a>Uwagi

W procesie jego przenosi w dół wszystkie elementy powyżej usunięto następującą liczbę elementów. Jego zmniejsza górnej granicy tablicy, ale nie spowoduje zwolnienia pamięci.

Jeśli próbujesz usunąć więcej elementów niż znajdują się w tablicy powyżej punktu usunięcie wersji do debugowania biblioteki potwierdzenia.

`RemoveAt` Funkcja usuwa `CObject` wskaźnika z tablicy, ale nie powoduje usunięcia samego obiektu.

W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::RemoveAt`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** *nCount* **= 1 );**|

### <a name="example"></a>Przykład

  Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.

[!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]

Wyniki z tego programu są następujące:

```Output
RemoveAt example: A CObArray with 1 elements
[0] = a CAge at $4606 40
```

##  <a name="setat"></a>  CObArray::SetAt

Ustawia element tablicy o określonym indeksie.

```
void SetAt(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez obiekt `GetUpperBound`.

*newElement*<br/>
Wskaźnik obiektu, który ma zostać wstawiony w tej tablicy. Wartość NULL jest dozwolona.

### <a name="remarks"></a>Uwagi

`SetAt` nie spowoduje, że tablica rośnie. Użyj `SetAtGrow` chcącym tablicy rośnie automatycznie.

Należy się upewnić, że wartość indeksu reprezentuje poprawnej pozycji w tablicy. Jeśli jest poza zakresem, wersja do debugowania biblioteki potwierdzenia.

W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::SetAt`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAt( INT_PTR** `nIndex` **, BYTE** `newElement` **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, DWORD** `newElement` **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, UINT** `newElement` **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, WORD** `newElement` **);**|

### <a name="example"></a>Przykład

  Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.

[!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]

Wyniki z tego programu są następujące:

```Output
SetAt example: A CObArray with 2 elements
[0] = a CAge at $47E0 30
[1] = a CAge at $47A0 40
```

##  <a name="setatgrow"></a>  CObArray::SetAtGrow

Ustawia element tablicy o określonym indeksie.

```
void SetAtGrow(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks liczby całkowitej, która jest większa lub równa 0.

*newElement*<br/>
Obiekt wskaźnika, który ma zostać dodany do tej tablicy. Wartość NULL jest dozwolona.

### <a name="remarks"></a>Uwagi

Tablica powiększa się automatycznie, jeśli to konieczne (górna granica jest dostosowane, aby pomieścić nowy element).

W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::SetAtGrow`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, BYTE** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, DWORD** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, UINT** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, WORD** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|

### <a name="example"></a>Przykład

  Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich przykładach w kolekcji.

[!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]

Wyniki z tego programu są następujące:

```Output
SetAtGrow example: A CObArray with 4 elements
[0] = a CAge at $47C0 21
[1] = a CAge at $4800 40
[2] = NULL
[3] = a CAge at $4840 65
```

##  <a name="setsize"></a>  CObArray::SetSize

Określa rozmiar tablicy pustego lub istniejącego; przydziela pamięć, jeśli to konieczne.

```
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Parametry

*nNewSize*<br/>
Nowy rozmiar tablicy (liczba elementów). Musi być większa lub równa 0.

*nGrowBy*<br/>
Minimalna liczba gniazd element do przydzielenia, jeśli konieczne jest zwiększenie rozmiaru.

### <a name="remarks"></a>Uwagi

Jeśli nowy rozmiar jest mniejszy niż stary rozmiar, tablica jest skracana i zwolnieniu wszystkich nieużywanej pamięci. W celu zwiększenia wydajności wywołań `SetSize` można ustawić rozmiar tablicy przed jego użyciem. Zapobiega to konieczność ponownego przydzielenia i skopiuj tablicy za każdym razem, gdy element zostanie dodany.

*NGrowBy* parametru wpływa na alokacji pamięci wewnętrznej, podczas gdy rośnie tablicy. Jego użycie nigdy nie wpływa na rozmiar tablicy zgłoszonej przez `GetSize` i `GetUpperBound`.

Jeśli rozmiar tablicy zwiększył się, wszystkie nowo przydzielone **CObject** <strong>\*</strong> wskaźniki są ustawione na wartość NULL.

W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::SetSize`.

|Class|Funkcja elementów członkowskich|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (CMemoryException\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (CMemoryException\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (CMemoryException\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (CMemoryException\* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (CMemoryException\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (CMemoryException\* );**|

### <a name="example"></a>Przykład

  Zobacz przykład [CObArray::GetData](#getdata).

## <a name="see-also"></a>Zobacz także

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CStringArray](../../mfc/reference/cstringarray-class.md)<br/>
[Klasa CPtrArray](../../mfc/reference/cptrarray-class.md)<br/>
[Klasa CByteArray](../../mfc/reference/cbytearray-class.md)<br/>
[Klasa CWordArray](../../mfc/reference/cwordarray-class.md)<br/>
[Klasa CDWordArray](../../mfc/reference/cdwordarray-class.md)
