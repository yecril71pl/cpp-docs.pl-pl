---
title: Klasa CStringElementTraitsI | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI::INARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::OUTARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::CompareElements
- ATLCOLL/ATL::CStringElementTraitsI::CompareElementsOrdered
- ATLCOLL/ATL::CStringElementTraitsI::Hash
dev_langs:
- C++
helpviewer_keywords:
- CStringElementTraitsI class
ms.assetid: c23f92b1-91e5-400f-96ed-258b02622b7a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d34277bd3c9b47c5ba9367d19348e43ea263f43b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089908"
---
# <a name="cstringelementtraitsi-class"></a>Klasa CStringElementTraitsI

Ta klasa dostarcza statyczne funkcje związane z przechowywanych w obiektach klasy kolekcji ciągów. Jest on podobny do [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), ale wykonuje porównania bez uwzględniania wielkości liter.

## <a name="syntax"></a>Składnia

```
template <typename T, class CharTraits = CDefaultCharTraits<T ::XCHAR>>
class CStringElementTraitsI : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych, które mają być przechowywane w kolekcji.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CStringElementTraitsI::INARGTYPE](#inargtype)|Typ danych na potrzeby dodawania elementów do obiektu klasy kolekcji.|
|[CStringElementTraitsI::OUTARGTYPE](#outargtype)|Typ danych używany do pobierania elementów z obiektu klasy kolekcji.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStringElementTraitsI::CompareElements](#compareelements)|Wywołaj tę funkcję statycznej, aby porównać dwa elementy ciągu dla równości, ignorowanie różnic w przypadku.|
|[CStringElementTraitsI::CompareElementsOrdered](#compareelementsordered)|Wywołaj tę funkcję statycznej, aby porównać dwa elementy ciągu, ignorowanie różnic w przypadku.|
|[CStringElementTraitsI::Hash](#hash)|Wywołaj tę funkcję statycznej, aby obliczyć wartość skrótu dla elementu dany ciąg znaków.|

## <a name="remarks"></a>Uwagi

Ta klasa dostarcza statycznej funkcji porównywania ciągów i tworzenia wartość skrótu. Te funkcje są przydatne w przypadku korzystania z klasy kolekcji do przechowywania danych w ciągu. Użyj [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) kiedy mają przy użyciu traktowany jako odwołania do obiektów w postaci ciągów.

Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringElementTraitsI`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

##  <a name="compareelements"></a>  CStringElementTraitsI::CompareElements

Wywołaj tę funkcję statycznej, aby porównać dwa elementy ciągu dla równości, ignorowanie różnic w przypadku.

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy ciąg elementu.

*str2*<br/>
Drugi ciąg elementu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli elementy są równe, wartość false w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Są to porównania bez uwzględniania wielkości liter.

##  <a name="compareelementsordered"></a>  CStringElementTraitsI::CompareElementsOrdered

Wywołaj tę funkcję statycznej, aby porównać dwa elementy ciągu, ignorowanie różnic w przypadku.

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

### <a name="remarks"></a>Uwagi

Są to porównania bez uwzględniania wielkości liter.

##  <a name="hash"></a>  CStringElementTraitsI::Hash

Wywołaj tę funkcję statycznej, aby obliczyć wartość skrótu dla elementu dany ciąg znaków.

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>Parametry

*str*<br/>
Element ciągu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość skrótu obliczane przy użyciu zawartości ciągu.

##  <a name="inargtype"></a>  CStringElementTraitsI::INARGTYPE

Typ danych na potrzeby dodawania elementów do obiektu klasy kolekcji.

```
typedef T::PCXSTR INARGTYPE;
```

##  <a name="outargtype"></a>  CStringElementTraitsI::OUTARGTYPE

Typ danych używany do pobierania elementów z obiektu klasy kolekcji.

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>Zobacz też

[Klasa CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Klasa CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)
