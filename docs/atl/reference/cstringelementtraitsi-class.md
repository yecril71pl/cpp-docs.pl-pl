---
title: Klasa CStringElementTraitsI
ms.date: 11/04/2016
f1_keywords:
- CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI::INARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::OUTARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::CompareElements
- ATLCOLL/ATL::CStringElementTraitsI::CompareElementsOrdered
- ATLCOLL/ATL::CStringElementTraitsI::Hash
helpviewer_keywords:
- CStringElementTraitsI class
ms.assetid: c23f92b1-91e5-400f-96ed-258b02622b7a
ms.openlocfilehash: 32980e19443cb17a3a688c85ff21195c60ed2124
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330590"
---
# <a name="cstringelementtraitsi-class"></a>Klasa CStringElementTraitsI

Ta klasa zawiera funkcje statyczne związane z ciągami przechowywanymi w obiektach klasy kolekcji. Jest podobny do [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), ale wykonuje porównania bez uwzględniania wielkości liter.

## <a name="syntax"></a>Składnia

```
template <typename T, class CharTraits = CDefaultCharTraits<T ::XCHAR>>
class CStringElementTraitsI : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych, które mają być przechowywane w kolekcji.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|[CStringElementTraitsI::INARGTYPE](#inargtype)|Typ danych do dodania elementów do obiektu klasy kolekcji.|
|[CStringElementTraitsI::OUTARGTYPE](#outargtype)|Typ danych do użycia do pobierania elementów z obiektu klasy kolekcji.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStringElementTraitsI::CompareElements](#compareelements)|Wywołanie tej funkcji statycznej, aby porównać dwa elementy ciągu dla równości, ignorując różnice w przypadku.|
|[CStringElementTraitsI::CompareElementsOrdered](#compareelementsordered)|Wywołanie tej funkcji statycznej, aby porównać dwa elementy ciągu, ignorując różnice w przypadku.|
|[CStringElementTraitsI::Hash](#hash)|Wywołanie tej funkcji statycznej, aby obliczyć wartość mieszania dla danego elementu ciągu.|

## <a name="remarks"></a>Uwagi

Ta klasa zawiera funkcje statyczne do porównywania ciągów i tworzenia wartości mieszania. Te funkcje są przydatne podczas korzystania z klasy kolekcji do przechowywania danych opartych na ciągu. Użyj [CStringRefElementTraits,](../../atl/reference/cstringrefelementtraits-class.md) gdy obiekty ciągu mają być traktowane jako odwołania.

Aby uzyskać więcej informacji, zobacz [ATL Collection Classes](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Baza CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringElementTraitsI`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="cstringelementtraitsicompareelements"></a><a name="compareelements"></a>CStringElementTraitsI::CompareElements

Wywołanie tej funkcji statycznej, aby porównać dwa elementy ciągu dla równości, ignorując różnice w przypadku.

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy element ciągu.

*str2*<br/>
Drugi element ciągu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli elementy są równe, false inaczej.

### <a name="remarks"></a>Uwagi

Porównania są niewrażliwe na wielkości liter.

## <a name="cstringelementtraitsicompareelementsordered"></a><a name="compareelementsordered"></a>CStringElementTraitsI::CompareElementsOrdered

Wywołanie tej funkcji statycznej, aby porównać dwa elementy ciągu, ignorując różnice w przypadku.

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

### <a name="remarks"></a>Uwagi

Porównania są niewrażliwe na wielkości liter.

## <a name="cstringelementtraitsihash"></a><a name="hash"></a>CStringElementTraitsI::Hash

Wywołanie tej funkcji statycznej, aby obliczyć wartość mieszania dla danego elementu ciągu.

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Element ciągu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość mieszania obliczoną przy użyciu zawartości ciągu.

## <a name="cstringelementtraitsiinargtype"></a><a name="inargtype"></a>CStringElementTraitsI::INARGTYPE

Typ danych do dodania elementów do obiektu klasy kolekcji.

```
typedef T::PCXSTR INARGTYPE;
```

## <a name="cstringelementtraitsioutargtype"></a><a name="outargtype"></a>CStringElementTraitsI::OUTARGTYPE

Typ danych do użycia do pobierania elementów z obiektu klasy kolekcji.

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>Zobacz też

[Klasa CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)
