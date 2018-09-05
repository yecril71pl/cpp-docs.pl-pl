---
title: Klasa CDefaultCompareTraits | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
dev_langs:
- C++
helpviewer_keywords:
- CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4983984c8bf1cad2996818625091b60cdb732a9
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758560"
---
# <a name="cdefaultcomparetraits-class"></a>Klasa CDefaultCompareTraits

Ta klasa udostępnia domyślny element porównanie funkcji.

## <a name="syntax"></a>Składnia

```
template<typename T>  
class CDefaultCompareTraits
```

#### <a name="parameters"></a>Parametry

*T*  
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

*element1*  
Pierwszy element.

*element2*  
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

*element1*  
Pierwszy element.

*element2*  
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

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)
