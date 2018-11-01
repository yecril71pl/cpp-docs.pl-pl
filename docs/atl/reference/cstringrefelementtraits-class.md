---
title: Klasa CStringRefElementTraits
ms.date: 11/04/2016
f1_keywords:
- CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits::CompareElements
- ATLCOLL/ATL::CStringRefElementTraits::CompareElementsOrdered
- ATLCOLL/ATL::CStringRefElementTraits::Hash
helpviewer_keywords:
- CStringRefElementTraits class
ms.assetid: cc15062d-5627-46cc-ac2b-1744afdc2dbd
ms.openlocfilehash: 86b8db169cbb0f0f43ebf37a8ea9bf959ee0ee06
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633349"
---
# <a name="cstringrefelementtraits-class"></a>Klasa CStringRefElementTraits

Ta klasa dostarcza statyczne funkcje związane z przechowywanych w obiektach klasy kolekcji ciągów. Obiektów w postaci ciągów są traktowane jako odwołania.

## <a name="syntax"></a>Składnia

```
template <typename T>
class CStringRefElementTraits : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych, które mają być przechowywane w kolekcji.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStringRefElementTraits::CompareElements](#compareelements)|Wywołaj tę funkcję statycznej, aby porównać dwa elementy ciągu dla równości.|
|[CStringRefElementTraits::CompareElementsOrdered](#compareelementsordered)|Wywołaj tę funkcję statycznej, aby porównać dwa elementy ciągu.|
|[CStringRefElementTraits::Hash](#hash)|Wywołaj tę funkcję statycznej, aby obliczyć wartość skrótu dla elementu dany ciąg znaków.|

## <a name="remarks"></a>Uwagi

Ta klasa dostarcza statycznej funkcji porównywania ciągów i tworzenia wartość skrótu. Te funkcje są przydatne w przypadku korzystania z klasy kolekcji do przechowywania danych w ciągu. W odróżnieniu od [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md) i [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md), `CStringRefElementTraits` powoduje, że `CString` argumenty do przekazania jako **const** `CString&` odwołania.

Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringRefElementTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

##  <a name="compareelements"></a>  CStringRefElementTraits::CompareElements

Wywołaj tę funkcję statycznej, aby porównać dwa elementy ciągu dla równości.

```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```

### <a name="parameters"></a>Parametry

*element1*<br/>
Pierwszy ciąg elementu.

*element2*<br/>
Drugi ciąg elementu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli elementy są równe, wartość false w przeciwnym razie.

##  <a name="compareelementsordered"></a>  CStringRefElementTraits::CompareElementsOrdered

Wywołaj tę funkcję statycznej, aby porównać dwa elementy ciągu.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy ciąg elementu.

*str2*<br/>
Drugi ciąg elementu.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli ciągi są identyczne, < 0 Jeśli *str1* jest mniejsza niż *str2*, lub > 0 Jeśli *str1* jest większa niż *str2*. [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) metoda służy do przeprowadzania porównania.

##  <a name="hash"></a>  CStringRefElementTraits::Hash

Wywołaj tę funkcję statycznej, aby obliczyć wartość skrótu dla elementu dany ciąg znaków.

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>Parametry

*str*<br/>
Element ciągu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość skrótu obliczane przy użyciu zawartości ciągu.

## <a name="see-also"></a>Zobacz też

[Klasa CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
