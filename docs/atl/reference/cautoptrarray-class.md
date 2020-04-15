---
title: Klasa CAutoPtrArray
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
helpviewer_keywords:
- CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
ms.openlocfilehash: 93fc5cfea4ea655e57e785ca234df59fe10d6570
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318895"
---
# <a name="cautoptrarray-class"></a>Klasa CAutoPtrArray

Ta klasa zawiera metody przydatne podczas konstruowania tablicy inteligentnych wskaźników.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <typename E>
class CAutoPtrArray : public CAtlArray<
                        ATL::CAutoPtr<E>,
                        CAutoPtrElementTraits<E>>
```

#### <a name="parameters"></a>Parametry

*E*<br/>
Typ wskaźnika.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAutoPtrArray::CAutoPtrArray](#cautoptrarray)|Konstruktor.|

## <a name="remarks"></a>Uwagi

Ta klasa udostępnia konstruktora i wyprowadza metody z [CAtlArray](../../atl/reference/catlarray-class.md) i [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) do tworzenia obiektu klasy kolekcji przechowywania inteligentnych wskaźników.

Aby uzyskać więcej informacji, zobacz [ATL Collection Classes](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CAtlArray`

`CAutoPtrArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="cautoptrarraycautoptrarray"></a><a name="cautoptrarray"></a>CAutoPtrArray::CAutoPtrArray

Konstruktor.

```
CAutoPtrArray() throw();
```

### <a name="remarks"></a>Uwagi

Inicjuje tablicę inteligentnych wskaźników.

## <a name="see-also"></a>Zobacz też

[Klasa CAtlArray](../../atl/reference/catlarray-class.md)<br/>
[Klasa CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[Klasa CAutoPtrList](../../atl/reference/cautoptrlist-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
