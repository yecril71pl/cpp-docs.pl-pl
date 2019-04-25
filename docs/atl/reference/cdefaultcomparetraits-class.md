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
ms.openlocfilehash: c5f4ab3737838af11501c4a0f2037b57087939c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245923"
---
# <a name="cdefaultcomparetraits-class"></a>Klasa CDefaultCompareTraits

Ta klasa udostępnia domyślny element porównanie funkcji.

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
|[CDefaultCompareTraits::CompareElements](#compareelements)|(Statyczny) Wywołaj tę funkcję, aby porównać dwa elementy pod kątem równości.|
|[CDefaultCompareTraits::CompareElementsOrdered](#compareelementsordered)|(Statyczny) Wywołaj tę funkcję, aby określić większe i mniejsze element.|

## <a name="remarks"></a>Uwagi

Ta klasa zawiera dwie funkcje statyczne do porównywania elementów przechowywanych w obiekcie klasy kolekcji. Ta klasa jest wykorzystywany przez [klasa CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md).

Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

##  <a name="compareelements"></a>  CDefaultCompareTraits::CompareElements

Wywołaj tę funkcję, aby porównać dwa elementy pod kątem równości.

```
static bool CompareElements(const T& element1, const T& element2);
```

### <a name="parameters"></a>Parametry

*element1*<br/>
Pierwszy element.

*element2*<br/>
Drugi element.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli elementy są równe, wartość false w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji jest równości (**==**) — operator. W przypadku obiektów innych niż proste typy danych ta funkcja może być konieczne można zastąpić.

##  <a name="compareelementsordered"></a>  CDefaultCompareTraits::CompareElementsOrdered

Wywołaj tę funkcję, aby określić większe i mniejsze element.

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

Domyślna implementacja tej funkcji używa **==**, **\<**, i **>** operatorów. W przypadku obiektów innych niż proste typy danych ta funkcja może być konieczne można zastąpić.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)
