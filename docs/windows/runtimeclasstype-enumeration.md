---
title: RuntimeClassType — Wyliczenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 62a82d5fab9fd22e23a5244d4fda3b7f5202304c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626814"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType — Wyliczenie

Określa typ [RuntimeClass](../windows/runtimeclass-class.md) wystąpienia, która jest obsługiwana.

## <a name="syntax"></a>Składnia

```cpp
enum RuntimeClassType;
```

## <a name="members"></a>Elementy członkowskie

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`ClassicCom`|Klasa klasycznego środowiska uruchomieniowego COM.|
|`Delegate`|Odpowiednikiem `ClassicCom`.|
|`InhibitFtmBase`|Wyłącza `FtmBase` obsługi podczas `__WRL_CONFIGURATION_LEGACY__` nie został zdefiniowany.|
|`InhibitWeakReference`|Wyłącza obsługę słabe odwołanie.|
|`WinRt`|Klasa środowiska wykonawczego Windows.|
|`WinRtClassicComMix`|Kombinacji `WinRt` i `ClassicCom`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)