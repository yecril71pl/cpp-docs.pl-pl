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
ms.openlocfilehash: 0e4ea8eef51431c100f5d3119d7f75e9673e276e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748737"
---
# <a name="catllist-class"></a>Klasa CAtlList

Ta klasa zawiera metody tworzenia i zarządzania obiektem listy.

## <a name="syntax"></a>Składnia

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlList
```

#### <a name="parameters"></a>Parametry

*E*<br/>
Typ elementu.

*ETraits ( eTraits )*<br/>
Kod używany do kopiowania lub przenoszenia elementów. Zobacz [CElementTraits Klasy,](../../atl/reference/celementtraits-class.md) aby uzyskać więcej informacji.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|[Lista CAtl::INARGTYPE](#inargtype)||

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Lista CAtlList::CAtlList](#catllist)|Konstruktor.|
|[Lista CAtlList::~CAtlList](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Lista CAtl::Głowica dodania](#addhead)|Wywołanie tej metody, aby dodać element do głowy listy.|
|[Lista CAtlList::Dodaj listę nagłówków](#addheadlist)|Wywołanie tej metody, aby dodać istniejącą listę do szefa listy.|
|[Lista CAtl::Dodajtail](#addtail)|Wywołanie tej metody, aby dodać element do ogona tej listy.|
|[Lista CAtlList::DodajtailList](#addtaillist)|Wywołanie tej metody, aby dodać istniejącą listę do ogona tej listy.|
|[Lista CAtl::AssertValid](#assertvalid)|Wywołanie tej metody, aby potwierdzić, że lista jest prawidłowa.|
|[Lista CAtl::Znajdź](#find)|Wywołanie tej metody, aby wyszukać listę dla określonego elementu.|
|[Lista CAtlList::FindIndex](#findindex)|Wywołanie tej metody, aby uzyskać położenie elementu, biorąc pod uwagę wartość indeksu.|
|[Lista CAtl::GetAt](#getat)|Wywołanie tej metody, aby zwrócić element w określonej pozycji na liście.|
|[Lista CAtlList::GetCount](#getcount)|Wywołanie tej metody, aby zwrócić liczbę obiektów na liście.|
|[Lista CAtl::GetHead](#gethead)|Wywołanie tej metody, aby zwrócić element na czele listy.|
|[Lista CAtl::GetHeadPosition](#getheadposition)|Wywołanie tej metody, aby uzyskać pozycję szefa listy.|
|[Lista CAtl::GetNext](#getnext)|Wywołanie tej metody, aby zwrócić następny element z listy.|
|[Lista CAtlList::GetPrev](#getprev)|Wywołanie tej metody, aby zwrócić poprzedni element z listy.|
|[Lista CAtl::GetTail](#gettail)|Wywołanie tej metody, aby zwrócić element w ogonie listy.|
|[Lista CAtl::GetTailPosition](#gettailposition)|Wywołanie tej metody, aby uzyskać położenie ogona listy.|
|[Lista CAtl::WstawianiePo](#insertafter)|Wywołanie tej metody, aby wstawić nowy element do listy po określonej pozycji.|
|[Lista CAtlList::InsertBefore](#insertbefore)|Wywołanie tej metody, aby wstawić nowy element do listy przed określonym pozycją.|
|[Lista CAtlList::IsEmpty](#isempty)|Wywołanie tej metody, aby ustalić, czy lista jest pusta.|
|[Lista CAtlList::MoveToHead](#movetohead)|Wywołanie tej metody, aby przenieść określony element do głowy listy.|
|[Lista CAtlList::MoveToTail](#movetotail)|Wywołanie tej metody, aby przenieść określony element do ogona listy.|
|[Lista CAtl::Usuńwszywszystki](#removeall)|Wywołanie tej metody, aby usunąć wszystkie elementy z listy.|
|[Lista CAtl::Usuń](#removeat)|Wywołanie tej metody, aby usunąć pojedynczy element z listy.|
|[Lista CAtl::Usuńgłowy](#removehead)|Wywołanie tej metody, aby usunąć element na czele listy.|
|[Lista CAtlList::RemoveHeadNoReturn](#removeheadnoreturn)|Wywołanie tej metody, aby usunąć element na czele listy bez zwracania wartości.|
|[Lista CAtl::Usuńtail](#removetail)|Wywołanie tej metody, aby usunąć element w ogonie listy.|
|[Lista CAtlList::RemoveTailNoReturn](#removetailnoreturn)|Wywołanie tej metody, aby usunąć element w ogonie listy bez zwracania wartości.|
|[Lista CAtl::SetAt](#setat)|Wywołanie tej metody, aby ustawić wartość elementu w danej pozycji na liście.|
|[Lista CAtlList::SwapElements](#swapelements)|Wywołanie tej metody, aby zamienić elementy na liście.|

## <a name="remarks"></a>Uwagi

Klasa `CAtlList` obsługuje uporządkowane listy obiektów nieunikalnych dostępnych sekwencyjnie lub według wartości. `CAtlList`listy zachowują się jak listy podwójnie połączone. Każda lista ma głowę i ogon, a nowe elementy (lub listy w niektórych przypadkach) można dodać do końca listy lub wstawić przed lub po określonych elementach.

Większość `CAtlList` metod korzysta z wartości pozycji. Ta wartość jest używana przez metody do odwoływania się do rzeczywistej lokalizacji pamięci, w której elementy są przechowywane i nie powinny być obliczane ani przewidywane bezpośrednio. Jeśli jest to konieczne, aby uzyskać dostęp do *n*th element na liście, metoda [CAtlList::FindIndex](#findindex) zwróci odpowiednią wartość pozycji dla danego indeksu. Metody [CAtlList::GetNext](#getnext) i [CAtlList::GetPrev](#getprev) może służyć do iteracji za pośrednictwem obiektów na liście.

Aby uzyskać więcej informacji na temat klas kolekcji dostępnych w atl, zobacz [ATL Collection Classes](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="catllistaddhead"></a><a name="addhead"></a>Lista CAtl::Głowica dodania

Wywołanie tej metody, aby dodać element do głowy listy.

```
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*Element*<br/>
Nowy element.

### <a name="return-value"></a>Wartość zwracana

Zwraca położenie nowo dodanego elementu.

### <a name="remarks"></a>Uwagi

Jeśli używana jest pierwsza wersja, pusty element jest tworzony przy użyciu jego domyślnego konstruktora, a nie jego konstruktora kopii.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#13](../../atl/codesnippet/cpp/catllist-class_1.cpp)]

## <a name="catllistaddheadlist"></a><a name="addheadlist"></a>Lista CAtlList::Dodaj listę nagłówków

Wywołanie tej metody, aby dodać istniejącą listę do szefa listy.

```cpp
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Parametry

*plNowy*<br/>
Lista, która ma zostać dodana.

### <a name="remarks"></a>Uwagi

Lista wskazana przez *plNew* jest wstawiana na początku istniejącej listy. W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli *plNew* jest równa NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#14](../../atl/codesnippet/cpp/catllist-class_2.cpp)]

## <a name="catllistaddtail"></a><a name="addtail"></a>Lista CAtl::Dodajtail

Wywołanie tej metody, aby dodać element do ogona tej listy.

```
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*Element*<br/>
Element do dodania.

### <a name="return-value"></a>Wartość zwracana

Zwraca położenie nowo dodanego elementu.

### <a name="remarks"></a>Uwagi

Jeśli używana jest pierwsza wersja, pusty element jest tworzony przy użyciu jego domyślnego konstruktora, a nie jego konstruktora kopii. Element jest dodawany na końcu listy, a więc teraz staje się ogonem. Ta metoda może być używana z pustą listą.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#15](../../atl/codesnippet/cpp/catllist-class_3.cpp)]

## <a name="catllistaddtaillist"></a><a name="addtaillist"></a>Lista CAtlList::DodajtailList

Wywołanie tej metody, aby dodać istniejącą listę do ogona tej listy.

```cpp
void AddTailList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Parametry

*plNowy*<br/>
Lista, która ma zostać dodana.

### <a name="remarks"></a>Uwagi

Lista wskazywany przez *plNew* jest wstawiana po ostatnim elemencie (jeśli istnieje) w obiekcie listy. Ostatnim elementem na *plNowy* lista staje się zatem ogon. W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli *plNew* jest równa NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#16](../../atl/codesnippet/cpp/catllist-class_4.cpp)]

## <a name="catllistassertvalid"></a><a name="assertvalid"></a>Lista CAtl::AssertValid

Wywołanie tej metody, aby potwierdzić, że lista jest prawidłowa.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli obiekt listy jest nieprawidłowy. Aby była prawidłowa, pusta lista musi mieć zarówno głowę, jak i ogon wskazujący wartość NULL, a lista, która nie jest pusta, musi mieć zarówno głowę, jak i ogon wskazujący prawidłowe adresy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#17](../../atl/codesnippet/cpp/catllist-class_5.cpp)]

## <a name="catllistcatllist"></a><a name="catllist"></a>Lista CAtlList::CAtlList

Konstruktor.

```
CAtlList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize (Rozmiar)*<br/>
Rozmiar bloku.

### <a name="remarks"></a>Uwagi

Konstruktor `CAtlList` dla obiektu. Rozmiar bloku jest miarą ilości pamięci przydzielonej, gdy wymagany jest nowy element. Większe rozmiary bloków zmniejszają liczbę wywołań procedur alokacji pamięci, ale zużywają więcej zasobów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#18](../../atl/codesnippet/cpp/catllist-class_6.cpp)]

## <a name="catllistcatllist"></a><a name="dtor"></a>Lista CAtlList::~CAtlList

Destruktor.

```
~CAtlList() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby, w tym wywołanie [CAtlList::RemoveAll,](#removeall) aby usunąć wszystkie elementy z listy.

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli lista nadal `RemoveAll`zawiera pewne elementy po wywołaniu .

## <a name="catllistfind"></a><a name="find"></a>Lista CAtl::Znajdź

Wywołanie tej metody, aby wyszukać listę dla określonego elementu.

```
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```

### <a name="parameters"></a>Parametry

*Element*<br/>
Element, który należy znaleźć na liście.

*posStartPo*<br/>
Pozycja początkowa wyszukiwania. Jeśli nie określono żadnej wartości, wyszukiwanie rozpoczyna się od elementu head.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość POSITION elementu, jeśli zostanie znaleziony, w przeciwnym razie zwraca wartość NULL.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli obiekt listy jest nieprawidłowy lub jeśli wartość *posStartAfter* jest poza zakresem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#19](../../atl/codesnippet/cpp/catllist-class_7.cpp)]

## <a name="catllistfindindex"></a><a name="findindex"></a>Lista CAtlList::FindIndex

Wywołanie tej metody, aby uzyskać położenie elementu, biorąc pod uwagę wartość indeksu.

```
POSITION FindIndex(size_t iElement) const throw();
```

### <a name="parameters"></a>Parametry

*Ielement*<br/>
Indeks od zera elementu listy wymaganej.

### <a name="return-value"></a>Wartość zwracana

Zwraca odpowiednią wartość POSITION lub WARTOŚĆ NULL, jeśli *funkcja iElement* jest poza zakresem.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca position odpowiadające danej wartości indeksu, umożliwiając dostęp do *n*th element na liście.

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli obiekt listy jest nieprawidłowy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#20](../../atl/codesnippet/cpp/catllist-class_8.cpp)]

## <a name="catllistgetat"></a><a name="getat"></a>Lista CAtl::GetAt

Wywołanie tej metody, aby zwrócić element w określonej pozycji na liście.

```
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Wartość POSITION określająca określony element.

### <a name="return-value"></a>Wartość zwracana

Odwołanie lub kopia elementu.

### <a name="remarks"></a>Uwagi

Jeśli lista jest **const**, `GetAt` zwraca kopię elementu. Dzięki temu metoda ma być używana tylko po prawej stronie instrukcji przypisania i chroni listę przed modyfikacją.

Jeśli lista nie jest `GetAt` **const**, zwraca odwołanie do elementu. Dzięki temu metoda ma być używana po obu stronach instrukcji przypisania, a tym samym umożliwia modyfikowanie wpisów listy.

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli *pos* jest równa NULL.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlList::FindIndex](#findindex).

## <a name="catllistgetcount"></a><a name="getcount"></a>Lista CAtlList::GetCount

Wywołanie tej metody, aby zwrócić liczbę obiektów na liście.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę elementów na liście.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlList::Find](#find).

## <a name="catllistgethead"></a><a name="gethead"></a>Lista CAtl::GetHead

Wywołanie tej metody, aby zwrócić element na czele listy.

```
E& GetHead() throw();
const E& GetHead() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do elementu na czele listy lub jego kopię.

### <a name="remarks"></a>Uwagi

Jeśli lista jest **const**, `GetHead` zwraca kopię elementu na czele listy. Dzięki temu metoda ma być używana tylko po prawej stronie instrukcji przypisania i chroni listę przed modyfikacją.

Jeśli lista nie jest `GetHead` **const**, zwraca odwołanie do elementu na czele listy. Dzięki temu metoda ma być używana po obu stronach instrukcji przypisania, a tym samym umożliwia modyfikowanie wpisów listy.

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli szef listy wskazuje wartość NULL.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlList::AddHead](#addhead).

## <a name="catllistgetheadposition"></a><a name="getheadposition"></a>Lista CAtl::GetHeadPosition

Wywołanie tej metody, aby uzyskać pozycję szefa listy.

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość POSITION odpowiadającą elementowi na czele listy.

### <a name="remarks"></a>Uwagi

Jeśli lista jest pusta, zwracaną wartością jest NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#21](../../atl/codesnippet/cpp/catllist-class_9.cpp)]

## <a name="catllistgetnext"></a><a name="getnext"></a>Lista CAtl::GetNext

Wywołanie tej metody, aby zwrócić następny element z listy.

```
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Wartość POSITION, zwrócona przez `GetNext`poprzednie wywołanie do , [CAtlList::GetHeadPosition](#getheadposition), lub innej `CAtlList` metody.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest **const**, `GetNext` zwraca kopię następnego elementu listy. Dzięki temu metoda ma być używana tylko po prawej stronie instrukcji przypisania i chroni listę przed modyfikacją.

Jeśli lista nie jest `GetNext` **const**, zwraca odwołanie do następnego elementu listy. Dzięki temu metoda ma być używana po obu stronach instrukcji przypisania, a tym samym umożliwia modyfikowanie wpisów listy.

### <a name="remarks"></a>Uwagi

Licznik POSITION, *poz*, jest aktualizowany w celu wskazanie następnego elementu na liście lub NULL, jeśli nie ma więcej elementów. W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli *pos* jest równa NULL.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlList::GetHeadPosition](#getheadposition).

## <a name="catllistgetprev"></a><a name="getprev"></a>Lista CAtlList::GetPrev

Wywołanie tej metody, aby zwrócić poprzedni element z listy.

```
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Wartość POSITION, zwrócona przez `GetPrev`poprzednie wywołanie do , [CAtlList::GetTailPosition](#gettailposition), lub innej `CAtlList` metody.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest **const**, `GetPrev` zwraca kopię elementu listy. Dzięki temu metoda ma być używana tylko po prawej stronie instrukcji przypisania i chroni listę przed modyfikacją.

Jeśli lista nie jest `GetPrev` **const**, zwraca odwołanie do elementu listy. Dzięki temu metoda ma być używana po obu stronach instrukcji przypisania, a tym samym umożliwia modyfikowanie wpisów listy.

### <a name="remarks"></a>Uwagi

Licznik POSITION, *poz*, jest aktualizowany w celu wskazanie poprzedniego elementu na liście lub NULL, jeśli nie ma więcej elementów. W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli *pos* jest równa NULL.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlList::GetTailPosition](#gettailposition).

## <a name="catllistgettail"></a><a name="gettail"></a>Lista CAtl::GetTail

Wywołanie tej metody, aby zwrócić element w ogonie listy.

```
E& GetTail() throw();
const E& GetTail() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do elementu lub kopię elementu na ogonie listy.

### <a name="remarks"></a>Uwagi

Jeśli lista jest **const**, `GetTail` zwraca kopię elementu na czele listy. Dzięki temu metoda ma być używana tylko po prawej stronie instrukcji przypisania i chroni listę przed modyfikacją.

Jeśli lista nie jest `GetTail` **const**, zwraca odwołanie do elementu na czele listy. Dzięki temu metoda ma być używana po obu stronach instrukcji przypisania, a tym samym umożliwia modyfikowanie wpisów listy.

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli ogon listy wskazuje wartość NULL.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlList::AddTail](#addtail).

## <a name="catllistgettailposition"></a><a name="gettailposition"></a>Lista CAtl::GetTailPosition

Wywołanie tej metody, aby uzyskać położenie ogona listy.

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość POSITION odpowiadającą elementowi w ogonie listy.

### <a name="remarks"></a>Uwagi

Jeśli lista jest pusta, zwracaną wartością jest NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#22](../../atl/codesnippet/cpp/catllist-class_10.cpp)]

## <a name="catllistinargtype"></a><a name="inargtype"></a>Lista CAtl::INARGTYPE

Typ używany, gdy element jest przekazywany jako argument wejściowy.

```
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catllistinsertafter"></a><a name="insertafter"></a>Lista CAtl::WstawianiePo

Wywołanie tej metody, aby wstawić nowy element do listy po określonej pozycji.

```
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Wartość POSITION, po której zostanie wstawiony nowy element.

*Element*<br/>
Element, który ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość POSITION nowego elementu.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli lista nie jest prawidłowa, jeśli wstawianie nie powiedzie się lub jeśli zostanie podjęta próba wstawienia elementu po ogonie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#23](../../atl/codesnippet/cpp/catllist-class_11.cpp)]

## <a name="catllistinsertbefore"></a><a name="insertbefore"></a>Lista CAtlList::InsertBefore

Wywołanie tej metody, aby wstawić nowy element do listy przed określonym pozycją.

```
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Nowy element zostanie wstawiony do listy przed tą wartością POSITION.

*Element*<br/>
Element, który ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość POSITION nowego elementu.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli lista nie jest prawidłowa, jeśli wstawianie nie powiedzie się lub jeśli zostanie podjęta próba wstawienia elementu przed głową.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#24](../../atl/codesnippet/cpp/catllist-class_12.cpp)]

## <a name="catllistisempty"></a><a name="isempty"></a>Lista CAtlList::IsEmpty

Wywołanie tej metody, aby ustalić, czy lista jest pusta.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli lista nie zawiera żadnych obiektów, w przeciwnym razie false.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#25](../../atl/codesnippet/cpp/catllist-class_13.cpp)]

## <a name="catllistmovetohead"></a><a name="movetohead"></a>Lista CAtlList::MoveToHead

Wywołanie tej metody, aby przenieść określony element do głowy listy.

```cpp
void MoveToHead(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Wartość POSITION elementu do przesunienia.

### <a name="remarks"></a>Uwagi

Określony element jest przenoszony z bieżącej pozycji do głowy listy. W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli *pos* jest równa NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#26](../../atl/codesnippet/cpp/catllist-class_14.cpp)]

## <a name="catllistmovetotail"></a><a name="movetotail"></a>Lista CAtlList::MoveToTail

Wywołanie tej metody, aby przenieść określony element do ogona listy.

```cpp
void MoveToTail(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Wartość POSITION elementu do przesunienia.

### <a name="remarks"></a>Uwagi

Określony element jest przenoszony z jego bieżącej pozycji do ogona listy. W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli *pos* jest równa NULL.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlList::MoveToHead](#movetohead).

## <a name="catllistremoveall"></a><a name="removeall"></a>Lista CAtl::Usuńwszywszystki

Wywołanie tej metody, aby usunąć wszystkie elementy z listy.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Uwagi

Ta metoda usuwa wszystkie elementy z listy i zwalnia przydzielonej pamięci. W kompilacjach debugowania atlassert zostanie podniesiona, jeśli wszystkie elementy nie są usuwane lub jeśli struktura listy została uszkodzona.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlList::IsEmpty](#isempty).

## <a name="catllistremoveat"></a><a name="removeat"></a>Lista CAtl::Usuń

Wywołanie tej metody, aby usunąć pojedynczy element z listy.

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Wartość POSITION elementu do usunięcia.

### <a name="remarks"></a>Uwagi

Element, do którego odwołuje *się poz,* zostanie usunięty, a pamięć zostanie zwolniona. Dopuszczalne jest `RemoveAt` użycie usunięcia głowy lub ogona listy.

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli lista jest nieprawidłowa lub jeśli usunięcie elementu powoduje, że lista ma dostęp do pamięci, która nie jest częścią struktury listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#27](../../atl/codesnippet/cpp/catllist-class_15.cpp)]

## <a name="catllistremovehead"></a><a name="removehead"></a>Lista CAtl::Usuńgłowy

Wywołanie tej metody, aby usunąć element na czele listy.

```
E RemoveHead();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca element na czele listy.

### <a name="remarks"></a>Uwagi

Element head zostanie usunięty z listy, a pamięć zostanie zwolniona. Zwracana jest kopia elementu. W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli lista jest pusta.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#28](../../atl/codesnippet/cpp/catllist-class_16.cpp)]

## <a name="catllistremoveheadnoreturn"></a><a name="removeheadnoreturn"></a>Lista CAtlList::RemoveHeadNoReturn

Wywołanie tej metody, aby usunąć element na czele listy bez zwracania wartości.

```cpp
void RemoveHeadNoReturn() throw();
```

### <a name="remarks"></a>Uwagi

Element head zostanie usunięty z listy, a pamięć zostanie zwolniona. W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli lista jest pusta.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlList::IsEmpty](#isempty).

## <a name="catllistremovetail"></a><a name="removetail"></a>Lista CAtl::Usuńtail

Wywołanie tej metody, aby usunąć element w ogonie listy.

```
E RemoveTail();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca element na ogonie listy.

### <a name="remarks"></a>Uwagi

Element ogona jest usuwany z listy, a pamięć jest zwalniana. Zwracana jest kopia elementu. W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli lista jest pusta.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#29](../../atl/codesnippet/cpp/catllist-class_17.cpp)]

## <a name="catllistremovetailnoreturn"></a><a name="removetailnoreturn"></a>Lista CAtlList::RemoveTailNoReturn

Wywołanie tej metody, aby usunąć element w ogonie listy bez zwracania wartości.

```cpp
void RemoveTailNoReturn() throw();
```

### <a name="remarks"></a>Uwagi

Element ogona jest usuwany z listy, a pamięć jest zwalniana. W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli lista jest pusta.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlList::IsEmpty](#isempty).

## <a name="catllistsetat"></a><a name="setat"></a>Lista CAtl::SetAt

Wywołanie tej metody, aby ustawić wartość elementu w danej pozycji na liście.

```cpp
void SetAt(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Wartość POSITION odpowiadająca elementowi do zmiany.

*Element*<br/>
Wartość nowego elementu.

### <a name="remarks"></a>Uwagi

Zastępuje istniejącą wartość *elementem*. W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli *pos* jest równa NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#30](../../atl/codesnippet/cpp/catllist-class_18.cpp)]

## <a name="catllistswapelements"></a><a name="swapelements"></a>Lista CAtlList::SwapElements

Wywołanie tej metody, aby zamienić elementy na liście.

```cpp
void SwapElements(POSITION pos1, POSITION pos2) throw();
```

### <a name="parameters"></a>Parametry

*poz1*<br/>
Pierwsza wartość POSITION.

*pos2*<br/>
Druga wartość POSITION.

### <a name="remarks"></a>Uwagi

Zamienia elementy w dwóch określonych pozycjach. W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli wartość położenia jest równa null.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#31](../../atl/codesnippet/cpp/catllist-class_19.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CList](../../mfc/reference/clist-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
