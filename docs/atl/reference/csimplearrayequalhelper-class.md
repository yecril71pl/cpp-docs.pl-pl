---
title: Klasa CSimpleArrayEqualHelper
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
ms.openlocfilehash: 386b005777b3e31dd74916a41bc5af2ab82df210
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330882"
---
# <a name="csimplearrayequalhelper-class"></a>Klasa CSimpleArrayEqualHelper

Ta klasa jest pomocnikiem dla [CSimpleArray](../../atl/reference/csimplearray-class.md) klasy.

## <a name="syntax"></a>Składnia

```
template <class T>
class CSimpleArrayEqualHelper
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa pochodna.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleArrayEqualHelper::IsEqual](#isequal)|(Statyczne) Testy `CSimpleArray` dwóch elementów obiektu dla równości.|

## <a name="remarks"></a>Uwagi

Ta klasa cech jest uzupełnieniem `CSimpleArray` klasy. Zapewnia metodę porównywania dwóch elementów `CSimpleArray` przechowywanych w obiekcie. Domyślnie elementy są porównywane przy użyciu **operator=()**, ale jeśli tablica zawiera złożone typy danych, które nie mają własnego operatora równości, należy zastąpić tę klasę.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpcoll.h

## <a name="csimplearrayequalhelperisequal"></a><a name="isequal"></a>CSimpleArrayEqualHelper::IsEqual

Testy `CSimpleArray` dwóch elementów obiektu dla równości.

```
static bool IsEqual(
    const T& t1,
    const T& t2);
```

### <a name="parameters"></a>Parametry

*T1*<br/>
Obiekt typu T.

*t2*<br/>
Obiekt typu T.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli elementy są równe, false inaczej.

## <a name="see-also"></a>Zobacz też

[Klasa CSimpleArray](../../atl/reference/csimplearray-class.md)<br/>
[Klasa CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
