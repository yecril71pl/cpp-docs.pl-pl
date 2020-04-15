---
title: Klasa CTypedPtrList
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrList
- AFXTEMPL/CTypedPtrList
- AFXTEMPL/CTypedPtrList::AddHead
- AFXTEMPL/CTypedPtrList::AddTail
- AFXTEMPL/CTypedPtrList::GetAt
- AFXTEMPL/CTypedPtrList::GetHead
- AFXTEMPL/CTypedPtrList::GetNext
- AFXTEMPL/CTypedPtrList::GetPrev
- AFXTEMPL/CTypedPtrList::GetTail
- AFXTEMPL/CTypedPtrList::RemoveHead
- AFXTEMPL/CTypedPtrList::RemoveTail
- AFXTEMPL/CTypedPtrList::SetAt
helpviewer_keywords:
- CTypedPtrList [MFC], AddHead
- CTypedPtrList [MFC], AddTail
- CTypedPtrList [MFC], GetAt
- CTypedPtrList [MFC], GetHead
- CTypedPtrList [MFC], GetNext
- CTypedPtrList [MFC], GetPrev
- CTypedPtrList [MFC], GetTail
- CTypedPtrList [MFC], RemoveHead
- CTypedPtrList [MFC], RemoveTail
- CTypedPtrList [MFC], SetAt
ms.assetid: c273096e-1756-4340-864b-4a08b674a65e
ms.openlocfilehash: 40dbfb822e71309e9675aba14d46d333ffa4ee06
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373265"
---
# <a name="ctypedptrlist-class"></a>Klasa CTypedPtrList

Zapewnia bezpieczne dla typu "otokę" `CPtrList`dla obiektów klasy.

## <a name="syntax"></a>Składnia

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrList : public BASE_CLASS
```

#### <a name="parameters"></a>Parametry

*BASE_CLASS*<br/>
Klasa podstawowa klasy listy wpisanych wskaźników; musi być klasą `CObList` listy `CPtrList`wskaźników ( lub ).

*TYP*<br/>
Typ elementów przechowywanych na liście klas podstawowych.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Lista CTypedPtrList::Głowica dodania](#addhead)|Dodaje element (lub wszystkie elementy na innej liście) do głowy listy (tworzy nową głowę).|
|[Lista CTypedPtrList::AddTail](#addtail)|Dodaje element (lub wszystkie elementy na innej liście) do ogona listy (tworzy nowy ogon).|
|[Lista CTypedPtrList::GetAt](#getat)|Pobiera element w danej pozycji.|
|[Lista CTypedPtrList::GetHead](#gethead)|Zwraca element head listy (nie może być pusty).|
|[Lista CTypedPtrList::GetNext](#getnext)|Pobiera następny element do iteracji.|
|[Lista CTypedPtrList::GetPrev](#getprev)|Pobiera poprzedni element do iteracji.|
|[Lista CTypedPtrList::GetTail](#gettail)|Zwraca element ogonowy listy (nie może być pusty).|
|[Lista CTypedPtrList::Usuńgłówkę](#removehead)|Usuwa element z głowy listy.|
|[Lista CTypedPtrList::Usuńtail](#removetail)|Usuwa element z ogona listy.|
|[Lista CTypedPtrList::SetAt](#setat)|Ustawia element w danej pozycji.|

## <a name="remarks"></a>Uwagi

Podczas korzystania, `CTypedPtrList` `CObList` a `CPtrList`nie lub , C++ funkcji sprawdzania typu pomaga wyeliminować błędy spowodowane przez niedopasowane typy wskaźników.

Ponadto `CTypedPtrList` otoka wykonuje większość odlewania, które byłyby wymagane, jeśli używany `CObList` lub `CPtrList`.

Ponieważ `CTypedPtrList` wszystkie funkcje są wbudowane, użycie tego szablonu nie ma znaczącego wpływu na rozmiar lub szybkość kodu.

Listy pochodzące `CObList` z mogą być serializowane, `CPtrList` ale te pochodzące z nie może.

Po `CTypedPtrList` usunięciu obiektu lub usunięciu jego elementów usuwane są tylko wskaźniki, a nie elementy, do których się odwołują.

Aby uzyskać więcej `CTypedPtrList`informacji na temat używania , zobacz artykuły [Kolekcje](../../mfc/collections.md) i [klasy oparte na szablonach](../../mfc/template-based-classes.md).

## <a name="example"></a>Przykład

W tym przykładzie `CTypedPtrList`tworzy wystąpienie , dodaje jeden obiekt, serializuje listę na dysku, a następnie usuwa obiekt:

[!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]

[!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`BASE_CLASS`

`_CTypedPtrList`

`CTypedPtrList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtempl.h

## <a name="ctypedptrlistaddhead"></a><a name="addhead"></a>Lista CTypedPtrList::Głowica dodania

Ta funkcja `BASE_CLASS`elementu członkowskiego wywołuje **::AddHead**.

```
POSITION AddHead(TYPE newElement);
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Typ elementów przechowywanych na liście klas podstawowych.

*nowyElement*<br/>
Wskaźnik obiektu, który ma zostać dodany do tej listy. Wartość NULL jest dozwolona.

*BASE_CLASS*<br/>
Klasa podstawowa klasy listy wpisanych wskaźników; musi być klasą listy wskaźników [(CObList](../../mfc/reference/coblist-class.md) lub [CPtrList).](../../mfc/reference/cptrlist-class.md)

*pNowa Lista*<br/>
Wskaźnik do innego obiektu [CTypedPtrList.](../../mfc/reference/ctypedptrlist-class.md) Elementy w *pNewList* zostaną dodane do tej listy.

### <a name="return-value"></a>Wartość zwracana

Pierwsza wersja zwraca wartość POSITION nowo wstawionego elementu.

### <a name="remarks"></a>Uwagi

Pierwsza wersja dodaje nowy element przed szefem listy. Druga wersja dodaje kolejną listę elementów przed głową.

## <a name="ctypedptrlistaddtail"></a><a name="addtail"></a>Lista CTypedPtrList::AddTail

Ta funkcja `BASE_CLASS`elementu członkowskiego wywołuje **::AddTail**.

```
POSITION AddTail(TYPE newElement);
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Typ elementów przechowywanych na liście klas podstawowych.

*nowyElement*<br/>
Wskaźnik obiektu, który ma zostać dodany do tej listy. Wartość NULL jest dozwolona.

*BASE_CLASS*<br/>
Klasa podstawowa klasy listy wpisanych wskaźników; musi być klasą listy wskaźników [(CObList](../../mfc/reference/coblist-class.md) lub [CPtrList).](../../mfc/reference/cptrlist-class.md)

*pNowa Lista*<br/>
Wskaźnik do innego obiektu [CTypedPtrList.](../../mfc/reference/ctypedptrlist-class.md) Elementy w *pNewList* zostaną dodane do tej listy.

### <a name="return-value"></a>Wartość zwracana

Pierwsza wersja zwraca wartość POSITION nowo wstawionego elementu.

### <a name="remarks"></a>Uwagi

Pierwsza wersja dodaje nowy element po ogonie listy. Druga wersja dodaje inną listę elementów po ogonie listy.

## <a name="ctypedptrlistgetat"></a><a name="getat"></a>Lista CTypedPtrList::GetAt

Zmienna typu POSITION jest kluczem listy.

```
TYPE& GetAt(POSITION position);
TYPE GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów przechowywanych na liście.

*Pozycji*<br/>
Wartość POSITION zwrócona `GetHeadPosition` przez `Find` poprzednie wywołanie funkcji lub element członkowski.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest dostępna za pomocą `const CTypedPtrList`wskaźnika do , a następnie `GetAt` zwraca wskaźnik typu określonego przez parametr szablonu *TYP*. Dzięki temu funkcja ma być używana tylko po prawej stronie instrukcji przypisania i w ten sposób chroni listę przed modyfikacją.

Jeśli lista jest dostępna bezpośrednio lub za `CTypedPtrList`pośrednictwem `GetAt` wskaźnika do , a następnie zwraca odwołanie do wskaźnika typu określonego przez parametr *szablonu TYPE*. Dzięki temu funkcja ma być używana po obu stronach instrukcji przypisania, a tym samym umożliwia modyfikowanie wpisów listy.

### <a name="remarks"></a>Uwagi

To nie jest to samo co indeks i nie można obsługiwać na position wartość samodzielnie. `GetAt`pobiera `CObject` wskaźnik skojarzony z danym pozycją.

Należy upewnić się, że wartość POSITION reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowania biblioteki klas programu Microsoft Foundation potwierdza.

Ta wbudowana `BASE_CLASS`funkcja wywołuje **::GetAt**.

## <a name="ctypedptrlistgethead"></a><a name="gethead"></a>Lista CTypedPtrList::GetHead

Pobiera wskaźnik, który reprezentuje element head tej listy.

```
TYPE& GetHead();
TYPE GetHead() const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów przechowywanych na liście.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest dostępna za pomocą `const CTypedPtrList`wskaźnika do , a następnie `GetHead` zwraca wskaźnik typu określonego przez parametr szablonu *TYP*. Dzięki temu funkcja ma być używana tylko po prawej stronie instrukcji przypisania i w ten sposób chroni listę przed modyfikacją.

Jeśli lista jest dostępna bezpośrednio lub za `CTypedPtrList`pośrednictwem `GetHead` wskaźnika do , a następnie zwraca odwołanie do wskaźnika typu określonego przez parametr *szablonu TYPE*. Dzięki temu funkcja ma być używana po obu stronach instrukcji przypisania, a tym samym umożliwia modyfikowanie wpisów listy.

### <a name="remarks"></a>Uwagi

Przed wywołaniem należy upewnić się, że lista nie jest pusta. `GetHead` Jeśli lista jest pusta, potwierdza to wersja debugowania biblioteki klas programu Microsoft Foundation. Użyj [IsEmpty,](../../mfc/reference/coblist-class.md#isempty) aby sprawdzić, czy lista zawiera elementy.

## <a name="ctypedptrlistgetnext"></a><a name="getnext"></a>Lista CTypedPtrList::GetNext

Pobiera element listy identyfikowany przez *rPosition*, a następnie ustawia *rPosition* do wartości POSITION następnego wpisu na liście.

```
TYPE& GetNext(POSITION& rPosition);
TYPE GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów zawartych na tej liście.

*rPozycja*<br/>
Odwołanie do wartości POSITION zwróconej `GetNext` `GetHeadPosition`przez poprzednie , lub inne wywołanie funkcji elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest dostępna za pomocą `const CTypedPtrList`wskaźnika do , a następnie `GetNext` zwraca wskaźnik typu określonego przez parametr szablonu *TYP*. Dzięki temu funkcja ma być używana tylko po prawej stronie instrukcji przypisania i w ten sposób chroni listę przed modyfikacją.

Jeśli lista jest dostępna bezpośrednio lub za `CTypedPtrList`pośrednictwem `GetNext` wskaźnika do , a następnie zwraca odwołanie do wskaźnika typu określonego przez parametr *szablonu TYPE*. Dzięki temu funkcja ma być używana po obu stronach instrukcji przypisania, a tym samym umożliwia modyfikowanie wpisów listy.

### <a name="remarks"></a>Uwagi

Można użyć `GetNext` w pętli iteracji do przodu, jeśli ustanowisz pozycję początkową za pomocą wywołania `GetHeadPosition` lub listy [CPtrList::Find](../../mfc/reference/coblist-class.md#find).

Należy upewnić się, że wartość POSITION reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowania biblioteki klas programu Microsoft Foundation potwierdza.

Jeśli pobrany element jest ostatnim na liście, nowa wartość *rPosition* jest ustawiona na WARTOŚĆ NULL.

Możliwe jest usunięcie elementu podczas iteracji. Zobacz przykład [CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat).

## <a name="ctypedptrlistgetprev"></a><a name="getprev"></a>Lista CTypedPtrList::GetPrev

Pobiera element listy identyfikowany przez *rPosition*, a następnie ustawia *rPosition* do wartości POSITION poprzedniego wpisu na liście.

```
TYPE& GetPrev(POSITION& rPosition);
TYPE GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów zawartych na tej liście.

*rPozycja*<br/>
Odwołanie do wartości POSITION zwróconej `GetPrev` przez poprzednie lub inne wywołanie funkcji elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest dostępna za pomocą `const CTypedPtrList`wskaźnika do , a następnie `GetPrev` zwraca wskaźnik typu określonego przez parametr szablonu *TYP*. Dzięki temu funkcja ma być używana tylko po prawej stronie instrukcji przypisania i w ten sposób chroni listę przed modyfikacją.

Jeśli lista jest dostępna bezpośrednio lub za `CTypedPtrList`pośrednictwem `GetPrev` wskaźnika do , a następnie zwraca odwołanie do wskaźnika typu określonego przez parametr *szablonu TYPE*. Dzięki temu funkcja ma być używana po obu stronach instrukcji przypisania, a tym samym umożliwia modyfikowanie wpisów listy.

### <a name="remarks"></a>Uwagi

Można użyć `GetPrev` w pętli reverse iteracji, jeśli ustalisz `GetTailPosition` `Find`pozycję początkową za pomocą wywołania lub .

Należy upewnić się, że wartość POSITION reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowania biblioteki klas programu Microsoft Foundation potwierdza.

Jeśli pobrany element jest pierwszym na liście, nowa wartość *rPosition* jest ustawiona na WARTOŚĆ NULL.

## <a name="ctypedptrlistgettail"></a><a name="gettail"></a>Lista CTypedPtrList::GetTail

Pobiera wskaźnik, który reprezentuje element head tej listy.

```
TYPE& GetTail();
TYPE GetTail() const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów przechowywanych na liście.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest dostępna za pomocą `const CTypedPtrList`wskaźnika do , a następnie `GetTail` zwraca wskaźnik typu określonego przez parametr szablonu *TYP*. Dzięki temu funkcja ma być używana tylko po prawej stronie instrukcji przypisania i w ten sposób chroni listę przed modyfikacją.

Jeśli lista jest dostępna bezpośrednio lub za `CTypedPtrList`pośrednictwem `GetTail` wskaźnika do , a następnie zwraca odwołanie do wskaźnika typu określonego przez parametr *szablonu TYPE*. Dzięki temu funkcja ma być używana po obu stronach instrukcji przypisania, a tym samym umożliwia modyfikowanie wpisów listy.

### <a name="remarks"></a>Uwagi

Przed wywołaniem należy upewnić się, że lista nie jest pusta. `GetTail` Jeśli lista jest pusta, potwierdza to wersja debugowania biblioteki klas programu Microsoft Foundation. Użyj [IsEmpty,](../../mfc/reference/coblist-class.md#isempty) aby sprawdzić, czy lista zawiera elementy.

## <a name="ctypedptrlistremovehead"></a><a name="removehead"></a>Lista CTypedPtrList::Usuńgłówkę

Usuwa element z głowy listy i zwraca go.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów przechowywanych na liście.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik wcześniej na czele listy. Ten wskaźnik jest typem określonym przez parametr szablonu *TYP*.

### <a name="remarks"></a>Uwagi

Przed wywołaniem należy upewnić się, że lista nie jest pusta. `RemoveHead` Jeśli lista jest pusta, potwierdza to wersja debugowania biblioteki klas programu Microsoft Foundation. Użyj [IsEmpty,](../../mfc/reference/coblist-class.md#isempty) aby sprawdzić, czy lista zawiera elementy.

## <a name="ctypedptrlistremovetail"></a><a name="removetail"></a>Lista CTypedPtrList::Usuńtail

Usuwa element z ogona listy i zwraca go.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów przechowywanych na liście.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik wcześniej na ogonie listy. Ten wskaźnik jest typem określonym przez parametr szablonu *TYP*.

### <a name="remarks"></a>Uwagi

Przed wywołaniem należy upewnić się, że lista nie jest pusta. `RemoveTail` Jeśli lista jest pusta, potwierdza to wersja debugowania biblioteki klas programu Microsoft Foundation. Użyj [IsEmpty,](../../mfc/reference/coblist-class.md#isempty) aby sprawdzić, czy lista zawiera elementy.

## <a name="ctypedptrlistsetat"></a><a name="setat"></a>Lista CTypedPtrList::SetAt

Ta funkcja `BASE_CLASS`elementu członkowskiego wywołuje **::SetAt**.

```
void SetAt(POSITION pos, TYPE newElement);
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Położenie elementu, który ma być ustawiony.

*TYP*<br/>
Typ elementów przechowywanych na liście klas podstawowych.

*nowyElement*<br/>
Wskaźnik obiektu, który ma zostać zapisany na liście.

### <a name="remarks"></a>Uwagi

Zmienna typu POSITION jest kluczem listy. To nie jest to samo co indeks i nie można obsługiwać na position wartość samodzielnie. `SetAt`zapisuje wskaźnik obiektu do określonej pozycji na liście.

Należy upewnić się, że wartość POSITION reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowania biblioteki klas programu Microsoft Foundation potwierdza.

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObList::SetAt](../../mfc/reference/coblist-class.md#setat).

## <a name="see-also"></a>Zobacz też

[MFC Próbki COLLECT](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CPtrList](../../mfc/reference/cptrlist-class.md)<br/>
[Klasa CObList](../../mfc/reference/coblist-class.md)
