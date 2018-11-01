---
title: Klasa CComFakeCriticalSection
ms.date: 11/04/2016
f1_keywords:
- CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection::Init
- ATLCORE/ATL::CComFakeCriticalSection::Lock
- ATLCORE/ATL::CComFakeCriticalSection::Term
- ATLCORE/ATL::CComFakeCriticalSection::Unlock
helpviewer_keywords:
- CComFakeCriticalSection class
ms.assetid: a4811b97-96bb-493b-ab9f-62822aeddb10
ms.openlocfilehash: cf2408afb70dd6e2be27e22605f46b51b75ad602
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519395"
---
# <a name="ccomfakecriticalsection-class"></a>Klasa CComFakeCriticalSection

Ta klasa udostępnia te same metody jako [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) , ale nie zapewnia sekcję krytyczną.

## <a name="syntax"></a>Składnia

```
class CComFakeCriticalSection
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComFakeCriticalSection::Init](#init)|Nie działają, ponieważ nie istnieje żadna sekcja krytycznego.|
|[CComFakeCriticalSection::Lock](#lock)|Nie działają, ponieważ nie istnieje żadna sekcja krytycznego.|
|[CComFakeCriticalSection::Term](#term)|Nie działają, ponieważ nie istnieje żadna sekcja krytycznego.|
|[CComFakeCriticalSection::Unlock](#unlock)|Nie działają, ponieważ nie istnieje żadna sekcja krytycznego.|

## <a name="remarks"></a>Uwagi

`CComFakeCriticalSection` odzwierciedla metod w [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Jednak `CComFakeCriticalSection` nie zawiera sekcję krytyczną; w związku z tym, nic nie rób jej metody.

Zazwyczaj można użyć `CComFakeCriticalSection` za pośrednictwem `typedef` nazwę albo `AutoCriticalSection` lub `CriticalSection`. Korzystając z [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) lub [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), oba te `typedef` nazwy odwołania `CComFakeCriticalSection`. Korzystając z [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), mogą odwoływać się do [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md) i `CComCriticalSection`, odpowiednio.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore.h

##  <a name="init"></a>  CComFakeCriticalSection::Init

Nie działają, ponieważ nie istnieje żadna sekcja krytycznego.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK.

##  <a name="lock"></a>  CComFakeCriticalSection::Lock

Nie działają, ponieważ nie istnieje żadna sekcja krytycznego.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK.

##  <a name="term"></a>  CComFakeCriticalSection::Term

Nie działają, ponieważ nie istnieje żadna sekcja krytycznego.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK.

##  <a name="unlock"></a>  CComFakeCriticalSection::Unlock

Nie działają, ponieważ nie istnieje żadna sekcja krytycznego.

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)
