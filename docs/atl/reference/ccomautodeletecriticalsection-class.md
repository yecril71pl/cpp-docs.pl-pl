---
title: Klasa CComAutoDeleteCriticalSection
ms.date: 11/04/2016
f1_keywords:
- CComAutoDeleteCriticalSection
- atlcore/ATL::CComAutoDeleteCriticalSection
helpviewer_keywords:
- CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
ms.openlocfilehash: d479adce489e0329be3a93b55a70aa3e58a0e038
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246661"
---
# <a name="ccomautodeletecriticalsection-class"></a>Klasa CComAutoDeleteCriticalSection

Ta klasa dostarcza metody do uzyskania i zwalniania własności obiektu sekcję krytyczną.

## <a name="syntax"></a>Składnia

```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```

## <a name="remarks"></a>Uwagi

`CComAutoDeleteCriticalSection` pochodzi z klasy [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md). Jednak `CComAutoDeleteCriticalSection` zastępuje [termin](ccomsafedeletecriticalsection-class.md#term) metody **prywatnej** dostępu, co zmusza czyszczenia pamięci wewnętrznej, tylko wtedy, gdy wystąpienia tej klasy wykraczają poza zakres lub jawnie są usuwane z ilość pamięci.

Ta klasa wprowadza żadnych dodatkowych metod za pośrednictwem swojej klasy bazowej. Zobacz [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) i [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) więcej informacji na temat klas pomocniczych sekcję krytyczną.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)

`CComAutoDeleteCriticalSection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore.h

## <a name="see-also"></a>Zobacz także

[Klasa CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)<br/>
[Klasa CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
