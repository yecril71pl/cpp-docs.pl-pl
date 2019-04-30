---
title: ModuleType — Wyliczenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
ms.openlocfilehash: 3c7486cbc761975dd133f229f23dcf0b70e7e3ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403233"
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

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)