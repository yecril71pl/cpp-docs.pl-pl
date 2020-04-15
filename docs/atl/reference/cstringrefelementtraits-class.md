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
ms.openlocfilehash: b4dd76b9592b255a1553be3ca7a249f58fb2672e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330584"
---
# <a name="cstringrefelementtraits-class"></a>Klasa CStringRefElementTraits

Ta klasa zawiera funkcje statyczne związane z ciągami przechowywanymi w obiektach klasy kolekcji. Obiekty ciągu są traktowane jako odwołania.

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
|[CStringRefElementTraits::CompareElements](#compareelements)|Wywołanie tej funkcji statycznej, aby porównać dwa elementy ciągu dla równości.|
|[CStringRefElementTraits::CompareElementsOrdered](#compareelementsordered)|Wywołanie tej funkcji statycznej, aby porównać dwa elementy ciągu.|
|[CStringRefElementTraits::Hash](#hash)|Wywołanie tej funkcji statycznej, aby obliczyć wartość mieszania dla danego elementu ciągu.|

## <a name="remarks"></a>Uwagi

Ta klasa zawiera funkcje statyczne do porównywania ciągów i tworzenia wartości mieszania. Te funkcje są przydatne podczas korzystania z klasy kolekcji do przechowywania danych opartych na ciągu. W przeciwieństwie do [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md) i [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md), `CStringRefElementTraits` powoduje, że `CString` argumenty mają być przekazywane jako **const** `CString&` odwołania.

Aby uzyskać więcej informacji, zobacz [ATL Collection Classes](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Baza CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringRefElementTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="cstringrefelementtraitscompareelements"></a><a name="compareelements"></a>CStringRefElementTraits::CompareElements

Wywołanie tej funkcji statycznej, aby porównać dwa elementy ciągu dla równości.

```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```

### <a name="parameters"></a>Parametry

*element1*<br/>
Pierwszy element ciągu.

*element2*<br/>
Drugi element ciągu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli elementy są równe, false inaczej.

## <a name="cstringrefelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a>CStringRefElementTraits::CompareElementsOrdered

Wywołanie tej funkcji statycznej, aby porównać dwa elementy ciągu.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy element ciągu.

*str2*<br/>
Drugi element ciągu.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli ciągi są identyczne, < 0, jeśli *str1* jest mniejsza niż *str2*lub > 0, jeśli *str1* jest większa niż *str2*. [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) Metoda jest używana do wykonywania porównań.

## <a name="cstringrefelementtraitshash"></a><a name="hash"></a>CStringRefElementTraits::Hash

Wywołanie tej funkcji statycznej, aby obliczyć wartość mieszania dla danego elementu ciągu.

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Element ciągu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość mieszania obliczoną przy użyciu zawartości ciągu.

## <a name="see-also"></a>Zobacz też

[Klasa CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
