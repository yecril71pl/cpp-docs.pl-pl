---
title: Klasa CElementTraits | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CElementTraits
- atlcoll/ATL::CElementTraits
dev_langs:
- C++
helpviewer_keywords:
- CElementTraits class
ms.assetid: 496528e5-7f80-4b45-be0c-6f646feb43c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45139b16ebb923acd004d995cd9466ea9e39e163
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765739"
---
# <a name="celementtraits-class"></a>Klasa CElementTraits

Ta klasa jest używana przez klasy kolekcji do zapewnienia metod i funkcji przenoszenie, kopiowanie, porównanie i operacje wyznaczania wartości skrótu.

## <a name="syntax"></a>Składnia

```
template<typename T>  
class CElementTraits : public CDefaultElementTraits<T>
```

#### <a name="parameters"></a>Parametry

`T`  
Typ danych, które mają być przechowywane w kolekcji.

## <a name="remarks"></a>Uwagi

Ta klasa udostępnia domyślną statyczne funkcje i metody, przenoszenie, kopiowanie, porównywanie i wyznaczania wartości skrótu elementów przechowywanych w obiekcie klasy kolekcji. `CElementTraits` jest określony jako domyślnego dostawcę tych operacji przez klasy kolekcji [CAtlArray](../../atl/reference/catlarray-class.md), [CAtlList](../../atl/reference/catllist-class.md), [CRBMap](../../atl/reference/crbmap-class.md), [CRBMultiMap](../../atl/reference/crbmultimap-class.md), i [CRBTree](../../atl/reference/crbtree-class.md).

Domyślna implementacja będzie wystarczająca dla typów prostych danych, ale jeśli klas kolekcji są używane do przechowywania obiektów bardziej złożone, funkcji i metor musi zostać zastąpiona przez implementacje dostarczone przez użytkownika.

Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="see-also"></a>Zobacz też

[Klasa CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)   
[Klasa — Przegląd](../../atl/atl-class-overview.md)
