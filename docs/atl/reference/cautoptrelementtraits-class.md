---
title: Klasa CAutoPtrElementTraits | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoPtrElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtrElementTraits class
ms.assetid: 777c1b14-6ab7-491f-b9a5-be149e71d4a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f406415afab907b7b00d75e52dce1fcac7166fd5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021086"
---
# <a name="cautoptrelementtraits-class"></a>Klasa CAutoPtrElementTraits

Ta klasa dostarcza metody, funkcje statyczne i definicje typów przydatne podczas tworzenia kolekcji inteligentnych wskaźników.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template<typename T>
class CAutoPtrElementTraits
    : public CDefaultElementTraits<ATL::CAutoPtr<T>>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ wskaźnika.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CAutoPtrElementTraits::INARGTYPE](#inargtype)|Typ danych na potrzeby dodawania elementów do obiektu klasy kolekcji.|
|[CAutoPtrElementTraits::OUTARGTYPE](#outargtype)|Typ danych używany do pobierania elementów z obiektu klasy kolekcji.|

## <a name="remarks"></a>Uwagi

Ta klasa dostarcza metody, funkcje statyczne i definicje typów dla łatwiejszemu tworzenia typów obiektów klas kolekcji zawierających inteligentnych wskaźników. Klasy [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) i [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) dziedziczyć `CAutoPtrElementTraits`. Jeśli tworzenie kolekcji inteligentnych wskaźników, który wymaga nowy wektor i delete, operatory, należy użyć [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) zamiast tego.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoPtrElementTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

##  <a name="inargtype"></a>  CAutoPtrElementTraits::INARGTYPE

Typ danych na potrzeby dodawania elementów do obiektu klasy kolekcji.

```
typedef CAutoPtr<T>& INARGTYPE;
```

##  <a name="outargtype"></a>  CAutoPtrElementTraits::OUTARGTYPE

Typ danych używany do pobierania elementów z obiektu klasy kolekcji.

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>Zobacz też

[Klasa CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
