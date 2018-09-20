---
title: Makra ActivatableClass | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ActivatableClass
- ActivatableClassWithFactory
- ActivatableClassWithFactoryEx
dev_langs:
- C++
helpviewer_keywords:
- ActivatableClassWithFactory
- ActivatableClass
- ActivatableClassWithFactoryEx
ms.assetid: 9bd64709-ec2c-4678-8c96-ea5982622bdd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5c97d69bbca685ca64245d5d784452029c14f73f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393635"
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