---
title: Klasa CSimpleArrayEqualHelperFalse
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
ms.openlocfilehash: 5eca3145d64895e34b599fbf83834af142b65973
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330895"
---
# <a name="csimplearrayequalhelperfalse-class"></a>Klasa CSimpleArrayEqualHelperFalse

Ta klasa jest pomocnikiem dla [CSimpleArray](../../atl/reference/csimplearray-class.md) klasy.

## <a name="syntax"></a>Składnia

```
template <class T>
class CSimpleArrayEqualHelperFalse
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa pochodna.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleArrayEqualHelperFalse::IsEqual](#isequal)|(Statyczne) Zwraca wartość false.|

## <a name="remarks"></a>Uwagi

Ta klasa cech jest uzupełnieniem `CSimpleArray` klasy. Zawsze zwraca false, a ponadto `ATLASSERT` wywoła argument false, jeśli kiedykolwiek odwołuje się. W sytuacjach, gdy test równości nie jest wystarczająco zdefiniowany, ta klasa umożliwia tablicy zawierającej elementy działać poprawnie dla większości metod, ale nie w sposób dobrze zdefiniowany dla metod, które zależą od porównań, takich jak [CSimpleArray::Find](../../atl/reference/csimplearray-class.md#find).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpcoll.h

## <a name="csimplearrayequalhelperfalseisequal"></a><a name="isequal"></a>CSimpleArrayEqualHelperFalse::IsEqual

Zwraca wartość false.

```
static bool IsEqual(const T&, const T&);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość false.

### <a name="remarks"></a>Uwagi

Ta metoda zawsze zwraca false `ATLASSERT` i wywoła argument false, jeśli odwołuje się. Celem jest `CSimpleArrayEqualHelperFalse::IsEqual` wymuszenie użycia porównań w sposób dobrze zdefiniowany, gdy testy równości nie zostały odpowiednio zdefiniowane.

## <a name="see-also"></a>Zobacz też

[Klasa CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
