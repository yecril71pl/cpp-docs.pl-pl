---
title: Klasa CComAutoCriticalSection | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff8687783907cb84af36122c5d7828f8845d595d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073463"
---
# <a name="ccomautocriticalsection-class"></a>Klasa CComAutoCriticalSection

`CComAutoCriticalSection` zawiera metody służące do uzyskania i zwalnianie własności obiektu sekcję krytyczną.

## <a name="syntax"></a>Składnia

```
class CComAutoCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|Konstruktor.|
|[CComAutoCriticalSection:: ~ CComAutoCriticalSection](#dtor)|Destruktor.|

## <a name="remarks"></a>Uwagi

`CComAutoCriticalSection` jest podobna do klasy [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md), z wyjątkiem `CComAutoCriticalSection` automatycznie inicjuje obiekt sekcję krytyczną w konstruktorze.

Zazwyczaj można użyć `CComAutoCriticalSection` za pośrednictwem `typedef` nazwa [AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection). Ta nazwa odwołuje się do `CComAutoCriticalSection` podczas [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) jest używana.  

`Init` i `Term` metody z [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) nie są dostępne w przypadku korzystania z tej klasy.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComAutoCriticalSection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore.h

##  <a name="ccomautocriticalsection"></a>  CComAutoCriticalSection::CComAutoCriticalSection

Konstruktor.

```
CComAutoCriticalSection();
```

### <a name="remarks"></a>Uwagi

Wywołuje funkcję Win32 [InitializeCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsection), która inicjuje obiekt sekcję krytyczną.

##  <a name="dtor"></a>  CComAutoCriticalSection:: ~ CComAutoCriticalSection

Destruktor.

```
~CComAutoCriticalSection() throw();
```

### <a name="remarks"></a>Uwagi

Wywołania destruktora [DeleteCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-deletecriticalsection), które zwalnia wszystkie zasoby systemowe używane przez obiekt sekcję krytyczną.

## <a name="see-also"></a>Zobacz też

[Klasa CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Klasa CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)
