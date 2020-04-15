---
title: Klasa CDefaultCompareTraits
ms.date: 11/04/2016
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
helpviewer_keywords:
- CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
ms.openlocfilehash: 8262800ef613424c37c53931d97dd4b1b1a71321
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327073"
---
# <a name="cdefaultcomparetraits-class"></a>Klasa CDefaultCompareTraits

Ta klasa zawiera domyślne funkcje porównywania elementów.

## <a name="syntax"></a>Składnia

```
template<typename T>
class CDefaultCompareTraits
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych, które mają być przechowywane w kolekcji.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDefaultCompareTraits::CompareElements](#compareelements)|(Statyczne) Wywołanie tej funkcji, aby porównać dwa elementy równości.|
|[CDefaultCompareTraits::CompareElementsOrdered](#compareelementsordered)|(Statyczne) Wywołanie tej funkcji, aby określić większy i mniejszy element.|

## <a name="remarks"></a>Uwagi

Ta klasa zawiera dwie funkcje statyczne do porównywania elementów przechowywanych w obiekcie klasy kolekcji. Ta klasa jest wykorzystywana przez [CDefaultElementTraits Klasy](../../atl/reference/cdefaultelementtraits-class.md).

Aby uzyskać więcej informacji, zobacz [ATL Collection Classes](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="cdefaultcomparetraitscompareelements"></a><a name="compareelements"></a>CDefaultCompareTraits::CompareElements

Wywołanie tej funkcji, aby porównać dwa elementy równości.

```
static bool CompareElements(const T& element1, const T& element2);
```

### <a name="parameters"></a>Parametry

*element1*<br/>
Pierwszy element.

*element2*<br/>
Drugi element.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli elementy są równe, false inaczej.

### <a name="remarks"></a>Uwagi

Domyślną implementacją tej funkcji**==** jest operator równości ( ). W przypadku obiektów innych niż proste typy danych ta funkcja może wymagać zastąpienia.

## <a name="cdefaultcomparetraitscompareelementsordered"></a><a name="compareelementsordered"></a>CDefaultCompareTraits::CompareElementsOrdered

Wywołanie tej funkcji, aby określić większy i mniejszy element.

```
static int CompareElementsOrdered(const T& element1, const T& element2);
```

### <a name="parameters"></a>Parametry

*element1*<br/>
Pierwszy element.

*element2*<br/>
Drugi element.

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę całkowitą na podstawie poniższej tabeli:

|Warunek|Wartość zwracana|
|---------------|------------------|
|*element1* < *element2*|<0|
|*element1* == *element2*|0|
|*element1* > *element2*|>0|

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji **==** **\<** używa **>** funkcji , i operatorów. W przypadku obiektów innych niż proste typy danych ta funkcja może wymagać zastąpienia.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
