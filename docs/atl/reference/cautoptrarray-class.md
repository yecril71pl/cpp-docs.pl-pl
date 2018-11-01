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
ms.openlocfilehash: c7a2a7e9592b120204582334f69e27e72cd7364f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677945"
---
# <a name="cautoptrarray-class"></a>Klasa CAutoPtrArray

Ta klasa dostarcza metody przydatne przy konstruowaniu tablicy inteligentnych wskaźników.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

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

Ta klasa zawiera konstruktora i pochodzi z metody z [CAtlArray](../../atl/reference/catlarray-class.md) i [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) ułatwiające tworzenie obiektu klasy kolekcji przechowywania inteligentnych wskaźników.

Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CAtlArray`

`CAutoPtrArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

##  <a name="cautoptrarray"></a>  CAutoPtrArray::CAutoPtrArray

Konstruktor.

```
CAutoPtrArray() throw();
```

### <a name="remarks"></a>Uwagi

Inicjuje tablicę inteligentnego wskaźnika.

## <a name="see-also"></a>Zobacz też

[Klasa CAtlArray](../../atl/reference/catlarray-class.md)<br/>
[Klasa CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[Klasa CAutoPtrList](../../atl/reference/cautoptrlist-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
