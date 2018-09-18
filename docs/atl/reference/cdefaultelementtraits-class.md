---
title: Klasa CDefaultElementTraits | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDefaultElementTraits
- atlcoll/ATL::CDefaultElementTraits
dev_langs:
- C++
helpviewer_keywords:
- CDefaultElementTraits class
ms.assetid: ac5ee610-7957-4b7c-92b6-38ff72e4118e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44822df983021846e9b4168343252affd971accd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097279"
---
# <a name="cdefaultelementtraits-class"></a>Klasa CDefaultElementTraits

Ta klasa dostarcza domyślne metody i funkcje dla klas kolekcji.

## <a name="syntax"></a>Składnia

```
template <typename T>
class CDefaultElementTraits : public CElementTraitsBase<T>,
    public CDefaultHashTraits<T>,
    public CDefaultCompareTraits<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych, które mają być przechowywane w kolekcji.

## <a name="remarks"></a>Uwagi

Ta klasa udostępnia domyślną statyczne funkcje i metody, przenoszenie, kopiowanie, porównywanie i wyznaczania wartości skrótu elementów przechowywanych w obiekcie klasy kolekcji. Ta klasa dziedziczy jej funkcje i metody z [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md), [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md), i [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)i jest wykorzystywany przez [ CElementTraits](../../atl/reference/celementtraits-class.md), [CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md), i [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md).

Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)
