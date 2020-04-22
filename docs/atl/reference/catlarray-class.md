---
title: Klasa CAtlArray
ms.date: 11/04/2016
f1_keywords:
- CAtlArray
- ATLCOLL/ATL::CAtlArray
- ATLCOLL/ATL::Add
- ATLCOLL/ATL::Append
- ATLCOLL/ATL::AssertValid
- ATLCOLL/ATL::Copy
- ATLCOLL/ATL::FreeExtra
- ATLCOLL/ATL::GetAt
- ATLCOLL/ATL::GetCount
- ATLCOLL/ATL::GetData
- ATLCOLL/ATL::InsertArrayAt
- ATLCOLL/ATL::InsertAt
- ATLCOLL/ATL::IsEmpty
- ATLCOLL/ATL::RemoveAll
- ATLCOLL/ATL::RemoveAt
- ATLCOLL/ATL::SetAt
- ATLCOLL/ATL::SetAtGrow
- ATLCOLL/ATL::SetCount
- ATLCOLL/ATL::INARGTYPE
- ATLCOLL/ATL::OUTARGTYPE
helpviewer_keywords:
- CAtlArray class
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
ms.openlocfilehash: 607af2adaa3ef28a768812f3c811eb2ed3169ad9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748791"
---
# <a name="catlarray-class"></a>Klasa CAtlArray

Ta klasa implementuje obiekt tablicy.

## <a name="syntax"></a>Składnia

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```

#### <a name="parameters"></a>Parametry

*E*<br/>
Typ danych, które mają być przechowywane w tablicy.

*ETraits ( eTraits )*<br/>
Kod używany do kopiowania lub przenoszenia elementów.

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Dodaj](#add)|Wywołanie tej metody, aby dodać element do obiektu tablicy.|
|[Append](#append)|Wywołanie tej metody, aby dodać zawartość jednej tablicy na końcu innego.|
|[Assertvalid](#assertvalid)|Wywołanie tej metody, aby potwierdzić, że obiekt tablicy jest prawidłowy.|
|[Catlarray](#catlarray)|Konstruktor.|
|[~CAtlArray](#dtor)|Destruktor.|
|[Kopii](#copy)|Wywołanie tej metody, aby skopiować elementy jednej tablicy do innej.|
|[FreeExtra (DarmoweWydajęcie](#freeextra)|Wywołanie tej metody, aby usunąć wszystkie puste elementy z tablicy.|
|[Getat](#getat)|Wywołanie tej metody, aby pobrać pojedynczy element z obiektu tablicy.|
|[GetCount](#getcount)|Wywołanie tej metody, aby zwrócić liczbę elementów przechowywanych w tablicy.|
|[GetData](#getdata)|Wywołanie tej metody, aby zwrócić wskaźnik do pierwszego elementu w tablicy.|
|[InsertArrayAt (WstawianieArrayAt)](#insertarrayat)|Wywołanie tej metody, aby wstawić jedną tablicę do innej.|
|[Insertat](#insertat)|Wywołanie tej metody, aby wstawić nowy element (lub wiele kopii elementu) do obiektu tablicy.|
|[Isempty](#isempty)|Wywołanie tej metody, aby sprawdzić, czy tablica jest pusta.|
|[Removeall](#removeall)|Wywołanie tej metody, aby usunąć wszystkie elementy z obiektu tablicy.|
|[Removeat](#removeat)|Wywołanie tej metody, aby usunąć jeden lub więcej elementów z tablicy.|
|[SetAt (ZestawAt)](#setat)|Wywołanie tej metody, aby ustawić wartość elementu w obiekcie tablicy.|
|[SetAtGrow (SetAtGrow)](#setatgrow)|Wywołanie tej metody, aby ustawić wartość elementu w obiekcie tablicy, rozwiń tablicy zgodnie z wymaganiami.|
|[SetCount (licz).](#setcount)|Wywołanie tej metody, aby ustawić rozmiar obiektu tablicy.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[ &#91;&#93;operatora](#operator_at)|Wywołaj ten operator, aby zwrócić odwołanie do elementu w tablicy.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[INARGTYPE ( INARGTYPE )](#inargtype)|Typ danych dodawania elementów do tablicy.|
|[RODZAJ OUTARGTYPE](#outargtype)|Typ danych do użycia do pobierania elementów z tablicy.|

## <a name="remarks"></a>Uwagi

`CAtlArray`udostępnia metody tworzenia i zarządzania tablicą elementów typu zdefiniowanego przez użytkownika. Chociaż podobnie jak standardowe tablice C, `CAtlArray` obiekt może dynamicznie zmniejszać i rosnąć w razie potrzeby. Indeks tablicy zawsze rozpoczyna się od pozycji 0, a górna granica może być ustalona lub może rozwinąć się w miarę dodawania nowych elementów.

Dla tablic z niewielką liczbą elementów można użyć klasy ATL [CSimpleArray.](../../atl/reference/csimplearray-class.md)

`CAtlArray`jest ściśle związane z `CArray` klasy MFC i będzie działać w projekcie MFC, choć bez obsługi serializacji.

Aby uzyskać więcej informacji, zobacz [ATL Collection Classes](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="catlarrayadd"></a><a name="add"></a>CAtlArray::Dodaj

Wywołanie tej metody, aby dodać element do obiektu tablicy.

```
size_t Add(INARGTYPE element);
size_t Add();
```

### <a name="parameters"></a>Parametry

*Element*<br/>
Element, który ma zostać dodany do tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca indeks dodanego elementu.

### <a name="remarks"></a>Uwagi

Nowy element jest dodawany na końcu tablicy. Jeśli nie podano żadnego elementu, dodaje się pusty element; oznacza to, że tablica jest zwiększona w rozmiarze, tak jakby dodano prawdziwy element. Jeśli operacja nie powiedzie się, [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow) jest wywoływana z argumentem E_OUTOFMEMORY.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]

## <a name="catlarrayappend"></a><a name="append"></a>CAtlArray::Dołącz

Wywołanie tej metody, aby dodać zawartość jednej tablicy na końcu innego.

```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Parametry

*Asrc*<br/>
Tablica do dołączona.

### <a name="return-value"></a>Wartość zwracana

Zwraca indeks pierwszego elementu dołączonego.

### <a name="remarks"></a>Uwagi

Elementy w dostarczonej tablicy są dodawane na końcu istniejącej tablicy. W razie potrzeby pamięć zostanie przydzielona do uwzględnienia nowych elementów.

Tablice muszą być tego samego typu i nie jest możliwe dołączenie tablicy do siebie.

W kompilacjach debugowania ATLASSERT zostanie `CAtlArray` podniesiona, jeśli argument nie jest prawidłową tablicą lub jeśli *aSrc* odwołuje się do tego samego obiektu. W kompilacjach wersji nieprawidłowe argumenty mogą prowadzić do nieprzewidywalnego zachowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]

## <a name="catlarrayassertvalid"></a><a name="assertvalid"></a>CAtlArray::AssertValid

Wywołanie tej metody, aby potwierdzić, że obiekt tablicy jest prawidłowy.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt tablicy jest nieprawidłowy, atlassert zrzuci asercja. Ta metoda jest dostępna tylko wtedy, gdy zdefiniowano _DEBUG.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]

## <a name="catlarraycatlarray"></a><a name="catlarray"></a>CAtlArray::CAtlArray

Konstruktor.

```
CAtlArray() throw();
```

### <a name="remarks"></a>Uwagi

Inicjuje obiekt tablicy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]

## <a name="catlarraycatlarray"></a><a name="dtor"></a>CAtlArray::~CAtlArray

Destruktor.

```
~CAtlArray() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie zasoby używane przez obiekt tablicy.

## <a name="catlarraycopy"></a><a name="copy"></a>CAtlArray::Kopiowanie

Wywołanie tej metody, aby skopiować elementy jednej tablicy do innej.

```cpp
void Copy(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Parametry

*Asrc*<br/>
Źródło elementów do skopiowania do tablicy.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby zastąpić elementy jednej tablicy z elementami innej tablicy. W razie potrzeby pamięć zostanie przydzielona do uwzględnienia nowych elementów. Nie jest możliwe skopiowanie elementów tablicy do siebie.

Jeśli istniejąca zawartość tablicy mają być zachowane, należy użyć [CAtlArray::Dołącz](#append) zamiast tego.

W kompilacjach debugowania ATLASSERT zostanie podniesiona, jeśli istniejący `CAtlArray` obiekt nie jest prawidłowy lub jeśli *aSrc* odwołuje się do tego samego obiektu. W kompilacjach wersji nieprawidłowe argumenty mogą prowadzić do nieprzewidywalnego zachowania.

> [!NOTE]
> `CAtlArray::Copy`nie obsługuje tablic składających się z elementów utworzonych za pomocą klasy [CAutoPtr.](../../atl/reference/cautoptr-class.md)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]

## <a name="catlarrayfreeextra"></a><a name="freeextra"></a>CAtlArray::FreeExtra

Wywołanie tej metody, aby usunąć wszystkie puste elementy z tablicy.

```cpp
void FreeExtra() throw();
```

### <a name="remarks"></a>Uwagi

Wszystkie puste elementy są usuwane, ale rozmiar i górna granica tablicy pozostają niezmienione.

W kompilacjach debugowania ATLASSERT zostanie podniesiona, jeśli CAtlArray obiekt nie jest prawidłowy lub jeśli tablica przekroczy jego maksymalny rozmiar.

## <a name="catlarraygetat"></a><a name="getat"></a>CAtlArray::GetAt

Wywołanie tej metody, aby pobrać pojedynczy element z obiektu tablicy.

```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```

### <a name="parameters"></a>Parametry

*Ielement*<br/>
Wartość indeksu elementu tablicy do zwrócenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do wymaganego elementu tablicy.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania ATLASSERT zostanie podniesiona, jeśli *iElement* przekracza liczbę elementów w tablicy. W kompilacjach wersji nieprawidłowy argument może prowadzić do nieprzewidywalnego zachowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]

## <a name="catlarraygetcount"></a><a name="getcount"></a>CAtlArray::GetCount

Wywołanie tej metody, aby zwrócić liczbę elementów przechowywanych w tablicy.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę elementów przechowywanych w tablicy.

### <a name="remarks"></a>Uwagi

Jako pierwszy element w tablicy znajduje się w `GetCount` pozycji 0, wartość zwracana przez jest zawsze 1 większa niż największy indeks.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlArray::GetAt](#getat).

## <a name="catlarraygetdata"></a><a name="getdata"></a>CAtlArray::GetData

Wywołanie tej metody, aby zwrócić wskaźnik do pierwszego elementu w tablicy.

```
E* GetData() throw();
const E* GetData() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do lokalizacji pamięci przechowywania pierwszego elementu w tablicy. Jeśli żadne elementy nie są dostępne, zwracana jest wartość NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]

## <a name="catlarrayinargtype"></a><a name="inargtype"></a>CAtlArray::INARGTYPE

Typ danych dodawania elementów do tablicy.

```
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catlarrayinsertarrayat"></a><a name="insertarrayat"></a>CAtlArray::InsertArrayAt

Wywołanie tej metody, aby wstawić jedną tablicę do innej.

```cpp
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```

### <a name="parameters"></a>Parametry

*Istart*<br/>
Indeks, w którym ma być wstawiana tablica.

*paNowy*<br/>
Tablica, która ma zostać wstawiona.

### <a name="remarks"></a>Uwagi

Elementy z tablicy *paNew* są kopiowane do obiektu tablicy, począwszy od elementu *iStart*. Istniejące elementy tablicy są przenoszone, aby uniknąć zastępowania.

W kompilacjach debugowania ATLASSERT zostanie `CAtlArray` podniesiony, jeśli obiekt nie jest prawidłowy lub jeśli wskaźnik *paNew* ma wartość NULL lub nieprawidłowy.

> [!NOTE]
> `CAtlArray::InsertArrayAt`nie obsługuje tablic składających się z elementów utworzonych za pomocą klasy [CAutoPtr.](../../atl/reference/cautoptr-class.md)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]

## <a name="catlarrayinsertat"></a><a name="insertat"></a>CAtlArray::Wstawianie

Wywołanie tej metody, aby wstawić nowy element (lub wiele kopii elementu) do obiektu tablicy.

```cpp
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```

### <a name="parameters"></a>Parametry

*Ielement*<br/>
Indeks, w którym element lub elementy mają być wstawiane.

*Element*<br/>
Wartość elementu lub elementów, które mają zostać wstawione.

*Ncount*<br/>
Liczba elementów do dodania.

### <a name="remarks"></a>Uwagi

Wstawia jeden lub więcej elementów do tablicy, począwszy od indeksu *iElement*. Istniejące elementy są przenoszone, aby uniknąć zastępowania.

W kompilacjach debugowania ATLASSERT zostanie `CAtlArray` podniesiona, jeśli obiekt jest nieprawidłowy, liczba elementów do dodania wynosi zero lub łączna liczba elementów jest zbyt duża, aby tablica zawierała. W kompilacjach sieci sprzedaży przekazywanie nieprawidłowych parametrów może spowodować nieprzewidywalne wyniki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]

## <a name="catlarrayisempty"></a><a name="isempty"></a>CAtlArray::IsEmpty

Wywołanie tej metody, aby sprawdzić, czy tablica jest pusta.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli tablica jest pusta, w przeciwnym razie false.

### <a name="remarks"></a>Uwagi

Tablica jest mówi się, że jest pusta, jeśli nie zawiera żadnych elementów. W związku z tym nawet jeśli tablica zawiera puste elementy, nie jest pusta.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]

## <a name="catlarrayoperator-"></a><a name="operator_at"></a>CAtlArray::operator []

Wywołaj ten operator, aby zwrócić odwołanie do elementu w tablicy.

```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```

### <a name="parameters"></a>Parametry

*Ielement*<br/>
Wartość indeksu elementu tablicy do zwrócenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do wymaganego elementu tablicy.

### <a name="remarks"></a>Uwagi

Wykonuje podobną funkcję do [CAtlArray::GetAt](#getat). W przeciwieństwie do klasy MFC [CArray,](../../mfc/reference/carray-class.md)ten operator nie może być używany jako substytut [CAtlArray::SetAt](#setat).

W kompilacjach debugowania ATLASSERT zostanie podniesiona, jeśli *iElement* przekracza całkowitą liczbę elementów w tablicy. W kompilacjach sieci sprzedaży nieprawidłowy parametr może powodować nieprzewidywalne wyniki.

## <a name="catlarrayoutargtype"></a><a name="outargtype"></a>CAtlArray::OUTARGTYPE

Typ danych do użycia do pobierania elementów z tablicy.

```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```

## <a name="catlarrayremoveall"></a><a name="removeall"></a>CAtlArray::UsuńWszystki

Wywołanie tej metody, aby usunąć wszystkie elementy z obiektu tablicy.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Uwagi

Usuwa wszystkie elementy z obiektu tablicy.

Ta metoda wywołuje [CAtlArray::SetCount,](#setcount) aby zmienić rozmiar tablicy, a następnie zwalnia przydzieloną pamięć.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlArray::IsEmpty](#isempty).

## <a name="catlarrayremoveat"></a><a name="removeat"></a>CAtlArray::Usuń

Wywołanie tej metody, aby usunąć jeden lub więcej elementów z tablicy.

```cpp
void RemoveAt(size_t iElement, size_t nCount = 1);
```

### <a name="parameters"></a>Parametry

*Ielement*<br/>
Indeks pierwszego elementu do usunięcia.

*Ncount*<br/>
Liczba elementów do usunięcia.

### <a name="remarks"></a>Uwagi

Usuwa jeden lub więcej elementów z tablicy. Wszystkie pozostałe elementy są przesuwane w dół. Górna granica jest zmniejszana, ale pamięć nie jest zwalniana, dopóki nie zostanie wykonane wywołanie [CAtlArray::FreeExtra.](#freeextra)

W kompilacjach debugowania ATLASSERT zostanie `CAtlArray` podniesiona, jeśli obiekt nie jest prawidłowy lub jeśli łączna suma *iElement* i *nCount* przekracza całkowitą liczbę elementów w tablicy. W kompilacjach sieci sprzedaży nieprawidłowe parametry mogą powodować nieprzewidywalne wyniki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]

## <a name="catlarraysetat"></a><a name="setat"></a>CAtlArray::SetAt

Wywołanie tej metody, aby ustawić wartość elementu w obiekcie tablicy.

```cpp
void SetAt(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*Ielement*<br/>
Indeks wskazujący element tablicy do skonfigurowania.

*Element*<br/>
Nowa wartość określonego elementu.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania ATLASSERT zostanie podniesiona, jeśli *iElement* przekracza liczbę elementów w tablicy. W kompilacjach sieci sprzedaży nieprawidłowy parametr może spowodować nieprzewidywalne wyniki.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlArray::GetAt](#getat).

## <a name="catlarraysetcount"></a><a name="setcount"></a>CAtlArray::SetCount

Wywołanie tej metody, aby ustawić rozmiar obiektu tablicy.

```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```

### <a name="parameters"></a>Parametry

*nNowy Rozmiar*<br/>
Wymagany rozmiar tablicy.

*nGrowBy ( nGrowBy )*<br/>
Wartość używana do określenia, jak duży, aby bufor. Wartość -1 powoduje, że używana jest wewnętrznie obliczona wartość.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli tablica została pomyślnie przesięta, w przeciwnym razie false.

### <a name="remarks"></a>Uwagi

Tablica może być zwiększona lub zmniejszona. Jeśli zwiększona, dodatkowe puste elementy są dodawane do tablicy. Jeśli zostanie zmniejszona, elementy z największych indeksów zostaną usunięte i pamięci zwolniona.

Ta metoda służy do ustawiania rozmiaru tablicy przed użyciem go. Jeśli `SetCount` nie jest używany, proces dodawania elementów — i późniejszej alokacji pamięci wykonywane — zmniejszy wydajność i pamięci fragmentu.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlArray::GetData](#getdata).

## <a name="catlarraysetatgrow"></a><a name="setatgrow"></a>CAtlArray::SetAtGrow

Wywołanie tej metody, aby ustawić wartość elementu w obiekcie tablicy, rozwiń tablicy zgodnie z wymaganiami.

```cpp
void SetAtGrow(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*Ielement*<br/>
Indeks wskazujący element tablicy do skonfigurowania.

*Element*<br/>
Nowa wartość określonego elementu.

### <a name="remarks"></a>Uwagi

Zastępuje wartość elementu wskazywała przez indeks. Jeśli *iElement* jest większy niż bieżący rozmiar tablicy, tablica jest automatycznie zwiększana za pomocą wywołania [CAtlArray::SetCount](#setcount). W kompilacjach debugowania ATLASSERT zostanie `CAtlArray` podniesiony, jeśli obiekt jest nieprawidłowy. W kompilacjach sieci sprzedaży nieprawidłowe parametry mogą powodować nieprzewidywalne wyniki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]

## <a name="see-also"></a>Zobacz też

[Próbka MMXSwarm](../../overview/visual-cpp-samples.md)<br/>
[Przykład dynamicznego konsumera](../../overview/visual-cpp-samples.md)<br/>
[Próbka aktualizacjiPV](../../overview/visual-cpp-samples.md)<br/>
[Przykłada markizy](../../overview/visual-cpp-samples.md)<br/>
[Klasa CArray](../../mfc/reference/carray-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
