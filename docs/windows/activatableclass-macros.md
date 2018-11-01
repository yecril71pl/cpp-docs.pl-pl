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
ms.openlocfilehash: 1b50d9ba59ef8aebe4eca388ee30449f4ddd53de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660671"
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

## <a name="see-also"></a>Zobacz też

[Klasa modułu](../windows/module-class.md)