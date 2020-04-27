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
ms.openlocfilehash: 5928a9bf8af12b2ce15a386871b845ef86cc7a2d
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168774"
---
# <a name="catlarray-class"></a>Klasa CAtlArray

Ta klasa implementuje obiekt Array.

## <a name="syntax"></a>Składnia

```cpp
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```

### <a name="parameters"></a>Parametry

*Adres*<br/>
Typ danych, które mają być przechowywane w tablicy.

*ETraits*<br/>
Kod używany do kopiowania lub przenoszenia elementów.

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Dodaj](#add)|Wywołaj tę metodę, aby dodać element do obiektu Array.|
|[Append](#append)|Wywołaj tę metodę, aby dodać zawartość jednej tablicy do końca innej.|
|[AssertValid](#assertvalid)|Wywołaj tę metodę, aby potwierdzić, że obiekt tablicy jest prawidłowy.|
|[CAtlArray](#catlarray)|Konstruktor.|
|[~ CAtlArray](#dtor)|Destruktor.|
|[Kopiowane](#copy)|Wywołaj tę metodę, aby skopiować elementy jednej tablicy do innej.|
|[FreeExtra](#freeextra)|Wywołaj tę metodę, aby usunąć wszelkie puste elementy z tablicy.|
|[GetAt](#getat)|Wywołaj tę metodę, aby pobrać pojedynczy element z obiektu Array.|
|[GetCount](#getcount)|Wywołaj tę metodę, aby zwrócić liczbę elementów przechowywanych w tablicy.|
|[GetData](#getdata)|Wywołaj tę metodę, aby zwrócić wskaźnik do pierwszego elementu w tablicy.|
|[InsertArrayAt](#insertarrayat)|Wywołaj tę metodę, aby wstawić jedną tablicę do innej.|
|[InsertAt](#insertat)|Wywołaj tę metodę, aby wstawić nowy element (lub wiele kopii elementu) do obiektu Array.|
|[IsEmpty](#isempty)|Wywołaj tę metodę, aby sprawdzić, czy tablica jest pusta.|
|[Pomniej](#removeall)|Wywołaj tę metodę, aby usunąć wszystkie elementy z obiektu Array.|
|[RemoveAt](#removeat)|Wywołaj tę metodę, aby usunąć co najmniej jeden element z tablicy.|
|[SetAt](#setat)|Wywołaj tę metodę, aby ustawić wartość elementu w obiekcie array.|
|[SetAtGrow](#setatgrow)|Wywołaj tę metodę, aby ustawić wartość elementu w obiekcie array, rozszerzając tablicę zgodnie z potrzebami.|
|[SetCount](#setcount)|Wywołaj tę metodę, aby ustawić rozmiar obiektu Array.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[ &#91;&#93;operatora](#operator_at)|Wywołaj ten operator, aby zwrócić odwołanie do elementu w tablicy.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[INARGTYPE](#inargtype)|Typ danych, który ma być używany do dodawania elementów do tablicy.|
|[OUTARGTYPE](#outargtype)|Typ danych, który ma być używany do pobierania elementów z tablicy.|

## <a name="remarks"></a>Uwagi

`CAtlArray`zapewnia metody tworzenia tablicy elementów typu zdefiniowanego przez użytkownika i zarządzania nią. Chociaż podobne do standardowych tablic języka C, `CAtlArray` obiekt może dynamicznie zmniejszać się i zwiększać w razie potrzeby. Indeks tablicy zawsze rozpoczyna się na pozycji 0, a górna granica może zostać naprawiona lub być rozwinięta, gdy dodawane są nowe elementy.

W przypadku tablic o niewielkiej liczbie elementów można użyć klasy ATL [CSimpleArray](../../atl/reference/csimplearray-class.md) .

`CAtlArray`jest blisko związany z `CArray` klasą MFC i będzie działał w projekcie MFC, chociaż bez obsługi serializacji.

Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll. h

## <a name="catlarrayadd"></a><a name="add"></a>CAtlArray:: Add

Wywołaj tę metodę, aby dodać element do obiektu Array.

```cpp
size_t Add(INARGTYPE element);
size_t Add();
```

### <a name="parameters"></a>Parametry

*postaci*<br/>
Element, który ma zostać dodany do tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca indeks dodanego elementu.

### <a name="remarks"></a>Uwagi

Nowy element zostanie dodany na końcu tablicy. Jeśli nie podano żadnego elementu, zostanie dodany pusty element; oznacza to, że rozmiar tablicy jest zwiększony tak, jakby został dodany prawdziwy element. Jeśli operacja nie powiedzie się, [funkcji AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow) jest wywoływana z argumentem E_OUTOFMEMORY.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]

## <a name="catlarrayappend"></a><a name="append"></a>CAtlArray:: Append

Wywołaj tę metodę, aby dodać zawartość jednej tablicy do końca innej.

```cpp
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Parametry

*aSrc*<br/>
Tablica do dołączenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca indeks pierwszego dołączonego elementu.

### <a name="remarks"></a>Uwagi

Elementy w podanej tablicy są dodawane do końca istniejącej tablicy. W razie potrzeby pamięć zostanie przypisana w celu uwzględnienia nowych elementów.

Tablice muszą być tego samego typu i nie można dołączać tablicy do samej siebie.

W kompilacjach debugowania ATLASSERT zostanie wywołane, jeśli `CAtlArray` argument nie jest prawidłową tablicą lub jeśli *ASRC* odwołuje się do tego samego obiektu. W kompilacjach wydania nieprawidłowe argumenty mogą prowadzić do nieprzewidywalnego zachowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]

## <a name="catlarrayassertvalid"></a><a name="assertvalid"></a>CAtlArray::AssertValid

Wywołaj tę metodę, aby potwierdzić, że obiekt tablicy jest prawidłowy.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt Array jest nieprawidłowy, ATLASSERT zgłosi potwierdzenie. Ta metoda jest dostępna tylko wtedy, gdy _DEBUG jest zdefiniowana.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]

## <a name="catlarraycatlarray"></a><a name="catlarray"></a>CAtlArray::CAtlArray

Konstruktor.

```cpp
CAtlArray() throw();
```

### <a name="remarks"></a>Uwagi

Inicjuje obiekt Array.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]

## <a name="catlarraycatlarray"></a><a name="dtor"></a>CAtlArray:: ~ CAtlArray

Destruktor.

```cpp
~CAtlArray() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie zasoby używane przez obiekt Array.

## <a name="catlarraycopy"></a><a name="copy"></a>CAtlArray:: Copy

Wywołaj tę metodę, aby skopiować elementy jednej tablicy do innej.

```cpp
void Copy(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Parametry

*aSrc*<br/>
Źródło elementów do skopiowania do tablicy.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zastąpić elementy jednej tablicy elementami innej tablicy. W razie potrzeby pamięć zostanie przypisana w celu uwzględnienia nowych elementów. Nie można skopiować elementów tablicy do samej siebie.

Jeśli istniejąca zawartość tablicy ma być zachowana, użyj [CAtlArray:: Append](#append) zamiast tego.

W kompilacjach debugowania ATLASSERT zostanie zgłoszony, jeśli istniejący `CAtlArray` obiekt jest nieprawidłowy lub *ASRC* odwołuje się do tego samego obiektu. W kompilacjach wydania nieprawidłowe argumenty mogą prowadzić do nieprzewidywalnego zachowania.

> [!NOTE]
> `CAtlArray::Copy`nie obsługuje tablic składających się z elementów utworzonych za pomocą klasy [CAutoPtr](../../atl/reference/cautoptr-class.md) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]

## <a name="catlarrayfreeextra"></a><a name="freeextra"></a>CAtlArray::FreeExtra

Wywołaj tę metodę, aby usunąć wszelkie puste elementy z tablicy.

```cpp
void FreeExtra() throw();
```

### <a name="remarks"></a>Uwagi

Wszystkie puste elementy są usuwane, ale rozmiar i górną granicę tablicy pozostaną bez zmian.

W kompilacjach debugowania ATLASSERT zostanie zgłoszony, jeśli obiekt CAtlArray jest nieprawidłowy, lub jeśli tablica przekroczy jego maksymalny rozmiar.

## <a name="catlarraygetat"></a><a name="getat"></a>CAtlArray::GetAt

Wywołaj tę metodę, aby pobrać pojedynczy element z obiektu Array.

```cpp
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Wartość indeksu elementu tablicy, która ma zostać zwrócona.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do wymaganego elementu tablicy.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania zostanie zgłoszony ATLASSERT, jeśli *IElement* przekroczy liczbę elementów w tablicy. W kompilacjach wydania nieprawidłowy argument może prowadzić do nieprzewidywalnego zachowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]

## <a name="catlarraygetcount"></a><a name="getcount"></a>CAtlArray:: GetCount

Wywołaj tę metodę, aby zwrócić liczbę elementów przechowywanych w tablicy.

```cpp
size_t GetCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę elementów przechowywanych w tablicy.

### <a name="remarks"></a>Uwagi

Jako pierwszy element w tablicy znajduje się na pozycji 0, wartość zwracana przez `GetCount` jest zawsze 1 większa od największego indeksu.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlArray:: GetAt](#getat).

## <a name="catlarraygetdata"></a><a name="getdata"></a>CAtlArray:: GetData

Wywołaj tę metodę, aby zwrócić wskaźnik do pierwszego elementu w tablicy.

```cpp
E* GetData() throw();
const E* GetData() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do lokalizacji pamięci przechowującej pierwszy element w tablicy. Jeśli żadne elementy nie są dostępne, zwracana jest wartość NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]

## <a name="catlarrayinargtype"></a><a name="inargtype"></a>CAtlArray::INARGTYPE

Typ danych, który ma być używany do dodawania elementów do tablicy.

```cpp
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catlarrayinsertarrayat"></a><a name="insertarrayat"></a>CAtlArray::InsertArrayAt

Wywołaj tę metodę, aby wstawić jedną tablicę do innej.

```cpp
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```

### <a name="parameters"></a>Parametry

*isrozpoczęcia*<br/>
Indeks, w którym ma zostać wstawiona tablica.

*paNew*<br/>
Tablica, która ma zostać wstawiona.

### <a name="remarks"></a>Uwagi

Elementy z tablicy *Panew* są kopiowane do obiektu Array, zaczynając *od elementu*ispoczątku. Istniejące elementy tablicy są przenoszone, aby uniknąć ich nadpisania.

W kompilacjach debugowania ATLASSERT zostanie zgłoszony, jeśli `CAtlArray` obiekt jest nieprawidłowy lub jeśli wskaźnik *Panew* ma wartość null lub jest nieprawidłowy.

> [!NOTE]
> `CAtlArray::InsertArrayAt`nie obsługuje tablic składających się z elementów utworzonych za pomocą klasy [CAutoPtr](../../atl/reference/cautoptr-class.md) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]

## <a name="catlarrayinsertat"></a><a name="insertat"></a>CAtlArray::InsertAt

Wywołaj tę metodę, aby wstawić nowy element (lub wiele kopii elementu) do obiektu Array.

```cpp
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Indeks, w którym element lub elementy mają zostać wstawione.

*postaci*<br/>
Wartość elementu lub elementów do wstawienia.

*nCount*<br/>
Liczba elementów do dodania.

### <a name="remarks"></a>Uwagi

Wstawia jeden lub więcej elementów do tablicy, zaczynając od indeksu *IElement*. Istniejące elementy są przenoszone, aby uniknąć ich nadpisania.

W kompilacjach debugowania ATLASSERT zostanie zgłoszony, jeśli `CAtlArray` obiekt jest nieprawidłowy, liczba elementów do dodania wynosi zero lub łączna liczba elementów jest zbyt duża dla tablicy, która ma zawierać. W kompilacjach detalicznych przekazywanie nieprawidłowych parametrów może spowodować nieprzewidywalne wyniki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]

## <a name="catlarrayisempty"></a><a name="isempty"></a>CAtlArray:: IsEmpty

Wywołaj tę metodę, aby sprawdzić, czy tablica jest pusta.

```cpp
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli tablica jest pusta, w przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

Tablica jest określana jako pusta, jeśli nie zawiera żadnych elementów. W związku z tym, nawet jeśli tablica zawiera puste elementy, nie jest pusta.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]

## <a name="catlarrayoperator-"></a><a name="operator_at"></a>CAtlArray:: operator []

Wywołaj ten operator, aby zwrócić odwołanie do elementu w tablicy.

```cpp
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Wartość indeksu elementu tablicy, która ma zostać zwrócona.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do wymaganego elementu tablicy.

### <a name="remarks"></a>Uwagi

Wykonuje podobną funkcję do [CAtlArray:: GetAt](#getat). W przeciwieństwie do klasy MFC [CArray](../../mfc/reference/carray-class.md), tego operatora nie można użyć jako zamiennika dla [CAtlArray:: SetAt](#setat).

W kompilacjach debugowania zostanie zgłoszony ATLASSERT, jeśli *IElement* przekroczy całkowitą liczbę elementów w tablicy. W kompilacjach detalicznych nieprawidłowy parametr może spowodować nieprzewidywalne wyniki.

## <a name="catlarrayoutargtype"></a><a name="outargtype"></a>CAtlArray::OUTARGTYPE

Typ danych, który ma być używany do pobierania elementów z tablicy.

```cpp
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```

## <a name="catlarrayremoveall"></a><a name="removeall"></a>CAtlArray::

Wywołaj tę metodę, aby usunąć wszystkie elementy z obiektu Array.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Uwagi

Usuwa wszystkie elementy z obiektu Array.

Ta metoda wywołuje [CAtlArray:: SetCount](#setcount) , aby zmienić rozmiar tablicy, a następnie zwalnia każdą przydzieloną pamięć.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlArray:: IsEmpty](#isempty).

## <a name="catlarrayremoveat"></a><a name="removeat"></a>CAtlArray::RemoveAt

Wywołaj tę metodę, aby usunąć co najmniej jeden element z tablicy.

```cpp
void RemoveAt(size_t iElement, size_t nCount = 1);
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Indeks pierwszego elementu do usunięcia.

*nCount*<br/>
Liczba elementów do usunięcia.

### <a name="remarks"></a>Uwagi

Usuwa jeden lub więcej elementów z tablicy. Wszystkie pozostałe elementy zostaną przesunięte w dół. Górna granica jest zmniejszana, ale pamięć nie jest zwalniana do momentu wywołania [CAtlArray:: FreeExtra](#freeextra) .

W kompilacjach debugowania ATLASSERT zostanie zgłoszony, jeśli `CAtlArray` obiekt jest nieprawidłowy lub łączny łączny *IElement* i *nCount* przekracza całkowitą liczbę elementów w tablicy. W kompilacjach detalicznych nieprawidłowe parametry mogą spowodować nieprzewidywalne wyniki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]

## <a name="catlarraysetat"></a><a name="setat"></a>CAtlArray::SetAt

Wywołaj tę metodę, aby ustawić wartość elementu w obiekcie array.

```cpp
void SetAt(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Indeks wskazujący element tablicy, który ma zostać ustawiony.

*postaci*<br/>
Nowa wartość określonego elementu.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania zostanie zgłoszony ATLASSERT, jeśli *IElement* przekroczy liczbę elementów w tablicy. W kompilacjach detalicznych nieprawidłowy parametr może spowodować nieprzewidywalne wyniki.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlArray:: GetAt](#getat).

## <a name="catlarraysetcount"></a><a name="setcount"></a>CAtlArray:: SetCount

Wywołaj tę metodę, aby ustawić rozmiar obiektu Array.

```cpp
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```

### <a name="parameters"></a>Parametry

*nNewSize*<br/>
Wymagany rozmiar tablicy.

*nGrowBy*<br/>
Wartość służąca do określenia, jak duża ma być wielkość bufora. Wartość-1 powoduje użycie wewnętrznie obliczanej wartości.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli rozmiar tablicy został pomyślnie zmieniony, wartość false w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Rozmiar tablicy można zwiększyć lub zmniejszyć. W przypadku zwiększenia dodatkowe puste elementy są dodawane do tablicy. W przypadku spadku elementy o największych indeksach zostaną usunięte i zwolnione pamięci.

Użyj tej metody, aby ustawić rozmiar tablicy przed jej użyciem. Jeśli `SetCount` nie jest używany, proces dodawania elementów i kolejnej alokacji pamięci zostanie zredukowany w celu zmniejszenia wydajności i fragmentacji pamięci.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlArray:: GetData](#getdata).

## <a name="catlarraysetatgrow"></a><a name="setatgrow"></a>CAtlArray::SetAtGrow

Wywołaj tę metodę, aby ustawić wartość elementu w obiekcie array, rozszerzając tablicę zgodnie z potrzebami.

```cpp
void SetAtGrow(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Indeks wskazujący element tablicy, który ma zostać ustawiony.

*postaci*<br/>
Nowa wartość określonego elementu.

### <a name="remarks"></a>Uwagi

Zamienia wartość elementu wskazywanego przez indeks. Jeśli wartość *IElement* jest większa niż bieżący rozmiar tablicy, tablica zostanie automatycznie zwiększona przy użyciu wywołania [CAtlArray:: SetCount](#setcount). W kompilacjach debugowania ATLASSERT zostanie zgłoszony, jeśli `CAtlArray` obiekt jest nieprawidłowy. W kompilacjach detalicznych nieprawidłowe parametry mogą spowodować nieprzewidywalne wyniki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]

## <a name="see-also"></a>Zobacz także

[Przykład MMXSwarm](../../overview/visual-cpp-samples.md)<br/>
[Przykład DynamicConsumer](../../overview/visual-cpp-samples.md)<br/>
[Przykład UpdatePV](../../overview/visual-cpp-samples.md)<br/>
[Przykład neonu](../../overview/visual-cpp-samples.md)<br/>
[Klasa CArray](../../mfc/reference/carray-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
