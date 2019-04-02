---
title: RuntimeClassType — Wyliczenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 3b869be00cdc405569b82bdf3730f8d4ca4f3aab
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787517"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType — Wyliczenie

Określa typ [RuntimeClass](runtimeclass-class.md) wystąpienia, która jest obsługiwana.

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

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)