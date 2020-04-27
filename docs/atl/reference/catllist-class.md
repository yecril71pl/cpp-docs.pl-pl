---
title: Klasa CAtlList
ms.date: 11/04/2016
f1_keywords:
- CAtlList
- ATLCOLL/ATL::CAtlList
- ATLCOLL/ATL::CAtlList::INARGTYPE
- ATLCOLL/ATL::CAtlList::CAtlList
- ATLCOLL/ATL::CAtlList::AddHead
- ATLCOLL/ATL::CAtlList::AddHeadList
- ATLCOLL/ATL::CAtlList::AddTail
- ATLCOLL/ATL::CAtlList::AddTailList
- ATLCOLL/ATL::CAtlList::AssertValid
- ATLCOLL/ATL::CAtlList::Find
- ATLCOLL/ATL::CAtlList::FindIndex
- ATLCOLL/ATL::CAtlList::GetAt
- ATLCOLL/ATL::CAtlList::GetCount
- ATLCOLL/ATL::CAtlList::GetHead
- ATLCOLL/ATL::CAtlList::GetHeadPosition
- ATLCOLL/ATL::CAtlList::GetNext
- ATLCOLL/ATL::CAtlList::GetPrev
- ATLCOLL/ATL::CAtlList::GetTail
- ATLCOLL/ATL::CAtlList::GetTailPosition
- ATLCOLL/ATL::CAtlList::InsertAfter
- ATLCOLL/ATL::CAtlList::InsertBefore
- ATLCOLL/ATL::CAtlList::IsEmpty
- ATLCOLL/ATL::CAtlList::MoveToHead
- ATLCOLL/ATL::CAtlList::MoveToTail
- ATLCOLL/ATL::CAtlList::RemoveAll
- ATLCOLL/ATL::CAtlList::RemoveAt
- ATLCOLL/ATL::CAtlList::RemoveHead
- ATLCOLL/ATL::CAtlList::RemoveHeadNoReturn
- ATLCOLL/ATL::CAtlList::RemoveTail
- ATLCOLL/ATL::CAtlList::RemoveTailNoReturn
- ATLCOLL/ATL::CAtlList::SetAt
- ATLCOLL/ATL::CAtlList::SwapElements
helpviewer_keywords:
- CAtlList class
ms.assetid: 09e98053-64b2-4efa-99ab-d0542caaf981
ms.openlocfilehash: 2c16713af11a915772085165ed294cba4ae337f2
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168049"
---
# <a name="catllist-class"></a>Klasa CAtlList

Ta klasa udostępnia metody tworzenia obiektu listy i zarządzania nim.

## <a name="syntax"></a>Składnia

```cpp
template<typename E, class ETraits = CElementTraits<E>>
class CAtlList
```

### <a name="parameters"></a>Parametry

*Adres*<br/>
Typ elementu.

*ETraits*<br/>
Kod używany do kopiowania lub przenoszenia elementów. Aby uzyskać więcej informacji, zobacz [Klasa CElementTraits](../../atl/reference/celementtraits-class.md) .

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CAtlList::INARGTYPE](#inargtype)||

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlList::CAtlList](#catllist)|Konstruktor.|
|[CAtlList:: ~ CAtlList](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlList:: addszef](#addhead)|Wywołaj tę metodę, aby dodać element do nagłówka listy.|
|[CAtlList::AddHeadList](#addheadlist)|Wywołaj tę metodę, aby dodać istniejącą listę do nagłówka listy.|
|[CAtlList:: AddTail](#addtail)|Wywołaj tę metodę, aby dodać element do ogona tej listy.|
|[CAtlList::AddTailList](#addtaillist)|Wywołaj tę metodę, aby dodać istniejącą listę do ogona tej listy.|
|[CAtlList::AssertValid](#assertvalid)|Wywołaj tę metodę, aby potwierdzić, że lista jest prawidłowa.|
|[CAtlList:: find](#find)|Wywołaj tę metodę, aby przeszukać listę dla określonego elementu.|
|[CAtlList:: FindIndex —](#findindex)|Wywołaj tę metodę, aby uzyskać położenie elementu, uwzględniając wartość indeksu.|
|[CAtlList::GetAt](#getat)|Wywołaj tę metodę, aby zwrócić element w określonej pozycji na liście.|
|[CAtlList:: GetCount](#getcount)|Wywołaj tę metodę, aby zwrócić liczbę obiektów na liście.|
|[CAtlList:: getszef](#gethead)|Wywołaj tę metodę, aby zwrócić element na początku listy.|
|[CAtlList::GetHeadPosition](#getheadposition)|Wywołaj tę metodę, aby uzyskać pozycję nagłówka listy.|
|[CAtlList:: GetNext](#getnext)|Wywołaj tę metodę, aby zwrócić następny element z listy.|
|[CAtlList:: getpoprz](#getprev)|Wywołaj tę metodę, aby zwrócić poprzedni element z listy.|
|[CAtlList:: GetTail](#gettail)|Wywołaj tę metodę, aby zwrócić element na końcu listy.|
|[CAtlList::GetTailPosition](#gettailposition)|Wywołaj tę metodę, aby uzyskać położenie ogona listy.|
|[CAtlList::InsertAfter](#insertafter)|Wywołaj tę metodę, aby wstawić nowy element do listy po określonej pozycji.|
|[CAtlList::InsertBefore](#insertbefore)|Wywołaj tę metodę, aby wstawić nowy element do listy przed określoną pozycją.|
|[CAtlList:: IsEmpty](#isempty)|Wywołaj tę metodę, aby określić, czy lista jest pusta.|
|[CAtlList::MoveToHead](#movetohead)|Wywołaj tę metodę, aby przenieść określony element do nagłówka listy.|
|[CAtlList::MoveToTail](#movetotail)|Wywołaj tę metodę, aby przenieść określony element do ogona listy.|
|[CAtlList::](#removeall)|Wywołaj tę metodę, aby usunąć wszystkie elementy z listy.|
|[CAtlList::RemoveAt](#removeat)|Wywołaj tę metodę, aby usunąć pojedynczy element z listy.|
|[CAtlList::RemoveHead](#removehead)|Wywołaj tę metodę, aby usunąć element znajdujący się na końcu listy.|
|[CAtlList::RemoveHeadNoReturn](#removeheadnoreturn)|Wywołaj tę metodę, aby usunąć element z nagłówka listy bez zwracania wartości.|
|[CAtlList::RemoveTail](#removetail)|Wywołaj tę metodę, aby usunąć element na końcu listy.|
|[CAtlList::RemoveTailNoReturn](#removetailnoreturn)|Wywołaj tę metodę, aby usunąć element na końcu listy bez zwracania wartości.|
|[CAtlList::SetAt](#setat)|Wywołaj tę metodę, aby ustawić wartość elementu w danej pozycji na liście.|
|[CAtlList::SwapElements](#swapelements)|Wywołaj tę metodę, aby zamienić elementy na liście.|

## <a name="remarks"></a>Uwagi

`CAtlList` Klasa obsługuje uporządkowane listy nieunikatowych obiektów dostępnych sekwencyjnie lub według wartości. `CAtlList`listy zachowują się jak listy połączone podwójnie. Każda lista ma nagłówek i ogon, a nowe elementy (lub listy w niektórych przypadkach) można dodać do dowolnego końca listy lub wstawić przed lub po określonych elementach.

Większość `CAtlList` metod używa wartości pozycji. Ta wartość jest używana przez metody do odwoływania się do rzeczywistej lokalizacji pamięci, w której są przechowywane elementy, i nie powinna być obliczana ani przewidywalna bezpośrednio. Jeśli konieczne jest uzyskanie dostępu do *n*-tego elementu na liście, Metoda [CAtlList:: FindIndex —](#findindex) zwróci odpowiadającą wartość pozycji dla danego indeksu. Metody [CAtlList:: GetNext](#getnext) i [CAtlList:: getpoprz](#getprev) mogą służyć do iteracji obiektów na liście.

Aby uzyskać więcej informacji na temat klas kolekcji dostępnych w przypadku biblioteki ATL, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll. h

## <a name="catllistaddhead"></a><a name="addhead"></a>CAtlList:: addszef

Wywołaj tę metodę, aby dodać element do nagłówka listy.

```cpp
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*postaci*<br/>
Nowy element.

### <a name="return-value"></a>Wartość zwracana

Zwraca pozycję nowo dodanego elementu.

### <a name="remarks"></a>Uwagi

Jeśli używana jest pierwsza wersja, pusty element jest tworzony przy użyciu jego konstruktora domyślnego, a nie jego konstruktora kopiującego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#13](../../atl/codesnippet/cpp/catllist-class_1.cpp)]

## <a name="catllistaddheadlist"></a><a name="addheadlist"></a>CAtlList::AddHeadList

Wywołaj tę metodę, aby dodać istniejącą listę do nagłówka listy.

```cpp
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Parametry

*plNew*<br/>
Lista, która ma zostać dodana.

### <a name="remarks"></a>Uwagi

Lista wskazywana przez *plNew* jest wstawiana na początku istniejącej listy. W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli *plNew* jest równa null.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#14](../../atl/codesnippet/cpp/catllist-class_2.cpp)]

## <a name="catllistaddtail"></a><a name="addtail"></a>CAtlList:: AddTail

Wywołaj tę metodę, aby dodać element do ogona tej listy.

```cpp
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*postaci*<br/>
Element, który ma zostać dodany.

### <a name="return-value"></a>Wartość zwracana

Zwraca pozycję nowo dodanego elementu.

### <a name="remarks"></a>Uwagi

Jeśli używana jest pierwsza wersja, pusty element jest tworzony przy użyciu jego konstruktora domyślnego, a nie jego konstruktora kopiującego. Element jest dodawany na końcu listy i dlatego teraz jest ogonem. Ta metoda może być używana z pustą listą.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#15](../../atl/codesnippet/cpp/catllist-class_3.cpp)]

## <a name="catllistaddtaillist"></a><a name="addtaillist"></a>CAtlList::AddTailList

Wywołaj tę metodę, aby dodać istniejącą listę do ogona tej listy.

```cpp
void AddTailList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Parametry

*plNew*<br/>
Lista, która ma zostać dodana.

### <a name="remarks"></a>Uwagi

Lista wskazywana przez *plNew* jest wstawiana po ostatnim elemencie (jeśli istnieje) w obiekcie list. W związku z tym ostatni element na liście *plNew* zmienia się na ogon. W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli *plNew* jest równa null.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#16](../../atl/codesnippet/cpp/catllist-class_4.cpp)]

## <a name="catllistassertvalid"></a><a name="assertvalid"></a>CAtlList::AssertValid

Wywołaj tę metodę, aby potwierdzić, że lista jest prawidłowa.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli obiekt listy jest nieprawidłowy. Aby można było korzystać z pustej listy, musi zawierać zarówno nagłówek, jak i zakończenie wskazujące wartość NULL, a lista, która nie jest pusta, musi mieć zarówno nagłówek, jak i ogon wskazujący prawidłowe adresy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#17](../../atl/codesnippet/cpp/catllist-class_5.cpp)]

## <a name="catllistcatllist"></a><a name="catllist"></a>CAtlList::CAtlList

Konstruktor.

```cpp
CAtlList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Rozmiar bloku.

### <a name="remarks"></a>Uwagi

Konstruktor dla `CAtlList` obiektu. Rozmiar bloku jest miarą ilości pamięci przydzieloną, gdy wymagany jest nowy element. Większe rozmiary bloków redukują wywołania procedur alokacji pamięci, ale wykorzystują więcej zasobów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#18](../../atl/codesnippet/cpp/catllist-class_6.cpp)]

## <a name="catllistcatllist"></a><a name="dtor"></a>CAtlList:: ~ CAtlList

Destruktor.

```cpp
~CAtlList() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzieloną zasoby, w tym wywołanie [CAtlList::](#removeall) Usuń wszystkie elementy z listy.

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli lista nadal zawiera pewne elementy po wywołaniu `RemoveAll`.

## <a name="catllistfind"></a><a name="find"></a>CAtlList:: find

Wywołaj tę metodę, aby przeszukać listę dla określonego elementu.

```cpp
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```

### <a name="parameters"></a>Parametry

*postaci*<br/>
Element, który ma znajdować się na liście.

*posStartAfter*<br/>
Pozycja początkowa dla wyszukiwania. Jeśli wartość nie jest określona, wyszukiwanie rozpoczyna się od elementu głównego.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość pozycji elementu, jeśli zostanie znaleziona. w przeciwnym razie zwraca wartość NULL.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli obiekt listy jest nieprawidłowy lub wartość *posStartAfter* jest poza zakresem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#19](../../atl/codesnippet/cpp/catllist-class_7.cpp)]

## <a name="catllistfindindex"></a><a name="findindex"></a>CAtlList:: FindIndex —

Wywołaj tę metodę, aby uzyskać położenie elementu, uwzględniając wartość indeksu.

```cpp
POSITION FindIndex(size_t iElement) const throw();
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Indeks (liczony od zera) wymaganego elementu listy.

### <a name="return-value"></a>Wartość zwracana

Zwraca odpowiadającą wartość pozycji lub wartość NULL, jeśli *IElement* jest poza zakresem.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca pozycję odpowiadającą danej wartości indeksu, umożliwiając dostęp do *n*-tego elementu na liście.

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli obiekt listy jest nieprawidłowy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#20](../../atl/codesnippet/cpp/catllist-class_8.cpp)]

## <a name="catllistgetat"></a><a name="getat"></a>CAtlList::GetAt

Wywołaj tę metodę, aby zwrócić element w określonej pozycji na liście.

```cpp
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Wartość pozycji określająca konkretny element.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu lub jego kopię.

### <a name="remarks"></a>Uwagi

Jeśli lista jest **stałą**, `GetAt` zwraca kopię elementu. Pozwala to na użycie metody tylko po prawej stronie instrukcji przypisania i ochronę listy przed modyfikacją.

Jeśli lista nie jest **stałą**, `GetAt` zwraca odwołanie do elementu. Pozwala to na użycie metody po obu stronach instrukcji przypisania i w ten sposób pozwala na modyfikowanie wpisów listy.

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli wartość *pos* będzie równa null.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlList:: FindIndex —](#findindex).

## <a name="catllistgetcount"></a><a name="getcount"></a>CAtlList:: GetCount

Wywołaj tę metodę, aby zwrócić liczbę obiektów na liście.

```cpp
size_t GetCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę elementów na liście.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlList:: find](#find).

## <a name="catllistgethead"></a><a name="gethead"></a>CAtlList:: getszef

Wywołaj tę metodę, aby zwrócić element na początku listy.

```cpp
E& GetHead() throw();
const E& GetHead() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do lub kopię elementu na początku listy.

### <a name="remarks"></a>Uwagi

Jeśli lista jest **stałą**, `GetHead` zwraca kopię elementu na początku listy. Pozwala to na użycie metody tylko po prawej stronie instrukcji przypisania i ochronę listy przed modyfikacją.

Jeśli lista nie jest **stałą**, `GetHead` zwraca odwołanie do elementu znajdującego się na końcu listy. Pozwala to na użycie metody po obu stronach instrukcji przypisania i w ten sposób pozwala na modyfikowanie wpisów listy.

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli nagłówek listy wskazuje wartość NULL.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlList:: addszef](#addhead).

## <a name="catllistgetheadposition"></a><a name="getheadposition"></a>CAtlList::GetHeadPosition

Wywołaj tę metodę, aby uzyskać pozycję nagłówka listy.

```cpp
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość pozycji odpowiadającą elementowi w nagłówku listy.

### <a name="remarks"></a>Uwagi

Jeśli lista jest pusta, zwrócona wartość jest RÓWNa NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#21](../../atl/codesnippet/cpp/catllist-class_9.cpp)]

## <a name="catllistgetnext"></a><a name="getnext"></a>CAtlList:: GetNext

Wywołaj tę metodę, aby zwrócić następny element z listy.

```cpp
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Wartość pozycji zwrócona przez poprzednie wywołanie do `GetNext`, [CAtlList:: GetHeadPosition](#getheadposition)lub inną `CAtlList` metodę.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest **stałą**, `GetNext` zwraca kopię następnego elementu listy. Pozwala to na użycie metody tylko po prawej stronie instrukcji przypisania i ochronę listy przed modyfikacją.

Jeśli lista nie jest **stałą**, `GetNext` zwraca odwołanie do następnego elementu listy. Pozwala to na użycie metody po obu stronach instrukcji przypisania i w ten sposób pozwala na modyfikowanie wpisów listy.

### <a name="remarks"></a>Uwagi

Licznik pozycji, *pos*został zaktualizowany tak, aby wskazywał następny element na liście, lub wartość null, jeśli nie ma więcej elementów. W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli wartość *pos* będzie równa null.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlList:: GetHeadPosition](#getheadposition).

## <a name="catllistgetprev"></a><a name="getprev"></a>CAtlList:: getpoprz

Wywołaj tę metodę, aby zwrócić poprzedni element z listy.

```cpp
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Wartość pozycji zwrócona przez poprzednie wywołanie do `GetPrev`, [CAtlList:: GetTailPosition](#gettailposition)lub inną `CAtlList` metodę.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest **stałą**, `GetPrev` zwraca kopię elementu listy. Pozwala to na użycie metody tylko po prawej stronie instrukcji przypisania i ochronę listy przed modyfikacją.

Jeśli lista nie jest **stałą**, `GetPrev` zwraca odwołanie do elementu listy. Pozwala to na użycie metody po obu stronach instrukcji przypisania i w ten sposób pozwala na modyfikowanie wpisów listy.

### <a name="remarks"></a>Uwagi

Licznik pozycji, *pos*został zaktualizowany tak, aby wskazywał poprzedni element na liście, lub wartość null, jeśli nie ma więcej elementów. W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli wartość *pos* będzie równa null.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlList:: GetTailPosition](#gettailposition).

## <a name="catllistgettail"></a><a name="gettail"></a>CAtlList:: GetTail

Wywołaj tę metodę, aby zwrócić element na końcu listy.

```cpp
E& GetTail() throw();
const E& GetTail() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do lub kopię elementu na końcu listy.

### <a name="remarks"></a>Uwagi

Jeśli lista jest **stałą**, `GetTail` zwraca kopię elementu na początku listy. Pozwala to na użycie metody tylko po prawej stronie instrukcji przypisania i ochronę listy przed modyfikacją.

Jeśli lista nie jest **stałą**, `GetTail` zwraca odwołanie do elementu znajdującego się na końcu listy. Pozwala to na użycie metody po obu stronach instrukcji przypisania i w ten sposób pozwala na modyfikowanie wpisów listy.

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli ogon listy wskazuje wartość NULL.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlList:: AddTail](#addtail).

## <a name="catllistgettailposition"></a><a name="gettailposition"></a>CAtlList::GetTailPosition

Wywołaj tę metodę, aby uzyskać położenie ogona listy.

```cpp
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość pozycji odpowiadającą elementowi na końcu listy.

### <a name="remarks"></a>Uwagi

Jeśli lista jest pusta, zwrócona wartość jest RÓWNa NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#22](../../atl/codesnippet/cpp/catllist-class_10.cpp)]

## <a name="catllistinargtype"></a><a name="inargtype"></a>CAtlList::INARGTYPE

Typ używany, gdy element jest przenoszona jako argument wejściowy.

```cpp
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catllistinsertafter"></a><a name="insertafter"></a>CAtlList::InsertAfter

Wywołaj tę metodę, aby wstawić nowy element do listy po określonej pozycji.

```cpp
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Wartość pozycji, po której zostanie wstawiony nowy element.

*postaci*<br/>
Element, który ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość pozycji nowego elementu.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli lista jest nieprawidłowa, jeśli nie powiedzie się, lub jeśli podjęto próbę wstawienia elementu po stronie ogonowej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#23](../../atl/codesnippet/cpp/catllist-class_11.cpp)]

## <a name="catllistinsertbefore"></a><a name="insertbefore"></a>CAtlList::InsertBefore

Wywołaj tę metodę, aby wstawić nowy element do listy przed określoną pozycją.

```cpp
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Nowy element zostanie wstawiony do listy przed tą wartością pozycji.

*postaci*<br/>
Element, który ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość pozycji nowego elementu.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli lista jest nieprawidłowa, jeśli nie powiedzie się, lub jeśli podjęto próbę wstawienia elementu przed nagłówkiem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#24](../../atl/codesnippet/cpp/catllist-class_12.cpp)]

## <a name="catllistisempty"></a><a name="isempty"></a>CAtlList:: IsEmpty

Wywołaj tę metodę, aby określić, czy lista jest pusta.

```cpp
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli lista nie zawiera żadnych obiektów, w przeciwnym razie false.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#25](../../atl/codesnippet/cpp/catllist-class_13.cpp)]

## <a name="catllistmovetohead"></a><a name="movetohead"></a>CAtlList::MoveToHead

Wywołaj tę metodę, aby przenieść określony element do nagłówka listy.

```cpp
void MoveToHead(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Wartość pozycji elementu do przeniesienia.

### <a name="remarks"></a>Uwagi

Określony element jest przenoszony z jego bieżącej pozycji do nagłówka listy. W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli wartość *pos* będzie równa null.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#26](../../atl/codesnippet/cpp/catllist-class_14.cpp)]

## <a name="catllistmovetotail"></a><a name="movetotail"></a>CAtlList::MoveToTail

Wywołaj tę metodę, aby przenieść określony element do ogona listy.

```cpp
void MoveToTail(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Wartość pozycji elementu do przeniesienia.

### <a name="remarks"></a>Uwagi

Określony element jest przenoszony z jego bieżącej pozycji do ogona listy. W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli wartość *pos* będzie równa null.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlList:: MoveToHead](#movetohead).

## <a name="catllistremoveall"></a><a name="removeall"></a>CAtlList::

Wywołaj tę metodę, aby usunąć wszystkie elementy z listy.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Uwagi

Ta metoda usuwa wszystkie elementy z listy i zwalnia przydzieloną pamięć. W kompilacjach debugowania program ATLASSERT zostanie zgłoszony, jeśli wszystkie elementy nie zostaną usunięte lub jeśli struktura listy uległa uszkodzeniu.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlList:: IsEmpty](#isempty).

## <a name="catllistremoveat"></a><a name="removeat"></a>CAtlList::RemoveAt

Wywołaj tę metodę, aby usunąć pojedynczy element z listy.

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Wartość pozycji elementu do usunięcia.

### <a name="remarks"></a>Uwagi

Element, do którego odwołuje się system *pos* , jest usuwany, a pamięć jest zwalniana. Można go użyć `RemoveAt` do usunięcia nagłówka lub ogona listy.

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli lista jest nieprawidłowa lub jeśli usunięcie elementu powoduje, że lista ma dostęp do pamięci, która nie jest częścią struktury listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#27](../../atl/codesnippet/cpp/catllist-class_15.cpp)]

## <a name="catllistremovehead"></a><a name="removehead"></a>CAtlList::RemoveHead

Wywołaj tę metodę, aby usunąć element znajdujący się na końcu listy.

```cpp
E RemoveHead();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca element znajdujący się na początku listy.

### <a name="remarks"></a>Uwagi

Element główny jest usuwany z listy, a pamięć jest zwalniana. Zostanie zwrócona kopia elementu. W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli lista jest pusta.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#28](../../atl/codesnippet/cpp/catllist-class_16.cpp)]

## <a name="catllistremoveheadnoreturn"></a><a name="removeheadnoreturn"></a>CAtlList::RemoveHeadNoReturn

Wywołaj tę metodę, aby usunąć element z nagłówka listy bez zwracania wartości.

```cpp
void RemoveHeadNoReturn() throw();
```

### <a name="remarks"></a>Uwagi

Element główny jest usuwany z listy, a pamięć jest zwalniana. W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli lista jest pusta.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlList:: IsEmpty](#isempty).

## <a name="catllistremovetail"></a><a name="removetail"></a>CAtlList::RemoveTail

Wywołaj tę metodę, aby usunąć element na końcu listy.

```cpp
E RemoveTail();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca element na końcu listy.

### <a name="remarks"></a>Uwagi

Element tail zostanie usunięty z listy, a pamięć jest zwalniana. Zostanie zwrócona kopia elementu. W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli lista jest pusta.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#29](../../atl/codesnippet/cpp/catllist-class_17.cpp)]

## <a name="catllistremovetailnoreturn"></a><a name="removetailnoreturn"></a>CAtlList::RemoveTailNoReturn

Wywołaj tę metodę, aby usunąć element na końcu listy bez zwracania wartości.

```cpp
void RemoveTailNoReturn() throw();
```

### <a name="remarks"></a>Uwagi

Element tail zostanie usunięty z listy, a pamięć jest zwalniana. W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli lista jest pusta.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlList:: IsEmpty](#isempty).

## <a name="catllistsetat"></a><a name="setat"></a>CAtlList::SetAt

Wywołaj tę metodę, aby ustawić wartość elementu w danej pozycji na liście.

```cpp
void SetAt(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Wartość pozycji odpowiadająca elementowi do zmiany.

*postaci*<br/>
Wartość nowego elementu.

### <a name="remarks"></a>Uwagi

Zamienia istniejącą wartość na *element*. W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli wartość *pos* będzie równa null.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#30](../../atl/codesnippet/cpp/catllist-class_18.cpp)]

## <a name="catllistswapelements"></a><a name="swapelements"></a>CAtlList::SwapElements

Wywołaj tę metodę, aby zamienić elementy na liście.

```cpp
void SwapElements(POSITION pos1, POSITION pos2) throw();
```

### <a name="parameters"></a>Parametry

*pos1*<br/>
Wartość pierwszej pozycji.

*pos2*<br/>
Wartość drugiego położenia.

### <a name="remarks"></a>Uwagi

Zamienia elementy na podane dwa położenia. W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli wartość pozycji jest równa NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#31](../../atl/codesnippet/cpp/catllist-class_19.cpp)]

## <a name="see-also"></a>Zobacz także

[Klasa CList](../../mfc/reference/clist-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
