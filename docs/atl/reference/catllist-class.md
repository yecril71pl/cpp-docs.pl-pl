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
ms.openlocfilehash: faed99197eb14da8ea095bef81d0d1a9845b18ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62247017"
---
# <a name="catllist-class"></a>Klasa CAtlList

Ta klasa dostarcza metody do tworzenia i zarządzania obiekt listy.

## <a name="syntax"></a>Składnia

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlList
```

#### <a name="parameters"></a>Parametry

*E*<br/>
Typ elementu.

*ETraits*<br/>
Kod używany do kopiowania lub przenoszenia elementów. Zobacz [klasa CElementTraits](../../atl/reference/celementtraits-class.md) Aby uzyskać więcej informacji.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CAtlList::INARGTYPE](#inargtype)||

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlList::CAtlList](#catllist)|Konstruktor.|
|[CAtlList::~CAtlList](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlList::AddHead](#addhead)|Wywołaj tę metodę, aby dodać element do głowy listy.|
|[CAtlList::AddHeadList](#addheadlist)|Wywołaj tę metodę, aby dodać istniejącą listę do głowy listy.|
|[CAtlList::AddTail](#addtail)|Wywołaj tę metodę w celu dodania elementu do tail tej listy.|
|[CAtlList::AddTailList](#addtaillist)|Wywołaj tę metodę, aby dodać istniejącą listę na końcu tej listy.|
|[CAtlList::AssertValid](#assertvalid)|Wywołaj tę metodę, aby potwierdzić, że lista jest nieprawidłowy.|
|[CAtlList::Find](#find)|Wywołaj tę metodę do listy dla określonego elementu wyszukiwania.|
|[CAtlList::FindIndex](#findindex)|Wywołaj tę metodę w celu uzyskania położenie elementu, biorąc pod uwagę wartości indeksu.|
|[CAtlList::GetAt](#getat)|Wywołaj tę metodę w celu zwrócenia elementu na określonej pozycji na liście.|
|[CAtlList::GetCount](#getcount)|Wywołaj tę metodę, aby zwrócić liczbę obiektów na liście.|
|[CAtlList::GetHead](#gethead)|Wywołaj tę metodę w celu zwrócenia elementu na czele listy.|
|[CAtlList::GetHeadPosition](#getheadposition)|Wywołaj tę metodę w celu uzyskania pozycja nagłówek listy.|
|[CAtlList::GetNext](#getnext)|Wywołaj tę metodę w celu zwrócenia następnego elementu z listy.|
|[CAtlList::GetPrev](#getprev)|Wywołaj tę metodę w celu zwrócenia poprzedni element z listy.|
|[CAtlList::GetTail](#gettail)|Wywołaj tę metodę w celu zwrócenia elementu na końcu listy.|
|[CAtlList::GetTailPosition](#gettailposition)|Wywołaj tę metodę w celu uzyskania pozycja tail listy.|
|[CAtlList::InsertAfter](#insertafter)|Wywołaj tę metodę, aby wstawić nowy element do listy od określonej pozycji.|
|[CAtlList::InsertBefore](#insertbefore)|Wywołaj tę metodę, aby wstawić nowy element do listy przed określonej pozycji.|
|[CAtlList::IsEmpty](#isempty)|Wywołaj tę metodę, aby określić, jeśli lista jest pusta.|
|[CAtlList::MoveToHead](#movetohead)|Wywołaj tę metodę, aby przenieść określony element główny listy.|
|[CAtlList::MoveToTail](#movetotail)|Wywołaj tę metodę, aby przenieść określony element do tail listy.|
|[CAtlList::RemoveAll](#removeall)|Wywołaj tę metodę, aby usunąć wszystkie elementy z listy.|
|[CAtlList::RemoveAt](#removeat)|Wywołaj tę metodę, aby usunąć pojedynczy element z listy.|
|[CAtlList::RemoveHead](#removehead)|Wywołaj tę metodę, aby usunąć element na czele listy.|
|[CAtlList::RemoveHeadNoReturn](#removeheadnoreturn)|Wywołaj tę metodę, aby usunąć element na czele listy bez zwracania wartości.|
|[CAtlList::RemoveTail](#removetail)|Wywołaj tę metodę, aby usunąć element na końcu listy.|
|[CAtlList::RemoveTailNoReturn](#removetailnoreturn)|Wywołaj tę metodę, aby usunąć element na końcu listy bez zwracania wartości.|
|[CAtlList::SetAt](#setat)|Wywołaj tę metodę, aby ustawić wartość elementu na określonej pozycji na liście.|
|[CAtlList::SwapElements](#swapelements)|Wywołaj tę metodę w celu wymiany elementów na liście.|

## <a name="remarks"></a>Uwagi

`CAtlList` Klasy obsługuje uporządkowane listy obiektów nieunikatowych dostępnych sekwencyjnie lub według wartości. `CAtlList` Wyświetla zachowują się jak podwójnie połączonej listy. Każda lista zawiera head i ogon i nowych elementów (lub listy w niektórych przypadkach) można dodać do dowolnego końca listy lub wstawiany przed lub po określonych elementów.

Większość `CAtlList` metody użycie wartości pozycji. Ta wartość jest używana przez metody można odwoływać się do rzeczywistej lokalizacji pamięci której elementy są przechowywane i nie obliczenia lub przewidzieć bezpośrednio. Jeśli to konieczne, aby uzyskać dostęp do *n*th element na liście Metoda [CAtlList::FindIndex](#findindex) zwróci odpowiadająca wartość w pozycji dla podanego indeksu. Metody [CAtlList::GetNext](#getnext) i [CAtlList::GetPrev](#getprev) może służyć do iterowania po obiektów na liście.

Aby uzyskać więcej informacji na temat klasy kolekcji ATL — udostępniono zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

##  <a name="addhead"></a>  CAtlList::AddHead

Wywołaj tę metodę, aby dodać element do głowy listy.

```
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*element*<br/>
Nowy element.

### <a name="return-value"></a>Wartość zwracana

Zwraca pozycję nowo dodanego elementu.

### <a name="remarks"></a>Uwagi

Jeśli pierwsza wersja jest używana, pustego elementu jest tworzony przy użyciu jego Konstruktor domyślny, a nie jego Konstruktor kopiujący.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#13](../../atl/codesnippet/cpp/catllist-class_1.cpp)]

##  <a name="addheadlist"></a>  CAtlList::AddHeadList

Wywołaj tę metodę, aby dodać istniejącą listę do głowy listy.

```
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Parametry

*plNew*<br/>
Lista, która ma zostać dodana.

### <a name="remarks"></a>Uwagi

Lista wskazywany przez *plNew* dodaje się na początku listy. W kompilacjach do debugowania błędu potwierdzenia wystąpi *plNew* jest równa NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#14](../../atl/codesnippet/cpp/catllist-class_2.cpp)]

##  <a name="addtail"></a>  CAtlList::AddTail

Wywołaj tę metodę w celu dodania elementu do tail tej listy.

```
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*element*<br/>
Element do dodania.

### <a name="return-value"></a>Wartość zwracana

Zwraca pozycję nowo dodanego elementu.

### <a name="remarks"></a>Uwagi

Jeśli pierwsza wersja jest używana, pustego elementu jest tworzony przy użyciu jego Konstruktor domyślny, a nie jego Konstruktor kopiujący. Element zostanie dodany na końcu listy, a więc teraz staje się ogon. Ta metoda może być używana z pustą listą.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#15](../../atl/codesnippet/cpp/catllist-class_3.cpp)]

##  <a name="addtaillist"></a>  CAtlList::AddTailList

Wywołaj tę metodę, aby dodać istniejącą listę na końcu tej listy.

```
void AddTailList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Parametry

*plNew*<br/>
Lista, która ma zostać dodana.

### <a name="remarks"></a>Uwagi

Lista wskazywany przez *plNew* jest wstawiany za ostatnim elementem (jeśli istnieją) w obiekcie listy. Po ostatnim elemencie w *plNew* lista staje się zatem ogon. W kompilacjach do debugowania błędu potwierdzenia wystąpi *plNew* jest równa NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#16](../../atl/codesnippet/cpp/catllist-class_4.cpp)]

##  <a name="assertvalid"></a>  CAtlList::AssertValid

Wywołaj tę metodę, aby potwierdzić, że lista jest nieprawidłowy.

```
void AssertValid() const;
```

### <a name="remarks"></a>Uwagi

W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli obiekt listy jest nieprawidłowy. Była poprawna, musi mieć pustą listę, head i zakończeniem wskazują na wartość NULL i musi mieć listę, która nie jest pusta, head i zakończeniem wskazujący prawidłowych adresów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#17](../../atl/codesnippet/cpp/catllist-class_5.cpp)]

##  <a name="catllist"></a>  CAtlList::CAtlList

Konstruktor.

```
CAtlList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Rozmiar bloku.

### <a name="remarks"></a>Uwagi

Konstruktor `CAtlList` obiektu. Rozmiar bloku jest miarą ilość pamięci przydzielonej, gdy nowy element jest wymagany. Większe rozmiary bloków zmniejszają liczbę interwencji do procedur alokacji pamięci, ale używa więcej zasobów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#18](../../atl/codesnippet/cpp/catllist-class_6.cpp)]

##  <a name="dtor"></a>  CAtlList::~CAtlList

Destruktor.

```
~CAtlList() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby, w tym wywołaniu [CAtlList::RemoveAll](#removeall) Aby usunąć wszystkie elementy z listy.

W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli lista zawiera niektóre elementy nadal po wywołaniu `RemoveAll`.

##  <a name="find"></a>  CAtlList::Find

Wywołaj tę metodę do listy dla określonego elementu wyszukiwania.

```
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```

### <a name="parameters"></a>Parametry

*element*<br/>
Element, który ma zostać odnaleziona na liście.

*posStartAfter*<br/>
Pozycja początkowa wyszukiwania. Jeśli nie określono wartości, wyszukiwanie rozpoczyna się od elementu głównego.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość pozycji elementu, jeśli znaleziono, w przeciwnym razie zwraca wartość NULL.

### <a name="remarks"></a>Uwagi

W kompilacjach do debugowania Błąd potwierdzenia wystąpi, jeśli obiekt listy jest nieprawidłowy lub *posStartAfter* wartość jest poza zakresem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#19](../../atl/codesnippet/cpp/catllist-class_7.cpp)]

##  <a name="findindex"></a>  CAtlList::FindIndex

Wywołaj tę metodę w celu uzyskania położenie elementu, biorąc pod uwagę wartości indeksu.

```
POSITION FindIndex(size_t iElement) const throw();
```

### <a name="parameters"></a>Parametry

*iElement*<br/>
Liczony od zera indeks elementu do listy wymaganych elementów.

### <a name="return-value"></a>Wartość zwracana

Zwraca odpowiedni pozycji wartość lub wartość NULL, jeśli *iElement* znajduje się poza zakresem.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość pozycji podana wartość indeksu, zezwalając na dostęp do *n*th elementu na liście.

W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli obiekt listy jest nieprawidłowy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#20](../../atl/codesnippet/cpp/catllist-class_8.cpp)]

##  <a name="getat"></a>  CAtlList::GetAt

Wywołaj tę metodę w celu zwrócenia elementu na określonej pozycji na liście.

```
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Wartość pozycji określenie konkretnego elementu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do lub kopię elementu.

### <a name="remarks"></a>Uwagi

Jeśli lista jest **const**, `GetAt` zwraca kopię tego elementu. Dzięki temu metody, które ma być używana tylko po prawej stronie instrukcji przypisania, a chroni listy przed modyfikacją.

Jeśli lista nie jest **const**, `GetAt` zwraca odwołanie do elementu. Dzięki temu metody, które ma być używana po obu stronach instrukcji przypisania, a ten sposób umożliwia pozycji listy do zmodyfikowania.

W kompilacjach do debugowania błędu potwierdzenia wystąpi *pos* jest równa NULL.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlList::FindIndex](#findindex).

##  <a name="getcount"></a>  CAtlList::GetCount

Wywołaj tę metodę, aby zwrócić liczbę obiektów na liście.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę elementów na liście.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlList::Find](#find).

##  <a name="gethead"></a>  CAtlList::GetHead

Wywołaj tę metodę w celu zwrócenia elementu na czele listy.

```
E& GetHead() throw();
const E& GetHead() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do lub kopię tego elementu na czele listy.

### <a name="remarks"></a>Uwagi

Jeśli lista jest **const**, `GetHead` zwraca kopię elementu na czele listy. Dzięki temu metody, które ma być używana tylko po prawej stronie instrukcji przypisania, a chroni listy przed modyfikacją.

Jeśli lista nie jest **const**, `GetHead` zwraca odwołanie do elementu na czele listy. Dzięki temu metody, które ma być używana po obu stronach instrukcji przypisania, a ten sposób umożliwia pozycji listy do zmodyfikowania.

W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli nagłówek listy wskazuje na wartość NULL.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlList::AddHead](#addhead).

##  <a name="getheadposition"></a>  CAtlList::GetHeadPosition

Wywołaj tę metodę w celu uzyskania pozycja nagłówek listy.

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość pozycji odpowiadający element na czele listy.

### <a name="remarks"></a>Uwagi

Jeśli lista jest pusta, wartość zwracana jest wartość NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#21](../../atl/codesnippet/cpp/catllist-class_9.cpp)]

##  <a name="getnext"></a>  CAtlList::GetNext

Wywołaj tę metodę w celu zwrócenia następnego elementu z listy.

```
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Wartość pozycji zwrócony przez poprzednie wywołanie `GetNext`, [CAtlList::GetHeadPosition](#getheadposition), lub inne `CAtlList` metody.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest **const**, `GetNext` zwraca kopię obiektu następnego elementu listy. Dzięki temu metody, które ma być używana tylko po prawej stronie instrukcji przypisania, a chroni listy przed modyfikacją.

Jeśli lista nie jest **const**, `GetNext` zwraca odwołanie do następnego elementu listy. Dzięki temu metody, które ma być używana po obu stronach instrukcji przypisania, a ten sposób umożliwia pozycji listy do zmodyfikowania.

### <a name="remarks"></a>Uwagi

Licznik pozycji *pos*, zostanie zaktualizowany w celu punktu do następnego elementu na liście, lub wartość NULL, jeśli nie ma elementów więcej. W kompilacjach do debugowania błędu potwierdzenia wystąpi *pos* jest równa NULL.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlList::GetHeadPosition](#getheadposition).

##  <a name="getprev"></a>  CAtlList::GetPrev

Wywołaj tę metodę w celu zwrócenia poprzedni element z listy.

```
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Wartość pozycji zwrócony przez poprzednie wywołanie `GetPrev`, [CAtlList::GetTailPosition](#gettailposition), lub inne `CAtlList` metody.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest **const**, `GetPrev` zwraca kopię elementu listy. Dzięki temu metody, które ma być używana tylko po prawej stronie instrukcji przypisania, a chroni listy przed modyfikacją.

Jeśli lista nie jest **const**, `GetPrev` zwraca odwołanie do elementu listy. Dzięki temu metody, które ma być używana po obu stronach instrukcji przypisania, a ten sposób umożliwia pozycji listy do zmodyfikowania.

### <a name="remarks"></a>Uwagi

Licznik pozycji *pos*, zostanie zaktualizowany w celu punkt do poprzedniego elementu na liście, lub wartość NULL, jeśli nie ma elementów więcej. W kompilacjach do debugowania błędu potwierdzenia wystąpi *pos* jest równa NULL.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlList::GetTailPosition](#gettailposition).

##  <a name="gettail"></a>  CAtlList::GetTail

Wywołaj tę metodę w celu zwrócenia elementu na końcu listy.

```
E& GetTail() throw();
const E& GetTail() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do lub kopiowanie elementu, na końcu listy.

### <a name="remarks"></a>Uwagi

Jeśli lista jest **const**, `GetTail` zwraca kopię elementu na czele listy. Dzięki temu metody, które ma być używana tylko po prawej stronie instrukcji przypisania, a chroni listy przed modyfikacją.

Jeśli lista nie jest **const**, `GetTail` zwraca odwołanie do elementu na czele listy. Dzięki temu metody, które ma być używana po obu stronach instrukcji przypisania, a ten sposób umożliwia pozycji listy do zmodyfikowania.

W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli wskazuje koniec listy o wartości NULL.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlList::AddTail](#addtail).

##  <a name="gettailposition"></a>  CAtlList::GetTailPosition

Wywołaj tę metodę w celu uzyskania pozycja tail listy.

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość pozycji odpowiadający element na końcu listy.

### <a name="remarks"></a>Uwagi

Jeśli lista jest pusta, wartość zwracana jest wartość NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#22](../../atl/codesnippet/cpp/catllist-class_10.cpp)]

##  <a name="inargtype"></a>  CAtlList::INARGTYPE

Typ używany, gdy element jest przekazywany jako argument wejściowy.

```
typedef ETraits::INARGTYPE INARGTYPE;
```

##  <a name="insertafter"></a>  CAtlList::InsertAfter

Wywołaj tę metodę, aby wstawić nowy element do listy od określonej pozycji.

```
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Wartość pozycji, po upływie którego nowy element zostanie wstawiony.

*element*<br/>
Element, który ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość pozycji nowy element.

### <a name="remarks"></a>Uwagi

W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli lista nie jest prawidłowa, czy insert nie powiedzie się, czy podejmowana jest próba Wstaw element po ogon.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#23](../../atl/codesnippet/cpp/catllist-class_11.cpp)]

##  <a name="insertbefore"></a>  CAtlList::InsertBefore

Wywołaj tę metodę, aby wstawić nowy element do listy przed określonej pozycji.

```
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Nowy element zostanie wstawiony do listy, zanim ta wartość pozycji.

*element*<br/>
Element, który ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość pozycji nowy element.

### <a name="remarks"></a>Uwagi

W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli lista nie jest prawidłowy, czy insert nie powiedzie się, czy podejmowana jest próba Wstaw element przed nagłówek.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#24](../../atl/codesnippet/cpp/catllist-class_12.cpp)]

##  <a name="isempty"></a>  CAtlList::IsEmpty

Wywołaj tę metodę, aby określić, jeśli lista jest pusta.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli lista nie zawiera żadnych obiektów, w przeciwnym razie wartość false.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#25](../../atl/codesnippet/cpp/catllist-class_13.cpp)]

##  <a name="movetohead"></a>  CAtlList::MoveToHead

Wywołaj tę metodę, aby przenieść określony element główny listy.

```
void MoveToHead(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Wartość pozycji elementu, aby przenieść.

### <a name="remarks"></a>Uwagi

Określony element jest przenoszony z jego bieżącej pozycji do głowy listy. W kompilacjach do debugowania błędu potwierdzenia wystąpi *pos* jest równa NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#26](../../atl/codesnippet/cpp/catllist-class_14.cpp)]

##  <a name="movetotail"></a>  CAtlList::MoveToTail

Wywołaj tę metodę, aby przenieść określony element do tail listy.

```
void MoveToTail(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Wartość pozycji elementu, aby przenieść.

### <a name="remarks"></a>Uwagi

Określony element jest przenoszony z jego bieżącej pozycji na koniec listy. W kompilacjach do debugowania błędu potwierdzenia wystąpi *pos* jest równa NULL.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlList::MoveToHead](#movetohead).

##  <a name="removeall"></a>  CAtlList::RemoveAll

Wywołaj tę metodę, aby usunąć wszystkie elementy z listy.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Uwagi

Ta metoda usuwa wszystkie elementy z listy i zwalnia ilość przydzielonej pamięci. W kompilacjach debuguje ATLASSERT zostanie wygenerowany, jeśli nie zostały usunięte wszystkie elementy, lub jeśli struktura listy uległa uszkodzeniu.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlList::IsEmpty](#isempty).

##  <a name="removeat"></a>  CAtlList::RemoveAt

Wywołaj tę metodę, aby usunąć pojedynczy element z listy.

```
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Wartość pozycji elementu do usunięcia.

### <a name="remarks"></a>Uwagi

Element odwołuje się *pos* zostanie usunięty, a pamięć jest zwalniana. Dopuszcza się użycia `RemoveAt` do usunięcia z węzłem głównym lub koniec listy.

W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli lista nie jest prawidłowy lub usunięcia elementu powoduje, że na liście, aby dostęp do pamięci, która nie jest częścią struktury listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#27](../../atl/codesnippet/cpp/catllist-class_15.cpp)]

##  <a name="removehead"></a>  CAtlList::RemoveHead

Wywołaj tę metodę, aby usunąć element na czele listy.

```
E RemoveHead();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca element na czele listy.

### <a name="remarks"></a>Uwagi

Element główny został usunięty z listy, a pamięć jest zwalniana. Zwracana jest kopia elementu. W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli lista jest pusta.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#28](../../atl/codesnippet/cpp/catllist-class_16.cpp)]

##  <a name="removeheadnoreturn"></a>  CAtlList::RemoveHeadNoReturn

Wywołaj tę metodę, aby usunąć element na czele listy bez zwracania wartości.

```
void RemoveHeadNoReturn() throw();
```

### <a name="remarks"></a>Uwagi

Element główny został usunięty z listy, a pamięć jest zwalniana. W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli lista jest pusta.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlList::IsEmpty](#isempty).

##  <a name="removetail"></a>  CAtlList::RemoveTail

Wywołaj tę metodę, aby usunąć element na końcu listy.

```
E RemoveTail();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca element na końcu listy.

### <a name="remarks"></a>Uwagi

Tail element został usunięty z listy, a pamięć jest zwalniana. Zwracana jest kopia elementu. W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli lista jest pusta.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#29](../../atl/codesnippet/cpp/catllist-class_17.cpp)]

##  <a name="removetailnoreturn"></a>  CAtlList::RemoveTailNoReturn

Wywołaj tę metodę, aby usunąć element na końcu listy bez zwracania wartości.

```
void RemoveTailNoReturn() throw();
```

### <a name="remarks"></a>Uwagi

Tail element został usunięty z listy, a pamięć jest zwalniana. W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli lista jest pusta.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlList::IsEmpty](#isempty).

##  <a name="setat"></a>  CAtlList::SetAt

Wywołaj tę metodę, aby ustawić wartość elementu na określonej pozycji na liście.

```
void SetAt(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Odpowiadający element, aby zmienić wartość pozycji.

*element*<br/>
Nowa wartość elementu.

### <a name="remarks"></a>Uwagi

Zastępuje istniejącą wartość z *elementu*. W kompilacjach do debugowania błędu potwierdzenia wystąpi *pos* jest równa NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#30](../../atl/codesnippet/cpp/catllist-class_18.cpp)]

##  <a name="swapelements"></a>  CAtlList::SwapElements

Wywołaj tę metodę w celu wymiany elementów na liście.

```
void SwapElements(POSITION pos1, POSITION pos2) throw();
```

### <a name="parameters"></a>Parametry

*pos1*<br/>
Pierwsza wartość pozycji.

*pos2*<br/>
Druga wartość pozycji.

### <a name="remarks"></a>Uwagi

Zamienia elementy w dwóch miejscach określony. W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli te wartości pozycji jest równa NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#31](../../atl/codesnippet/cpp/catllist-class_19.cpp)]

## <a name="see-also"></a>Zobacz także

[Klasa CList](../../mfc/reference/clist-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
