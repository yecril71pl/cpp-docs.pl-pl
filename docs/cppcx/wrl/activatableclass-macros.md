---
title: ActivatableClass Makra
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ActivatableClass
- ActivatableClassWithFactory
- ActivatableClassWithFactoryEx
helpviewer_keywords:
- ActivatableClassWithFactory
- ActivatableClass
- ActivatableClassWithFactoryEx
ms.assetid: 9bd64709-ec2c-4678-8c96-ea5982622bdd
ms.openlocfilehash: 7d38db9e7d3fa94c89195b6379e14692f26f7ee5
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037597"
---
# <a name="activatableclass-macros"></a>ActivatableClass Makra

Wypełnia wewnętrzną pamięć podręczną zawierającą fabryki, który można utworzyć wystąpienie określonej klasy.

## <a name="syntax"></a>Składnia

```cpp
ActivatableClass(
   className
);

ActivatableClassWithFactory(
   className,
   factory
);

ActivatableClassWithFactoryEx(
   className,
   factory,
   serverName
);
```

### <a name="parameters"></a>Parametry

*className*<br/>
Nazwa klasy w celu utworzenia.

*Fabryka*<br/>
Fabryka, który utworzy wystąpienie określonej klasy.

*serverName*<br/>
Nazwa, która określa podzestaw fabryk w module.

## <a name="remarks"></a>Uwagi

Nie należy używać tych makr z klasycznego modelu COM, chyba że używasz `#undef` dyrektywy, aby upewnić się, że `__WRL_WINRT_STRICT__` definicji makra zostanie usunięty.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz także

[Klasa modułu](module-class.md)