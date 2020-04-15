---
title: CComFakeCriticalKuction Klasa
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
ms.openlocfilehash: 4a5b9ba3551397a9c3d59a343e9c6b55b1c1207e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327850"
---
# <a name="ccomfakecriticalsection-class"></a>CComFakeCriticalKuction Klasa

Ta klasa zawiera te same metody co [CComCriticalSection,](../../atl/reference/ccomcriticalsection-class.md) ale nie zapewnia sekcji krytycznej.

## <a name="syntax"></a>Składnia

```
class CComFakeCriticalSection
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComFakeCriticalSekcja::Init](#init)|Nic nie robi, ponieważ nie ma sekcji krytycznej.|
|[CComFakeCriticalSekcja::Lock](#lock)|Nic nie robi, ponieważ nie ma sekcji krytycznej.|
|[CComFakeCriticalSekcja::Termin](#term)|Nic nie robi, ponieważ nie ma sekcji krytycznej.|
|[CComFakeCriticalSekcja::Odblokuj](#unlock)|Nic nie robi, ponieważ nie ma sekcji krytycznej.|

## <a name="remarks"></a>Uwagi

`CComFakeCriticalSection`odzwierciedla metody znalezione w [CComCriticalSekcja](../../atl/reference/ccomcriticalsection-class.md). Jednak `CComFakeCriticalSection` nie zapewnia sekcji krytycznej; dlatego jego metody nic nie robią.

`CComFakeCriticalSection` Zazwyczaj używa się za `typedef` pomocą nazwy, albo `AutoCriticalSection` lub `CriticalSection`. W przypadku korzystania [z CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) lub [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), obie te `typedef` nazwy odwołują się . `CComFakeCriticalSection` Podczas korzystania [z CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), odnoszą [się one CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md) i `CComCriticalSection`, odpowiednio.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore.h

## <a name="ccomfakecriticalsectioninit"></a><a name="init"></a>CComFakeCriticalSekcja::Init

Nic nie robi, ponieważ nie ma sekcji krytycznej.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

## <a name="ccomfakecriticalsectionlock"></a><a name="lock"></a>CComFakeCriticalSekcja::Lock

Nic nie robi, ponieważ nie ma sekcji krytycznej.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

## <a name="ccomfakecriticalsectionterm"></a><a name="term"></a>CComFakeCriticalSekcja::Termin

Nic nie robi, ponieważ nie ma sekcji krytycznej.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

## <a name="ccomfakecriticalsectionunlock"></a><a name="unlock"></a>CComFakeCriticalSekcja::Odblokuj

Nic nie robi, ponieważ nie ma sekcji krytycznej.

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
