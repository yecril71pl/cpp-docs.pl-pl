---
title: Klasa CList
ms.date: 11/04/2016
f1_keywords:
- CList
- AFXTEMPL/CList
- AFXTEMPL/CList::CList
- AFXTEMPL/CList::AddHead
- AFXTEMPL/CList::AddTail
- AFXTEMPL/CList::Find
- AFXTEMPL/CList::FindIndex
- AFXTEMPL/CList::GetAt
- AFXTEMPL/CList::GetCount
- AFXTEMPL/CList::GetHead
- AFXTEMPL/CList::GetHeadPosition
- AFXTEMPL/CList::GetNext
- AFXTEMPL/CList::GetPrev
- AFXTEMPL/CList::GetSize
- AFXTEMPL/CList::GetTail
- AFXTEMPL/CList::GetTailPosition
- AFXTEMPL/CList::InsertAfter
- AFXTEMPL/CList::InsertBefore
- AFXTEMPL/CList::IsEmpty
- AFXTEMPL/CList::RemoveAll
- AFXTEMPL/CList::RemoveAt
- AFXTEMPL/CList::RemoveHead
- AFXTEMPL/CList::RemoveTail
- AFXTEMPL/CList::SetAt
helpviewer_keywords:
- CList [MFC], CList
- CList [MFC], AddHead
- CList [MFC], AddTail
- CList [MFC], Find
- CList [MFC], FindIndex
- CList [MFC], GetAt
- CList [MFC], GetCount
- CList [MFC], GetHead
- CList [MFC], GetHeadPosition
- CList [MFC], GetNext
- CList [MFC], GetPrev
- CList [MFC], GetSize
- CList [MFC], GetTail
- CList [MFC], GetTailPosition
- CList [MFC], InsertAfter
- CList [MFC], InsertBefore
- CList [MFC], IsEmpty
- CList [MFC], RemoveAll
- CList [MFC], RemoveAt
- CList [MFC], RemoveHead
- CList [MFC], RemoveTail
- CList [MFC], SetAt
ms.assetid: 6f6273c3-c8f6-47f5-ac2a-0a950379ae5d
ms.openlocfilehash: 7ba85445e3aba1df853d7d3666c92fdabdfa3970
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87182879"
---
# <a name="clist-class"></a>Klasa CList

Obsługuje uporządkowane listy nieunikatowych obiektów dostępnych sekwencyjnie lub według wartości.

## <a name="syntax"></a>Składnia

```
template<class TYPE, class ARG_TYPE = const TYPE&>
class CList : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CList::CList](#clist)|Tworzy pustą listę uporządkowaną.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CList:: addszef](#addhead)|Dodaje element (lub wszystkie elementy z innej listy) do nagłówka listy (tworzy nowy nagłówek).|
|[CList:: AddTail](#addtail)|Dodaje element (lub wszystkie elementy z innej listy) do ogona listy (tworzy nowy ogon).|
|[CList:: find](#find)|Pobiera pozycję elementu określonego przez wartość wskaźnika.|
|[CList:: FindIndex —](#findindex)|Pobiera pozycję elementu określonego przez indeks (liczony od zera).|
|[CList::GetAt](#getat)|Pobiera element w danym położeniu.|
|[CList:: GetCount](#getcount)|Zwraca liczbę elementów na liście.|
|[CList:: getszef](#gethead)|Zwraca element główny listy (nie może być pusty).|
|[CList::GetHeadPosition](#getheadposition)|Zwraca pozycję elementu nagłówkowego listy.|
|[CList:: GetNext](#getnext)|Pobiera następny element do iteracji.|
|[CList:: getpoprz](#getprev)|Pobiera poprzedni element do iteracji.|
|[CList:: GetSize](#getsize)|Zwraca liczbę elementów na liście.|
|[CList:: GetTail](#gettail)|Zwraca element końcowy listy (nie może być pusty).|
|[CList::GetTailPosition](#gettailposition)|Zwraca pozycję elementu ogona listy.|
|[CList::InsertAfter](#insertafter)|Wstawia nowy element po danej pozycji.|
|[CList::InsertBefore](#insertbefore)|Wstawia nowy element przed daną pozycją.|
|[CList:: IsEmpty](#isempty)|Testy dla warunku pustej listy (brak elementów).|
|[CList::](#removeall)|Usuwa wszystkie elementy z tej listy.|
|[CList::RemoveAt](#removeat)|Usuwa element z tej listy, określony według pozycji.|
|[CList::RemoveHead](#removehead)|Usuwa element z nagłówka listy.|
|[CList::RemoveTail](#removetail)|Usuwa element z ogona listy.|
|[CList::SetAt](#setat)|Ustawia element w danym położeniu.|

#### <a name="parameters"></a>Parametry

*TYP*<br/>
Typ obiektu przechowywanego na liście.

*ARG_TYPE*<br/>
Typ używany do odwoływania się do obiektów znajdujących się na liście. Może być odwołaniem.

## <a name="remarks"></a>Uwagi

`CList`listy zachowują się jak listy połączone podwójnie.

Zmienna typu pozycja jest kluczem dla listy. Można użyć zmiennej POSITION jako iteratora w celu przechodzenia listy sekwencyjnie i jako zakładki do przechowania. Pozycja nie jest jednak taka sama jak indeks.

Wstawianie elementów jest bardzo szybkie na początku listy, na końcu i na znanym miejscu. Wyszukiwanie sekwencyjne jest niezbędne do wyszukania elementu według wartości lub indeksu. To wyszukiwanie może być wolne, jeśli lista jest długa.

Jeśli potrzebujesz zrzutu poszczególnych elementów na liście, musisz ustawić głębokość kontekstu zrzutu na 1 lub większą.

Niektóre funkcje członkowskie tej klasy wywołują globalne funkcje pomocnika, które muszą być dostosowane do większości zastosowania `CList` klasy. Zobacz [pomocników klasy kolekcji](../../mfc/reference/collection-class-helpers.md) w sekcji "MACROS and Globals".

Aby uzyskać więcej informacji na temat korzystania z programu `CList` , zobacz [kolekcje](../../mfc/collections.md)artykułów.

## <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtempl. h

## <a name="clistaddhead"></a><a name="addhead"></a>CList:: addszef

Dodaje nowy element lub listę elementów do nagłówka tej listy.

```
POSITION AddHead(ARG_TYPE newElement);
void AddHead(CList* pNewList);
```

### <a name="parameters"></a>Parametry

*ARG_TYPE*<br/>
Parametr szablonu określający typ elementu listy (może to być odwołanie).

*newElement*<br/>
Nowy element.

*pNewList*<br/>
Wskaźnik do innej `CList` listy. Elementy w *pNewList* zostaną dodane do tej listy.

### <a name="return-value"></a>Wartość zwracana

Pierwsza wersja zwraca wartość pozycji nowo wstawionego elementu.

### <a name="remarks"></a>Uwagi

Lista może być pusta przed operacją.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]

## <a name="clistaddtail"></a><a name="addtail"></a>CList:: AddTail

Dodaje nowy element lub listę elementów do ogona tej listy.

```
POSITION AddTail(ARG_TYPE newElement);
void AddTail(CList* pNewList);
```

### <a name="parameters"></a>Parametry

*ARG_TYPE*<br/>
Parametr szablonu określający typ elementu listy (może to być odwołanie).

*newElement*<br/>
Element, który ma zostać dodany do tej listy.

*pNewList*<br/>
Wskaźnik do innej `CList` listy. Elementy w *pNewList* zostaną dodane do tej listy.

### <a name="return-value"></a>Wartość zwracana

Pierwsza wersja zwraca wartość pozycji nowo wstawionego elementu.

### <a name="remarks"></a>Uwagi

Lista może być pusta przed operacją.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]

## <a name="clistclist"></a><a name="clist"></a>CList::CList

Tworzy pustą listę uporządkowaną.

```
CList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Stopień szczegółowości alokacji pamięci na potrzeby rozszerzania listy.

### <a name="remarks"></a>Uwagi

Gdy lista zostanie powiększona, pamięć jest przypisana w jednostkach wpisów *nBlockSize* .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]

## <a name="clistfind"></a><a name="find"></a>CList:: find

Wyszukuje pierwszy element pasujący do określonego *searchValue*.

```
POSITION Find(
    ARG_TYPE searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Parametry

*ARG_TYPE*<br/>
Parametr szablonu określający typ elementu listy (może to być odwołanie).

*searchValue*<br/>
Wartość, która ma zostać znaleziona na liście.

*startAfter*<br/>
Pozycja początkowa dla wyszukiwania. Jeśli wartość nie jest określona, wyszukiwanie rozpoczyna się od elementu głównego.

### <a name="return-value"></a>Wartość zwracana

Wartość pozycji, która może być używana do pobierania iteracji lub wskaźnika obiektu; Wartość NULL, jeśli nie można odnaleźć obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]

## <a name="clistfindindex"></a><a name="findindex"></a>CList:: FindIndex —

Używa wartości *nIndex* jako indeksu do listy.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks (liczony od zera) elementu listy, który ma zostać znaleziony.

### <a name="return-value"></a>Wartość zwracana

Wartość pozycji, która może być używana do pobierania iteracji lub wskaźnika obiektu; Wartość NULL, jeśli *nIndex* jest ujemny lub zbyt duży.

### <a name="remarks"></a>Uwagi

Rozpocznie skanowanie sekwencyjne od szefa listy, zatrzymując na *n*-tym elemencie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#40](../../mfc/codesnippet/cpp/clist-class_6.cpp)]

## <a name="clistgetat"></a><a name="getat"></a>CList::GetAt

Pobiera element listy w danym położeniu.

```
TYPE& GetAt(POSITION position);
const TYPE& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ obiektu na liście.

*umieścić*<br/>
Pozycja na liście elementu do pobrania.

### <a name="return-value"></a>Wartość zwracana

Zobacz opis wartości zwracanej dla `GetHead` .

### <a name="remarks"></a>Uwagi

`GetAt`Zwraca element (lub odwołanie do elementu) skojarzony z daną pozycją. Nie jest taki sam jak indeks i nie można wykonać operacji na wartości pozycji samodzielnie. Zmienna typu pozycja jest kluczem dla listy.

Musisz się upewnić, że wartość pozycji reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowana biblioteka MFC potwierdzenia.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CList:: GetHeadPosition](#getheadposition).

## <a name="clistgetcount"></a><a name="getcount"></a>CList:: GetCount

Pobiera liczbę elementów na tej liście.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość całkowita zawierająca liczbę elementów.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody spowoduje wygenerowanie tego samego wyniku co Metoda [CList:: GetSize](#getsize) .

### <a name="example"></a>Przykład

  Zobacz przykład dla [CList:: RemoveHead](#removehead).

## <a name="clistgethead"></a><a name="gethead"></a>CList:: getszef

Pobiera element główny (lub odwołanie do elementu głównego) tej listy.

```
const TYPE& GetHead() const;

TYPE& GetHead();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ obiektu na liście.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest **`const`** , `GetHead` zwraca kopię elementu na początku listy. Dzięki temu funkcja może być używana tylko po prawej stronie instrukcji przypisania i chroni listę przed modyfikacją.

Jeśli lista nie jest **`const`** , `GetHead` zwraca odwołanie do elementu znajdującego się na końcu listy. Dzięki temu funkcja może być używana po obu stronach instrukcji przypisania i w ten sposób zezwala na modyfikowanie wpisów listy.

### <a name="remarks"></a>Uwagi

Przed wywołaniem należy upewnić się, że lista nie jest pusta `GetHead` . Jeśli lista jest pusta, wówczas wersja do debugowania biblioteka MFC potwierdzenia. Użyj [IsEmpty](#isempty) , aby sprawdzić, czy lista zawiera elementy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]

## <a name="clistgetheadposition"></a><a name="getheadposition"></a>CList::GetHeadPosition

Pobiera pozycję elementu nagłówkowego tej listy.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość pozycji, która może być używana do pobierania iteracji lub wskaźnika obiektu; Wartość NULL, jeśli lista jest pusta.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]

## <a name="clistgetnext"></a><a name="getnext"></a>CList:: GetNext

Pobiera element list identyfikowany przez *elemencie rPosition*, a następnie ustawia *elemencie RPOSITION* na wartość pozycji następnego wpisu na liście.

```
TYPE& GetNext(POSITION& rPosition);
const TYPE& GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów na liście.

*Elemencie rPosition*<br/>
Odwołanie do wartości pozycji zwróconej przez poprzednie `GetNext` , [GetHeadPosition](#getheadposition)lub inne wywołanie funkcji składowej.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest **`const`** , `GetNext` zwraca kopię elementu listy. Dzięki temu funkcja może być używana tylko po prawej stronie instrukcji przypisania i chroni listę przed modyfikacją.

Jeśli lista nie jest **`const`** , `GetNext` zwraca odwołanie do elementu listy. Dzięki temu funkcja może być używana po obu stronach instrukcji przypisania i w ten sposób zezwala na modyfikowanie wpisów listy.

### <a name="remarks"></a>Uwagi

Można użyć `GetNext` w pętli iteracji do przodu, jeśli ustanowi początkową pozycję z wywołaniem `GetHeadPosition` lub `Find` .

Musisz się upewnić, że wartość pozycji reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowana biblioteka MFC potwierdzenia.

Jeśli pobrany element jest ostatni na liście, Nowa wartość jest równa `rPosition` null.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]

## <a name="clistgetprev"></a><a name="getprev"></a>CList:: getpoprz

Pobiera element listy identyfikowany przez `rPosition` , a następnie ustawia `rPosition` wartość pozycji powyższej pozycji na liście.

```
TYPE& GetPrev(POSITION& rPosition);
const TYPE& GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów na liście.

*Elemencie rPosition*<br/>
Odwołanie do wartości pozycji zwróconej przez poprzednie `GetPrev` lub inne wywołanie funkcji składowej.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest **`const`** , `GetPrev` zwraca kopię elementu na początku listy. Dzięki temu funkcja może być używana tylko po prawej stronie instrukcji przypisania i chroni listę przed modyfikacją.

Jeśli lista nie jest **`const`** , `GetPrev` zwraca odwołanie do elementu listy. Dzięki temu funkcja może być używana po obu stronach instrukcji przypisania i w ten sposób zezwala na modyfikowanie wpisów listy.

### <a name="remarks"></a>Uwagi

Można użyć `GetPrev` w pętli wstecznej iteracji, jeśli zostanie nadana początkowa pozycja z wywołaniem `GetTailPosition` lub `Find` .

Musisz się upewnić, że wartość pozycji reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowana biblioteka MFC potwierdzenia.

Jeśli pobrany element jest pierwszy na liście, Nowa wartość *elemencie rPosition* jest ustawiona na wartość null.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#44](../../mfc/codesnippet/cpp/clist-class_10.cpp)]

## <a name="clistgetsize"></a><a name="getsize"></a>CList:: GetSize

Zwraca liczbę elementów listy.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

liczba elementów na liście.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby pobrać liczbę elementów na liście.  Wywołanie tej metody spowoduje wygenerowanie tego samego wyniku co Metoda [CList:: GetCount](#getcount) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]

## <a name="clistgettail"></a><a name="gettail"></a>CList:: GetTail

Pobiera `CObject` wskaźnik reprezentujący element końcowy tej listy.

```
TYPE& GetTail();
const TYPE& GetTail() const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów na liście.

### <a name="return-value"></a>Wartość zwracana

Zobacz opis wartości zwracanej dla elementu [Getnagłówke](../../mfc/reference/coblist-class.md#gethead).

### <a name="remarks"></a>Uwagi

Przed wywołaniem należy upewnić się, że lista nie jest pusta `GetTail` . Jeśli lista jest pusta, wówczas wersja do debugowania biblioteka MFC potwierdzenia. Użyj [IsEmpty](../../mfc/reference/coblist-class.md#isempty) , aby sprawdzić, czy lista zawiera elementy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]

## <a name="clistgettailposition"></a><a name="gettailposition"></a>CList::GetTailPosition

Pobiera pozycję elementu końcowego z tej listy. Wartość NULL, jeśli lista jest pusta.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość pozycji, która może być używana do pobierania iteracji lub wskaźnika obiektu; Wartość NULL, jeśli lista jest pusta.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]

## <a name="clistinsertafter"></a><a name="insertafter"></a>CList::InsertAfter

Dodaje element do tej listy po elemencie na określonej pozycji.

```
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*umieścić*<br/>
Wartość pozycji zwrócona przez poprzednie `GetNext` `GetPrev` `Find` wywołanie funkcji składowej.

*ARG_TYPE*<br/>
Parametr szablonu określający typ elementu listy.

*newElement*<br/>
Element, który ma zostać dodany do tej listy.

### <a name="return-value"></a>Wartość zwracana

Wartość pozycji, która może być używana do pobierania iteracji lub elementu listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]

## <a name="clistinsertbefore"></a><a name="insertbefore"></a>CList::InsertBefore

Dodaje element do tej listy przed elementem w określonej pozycji.

```
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*umieścić*<br/>
Wartość pozycji zwrócona przez poprzednie `GetNext` `GetPrev` `Find` wywołanie funkcji składowej.

*ARG_TYPE*<br/>
Parametr szablonu określający typ elementu listy (może to być odwołanie).

*newElement*<br/>
Element, który ma zostać dodany do tej listy.

### <a name="return-value"></a>Wartość zwracana

Wartość pozycji, która może być używana do pobierania iteracji lub elementu listy.

### <a name="remarks"></a>Uwagi

Jeśli *pozycja* ma wartość null, element zostanie wstawiony na początku listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]

## <a name="clistisempty"></a><a name="isempty"></a>CList:: IsEmpty

Wskazuje, czy ta lista nie zawiera żadnych elementów.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli ta lista jest pusta; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]

## <a name="clistremoveall"></a><a name="removeall"></a>CList::

Usuwa wszystkie elementy z tej listy i zwalnia skojarzoną pamięć.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Uwagi

Nie Wygenerowano żadnego błędu, jeśli lista jest już pusta.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#51](../../mfc/codesnippet/cpp/clist-class_17.cpp)]

## <a name="clistremoveat"></a><a name="removeat"></a>CList::RemoveAt

Usuwa określony element z tej listy.

```cpp
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Parametry

*umieścić*<br/>
Pozycja elementu, który ma zostać usunięty z listy.

### <a name="remarks"></a>Uwagi

Musisz się upewnić, że wartość pozycji reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowana biblioteka MFC potwierdzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]

## <a name="clistremovehead"></a><a name="removehead"></a>CList::RemoveHead

Usuwa element z nagłówka listy i zwraca do niego wskaźnik.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów na liście.

### <a name="return-value"></a>Wartość zwracana

Element wcześniej na początku listy.

### <a name="remarks"></a>Uwagi

Przed wywołaniem należy upewnić się, że lista nie jest pusta `RemoveHead` . Jeśli lista jest pusta, wówczas wersja do debugowania biblioteka MFC potwierdzenia. Użyj [IsEmpty](#isempty) , aby sprawdzić, czy lista zawiera elementy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]

## <a name="clistremovetail"></a><a name="removetail"></a>CList::RemoveTail

Usuwa element z ogona listy i zwraca do niego wskaźnik.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów na liście.

### <a name="return-value"></a>Wartość zwracana

Element, który znajduje się na końcu listy.

### <a name="remarks"></a>Uwagi

Przed wywołaniem należy upewnić się, że lista nie jest pusta `RemoveTail` . Jeśli lista jest pusta, wówczas wersja do debugowania biblioteka MFC potwierdzenia. Użyj [IsEmpty](#isempty) , aby sprawdzić, czy lista zawiera elementy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]

## <a name="clistsetat"></a><a name="setat"></a>CList::SetAt

Zmienna typu pozycja jest kluczem dla listy.

```cpp
void SetAt(POSITION pos, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Pozycja elementu, który ma zostać ustawiony.

*ARG_TYPE*<br/>
Parametr szablonu określający typ elementu listy (może to być odwołanie).

*newElement*<br/>
Element, który ma zostać dodany do listy.

### <a name="remarks"></a>Uwagi

Nie jest taki sam jak indeks i nie można wykonać operacji na wartości pozycji samodzielnie. `SetAt`zapisuje element do określonej pozycji na liście.

Musisz się upewnić, że wartość pozycji reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowana biblioteka MFC potwierdzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]

## <a name="see-also"></a>Zobacz także

[ZBIERANIE próbek MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CMap](../../mfc/reference/cmap-class.md)<br/>
[Klasa CArray](../../mfc/reference/carray-class.md)
