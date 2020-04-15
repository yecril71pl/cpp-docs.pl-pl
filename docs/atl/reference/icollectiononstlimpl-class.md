---
title: Klasa ICollectionOnSTLImpl
ms.date: 11/04/2016
f1_keywords:
- ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl::get__NewEnum
- ATLCOM/ATL::ICollectionOnSTLImpl::getcount
- ATLCOM/ATL::ICollectionOnSTLImpl::get_Item
- ATLCOM/ATL::ICollectionOnSTLImpl::m_coll
helpviewer_keywords:
- ICollectionOnSTLImpl class
ms.assetid: 683c88b0-0d97-4779-a762-e493334ba7f9
ms.openlocfilehash: a8ccab08b89da8c1b8ef56c8932e27a6c74e62aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329907"
---
# <a name="icollectiononstlimpl-class"></a>Klasa ICollectionOnSTLImpl

Ta klasa zawiera metody używane przez klasę kolekcji.

## <a name="syntax"></a>Składnia

```
template <class T, class CollType, class ItemType, class CopyItem, class EnumType>
class ICollectionOnSTLImpl : public T
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Interfejs kolekcji COM.

*Typ sortowania*<br/>
Klasa kontenera biblioteki standardowej języka C++.

*ItemType*<br/>
Typ elementu udostępniane przez interfejs kontenera.

*CopyItem (Kopia 1/*<br/>
[Klasa zasad kopiowania](../../atl/atl-copy-policy-classes.md).

*Enumtype*<br/>
Klasa wyliczeniowa zgodna z [CComEnumOnSTL.](../../atl/reference/ccomenumonstl-class.md)

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ICollectionOnSTLImpl::get__NewEnum](#newenum)|Zwraca obiekt wyliczacza dla kolekcji.|
|[ICollectionOnSTLImpl::getcount](#get_count)|Zwraca liczbę elementów w kolekcji.|
|[ICollectionOnSTLImpl::get_Item](#get_item)|Zwraca żądany element z kolekcji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[ICollectionOnSTLImpl::m_coll](#m_coll)|Kolekcja.|

## <a name="remarks"></a>Uwagi

Ta klasa zapewnia implementację dla trzech metod interfejsu kolekcji: [getcount](#get_count), [get_Item](#get_item)i [get__NewEnum](#newenum).

Aby użyć tej klasy:

- Zdefiniuj (lub pożycz) interfejs kolekcji, który chcesz zaimplementować.

- Wywodź swoją klasę `ICollectionOnSTLImpl` ze specjalizacji opartej na tym interfejsie kolekcji.

- Użyj klasy pochodnej, aby zaimplementować wszelkie `ICollectionOnSTLImpl`metody z interfejsu kolekcji, które nie są obsługiwane przez program .

> [!NOTE]
> Jeśli interfejs kolekcji jest interfejsem dualnym, należy wyprowadzić klasę `ICollectionOnSTLImpl` z [IDispatchImpl](../../atl/reference/idispatchimpl-class.md), przekazując specjalizację `IDispatch` jako pierwszy parametr szablonu, jeśli chcesz ATL, aby zapewnić implementację metod.

- Dodaj elementy do [m_coll](#m_coll) elementu członkowskiego, aby wypełnić kolekcję.

Aby uzyskać więcej informacji i przykładów, zobacz [Kolekcje ATL i wyliczacze](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`T`

`ICollectionOnSTLImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="icollectiononstlimplgetcount"></a><a name="get_count"></a>ICollectionOnSTLImpl::getcount

Ta metoda zwraca liczbę elementów w kolekcji.

```
STDMETHOD(getcount)(long* pcount);
```

### <a name="parameters"></a>Parametry

*pcount (liczba pcount)*<br/>
[na zewnątrz] Liczba elementów w kolekcji.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="icollectiononstlimplget_item"></a><a name="get_item"></a>ICollectionOnSTLImpl::get_Item

Ta metoda zwraca określony element z kolekcji.

```
STDMETHOD(get_Item)(long Index, ItemType* pvar);
```

### <a name="parameters"></a>Parametry

*Indeks*<br/>
[w] Indeks 1 na podstawie elementu w kolekcji.

*pvar (pvar)*<br/>
[na zewnątrz] Pozycja odpowiadająca *indeksowi*.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Element jest uzyskiwany przez skopiowanie danych w określonej pozycji w [m_coll](#m_coll) przy użyciu metody kopiowania [klasy zasad kopiowania](../../atl/atl-copy-policy-classes.md) przekazywane jako argument szablonu `ICollectionOnSTLImpl` w specjalizacji.

## <a name="icollectiononstlimplget__newenum"></a><a name="newenum"></a>ICollectionOnSTLImpl::get__NewEnum

Zwraca obiekt wyliczacza dla kolekcji.

```
STDMETHOD(get__NewEnum)(IUnknown** ppUnk);
```

### <a name="parameters"></a>Parametry

*ppUnk (polski)*<br/>
[na zewnątrz] **Wskaźnik IUnknown** nowo utworzonego obiektu wyliczacza.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Nowo utworzony wyliczacz utrzymuje iteratora w `m_coll`oryginalnej kolekcji , (więc nie jest wykonana kopia) i posiada odwołanie COM na obiekt kolekcji, aby upewnić się, że kolekcja pozostaje przy życiu, podczas gdy istnieją wybitne wyliczacze.

## <a name="icollectiononstlimplm_coll"></a><a name="m_coll"></a>ICollectionOnSTLImpl::m_coll

Ten element członkowski przechowuje elementy reprezentowane przez kolekcję.

```
CollType m_coll;
```

## <a name="see-also"></a>Zobacz też

[AtlCollections Przykład](../../overview/visual-cpp-samples.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
