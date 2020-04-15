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
ms.openlocfilehash: 253cf12033af497115ad600e457630ae834cc69c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372243"
---
# <a name="clist-class"></a>Klasa CList

Obsługuje uporządkowane listy obiektów nieunikalnych dostępnych sekwencyjnie lub według wartości.

## <a name="syntax"></a>Składnia

```
template<class TYPE, class ARG_TYPE = const TYPE&>
class CList : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Lista C::CList](#clist)|Konstruuje pustą uporządkowaną listę.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Lista C::Dodajgłowy](#addhead)|Dodaje element (lub wszystkie elementy na innej liście) do głowy listy (tworzy nową głowę).|
|[Lista C::Dodajtail](#addtail)|Dodaje element (lub wszystkie elementy na innej liście) do ogona listy (tworzy nowy ogon).|
|[Lista C::Znajdź](#find)|Pobiera położenie elementu określonego przez wartość wskaźnika.|
|[Lista C::FindIndex](#findindex)|Pobiera położenie elementu określonego przez indeks oparty na wartości zero.|
|[Lista C::GetAt](#getat)|Pobiera element w danej pozycji.|
|[Lista C::GetCount](#getcount)|Zwraca liczbę elementów na tej liście.|
|[Lista C::GetHead](#gethead)|Zwraca element head listy (nie może być pusty).|
|[Lista C::Pozycja GetHead](#getheadposition)|Zwraca położenie elementu head listy.|
|[Lista C::GetNext](#getnext)|Pobiera następny element do iteracji.|
|[Lista C::GetPrev](#getprev)|Pobiera poprzedni element do iteracji.|
|[Lista C::GetSize](#getsize)|Zwraca liczbę elementów na tej liście.|
|[Lista C::GetTail](#gettail)|Zwraca element ogonowy listy (nie może być pusty).|
|[Lista C::GetTailPosition](#gettailposition)|Zwraca położenie elementu ogonowego listy.|
|[Lista C::WstawianiePo](#insertafter)|Wstawia nowy element po danej pozycji.|
|[Lista C::WstawianiePrzed](#insertbefore)|Wstawia nowy element przed danym pozycją.|
|[CList::IsEmpty](#isempty)|Testy stanu pustej listy (bez elementów).|
|[Lista C::Usuńwszywszystko](#removeall)|Usuwa wszystkie elementy z tej listy.|
|[Lista C::Usuń](#removeat)|Usuwa element z tej listy, określony przez położenie.|
|[Lista C::Usuńgłowy](#removehead)|Usuwa element z głowy listy.|
|[Lista C::Usuńtail](#removetail)|Usuwa element z ogona listy.|
|[Lista C::SetAt](#setat)|Ustawia element w danej pozycji.|

#### <a name="parameters"></a>Parametry

*TYP*<br/>
Typ obiektu przechowywanego na liście.

*ARG_TYPE*<br/>
Typ używany do odwoływania się do obiektów przechowywanych na liście. Może być odwołaniem.

## <a name="remarks"></a>Uwagi

`CList`listy zachowują się jak listy podwójnie połączone.

Zmienna typu POSITION jest kluczem listy. Zmienną POSITION można użyć jako iteratora do przechodzenia przez listę sekwencyjnie i jako zakładki do przechowywania miejsca. Pozycja nie jest jednak taka sama jak indeks.

Wstawianie elementu jest bardzo szybkie na głowicy listy, na ogonie i w znanej pozycji. Wyszukiwanie sekwencyjne jest konieczne, aby wyszukać element według wartości lub indeksu. To wyszukiwanie może być powolne, jeśli lista jest długa.

Jeśli potrzebujesz zrzutu poszczególnych elementów na liście, należy ustawić głębokość kontekstu zrzutu na 1 lub większą.

Niektóre funkcje członkowskie tej klasy wywołać globalne funkcje pomocnika, `CList` które muszą być dostosowane do większości zastosowań klasy. Zobacz [Pomocnicy klas kolekcji](../../mfc/reference/collection-class-helpers.md) w sekcji "Makra i globalne".

Aby uzyskać więcej `CList`informacji na temat korzystania z programu , zobacz artykuł [Kolekcje](../../mfc/collections.md).

## <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtempl.h

## <a name="clistaddhead"></a><a name="addhead"></a>Lista C::Dodajgłowy

Dodaje nowy element lub listę elementów do głowy tej listy.

```
POSITION AddHead(ARG_TYPE newElement);
void AddHead(CList* pNewList);
```

### <a name="parameters"></a>Parametry

*ARG_TYPE*<br/>
Parametr szablonu określający typ elementu listy (może być odwołaniem).

*nowyElement*<br/>
Nowy element.

*pNowa Lista*<br/>
Wskaźnik do `CList` innej listy. Elementy w *pNewList* zostaną dodane do tej listy.

### <a name="return-value"></a>Wartość zwracana

Pierwsza wersja zwraca wartość POSITION nowo wstawionego elementu.

### <a name="remarks"></a>Uwagi

Lista może być pusta przed operacją.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]

## <a name="clistaddtail"></a><a name="addtail"></a>Lista C::Dodajtail

Dodaje nowy element lub listę elementów do ogona tej listy.

```
POSITION AddTail(ARG_TYPE newElement);
void AddTail(CList* pNewList);
```

### <a name="parameters"></a>Parametry

*ARG_TYPE*<br/>
Parametr szablonu określający typ elementu listy (może być odwołaniem).

*nowyElement*<br/>
Element, który ma zostać dodany do tej listy.

*pNowa Lista*<br/>
Wskaźnik do `CList` innej listy. Elementy w *pNewList* zostaną dodane do tej listy.

### <a name="return-value"></a>Wartość zwracana

Pierwsza wersja zwraca wartość POSITION nowo wstawionego elementu.

### <a name="remarks"></a>Uwagi

Lista może być pusta przed operacją.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]

## <a name="clistclist"></a><a name="clist"></a>Lista C::CList

Konstruuje pustą uporządkowaną listę.

```
CList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parametry

*nBlockSize (Rozmiar)*<br/>
Szczegółowość alokacji pamięci w celu rozszerzenia listy.

### <a name="remarks"></a>Uwagi

Wraz z rozwojem listy pamięć jest przydzielana w jednostkach wpisów *nBlockSize.*

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]

## <a name="clistfind"></a><a name="find"></a>Lista C::Znajdź

Przeszukuje listę sekwencyjnie, aby znaleźć pierwszy element pasujący do określonej *searchValue*.

```
POSITION Find(
    ARG_TYPE searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Parametry

*ARG_TYPE*<br/>
Parametr szablonu określający typ elementu listy (może być odwołaniem).

*wyszukiwanieValue*<br/>
Wartość, która ma zostać znaleziona na liście.

*startPoteru*<br/>
Pozycja początkowa wyszukiwania. Jeśli nie określono żadnej wartości, wyszukiwanie rozpoczyna się od elementu head.

### <a name="return-value"></a>Wartość zwracana

Wartość POSITION, która może służyć do iteracji lub pobierania wskaźnika obiektu; NULL, jeśli obiekt nie zostanie znaleziony.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]

## <a name="clistfindindex"></a><a name="findindex"></a>Lista C::FindIndex

Używa wartości *nIndex* jako indeksu na liście.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks od zera elementu listy, który ma zostać znaleziony.

### <a name="return-value"></a>Wartość zwracana

Wartość POSITION, która może służyć do iteracji lub pobierania wskaźnika obiektu; NULL, jeśli *nIndex* jest ujemny lub zbyt duży.

### <a name="remarks"></a>Uwagi

Rozpoczyna skanowanie sekwencyjne z głowy listy, zatrzymując się na *n*th element.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#40](../../mfc/codesnippet/cpp/clist-class_6.cpp)]

## <a name="clistgetat"></a><a name="getat"></a>Lista C::GetAt

Pobiera element listy w danej pozycji.

```
TYPE& GetAt(POSITION position);
const TYPE& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ obiektu na liście.

*Pozycji*<br/>
Pozycja na liście elementu, aby uzyskać.

### <a name="return-value"></a>Wartość zwracana

Zobacz opis wartości `GetHead`zwracanej dla .

### <a name="remarks"></a>Uwagi

`GetAt`zwraca element (lub odwołanie do elementu) skojarzony z danym pozycją. To nie jest to samo co indeks i nie można obsługiwać na position wartość samodzielnie. Zmienna typu POSITION jest kluczem listy.

Należy upewnić się, że wartość POSITION reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowania biblioteki klas programu Microsoft Foundation potwierdza.

### <a name="example"></a>Przykład

  Zobacz przykład [CList::GetHeadPosition](#getheadposition).

## <a name="clistgetcount"></a><a name="getcount"></a>Lista C::GetCount

Pobiera liczbę elementów na tej liście.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość całkowita zawierająca liczbę elementów.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody wygeneruje taki sam wynik jak [CList::GetSize](#getsize) metody.

### <a name="example"></a>Przykład

  Zobacz przykład [CList::RemoveHead](#removehead).

## <a name="clistgethead"></a><a name="gethead"></a>Lista C::GetHead

Pobiera element head (lub odwołanie do elementu head) tej listy.

```
const TYPE& GetHead() const;

TYPE& GetHead();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ obiektu na liście.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest **const**, `GetHead` zwraca kopię elementu na czele listy. Dzięki temu funkcja ma być używana tylko po prawej stronie instrukcji przypisania i chroni listę przed modyfikacją.

Jeśli lista nie jest `GetHead` **const**, zwraca odwołanie do elementu na czele listy. Dzięki temu funkcja ma być używana po obu stronach instrukcji przypisania, a tym samym umożliwia modyfikowanie wpisów listy.

### <a name="remarks"></a>Uwagi

Przed wywołaniem należy upewnić się, że lista nie jest pusta. `GetHead` Jeśli lista jest pusta, potwierdza to wersja debugowania biblioteki klas programu Microsoft Foundation. Użyj [IsEmpty,](#isempty) aby sprawdzić, czy lista zawiera elementy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]

## <a name="clistgetheadposition"></a><a name="getheadposition"></a>Lista C::Pozycja GetHead

Pobiera pozycję elementu head tej listy.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość POSITION, która może służyć do iteracji lub pobierania wskaźnika obiektu; NULL, jeśli lista jest pusta.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]

## <a name="clistgetnext"></a><a name="getnext"></a>Lista C::GetNext

Pobiera element listy identyfikowany przez *rPosition*, a następnie ustawia *rPosition* do wartości POSITION następnego wpisu na liście.

```
TYPE& GetNext(POSITION& rPosition);
const TYPE& GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów na liście.

*rPozycja*<br/>
Odwołanie do wartości POSITION zwróconej `GetNext`przez poprzednie wywołanie funkcji [GetHeadPosition](#getheadposition)lub inne wywołanie funkcji elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest **const**, `GetNext` zwraca kopię elementu listy. Dzięki temu funkcja ma być używana tylko po prawej stronie instrukcji przypisania i chroni listę przed modyfikacją.

Jeśli lista nie jest `GetNext` **const**, zwraca odwołanie do elementu listy. Dzięki temu funkcja ma być używana po obu stronach instrukcji przypisania, a tym samym umożliwia modyfikowanie wpisów listy.

### <a name="remarks"></a>Uwagi

Można użyć `GetNext` w pętli iteracji do przodu, jeśli ustalisz pozycję początkową za pomocą połączenia lub `GetHeadPosition` `Find`.

Należy upewnić się, że wartość POSITION reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowania biblioteki klas programu Microsoft Foundation potwierdza.

Jeśli pobrany element jest ostatnim na liście, nowa `rPosition` wartość jest ustawiona na WARTOŚĆ NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]

## <a name="clistgetprev"></a><a name="getprev"></a>Lista C::GetPrev

Pobiera element listy identyfikowany `rPosition` `rPosition` przez , a następnie ustawia wartość POSITION poprzedniego wpisu na liście.

```
TYPE& GetPrev(POSITION& rPosition);
const TYPE& GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów na liście.

*rPozycja*<br/>
Odwołanie do wartości POSITION zwróconej `GetPrev` przez poprzednie lub inne wywołanie funkcji elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest **const**, `GetPrev` zwraca kopię elementu na czele listy. Dzięki temu funkcja ma być używana tylko po prawej stronie instrukcji przypisania i chroni listę przed modyfikacją.

Jeśli lista nie jest `GetPrev` **const**, zwraca odwołanie do elementu listy. Dzięki temu funkcja ma być używana po obu stronach instrukcji przypisania, a tym samym umożliwia modyfikowanie wpisów listy.

### <a name="remarks"></a>Uwagi

Można użyć `GetPrev` w pętli reverse iteracji, jeśli ustalisz `GetTailPosition` `Find`pozycję początkową za pomocą wywołania lub .

Należy upewnić się, że wartość POSITION reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowania biblioteki klas programu Microsoft Foundation potwierdza.

Jeśli pobrany element jest pierwszym na liście, nowa wartość *rPosition* jest ustawiona na WARTOŚĆ NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#44](../../mfc/codesnippet/cpp/clist-class_10.cpp)]

## <a name="clistgetsize"></a><a name="getsize"></a>Lista C::GetSize

Zwraca liczbę elementów listy.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

liczba elementów na liście.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby pobrać liczbę elementów na liście.  Wywołanie tej metody wygeneruje taki sam wynik jak [CList::GetCount](#getcount) metody.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]

## <a name="clistgettail"></a><a name="gettail"></a>Lista C::GetTail

Pobiera `CObject` wskaźnik, który reprezentuje element ogona tej listy.

```
TYPE& GetTail();
const TYPE& GetTail() const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów na liście.

### <a name="return-value"></a>Wartość zwracana

Zobacz opis wartości zwracanej dla [GetHead](../../mfc/reference/coblist-class.md#gethead).

### <a name="remarks"></a>Uwagi

Przed wywołaniem należy upewnić się, że lista nie jest pusta. `GetTail` Jeśli lista jest pusta, potwierdza to wersja debugowania biblioteki klas programu Microsoft Foundation. Użyj [IsEmpty,](../../mfc/reference/coblist-class.md#isempty) aby sprawdzić, czy lista zawiera elementy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]

## <a name="clistgettailposition"></a><a name="gettailposition"></a>Lista C::GetTailPosition

Pobiera położenie elementu ogona tej listy; NULL, jeśli lista jest pusta.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość POSITION, która może służyć do iteracji lub pobierania wskaźnika obiektu; NULL, jeśli lista jest pusta.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]

## <a name="clistinsertafter"></a><a name="insertafter"></a>Lista C::WstawianiePo

Dodaje element do tej listy po elemencie w określonym położeniu.

```
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*Pozycji*<br/>
Wartość POSITION zwrócona `GetNext`przez `GetPrev`poprzednie `Find` , lub wywołanie funkcji elementu członkowskiego.

*ARG_TYPE*<br/>
Parametr szablonu określający typ elementu listy.

*nowyElement*<br/>
Element, który ma zostać dodany do tej listy.

### <a name="return-value"></a>Wartość zwracana

Wartość POSITION, która może służyć do iteracji lub pobierania elementu listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]

## <a name="clistinsertbefore"></a><a name="insertbefore"></a>Lista C::WstawianiePrzed

Dodaje element do tej listy przed elementem w określonym położeniu.

```
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*Pozycji*<br/>
Wartość POSITION zwrócona `GetNext`przez `GetPrev`poprzednie `Find` , lub wywołanie funkcji elementu członkowskiego.

*ARG_TYPE*<br/>
Parametr szablonu określający typ elementu listy (może być odwołaniem).

*nowyElement*<br/>
Element, który ma zostać dodany do tej listy.

### <a name="return-value"></a>Wartość zwracana

Wartość POSITION, która może służyć do iteracji lub pobierania elementu listy.

### <a name="remarks"></a>Uwagi

Jeśli pozycja ma *wartość* NULL, element jest wstawiany na czele listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]

## <a name="clistisempty"></a><a name="isempty"></a>CList::IsEmpty

Wskazuje, czy ta lista nie zawiera żadnych elementów.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli ta lista jest pusta; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]

## <a name="clistremoveall"></a><a name="removeall"></a>Lista C::Usuńwszywszystko

Usuwa wszystkie elementy z tej listy i zwalnia skojarzoną pamięć.

```
void RemoveAll();
```

### <a name="remarks"></a>Uwagi

Jeśli lista jest już pusta, nie jest generowany żaden błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#51](../../mfc/codesnippet/cpp/clist-class_17.cpp)]

## <a name="clistremoveat"></a><a name="removeat"></a>Lista C::Usuń

Usuwa określony element z tej listy.

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Parametry

*Pozycji*<br/>
Położenie elementu, który ma zostać usunięty z listy.

### <a name="remarks"></a>Uwagi

Należy upewnić się, że wartość POSITION reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowania biblioteki klas programu Microsoft Foundation potwierdza.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]

## <a name="clistremovehead"></a><a name="removehead"></a>Lista C::Usuńgłowy

Usuwa element z głowy listy i zwraca do niego wskaźnik.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów na liście.

### <a name="return-value"></a>Wartość zwracana

Element wcześniej na czele listy.

### <a name="remarks"></a>Uwagi

Przed wywołaniem należy upewnić się, że lista nie jest pusta. `RemoveHead` Jeśli lista jest pusta, potwierdza to wersja debugowania biblioteki klas programu Microsoft Foundation. Użyj [IsEmpty,](#isempty) aby sprawdzić, czy lista zawiera elementy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]

## <a name="clistremovetail"></a><a name="removetail"></a>Lista C::Usuńtail

Usuwa element z ogona listy i zwraca do niego wskaźnik.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów na liście.

### <a name="return-value"></a>Wartość zwracana

Element, który był na ogonie listy.

### <a name="remarks"></a>Uwagi

Przed wywołaniem należy upewnić się, że lista nie jest pusta. `RemoveTail` Jeśli lista jest pusta, potwierdza to wersja debugowania biblioteki klas programu Microsoft Foundation. Użyj [IsEmpty,](#isempty) aby sprawdzić, czy lista zawiera elementy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]

## <a name="clistsetat"></a><a name="setat"></a>Lista C::SetAt

Zmienna typu POSITION jest kluczem listy.

```
void SetAt(POSITION pos, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Położenie elementu, który ma być ustawiony.

*ARG_TYPE*<br/>
Parametr szablonu określający typ elementu listy (może być odwołaniem).

*nowyElement*<br/>
Element, który ma zostać dodany do listy.

### <a name="remarks"></a>Uwagi

To nie jest to samo co indeks i nie można obsługiwać na position wartość samodzielnie. `SetAt`zapisuje element do określonej pozycji na liście.

Należy upewnić się, że wartość POSITION reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowania biblioteki klas programu Microsoft Foundation potwierdza.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]

## <a name="see-also"></a>Zobacz też

[MFC Próbki COLLECT](../../overview/visual-cpp-samples.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CMap](../../mfc/reference/cmap-class.md)<br/>
[Klasa CArray](../../mfc/reference/carray-class.md)
