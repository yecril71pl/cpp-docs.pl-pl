---
title: Klasa CDefaultHashTraits
ms.date: 11/04/2016
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
helpviewer_keywords:
- CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
ms.openlocfilehash: c8896ce27afc40ad095e02a2453628ffc05900da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466147"
---
# <a name="cdefaulthashtraits-class"></a>Klasa CDefaultHashTraits

Ta klasa udostępnia funkcję statyczną do obliczania wartości skrótu.

## <a name="syntax"></a>Składnia

```
template<typename T>
class CDefaultHashTraits
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych, które mają być przechowywane w kolekcji.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDefaultHashTraits::Hash](#hash)|(Statyczny) Wywołaj tę funkcję, aby obliczyć wartość skrótu dla danego elementu.|

## <a name="remarks"></a>Uwagi

Ta klasa zawiera pojedynczy funkcję statyczną, która zwraca wartość skrótu dla danego elementu. Ta klasa jest wykorzystywany przez [klasa CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md).

Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

##  <a name="hash"></a>  CDefaultHashTraits::Hash

Wywołaj tę funkcję, aby obliczyć wartość skrótu dla danego elementu.

```
static ULONG Hash(const T& element) throw();
```

### <a name="parameters"></a>Parametry

*Element*<br/>
Element.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość skrótu.

### <a name="remarks"></a>Uwagi

Wartość domyślna algorytmem wyznaczania wartości skrótu jest bardzo prosta: wartość zwracana jest liczba elementów. Należy przesłonić tę funkcję, jeśli wymagane jest bardziej skomplikowany algorytmu.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)
