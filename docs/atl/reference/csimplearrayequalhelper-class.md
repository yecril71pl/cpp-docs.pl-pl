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
ms.openlocfilehash: 8b7e32ddab5b2f0667b17b0f127ac2e7e5d9a426
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293254"
---
# <a name="csimplearrayequalhelper-class"></a>Klasa CSimpleArrayEqualHelper

Ta klasa jest pomocnika dla [CSimpleArray](../../atl/reference/csimplearray-class.md) klasy.

## <a name="syntax"></a>Składnia

```
template <class T>
class CSimpleArrayEqualHelper
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasy pochodnej.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleArrayEqualHelper::IsEqual](#isequal)|(Statyczny) Testuje dwa `CSimpleArray` obiektu elementy pod kątem równości.|

## <a name="remarks"></a>Uwagi

Ta klasa cech jest uzupełnieniem `CSimpleArray` klasy. Zapewnia metodę porównywania dwóch elementów przechowywanych w `CSimpleArray` obiektu. Domyślnie elementy są porównywane za pomocą **operator=()**, ale jeśli tablica zawiera złożone typy danych, które nie mają własne operator równości, trzeba będzie zastąpić tę klasę.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpcoll.h

##  <a name="isequal"></a>  CSimpleArrayEqualHelper::IsEqual

Testuje dwa `CSimpleArray` obiektu elementy pod kątem równości.

```
static bool IsEqual(
    const T& t1,
    const T& t2);
```

### <a name="parameters"></a>Parametry

*t1*<br/>
Obiekt typu T.

*t2*<br/>
Obiekt typu T.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli elementy są równe, wartość false w przeciwnym razie.

## <a name="see-also"></a>Zobacz także

[Klasa CSimpleArray](../../atl/reference/csimplearray-class.md)<br/>
[Klasa CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
