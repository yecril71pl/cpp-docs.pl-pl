---
title: ModuleType — Wyliczenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
ms.openlocfilehash: d822d214d9bad564286cd2c7494c9f480abdcf00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524751"
---
# <a name="moduletype-enumeration"></a>ModuleType — Wyliczenie

Określa, czy moduł powinien obsługiwać wewnątrz procesowego lub serwera spoza procesu.

## <a name="syntax"></a>Składnia

```cpp
enum ModuleType;
```

## <a name="members"></a>Elementy członkowskie

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`InProc`|Serwer usługi w trakcie.|
|`OutOfProc`|Serwer usługi poza procesem.|
|`DisableCaching`|Wyłącz mechanizm buforowania w Module.|
|`InProcDisableCaching`|Kombinacja `InProc` i `DisableCaching`.|
|`OutOfProcDisableCaching`|Kombinacja `OutOfProc` i `DisableCaching`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)