---
title: Klasa CComAutoDeleteCriticalSection
ms.date: 11/04/2016
f1_keywords:
- CComAutoDeleteCriticalSection
- atlcore/ATL::CComAutoDeleteCriticalSection
helpviewer_keywords:
- CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
ms.openlocfilehash: f44dbff7d353cb09142ac742b526d3541e9b2265
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224334"
---
# <a name="ccomautodeletecriticalsection-class"></a>Klasa CComAutoDeleteCriticalSection

Ta klasa zapewnia metody uzyskiwania i zwalniania własności obiektu sekcji krytycznej.

## <a name="syntax"></a>Składnia

```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```

## <a name="remarks"></a>Uwagi

`CComAutoDeleteCriticalSection`pochodzi z klasy [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md). Jednak `CComAutoDeleteCriticalSection` przesłania metodę [terminu](ccomsafedeletecriticalsection-class.md#term) do **`private`** dostępu, która wymusza czyszczenie pamięci wewnętrznej tylko wtedy, gdy wystąpienia tej klasy wykraczają poza zakres lub są jawnie usuwane z pamięci.

Ta klasa nie wprowadza żadnych dodatkowych metod w klasie podstawowej. Aby uzyskać więcej informacji na temat krytycznych klas pomocników sekcji, zobacz [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) i [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)

`CComAutoDeleteCriticalSection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore. h

## <a name="see-also"></a>Zobacz także

[Klasa CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)<br/>
[Klasa CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
