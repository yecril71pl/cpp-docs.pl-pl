---
title: Ctypedptrlist — klasa
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
ms.openlocfilehash: 9233e83a08fde87c15be5cc1c42a2f1dd3b56511
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324509"
---
# <a name="ctypedptrlist-class"></a>Ctypedptrlist — klasa

Oferuje bezpieczne "opakowanie" dla obiektów klasy `CPtrList`.

## <a name="syntax"></a>Składnia

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrList : public BASE_CLASS
```

#### <a name="parameters"></a>Parametry

*BASE_CLASS*<br/>
Klasa bazowa, klasy typizowanych wskaźników listy; musi być klasą listy wskaźnika ( `CObList` lub `CPtrList`).

*TYP*<br/>
Typ elementów przechowywane na liście klas podstawowych.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTypedPtrList::AddHead](#addhead)|Dodaje nagłówek listy (sprawia, że nowy główny) elementu (lub wszystkie elementy w innej listy).|
|[CTypedPtrList::AddTail](#addtail)|Dodaje ogona listy (sprawia, że nowe tail) elementu (lub wszystkie elementy w innej listy).|
|[CTypedPtrList::GetAt](#getat)|Pobiera element na określonej pozycji.|
|[CTypedPtrList::GetHead](#gethead)|Zwraca element główny listy (nie może być pusta).|
|[CTypedPtrList::GetNext](#getnext)|Pobiera następny element do wykonania iteracji.|
|[CTypedPtrList::GetPrev](#getprev)|Pobiera poprzedni element do wykonania iteracji.|
|[CTypedPtrList::GetTail](#gettail)|Zwraca element tail listy (nie może być pusta).|
|[CTypedPtrList::RemoveHead](#removehead)|Usuwa element z głowy listy.|
|[CTypedPtrList::RemoveTail](#removetail)|Usuwa element z zakończeniem listy.|
|[CTypedPtrList::SetAt](#setat)|Ustawia element na określonej pozycji.|

## <a name="remarks"></a>Uwagi

Kiedy używasz `CTypedPtrList` zamiast `CObList` lub `CPtrList`, funkcji Kontrola typów w języku C++, pomaga wyeliminować sytuację błędów spowodowanych przez wskaźnik niezgodne typy.

Ponadto `CTypedPtrList` otoki wykonuje większość rzutowania, które będą wymagane, jeśli użyto `CObList` lub `CPtrList`.

Ponieważ wszystkie `CTypedPtrList` funkcje są wbudowane, użyj tego szablonu nie znacząco wpływa na rozmiar lub prędkość kodu.

Wyświetla pochodną `CObList` może być Zserializowany, ale te pochodzące z `CPtrList` nie.

Gdy `CTypedPtrList` obiekt zostanie usunięty lub usunięcie jej elementy są usuwane tylko wskaźników, nie mogą odwoływać się do jednostki.

Aby uzyskać więcej informacji na temat korzystania z `CTypedPtrList`, zobacz artykuły [kolekcje](../../mfc/collections.md) i [oparte na szablonach klas](../../mfc/template-based-classes.md).

## <a name="example"></a>Przykład

W tym przykładzie tworzone jest wystąpienie `CTypedPtrList`, dodaje jeden obiekt, serializuje listy na dysku, a następnie usuwa obiekt:

[!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]

[!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`BASE_CLASS`

`_CTypedPtrList`

`CTypedPtrList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtempl.h

##  <a name="addhead"></a>  CTypedPtrList::AddHead

Ta funkcja elementu członkowskiego wywołuje `BASE_CLASS` **:: AddHead**.

```
POSITION AddHead(TYPE newElement);
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Typ elementów przechowywane na liście klas podstawowych.

*newElement*<br/>
Wskaźnik obiektu, który ma zostać dodany do tej listy. Wartość NULL jest dozwolona.

*BASE_CLASS*<br/>
Klasa bazowa, klasy typizowanych wskaźników listy; musi być klasą listy wskaźnika ( [CObList](../../mfc/reference/coblist-class.md) lub [CPtrList](../../mfc/reference/cptrlist-class.md)).

*pNewList*<br/>
Wskaźnik do innego [CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md) obiektu. Elementy w *pNewList* zostaną dodane do tej listy.

### <a name="return-value"></a>Wartość zwracana

Pierwsza wersja zwraca wartość pozycji nowo wstawionego elementu.

### <a name="remarks"></a>Uwagi

Pierwsza wersja dodaje nowy element przed nagłówek listy. Druga wersja dodaje kolejną listą elementów przed nagłówek.

##  <a name="addtail"></a>  CTypedPtrList::AddTail

Ta funkcja elementu członkowskiego wywołuje `BASE_CLASS` **:: addtail —**.

```
POSITION AddTail(TYPE newElement);
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Typ elementów przechowywane na liście klas podstawowych.

*newElement*<br/>
Wskaźnik obiektu, który ma zostać dodany do tej listy. Wartość NULL jest dozwolona.

*BASE_CLASS*<br/>
Klasa bazowa, klasy typizowanych wskaźników listy; musi być klasą listy wskaźnika ( [CObList](../../mfc/reference/coblist-class.md) lub [CPtrList](../../mfc/reference/cptrlist-class.md)).

*pNewList*<br/>
Wskaźnik do innego [CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md) obiektu. Elementy w *pNewList* zostaną dodane do tej listy.

### <a name="return-value"></a>Wartość zwracana

Pierwsza wersja zwraca wartość pozycji nowo wstawionego elementu.

### <a name="remarks"></a>Uwagi

Pierwsza wersja dodaje nowy element po koniec listy. Druga wersja dodaje kolejną listą elementów po koniec listy.

##  <a name="getat"></a>  CTypedPtrList::GetAt

Zmienna typu pozycja jest kluczem dla listy.

```
TYPE& GetAt(POSITION position);
TYPE GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów przechowywanych na liście.

*Stanowisko*<br/>
Wartość pozycji zwrócony przez poprzednie `GetHeadPosition` lub `Find` wywołanie funkcji elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest dostępna za pośrednictwem wskaźnik do `const CTypedPtrList`, następnie `GetAt` zwraca wskaźnik typu określonego przez parametr szablonu *typu*. Umożliwia korzystanie z funkcji ma być używany tylko po prawej stronie instrukcji przypisania, a zatem chroni listy przed modyfikacją.

Jeśli lista jest dostępny bezpośrednio lub za pomocą wskaźnika do `CTypedPtrList`, następnie `GetAt` zwraca odwołanie do wskaźnika typu określonego przez parametr szablonu *typu*. Umożliwia korzystanie z funkcji ma być używany po obu stronach instrukcji przypisania, a zatem umożliwia pozycji listy do zmodyfikowania.

### <a name="remarks"></a>Uwagi

Nie jest taka sama jak indeksu, a użytkownik nie może działać na wartość pozycji samodzielnie. `GetAt` pobiera `CObject` kursor skojarzony z określonej pozycji.

Należy się upewnić, że wartość pozycji reprezentuje poprawnej pozycji na liście. Jeśli jest nieprawidłowy, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation.

Ta funkcja śródwierszowa wywołuje `BASE_CLASS` **:: GetAt**.

##  <a name="gethead"></a>  CTypedPtrList::GetHead

Pobiera wskaźnik, który reprezentuje główny element tej listy.

```
TYPE& GetHead();
TYPE GetHead() const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów przechowywanych na liście.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest dostępna za pośrednictwem wskaźnik do `const CTypedPtrList`, następnie `GetHead` zwraca wskaźnik typu określonego przez parametr szablonu *typu*. Umożliwia korzystanie z funkcji ma być używany tylko po prawej stronie instrukcji przypisania, a zatem chroni listy przed modyfikacją.

Jeśli lista jest dostępny bezpośrednio lub za pomocą wskaźnika do `CTypedPtrList`, następnie `GetHead` zwraca odwołanie do wskaźnika typu określonego przez parametr szablonu *typu*. Umożliwia korzystanie z funkcji ma być używany po obu stronach instrukcji przypisania, a zatem umożliwia pozycji listy do zmodyfikowania.

### <a name="remarks"></a>Uwagi

Należy upewnić się, lista nie jest pusta, przed wywołaniem `GetHead`. Jeśli lista jest pusta, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation. Użyj [IsEmpty](../../mfc/reference/coblist-class.md#isempty) Aby sprawdzić, czy lista zawiera elementy.

##  <a name="getnext"></a>  CTypedPtrList::GetNext

Pobiera element listy identyfikowane przez *elemencie rPosition*, następnie ustawia *elemencie rPosition* wartość pozycji następnego wpisu na liście.

```
TYPE& GetNext(POSITION& rPosition);
TYPE GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów znajdujących się na tej liście.

*elemencie rPosition*<br/>
Odwołanie do wartości pozycji, zwrócony przez poprzednie `GetNext`, `GetHeadPosition`, lub inne wywołanie funkcji elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest dostępna za pośrednictwem wskaźnik do `const CTypedPtrList`, następnie `GetNext` zwraca wskaźnik typu określonego przez parametr szablonu *typu*. Umożliwia korzystanie z funkcji ma być używany tylko po prawej stronie instrukcji przypisania, a zatem chroni listy przed modyfikacją.

Jeśli lista jest dostępny bezpośrednio lub za pomocą wskaźnika do `CTypedPtrList`, następnie `GetNext` zwraca odwołanie do wskaźnika typu określonego przez parametr szablonu *typu*. Umożliwia korzystanie z funkcji ma być używany po obu stronach instrukcji przypisania, a zatem umożliwia pozycji listy do zmodyfikowania.

### <a name="remarks"></a>Uwagi

Możesz użyć `GetNext` w pętli do przodu iteracji, jeśli ustanowisz początkowe położenie w wyniku wywołania `GetHeadPosition` lub [CPtrList::Find](../../mfc/reference/coblist-class.md#find).

Należy się upewnić, że wartość pozycji reprezentuje poprawnej pozycji na liście. Jeśli jest nieprawidłowy, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation.

Jeśli element pobrane ostatnio na liście jest następnie nowa wartość *elemencie rPosition* ma wartość NULL.

Istnieje możliwość usunięcia elementu podczas iteracji. Zobacz przykład [CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat).

##  <a name="getprev"></a>  CTypedPtrList::GetPrev

Pobiera element listy identyfikowane przez *elemencie rPosition*, następnie ustawia *elemencie rPosition* wartość pozycji poprzedni wpis na liście.

```
TYPE& GetPrev(POSITION& rPosition);
TYPE GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów znajdujących się na tej liście.

*elemencie rPosition*<br/>
Odwołanie do wartości pozycji, zwrócony przez poprzednie `GetPrev` lub inne wywołanie funkcji elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest dostępna za pośrednictwem wskaźnik do `const CTypedPtrList`, następnie `GetPrev` zwraca wskaźnik typu określonego przez parametr szablonu *typu*. Umożliwia korzystanie z funkcji ma być używany tylko po prawej stronie instrukcji przypisania, a zatem chroni listy przed modyfikacją.

Jeśli lista jest dostępny bezpośrednio lub za pomocą wskaźnika do `CTypedPtrList`, następnie `GetPrev` zwraca odwołanie do wskaźnika typu określonego przez parametr szablonu *typu*. Umożliwia korzystanie z funkcji ma być używany po obu stronach instrukcji przypisania, a zatem umożliwia pozycji listy do zmodyfikowania.

### <a name="remarks"></a>Uwagi

Możesz użyć `GetPrev` w iteracji odwrotnej pętli, jeśli ustanowisz początkowe położenie w wyniku wywołania `GetTailPosition` lub `Find`.

Należy się upewnić, że wartość pozycji reprezentuje poprawnej pozycji na liście. Jeśli jest nieprawidłowy, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation.

Jeśli element pobrane jest pierwsze na liście, nowa wartość *elemencie rPosition* ma wartość NULL.

##  <a name="gettail"></a>  CTypedPtrList::GetTail

Pobiera wskaźnik, który reprezentuje główny element tej listy.

```
TYPE& GetTail();
TYPE GetTail() const;
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów przechowywanych na liście.

### <a name="return-value"></a>Wartość zwracana

Jeśli lista jest dostępna za pośrednictwem wskaźnik do `const CTypedPtrList`, następnie `GetTail` zwraca wskaźnik typu określonego przez parametr szablonu *typu*. Umożliwia korzystanie z funkcji ma być używany tylko po prawej stronie instrukcji przypisania, a zatem chroni listy przed modyfikacją.

Jeśli lista jest dostępny bezpośrednio lub za pomocą wskaźnika do `CTypedPtrList`, następnie `GetTail` zwraca odwołanie do wskaźnika typu określonego przez parametr szablonu *typu*. Umożliwia korzystanie z funkcji ma być używany po obu stronach instrukcji przypisania, a zatem umożliwia pozycji listy do zmodyfikowania.

### <a name="remarks"></a>Uwagi

Należy upewnić się, lista nie jest pusta, przed wywołaniem `GetTail`. Jeśli lista jest pusta, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation. Użyj [IsEmpty](../../mfc/reference/coblist-class.md#isempty) Aby sprawdzić, czy lista zawiera elementy.

##  <a name="removehead"></a>  CTypedPtrList::RemoveHead

Usuwa element z głowy listy i zwraca go.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów przechowywanych na liście.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik wcześniej na czele listy. Ten wskaźnik jest typu określonego przez parametr szablonu *typu*.

### <a name="remarks"></a>Uwagi

Należy upewnić się, lista nie jest pusta, przed wywołaniem `RemoveHead`. Jeśli lista jest pusta, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation. Użyj [IsEmpty](../../mfc/reference/coblist-class.md#isempty) Aby sprawdzić, czy lista zawiera elementy.

##  <a name="removetail"></a>  CTypedPtrList::RemoveTail

Usuwa element z zakończeniem listy i zwraca go.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr szablonu określający typ elementów przechowywanych na liście.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik wcześniej na końcu listy. Ten wskaźnik jest typu określonego przez parametr szablonu *typu*.

### <a name="remarks"></a>Uwagi

Należy upewnić się, lista nie jest pusta, przed wywołaniem `RemoveTail`. Jeśli lista jest pusta, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation. Użyj [IsEmpty](../../mfc/reference/coblist-class.md#isempty) Aby sprawdzić, czy lista zawiera elementy.

##  <a name="setat"></a>  CTypedPtrList::SetAt

Ta funkcja elementu członkowskiego wywołuje `BASE_CLASS` **:: SetAt**.

```
void SetAt(POSITION pos, TYPE newElement);
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
POŁOŻENIE elementu do ustawienia.

*TYP*<br/>
Typ elementów przechowywane na liście klas podstawowych.

*newElement*<br/>
Wskaźnik obiektu ma on zostać zapisany na liście.

### <a name="remarks"></a>Uwagi

Zmienna typu pozycja jest kluczem dla listy. Nie jest taka sama jak indeksu, a użytkownik nie może działać na wartość pozycji samodzielnie. `SetAt` zapisuje wskaźnik do obiektu w określonej pozycji na liście.

Należy się upewnić, że wartość pozycji reprezentuje poprawnej pozycji na liście. Jeśli jest nieprawidłowy, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation.

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObList::SetAt](../../mfc/reference/coblist-class.md#setat).

## <a name="see-also"></a>Zobacz także

[Próbki MFC ZBIERANIE](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CPtrList](../../mfc/reference/cptrlist-class.md)<br/>
[Klasa CObList](../../mfc/reference/coblist-class.md)
