---
title: Klasa CElementTraits
ms.date: 11/04/2016
f1_keywords:
- CElementTraits
- atlcoll/ATL::CElementTraits
helpviewer_keywords:
- CElementTraits class
ms.assetid: 496528e5-7f80-4b45-be0c-6f646feb43c5
ms.openlocfilehash: 646b445aed93c9041932c60442f61792f5e1a7e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245771"
---
# <a name="celementtraits-class"></a>Klasa CElementTraits

Ta klasa jest używana przez klasy kolekcji do zapewnienia metod i funkcji przenoszenie, kopiowanie, porównanie i operacje wyznaczania wartości skrótu.

## <a name="syntax"></a>Składnia

```
template<typename T>
class CElementTraits : public CDefaultElementTraits<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych, które mają być przechowywane w kolekcji.

## <a name="remarks"></a>Uwagi

Ta klasa udostępnia domyślną statyczne funkcje i metody, przenoszenie, kopiowanie, porównywanie i wyznaczania wartości skrótu elementów przechowywanych w obiekcie klasy kolekcji. `CElementTraits` jest określony jako domyślnego dostawcę tych operacji przez klasy kolekcji [CAtlArray](../../atl/reference/catlarray-class.md), [CAtlList](../../atl/reference/catllist-class.md), [CRBMap](../../atl/reference/crbmap-class.md), [CRBMultiMap](../../atl/reference/crbmultimap-class.md), i [CRBTree](../../atl/reference/crbtree-class.md).

Domyślna implementacja będzie wystarczająca dla typów prostych danych, ale jeśli klas kolekcji są używane do przechowywania obiektów bardziej złożone, funkcji i metor musi zostać zastąpiona przez implementacje dostarczone przez użytkownika.

Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="see-also"></a>Zobacz także

[Klasa CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
