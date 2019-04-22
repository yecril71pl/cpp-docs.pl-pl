---
title: ICollectionOnSTLImpl Class
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
ms.openlocfilehash: 6842f1c75ebbc9c3dfdd93f30d52fd2cb2936c03
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58779225"
---
# <a name="icollectiononstlimpl-class"></a>ICollectionOnSTLImpl Class

Ta klasa udostępnia metody używane przez klasę kolekcji.

## <a name="syntax"></a>Składnia

```
template <class T, class CollType, class ItemType, class CopyItem, class EnumType>
class ICollectionOnSTLImpl : public T
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Interfejs kolekcji COM.

*CollType*<br/>
Klasa kontenera standardowej biblioteki języka C++.

*ItemType*<br/>
Typ elementu udostępnianych przez interfejs kontenera.

*CopyItem*<br/>
A [kopiowania klasy zasad](../../atl/atl-copy-policy-classes.md).

*EnumType*<br/>
A [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)— klasa zgodna modułu wyliczającego.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ICollectionOnSTLImpl::get__NewEnum](#newenum)|Zwraca obiekt modułu wyliczającego dla kolekcji.|
|[ICollectionOnSTLImpl::getcount](#get_count)|Zwraca liczbę elementów w kolekcji.|
|[ICollectionOnSTLImpl::get_Item](#get_item)|Zwraca żądany element z kolekcji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[ICollectionOnSTLImpl::m_coll](#m_coll)|Kolekcja.|

## <a name="remarks"></a>Uwagi

Ta klasa dostarcza implementację dla trzech metod interfejsu kolekcji: [getcount](#get_count), [metody get_Item](#get_item), i [get__NewEnum](#newenum).

Aby użyć tej klasy:

- Zdefiniuj (lub "pożyczać") to interfejs kolekcji, który chcesz wdrożyć.

- Dziedziczyć klasy specjalizacją `ICollectionOnSTLImpl` oparte na tej kolekcji interfejs.

- Użycie klasy pochodnej w celu wdrożenia dowolnej metody z kolekcji interfejs nie jest obsługiwane przez `ICollectionOnSTLImpl`.

> [!NOTE]
>  Jeśli interfejs kolekcji jest podwójnego interfejsu, pochodzi z klasy [IDispatchImpl](../../atl/reference/idispatchimpl-class.md), przekazując `ICollectionOnSTLImpl` specjalizacji jako pierwszy parametr szablonu chcącym ATL, aby zapewnić wykonania `IDispatch` metody.

- Dodaj elementy do [m_coll](#m_coll) elementu członkowskiego, aby wypełnić kolekcję.

Aby uzyskać więcej informacji i przykładów, zobacz [kolekcje i wyliczenia ATL](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`T`

`ICollectionOnSTLImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="get_count"></a>  ICollectionOnSTLImpl::getcount

Ta metoda zwraca liczbę elementów w kolekcji.

```
STDMETHOD(getcount)(long* pcount);
```

### <a name="parameters"></a>Parametry

*pcount —*<br/>
[out] Liczba elementów w kolekcji.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="get_item"></a>  ICollectionOnSTLImpl::get_Item

Ta metoda zwraca określony element z kolekcji.

```
STDMETHOD(get_Item)(long Index, ItemType* pvar);
```

### <a name="parameters"></a>Parametry

*Index*<br/>
[in] Indeks oparty na 1 element w kolekcji.

*pvar*<br/>
[out] Element odpowiadający *indeksu*.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Element uzyskany przez kopiowanie danych w określonej pozycji w [m_coll](#m_coll) przy użyciu metody kopiowania [kopiowania klasy zasad](../../atl/atl-copy-policy-classes.md) przekazywany jako argument szablonu w `ICollectionOnSTLImpl` specjalizacji.

##  <a name="newenum"></a>  ICollectionOnSTLImpl::get__NewEnum

Zwraca obiekt modułu wyliczającego dla kolekcji.

```
STDMETHOD(get__NewEnum)(IUnknown** ppUnk);
```

### <a name="parameters"></a>Parametry

*ppUnk*<br/>
[out] **IUnknown** wskaźnika obiektu nowo utworzony moduł wyliczający.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Nowo utworzony moduł wyliczający przechowuje iterator w oryginalnej kolekcji `m_coll`, (dlatego kopia nie jest wykonywana) i zawiera odwołanie COM na obiekt kolekcji, aby upewnić się, Kolekcja pozostaje aktywne, gdy istnieją oczekujące modułów wyliczających.

##  <a name="m_coll"></a>  ICollectionOnSTLImpl::m_coll

Ten element członkowski zawiera elementy reprezentowane przez kolekcję.

```
CollType m_coll;
```

## <a name="see-also"></a>Zobacz także

[ATLCollections Sample](../../overview/visual-cpp-samples.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
