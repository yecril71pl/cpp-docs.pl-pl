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
ms.openlocfilehash: 6a0b83f722d1b616e9c10713646d337f9cb090a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260847"
---
# <a name="catlarray-class"></a>Klasa CAtlArray

Ta klasa implementuje obiektu array.

## <a name="syntax"></a>Składnia

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```

#### <a name="parameters"></a>Parametry

*E*<br/>
Typ danych, które mają być przechowywane w tablicy.

*ETraits*<br/>
Kod używany do kopiowania lub przenoszenia elementów.

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Add](#add)|Wywołaj tę metodę, aby dodać element do obiektu tablicy.|
|[Dołącz](#append)|Wywołaj tę metodę, aby dodać zawartość jednej tablicy do końca innej.|
|[AssertValid](#assertvalid)|Wywołaj tę metodę, aby upewnić się, że obiekt array jest prawidłowy.|
|[CAtlArray](#catlarray)|Konstruktor.|
|[~CAtlArray](#dtor)|Destruktor.|
|[Kopiuj](#copy)|Wywołaj tę metodę, aby skopiować elementy tablicy do innej.|
|[FreeExtra](#freeextra)|Wywołaj tę metodę w celu usunięcia żadnych pustych elementów z tablicy.|
|[GetAt](#getat)|Wywołaj tę metodę, aby pobrać jeden element z obiektu tablicy.|
|[GetCount](#getcount)|Wywołaj tę metodę, aby zwrócić liczbę elementów przechowywanych w tablicy.|
|[GetData](#getdata)|Wywołaj tę metodę, aby zwrócić wskaźnik do pierwszego elementu w tablicy.|
|[InsertArrayAt](#insertarrayat)|Wywołaj tę metodę, aby wstawić jednej tablicy do innej.|
|[InsertAt](#insertat)|Wywołaj tę metodę, aby wstawić nowego elementu (lub wiele kopii elementu) do obiektu tablicy.|
|[IsEmpty](#isempty)|Wywołaj tę metodę, aby sprawdzić, czy tablica jest pusta.|
|[RemoveAll](#removeall)|Wywołaj tę metodę, aby usunąć wszystkie elementy z obiektu array.|
|[Element RemoveAt](#removeat)|Wywołaj tę metodę, aby usunąć jeden lub więcej elementów z tablicy.|
|[SetAt](#setat)|Wywołaj tę metodę, aby ustawić wartość elementu w obiekcie tablicy.|
|[SetAtGrow](#setatgrow)|Wywołaj tę metodę, aby ustawić wartość elementu w obiekcie tablicy, rozszerzając tablicy zgodnie z potrzebami.|
|[SetCount](#setcount)|Wywołaj tę metodę, aby ustawić rozmiar obiektu array.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator&#91;&#93;](#operator_at)|Wywołaj Ten operator zwraca odwołanie do elementu w tablicy.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[INARGTYPE](#inargtype)|Typ danych na potrzeby dodawania elementów do tablicy.|
|[OUTARGTYPE](#outargtype)|Typ danych używany do pobierania elementów z tablicy.|

## <a name="remarks"></a>Uwagi

`CAtlArray` zawiera metody służące do tworzenia i zarządzania nimi tablicy elementów typu zdefiniowanego przez użytkownika. Mimo że jest to podobne do standardowego tablice języka C, `CAtlArray` obiektu można dynamicznie zmniejszać i powiększać w razie. Indeks tablicy zawsze uruchamia się na pozycji 0, a górną granicę mogą być rozwiązane lub mogą rozszerzyć w miarę dodawania nowych elementów.

Dla tablic z mniejszą liczbą elementów klasy ATL [CSimpleArray](../../atl/reference/csimplearray-class.md) mogą być używane.

`CAtlArray` jest ściśle powiązane z biblioteki MFC `CArray` klasy i będzie działać w projekcie MFC, jednakże bez obsługi serializacji.

Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

##  <a name="add"></a>  CAtlArray::Add

Wywołaj tę metodę, aby dodać element do obiektu tablicy.

```
size_t Add(INARGTYPE element);
size_t Add();
```

### <a name="parameters"></a>Parametry

*element*<br/>
Element, który ma zostać dodany do tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca indeks elementu dodane.

### <a name="remarks"></a>Uwagi

Nowy element zostanie dodany do końca tablicy. Jeśli element nie zostanie podana, pusty element zostanie dodany; oznacza to, że tablica jest zwiększyć rozmiar tak, jakby rzeczywistych element został dodany. Jeśli operacja zakończy się niepowodzeniem, [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow) jest wywoływana z argumentem E_OUTOFMEMORY.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]

##  <a name="append"></a>  CAtlArray::Append

Wywołaj tę metodę, aby dodać zawartość jednej tablicy do końca innej.

```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Parametry

*aSrc*<br/>
Tablica do dołączenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca indeks pierwszego elementu dołączonych.

### <a name="remarks"></a>Uwagi

Elementy w tablicy podane są dodawane na końcu istniejącej tablicy. Jeśli to konieczne, aby uwzględnić nowe elementy zostaną przydzielone pamięci.

Tablice muszą być tego samego typu, a nie jest możliwe, Dołącz tablicę do samego siebie.

W kompilacjach do debugowania ATLASSERT zostanie wygenerowany, jeśli `CAtlArray` argument nie jest prawidłową tablicą lub jeśli *aSrc* odwołuje się do tego samego obiektu. W kompilacjach do wydania nieprawidłowe argumenty może prowadzić do nieprzewidywalne zachowanie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]

##  <a name="assertvalid"></a>  CAtlArray::AssertValid

Wywołaj tę metodę, aby upewnić się, że obiekt array jest prawidłowy.

```
void AssertValid() const;
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt tablicy nie jest prawidłowy, ATLASSERT zgłosi potwierdzenie. Ta metoda jest dostępna tylko wtedy, gdy zdefiniowano _DEBUG.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]

##  <a name="catlarray"></a>  CAtlArray::CAtlArray

Konstruktor.

```
CAtlArray() throw();
```

### <a name="remarks"></a>Uwagi

Inicjuje obiekt array.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]

##  <a name="dtor"></a>  CAtlArray:: ~ CAtlArray

Destruktor.

```
~CAtlArray() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszelkie zasoby używane przez obiekt array.

##  <a name="copy"></a>  CAtlArray::Copy

Wywołaj tę metodę, aby skopiować elementy tablicy do innej.

```
void Copy(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Parametry

*aSrc*<br/>
Źródło elementy do skopiowania do tablicy.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę w celu zastąpienia elementów tablicy elementów innej tablicy. Jeśli to konieczne, aby uwzględnić nowe elementy zostaną przydzielone pamięci. Nie jest możliwe skopiować elementy tablicy do samego siebie.

Jeśli ma zostać zachowana istniejącą zawartość elementu tablicy, użyj [CAtlArray::Append](#append) zamiast tego.

W kompilacjach do debugowania ATLASSERT zostanie wygenerowany, jeśli istniejące `CAtlArray` obiekt nie jest prawidłowa, lub jeśli *aSrc* odwołuje się do tego samego obiektu. W kompilacjach do wydania nieprawidłowe argumenty może prowadzić do nieprzewidywalne zachowanie.

> [!NOTE]
> `CAtlArray::Copy` obsługuje tablice składające się z elementów utworzonych za pomocą [CAutoPtr](../../atl/reference/cautoptr-class.md) klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]

##  <a name="freeextra"></a>  CAtlArray::FreeExtra

Wywołaj tę metodę w celu usunięcia żadnych pustych elementów z tablicy.

```
void FreeExtra() throw();
```

### <a name="remarks"></a>Uwagi

Wszelkie puste elementy są usuwane, ale rozmiar i górna granica tablicy pozostają niezmienione.

W kompilacjach do debugowania ATLASSERT zostanie wygenerowany, jeśli obiekt CAtlArray jest nieprawidłowy lub tablicy spowodowałoby przekroczenie maksymalnego rozmiaru.

##  <a name="getat"></a>  CAtlArray::GetAt

Za pośrednictwem wywołania tej metody pobiera pojedynczy element z obiektu array.

```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Wartość indeksu elementu tablicy do zwrócenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do elementu tablicy wymagane.

### <a name="remarks"></a>Uwagi

W kompilacjach do debugowania ATLASSERT zostanie wygenerowany, jeśli *iElement* przekracza liczbę elementów w tablicy. W kompilacjach do wydania nieprawidłowy argument może prowadzić do nieprzewidywalne zachowanie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]

##  <a name="getcount"></a>  CAtlArray::GetCount

Wywołaj tę metodę, aby zwrócić liczbę elementów przechowywanych w tablicy.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę elementów przechowywanych w tablicy.

### <a name="remarks"></a>Uwagi

Podobnie jak do pierwszego elementu w tablicy na pozycji 0, wartość zwracana przez `GetCount` ma zawsze numer 1 większy od największego indeksu.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlArray::GetAt](#getat).

##  <a name="getdata"></a>  CAtlArray::GetData

Wywołaj tę metodę, aby zwrócić wskaźnik do pierwszego elementu w tablicy.

```
E* GetData() throw();
const E* GetData() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do lokalizacji pamięci, przechowywania pierwszego elementu w tablicy. Jeśli żadne elementy są dostępne, zwracana jest wartość NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]

##  <a name="inargtype"></a>  CAtlArray::INARGTYPE

Typ danych na potrzeby dodawania elementów do tablicy.

```
typedef ETraits::INARGTYPE INARGTYPE;
```

##  <a name="insertarrayat"></a>  CAtlArray::InsertArrayAt

Wywołaj tę metodę, aby wstawić jednej tablicy do innej.

```
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```

### <a name="parameters"></a>Parametry

*iStart*<br/>
Indeks, w którym ma zostać wstawiony tablicy.

*paNew*<br/>
Tablica, która ma zostać wstawiony.

### <a name="remarks"></a>Uwagi

Elementy z tablicy *paNew* są kopiowane do obiektu tablicy, zaczynając od elementu *iStart*. Istniejące elementy tablicy są przenoszone w celu uniknięcia zastąpieniem.

W kompilacjach do debugowania ATLASSERT zostanie wygenerowany, jeśli `CAtlArray` obiekt nie jest prawidłowa, lub jeśli *paNew* wskaźnik jest wartość NULL lub jest nieprawidłowy.

> [!NOTE]
> `CAtlArray::InsertArrayAt` obsługuje tablice składające się z elementów utworzonych za pomocą [CAutoPtr](../../atl/reference/cautoptr-class.md) klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]

##  <a name="insertat"></a>  CAtlArray::InsertAt

Wywołaj tę metodę, aby wstawić nowego elementu (lub wiele kopii elementu) do obiektu tablicy.

```
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Indeks, w którym element lub elementy mają zostać wstawione.

*element*<br/>
Wartość elementu lub elementów do wstawienia.

*nCount*<br/>
Liczba elementów do dodania.

### <a name="remarks"></a>Uwagi

Wstawia jedną lub więcej elementów do tablicy, zaczynając od indeksu *iElement*. Istniejące elementy są przenoszone w celu uniknięcia zastąpieniem.

W kompilacjach do debugowania ATLASSERT zostanie wygenerowany, jeśli `CAtlArray` obiekt jest nieprawidłowy, liczbę elementów do dodania ma wartość zero lub łączna liczba elementów jest za duży dla tablicy zawiera. W kompilacjach do sprzedaży detalicznej przekazując nieprawidłowe parametry mogą powodować nieprzewidywalne skutki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]

##  <a name="isempty"></a>  CAtlArray::IsEmpty

Wywołaj tę metodę, aby sprawdzić, czy tablica jest pusta.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli tablica jest pusta, wartość false w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Tablica jest określane jako puste, jeśli go nie zawiera żadnych elementów. W związku z tym nawet jeśli tablica zawiera puste elementy, nie jest pusty.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]

##  <a name="operator_at"></a>  [] CAtlArray::operator

Wywołaj Ten operator zwraca odwołanie do elementu w tablicy.

```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Wartość indeksu elementu tablicy do zwrócenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do elementu tablicy wymagane.

### <a name="remarks"></a>Uwagi

Pełni funkcję podobną do [CAtlArray::GetAt](#getat). W odróżnieniu od klasy MFC [CArray](../../mfc/reference/carray-class.md), nie można używać tego operatora w zastępstwie [CAtlArray::SetAt](#setat).

W kompilacjach do debugowania ATLASSERT zostanie wygenerowany, jeśli *iElement* przekracza całkowitą liczbę elementów w tablicy. W kompilacjach do sprzedaży detalicznej nieprawidłowy parametr mogą powodować nieprzewidywalne skutki.

##  <a name="outargtype"></a>  CAtlArray::OUTARGTYPE

Typ danych używany do pobierania elementów z tablicy.

```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```

##  <a name="removeall"></a>  CAtlArray::RemoveAll

Wywołaj tę metodę, aby usunąć wszystkie elementy z obiektu array.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Uwagi

Usuwa wszystkie elementy z obiektu array.

Ta metoda wywołuje [CAtlArray::SetCount](#setcount) zmiany rozmiaru tablicy i następnie zwalnia wszelkie ilość przydzielonej pamięci.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlArray::IsEmpty](#isempty).

##  <a name="removeat"></a>  CAtlArray::RemoveAt

Wywołaj tę metodę, aby usunąć jeden lub więcej elementów z tablicy.

```
void RemoveAt(size_t iElement, size_t nCount = 1);
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Indeks pierwszego elementu do usunięcia.

*nCount*<br/>
Liczba elementów do usunięcia.

### <a name="remarks"></a>Uwagi

Usuwa jeden lub więcej elementów z tablicy. Wszystkie pozostałe elementy są przesuwane w dół. Górna granica zostanie zmniejszony, ale pamięć nie jest zwalniana do momentu wywołania [CAtlArray::FreeExtra](#freeextra) wykonano.

W kompilacjach do debugowania ATLASSERT zostanie wygenerowany, jeśli `CAtlArray` obiekt nie jest prawidłowa, lub jeśli łączna liczba *iElement* i *nCount* przekracza całkowitą liczbę elementów w tablicy. W kompilacjach do sprzedaży detalicznej nieprawidłowe parametry mogą powodować nieprzewidywalne skutki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]

##  <a name="setat"></a>  CAtlArray::SetAt

Wywołaj tę metodę, aby ustawić wartość elementu w obiekcie tablicy.

```
void SetAt(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Indeks wskazujący element tablicy do ustawienia.

*element*<br/>
Nowa wartość określonego elementu.

### <a name="remarks"></a>Uwagi

W kompilacjach do debugowania ATLASSERT zostanie wygenerowany, jeśli *iElement* przekracza liczbę elementów w tablicy. Nieprawidłowy parametr w kompilacjach do sprzedaży detalicznej, może spowodować nieprzewidywalne rezultaty.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlArray::GetAt](#getat).

##  <a name="setcount"></a>  CAtlArray::SetCount

Wywołaj tę metodę, aby ustawić rozmiar obiektu array.

```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```

### <a name="parameters"></a>Parametry

*nNewSize*<br/>
Wymagany rozmiar tablicy.

*nGrowBy*<br/>
Wartość używana do określenia wielkość bufora. Wartość -1 powoduje, że wewnętrznie obliczoną wartość ma być używany.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli tablica jest pomyślnie o zmienionym rozmiarze, wartość false w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Można zwiększyć lub zmniejszyć rozmiar tablicy. Jeśli zwiększona, bardzo puste elementy są dodawane do tablicy. Jeśli spadły, elementy z największych indeksy zostaną usunięte, a pamięć zwolniona.

Użyj tej metody można ustawić rozmiar tablicy przed jego użyciem. Jeśli `SetCount` nie jest używany, proces dodawania elementów — i wykonać alokacji pamięci kolejnych — spowoduje to zmniejszyć wydajność i fragmentu pamięci.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlArray::GetData](#getdata).

##  <a name="setatgrow"></a>  CAtlArray::SetAtGrow

Wywołaj tę metodę, aby ustawić wartość elementu w obiekcie tablicy, rozszerzając tablicy zgodnie z potrzebami.

```
void SetAtGrow(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Indeks wskazujący element tablicy do ustawienia.

*element*<br/>
Nowa wartość określonego elementu.

### <a name="remarks"></a>Uwagi

Zamienia wartość elementu wskazywanego przez indeks. Jeśli *iElement* jest większy niż bieżący rozmiar tablicy, tablica jest automatycznie zwiększana przy użyciu wywołania do [CAtlArray::SetCount](#setcount). W kompilacjach do debugowania ATLASSERT zostanie wygenerowany, jeśli `CAtlArray` obiektu jest nieprawidłowy. W kompilacjach do sprzedaży detalicznej nieprawidłowe parametry mogą powodować nieprzewidywalne skutki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]

## <a name="see-also"></a>Zobacz także

[Przykładowe MMXSwarm](../../overview/visual-cpp-samples.md)<br/>
[Przykładowe DynamicConsumer](../../overview/visual-cpp-samples.md)<br/>
[Przykładowe UpdatePV](../../overview/visual-cpp-samples.md)<br/>
[Przykładowe Neon](../../overview/visual-cpp-samples.md)<br/>
[Klasa CArray](../../mfc/reference/carray-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
