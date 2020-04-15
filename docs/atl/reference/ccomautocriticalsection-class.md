---
title: Klasa CComAutoCriticalSekcja
ms.date: 11/04/2016
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
ms.openlocfilehash: 8cbf08082fd24ef2cf0e8794e2944a799baec084
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321089"
---
# <a name="ccomautocriticalsection-class"></a>Klasa CComAutoCriticalSekcja

`CComAutoCriticalSection`zawiera metody uzyskiwania i zwalniania własności obiektu sekcji krytycznej.

## <a name="syntax"></a>Składnia

```
class CComAutoCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComAutoCriticalSekcja::CComAutoCriticalSekcja](#ccomautocriticalsection)|Konstruktor.|
|[CComAutoCriticalSekcja::~CComAutoCriticalSekcja](#dtor)|Destruktor.|

## <a name="remarks"></a>Uwagi

`CComAutoCriticalSection`jest podobny do klasy [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md), z wyjątkiem `CComAutoCriticalSection` automatycznego inicjowania obiektu sekcji krytycznej w konstruktorze.

Zazwyczaj można używać `CComAutoCriticalSection` za `typedef` pomocą nazwy [AutoCriticalSekcja](ccommultithreadmodel-class.md#autocriticalsection). Ta nazwa `CComAutoCriticalSection` odwołuje się, gdy [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) jest używany.

I `Init` `Term` metody z [CComCriticalSekcja](../../atl/reference/ccomcriticalsection-class.md) nie są dostępne podczas korzystania z tej klasy.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Ccomcriticalsection](../../atl/reference/ccomcriticalsection-class.md)

`CComAutoCriticalSection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore.h

## <a name="ccomautocriticalsectionccomautocriticalsection"></a><a name="ccomautocriticalsection"></a>CComAutoCriticalSekcja::CComAutoCriticalSekcja

Konstruktor.

```
CComAutoCriticalSection();
```

### <a name="remarks"></a>Uwagi

Wywołuje funkcję Win32 [InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection), która inicjuje obiekt sekcji krytycznej.

## <a name="ccomautocriticalsectionccomautocriticalsection"></a><a name="dtor"></a>CComAutoCriticalSekcja::~CComAutoCriticalSekcja

Destruktor.

```
~CComAutoCriticalSection() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor wywołuje [DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection), który zwalnia wszystkie zasoby systemowe używane przez obiekt sekcji krytycznej.

## <a name="see-also"></a>Zobacz też

[CComFakeCriticalKuction Klasa](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa CComCriticalSekcja](../../atl/reference/ccomcriticalsection-class.md)
