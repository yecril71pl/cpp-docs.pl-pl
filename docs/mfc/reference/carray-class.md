---
title: Klasa CArray
ms.date: 11/04/2016
f1_keywords:
- CArray
- AFXTEMPL/CArray
- AFXTEMPL/CArray::CArray
- AFXTEMPL/CArray::Add
- AFXTEMPL/CArray::Append
- AFXTEMPL/CArray::Copy
- AFXTEMPL/CArray::ElementAt
- AFXTEMPL/CArray::FreeExtra
- AFXTEMPL/CArray::GetAt
- AFXTEMPL/CArray::GetCount
- AFXTEMPL/CArray::GetData
- AFXTEMPL/CArray::GetSize
- AFXTEMPL/CArray::GetUpperBound
- AFXTEMPL/CArray::InsertAt
- AFXTEMPL/CArray::IsEmpty
- AFXTEMPL/CArray::RemoveAll
- AFXTEMPL/CArray::RemoveAt
- AFXTEMPL/CArray::SetAt
- AFXTEMPL/CArray::SetAtGrow
- AFXTEMPL/CArray::SetSize
helpviewer_keywords:
- CArray [MFC], CArray
- CArray [MFC], Add
- CArray [MFC], Append
- CArray [MFC], Copy
- CArray [MFC], ElementAt
- CArray [MFC], FreeExtra
- CArray [MFC], GetAt
- CArray [MFC], GetCount
- CArray [MFC], GetData
- CArray [MFC], GetSize
- CArray [MFC], GetUpperBound
- CArray [MFC], InsertAt
- CArray [MFC], IsEmpty
- CArray [MFC], RemoveAll
- CArray [MFC], RemoveAt
- CArray [MFC], SetAt
- CArray [MFC], SetAtGrow
- CArray [MFC], SetSize
ms.assetid: fead8b00-4cfd-4625-ad0e-251df62ba92f
ms.openlocfilehash: 3355e72c58365e97f8f3f8ce09754285f671915a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753980"
---
# <a name="carray-class"></a>Klasa CArray

Obsługuje tablice, które są jak tablice C, ale można dynamicznie zmniejszyć i rozwijać w razie potrzeby.

## <a name="syntax"></a>Składnia

```
template <class TYPE, class ARG_TYPE = const TYPE&>
class CArray : public CObject
```

#### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ obiektów przechowywanych w tablicy. *TYPE* jest parametrem zwracanym przez `CArray`plik .

*ARG_TYPE*<br/>
Parametr Szablon, który określa typ argumentu, który jest używany do uzyskiwania dostępu do obiektów przechowywanych w tablicy. Często odniesienie do *TYPE*. *ARG_TYPE* jest parametrem przekazywanym do `CArray`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CArray::CArray](#carray)|Konstruuje pustą tablicę.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CArray::Dodaj](#add)|Dodaje element na końcu tablicy; w razie potrzeby zwiększa tablicę.|
|[CArray::Dołącz](#append)|Dołącza inną tablicę do tablicy; w razie potrzeby zwiększa tablicę|
|[CArray::Kopiowanie](#copy)|Kopiuje inną tablicę do tablicy; w razie potrzeby zwiększa tablicę.|
|[CArray::ElementAt](#elementat)|Zwraca tymczasowe odwołanie do wskaźnika elementu w tablicy.|
|[CArray::FreeExtra](#freeextra)|Zwalnia całą nieużytą pamięć powyżej bieżącej górnej granicy.|
|[CArray::GetAt](#getat)|Zwraca wartość w danym indeksie.|
|[CArray::GetCount](#getcount)|Pobiera liczbę elementów w tej tablicy.|
|[CArray::GetData](#getdata)|Umożliwia dostęp do elementów w tablicy. Może mieć wartość NULL.|
|[CArray::GetSize](#getsize)|Pobiera liczbę elementów w tej tablicy.|
|[CArray::GetUpperBound](#getupperbound)|Zwraca największy prawidłowy indeks.|
|[CArray::Wstawianie](#insertat)|Wstawia element (lub wszystkie elementy w innej tablicy) w określonym indeksie.|
|[CArray::IsEmpty](#isempty)|Określa, czy tablica jest pusta.|
|[CArray::Usuńwszywszystko](#removeall)|Usuwa wszystkie elementy z tej tablicy.|
|[CArray::Usuń](#removeat)|Usuwa element w określonym indeksie.|
|[CArray::SetAt](#setat)|Ustawia wartość dla danego indeksu; tablicy nie może rosnąć.|
|[CArray::SetAtGrow](#setatgrow)|Ustawia wartość dla danego indeksu; w razie potrzeby zwiększa tablicę.|
|[CArray::SetSize](#setsize)|Ustawia liczbę elementów, które mają być zawarte w tej tablicy.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[&#91;&#93;operatora](#operator_at)|Ustawia lub pobiera element w określonym indeksie.|

## <a name="remarks"></a>Uwagi

Indeksy tablicy zawsze zaczynają się od pozycji 0. Można zdecydować, czy naprawić górną granicę lub włączyć tablicy, aby rozwinąć po dodaniu elementów poza bieżącą powiązaną. Pamięć jest przydzielana w sposób ciągły do górnej granicy, nawet jeśli niektóre elementy są null.

> [!NOTE]
> Większość metod, które `CArray` zmienić rozmiar obiektu lub dodać elementy do niego używać [memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md) do przenoszenia elementów. Jest to problem, ponieważ `memcpy_s` nie jest zgodny z żadnych obiektów, które wymagają konstruktora do wywołania. Jeśli elementy w `CArray` nie są `memcpy_s`zgodne z , `CArray` należy utworzyć nowy o odpowiednim rozmiarze. Następnie należy użyć [CArray::Copy](#copy) i [CArray::SetAt,](#setat) aby wypełnić nową tablicę, `memcpy_s`ponieważ metody te używają operatora przypisania zamiast .

Podobnie jak w przypadku tablicy `CArray` C, czas dostępu dla elementu indeksowanego jest stały i jest niezależny od rozmiaru tablicy.

> [!TIP]
> Przed użyciem tablicy należy użyć [SetSize,](#setsize) aby ustalić jego rozmiar i przydzielić dla niego pamięć. Jeśli nie używasz `SetSize`, dodawanie elementów do tablicy powoduje, że często są ponownie przydzielane i kopiowane. Częste ponowne przydzielanie i kopiowanie są nieefektywne i mogą fragmentować pamięć.

Jeśli potrzebujesz zrzutu poszczególnych elementów w tablicy, należy ustawić głębokość [obiektu CDumpContext](../../mfc/reference/cdumpcontext-class.md) na 1 lub większy.

Niektóre funkcje członkowskie tej klasy wywołać globalne funkcje pomocnika, `CArray` które muszą być dostosowane do większości zastosowań klasy. Zobacz temat [Pomocników klasy kolekcji](../../mfc/reference/collection-class-helpers.md) w sekcji Makra MFC i Globals.

Wyprowadzanie klasy tablicy jest jak wyprowadzanie listy.

Aby uzyskać więcej informacji `CArray`na temat używania , zobacz artykuł [Kolekcje](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtempl.h

## <a name="carrayadd"></a><a name="add"></a>CArray::Dodaj

Dodaje nowy element na końcu tablicy, powiększając tablicę o 1.

```
INT_PTR Add(ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*ARG_TYPE*<br/>
Parametr szablonu określający typ argumentów odwołujących się do elementów w tej tablicy.

*nowyElement*<br/>
Element, który ma zostać dodany do tej tablicy.

### <a name="return-value"></a>Wartość zwracana

Indeks dodanego elementu.

### <a name="remarks"></a>Uwagi

Jeśli [SetSize](#setsize) został użyty z wartością `nGrowBy` większą niż 1, można przydzielić dodatkową pamięć. Jednak górna granica wzrośnie tylko o 1.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]

## <a name="carrayappend"></a><a name="append"></a>CArray::Dołącz

Wywołanie tej funkcji elementu członkowskiego, aby dodać zawartość jednej tablicy na końcu innej.

```
INT_PTR Append(const CArray& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
Źródło elementów, które mają być dołączone do tablicy.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszego dołączonego elementu.

### <a name="remarks"></a>Uwagi

Tablice muszą być tego samego typu.

W razie `Append` potrzeby może przydzielić dodatkową pamięć, aby pomieścić elementy dołączone do tablicy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]

## <a name="carraycarray"></a><a name="carray"></a>CArray::CArray

Konstruuje pustą tablicę.

```
CArray();
```

### <a name="remarks"></a>Uwagi

Tablica rośnie jeden element naraz.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]

## <a name="carraycopy"></a><a name="copy"></a>CArray::Kopiowanie

Ta funkcja elementu członkowskiego służy do kopiowania elementów jednej tablicy do innej.

```cpp
void Copy(const CArray& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
Źródło elementów, które mają zostać skopiowane do tablicy.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji elementu członkowskiego, aby zastąpić elementy jednej tablicy z elementami innej tablicy.

`Copy`nie zwalnia pamięci; jednak w razie `Copy` potrzeby może przydzielić dodatkową pamięć, aby pomieścić elementy skopiowane do tablicy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]

## <a name="carrayelementat"></a><a name="elementat"></a>CArray::ElementAt

Zwraca tymczasowe odwołanie do określonego elementu w tablicy.

```
TYPE& ElementAt(INT_PTR nIndex);
const TYPE& ElementAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0 i mniejszy lub równy wartości zwracanej przez [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu tablicy.

### <a name="remarks"></a>Uwagi

Służy do implementowania operatora przypisania po lewej stronie dla tablic.

### <a name="example"></a>Przykład

  Zobacz przykład [getsize](#getsize).

## <a name="carrayfreeextra"></a><a name="freeextra"></a>CArray::FreeExtra

Zwalnia wszelkie dodatkowe pamięci, która została przydzielona, gdy tablica została wyhodowana.

```cpp
void FreeExtra();
```

### <a name="remarks"></a>Uwagi

Ta funkcja nie ma wpływu na rozmiar lub górną granicę tablicy.

### <a name="example"></a>Przykład

  Zobacz przykład [getdata](#getdata).

## <a name="carraygetat"></a><a name="getat"></a>CArray::GetAt

Zwraca element tablicy w określonym indeksie.

```
TYPE& GetAt(INT_PTR nIndex);
const TYPE& GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów tablicy.

*Nindex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0 i mniejszy lub równy wartości zwracanej przez [GetUpperBound](#getupperbound).

### <a name="return-value"></a>Wartość zwracana

Element tablicy obecnie w tym indeksie.

### <a name="remarks"></a>Uwagi

Przekazywanie wartości ujemnej lub wartości większej `GetUpperBound` niż wartość zwrócona przez spowoduje niepowodzenie potwierdzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]

## <a name="carraygetcount"></a><a name="getcount"></a>CArray::GetCount

Zwraca liczbę elementów tablicy.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w tablicy.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby pobrać liczbę elementów w tablicy. Ponieważ indeksy są oparte na wartościach zerowych, rozmiar jest o 1 większy niż największy indeks. Wywołanie tej metody wygeneruje taki sam wynik jak [CArray::GetSize](#getsize) metody.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]

## <a name="carraygetdata"></a><a name="getdata"></a>CArray::GetData

Ta funkcja elementu członkowskiego służy do uzyskiwania bezpośredniego dostępu do elementów w tablicy.

```
const TYPE* GetData() const;
TYPE* GetData();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów tablicy.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu tablicy.

### <a name="remarks"></a>Uwagi

Jeśli żadne elementy `GetData` nie są dostępne, zwraca wartość null.

Podczas gdy bezpośredni dostęp do elementów tablicy może pomóc `GetData`w ciężej pracy, należy zachować ostrożność podczas wywoływania; wszelkie błędy, które można wprowadzić bezpośrednio wpływają na elementy tablicy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]

## <a name="carraygetsize"></a><a name="getsize"></a>CArray::GetSize

Zwraca rozmiar tablicy.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Uwagi

Ponieważ indeksy są oparte na wartościach zerowych, rozmiar jest o 1 większy niż największy indeks. Wywołanie tej metody wygeneruje taki sam wynik jak [CArray::GetCount](#getcount) metody.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]

## <a name="carraygetupperbound"></a><a name="getupperbound"></a>CArray::GetUpperBound

Zwraca bieżącą górną granicę tej tablicy.

```
INT_PTR GetUpperBound() const;
```

### <a name="remarks"></a>Uwagi

Ponieważ indeksy tablicowe są oparte na wartości zero, `GetSize`ta funkcja zwraca wartość o 1 mniejszą niż .

Warunek `GetUpperBound( )` = -1 wskazuje, że tablica nie zawiera żadnych elementów.

### <a name="example"></a>Przykład

  Zobacz przykład [CArray::GetAt](#getat).

## <a name="carrayinsertat"></a><a name="insertat"></a>CArray::Wstawianie

Pierwsza wersja `InsertAt` wstawia jeden element (lub wiele kopii elementu) w określonym indeksie w tablicy.

```cpp
void InsertAt(
    INT_PTR nIndex,
    ARG_TYPE newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CArray* pNewArray);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks liczby całkowitej, który może być `GetUpperBound`większy niż wartość zwracana przez .

*ARG_TYPE*<br/>
Parametr szablonu określający typ elementów w tej tablicy.

*nowyElement*<br/>
Element, który ma zostać umieszczony w tej tablicy.

*Ncount*<br/>
Liczba wstawienia tego elementu (wartość domyślna to 1).

*nStartIndex*<br/>
Indeks liczby całkowitej, który może być większy niż wartość zwracana przez [GetUpperBound](#getupperbound).

*pNewArray (Nienawisłość)*<br/>
Inna tablica, która zawiera elementy, które mają zostać dodane do tej tablicy.

### <a name="remarks"></a>Uwagi

W procesie przesuwa się w górę (przez zwiększanie indeksu) istniejący element w tym indeksie i przesuwa się w górę wszystkie elementy nad nim.

Druga wersja wstawia wszystkie `CArray` elementy z innej kolekcji, począwszy od pozycji *nStartIndex.*

Funkcja `SetAt` natomiast zastępuje jeden określony element tablicy i nie przesuwa żadnych elementów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]

## <a name="carrayisempty"></a><a name="isempty"></a>CArray::IsEmpty

Określa, czy tablica jest pusta.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli tablica nie zawiera żadnych elementów; w przeciwnym razie 0.

## <a name="carrayoperator-"></a><a name="operator_at"></a>CArray::operator\[\]

Te operatory indeksu dolnego są wygodnym substytutem funkcji [SetAt](#setat) i [GetAt.](#getat)

```
TYPE& operator[](int_ptr nindex);
const TYPE& operator[](int_ptr nindex) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów w tej tablicy.

*Nindex*<br/>
Indeks elementu, do który ma być dostęp.

### <a name="remarks"></a>Uwagi

Pierwszy operator, wywoływany dla tablic, które nie są **const,** mogą być używane po prawej stronie (r-value) lub po lewej stronie (l-value) instrukcji przypisania. Drugi, wywoływany dla **const** tablice, mogą być używane tylko po prawej stronie.

Wersja debugowania biblioteki potwierdza, jeśli indeks dolny (po lewej lub prawej stronie instrukcji przypisania) jest poza granicami.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]

## <a name="carrayrelocateelements"></a><a name="relocateelements"></a>CArray::RelocateElements

Przenosi dane do nowego buforu, gdy tablica powinna rosnąć lub zmniejszać.

```
template<class TYPE, class ARG_TYPE>
AFX_INLINE void CArray<TYPE, ARG_TYPE>::RelocateElements(
    TYPE* pNewData,
    const TYPE* pData,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parametry

*pNewData*<br/>
Nowy bufor dla tablicy elementów.

*Pdata*<br/>
Stara tablica elementów.

*Ncount*<br/>
Liczba elementów w starej tablicy.

### <a name="remarks"></a>Uwagi

*pNewData* jest zawsze wystarczająco duży, aby pomieścić wszystkie elementy *pData.*

Implementacja [CArray](../../mfc/reference/carray-class.md) używa tej metody do kopiowania starych danych do nowego buforu, gdy tablica powinna rosnąć lub zmniejszać (gdy wywoływane są [SetSize](#setsize) lub [FreeExtra).](#freeextra) Domyślna implementacja po prostu kopiuje dane.

Dla tablic, w których element zawiera wskaźnik do jednego z własnych elementów członkowskich lub innej struktury zawiera wskaźnik do jednego z elementów tablicy, wskaźniki nie są aktualizowane w zwykłej kopii. W takim przypadku można poprawić wskaźniki, implementując `RelocateElements` specjalizację z odpowiednimi typami. Użytkownik jest również odpowiedzialny za kopiowanie danych.

## <a name="carrayremoveall"></a><a name="removeall"></a>CArray::Usuńwszywszystko

Usuwa wszystkie elementy z tej tablicy.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Uwagi

Jeśli tablica jest już pusta, funkcja nadal działa.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]

## <a name="carrayremoveat"></a><a name="removeat"></a>CArray::Usuń

Usuwa jeden lub więcej elementów, począwszy od określonego indeksu w tablicy.

```cpp
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0 i mniejszy lub równy wartości zwracanej przez [GetUpperBound](#getupperbound).

*Ncount*<br/>
Liczba elementów do usunięcia.

### <a name="remarks"></a>Uwagi

W procesie przesuwa się w dół wszystkie elementy powyżej usuniętego elementu(-ów). Zmniejsza górną granicę tablicy, ale nie zwalnia pamięci.

Jeśli spróbujesz usunąć więcej elementów niż są zawarte w tablicy powyżej punktu usuwania, a następnie debugowania wersji biblioteki potwierdza.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]

## <a name="carraysetat"></a><a name="setat"></a>CArray::SetAt

Ustawia element tablicy w określonym indeksie.

```cpp
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0 i mniejszy lub równy wartości zwracanej przez [GetUpperBound](#getupperbound).

*ARG_TYPE*<br/>
Parametr szablonu określający typ argumentów używanych do odwoływania się do elementów tablicy.

*nowyElement*<br/>
Wartość nowego elementu, która ma być przechowywana w określonym położeniu.

### <a name="remarks"></a>Uwagi

`SetAt`nie spowoduje, że tablica wzrośnie. Użyj [SetAtGrow,](#setatgrow) jeśli chcesz, aby tablica rosła automatycznie.

Należy upewnić się, że wartość indeksu reprezentuje prawidłową pozycję w tablicy. Jeśli jest poza granicami, a następnie debugowania wersji biblioteki potwierdza.

### <a name="example"></a>Przykład

  Zobacz przykład [getat](#getat).

## <a name="carraysetatgrow"></a><a name="setatgrow"></a>CArray::SetAtGrow

Ustawia element tablicy w określonym indeksie.

```cpp
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks liczby całkowitej, który jest większy lub równy 0.

*ARG_TYPE*<br/>
Parametr szablonu określający typ elementów w tablicy.

*nowyElement*<br/>
Element, który ma zostać dodany do tej tablicy. Wartość NULL jest dozwolona.

### <a name="remarks"></a>Uwagi

Tablica rośnie automatycznie, jeśli to konieczne (oznacza to, że górna granica jest dostosowana do nowego elementu).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]

## <a name="carraysetsize"></a><a name="setsize"></a>CArray::SetSize

Ustanawia rozmiar pustej lub istniejącej tablicy; przydziela pamięć, jeśli to konieczne.

```cpp
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

Jeśli nowy rozmiar jest mniejszy niż stary rozmiar, tablica jest obcinana i zwalniana jest cała nieużywana pamięć.

Ta funkcja służy do ustawiania rozmiaru tablicy przed rozpoczęciem korzystania z tablicy. Jeśli nie używasz `SetSize`, dodawanie elementów do tablicy powoduje, że często są ponownie przydzielane i kopiowane. Częste ponowne przydzielanie i kopiowanie są nieefektywne i mogą fragmentować pamięć.

Parametr *nGrowBy* wpływa na alokację pamięci wewnętrznej, gdy tablica rośnie. Jego użycie nigdy nie wpływa na rozmiar tablicy zgłoszony przez [GetSize](#getsize) i [GetUpperBound](#getupperbound). Jeśli używana jest wartość domyślna, MFC przydziela pamięć w sposób obliczony, aby uniknąć fragmentacji pamięci i zoptymalizować wydajność w większości przypadków.

### <a name="example"></a>Przykład

  Zobacz przykład [getdata](#getdata).

## <a name="see-also"></a>Zobacz też

[MFC Próbki COLLECT](../../overview/visual-cpp-samples.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CObArray](../../mfc/reference/cobarray-class.md)<br/>
[Pomocnicy klasy kolekcji](../../mfc/reference/collection-class-helpers.md)
