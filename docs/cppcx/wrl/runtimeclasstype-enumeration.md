---
title: RuntimeClassType — Wyliczenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 80e8a120f7e3666721ff839a2a696388a64d734e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035961"
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

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL — Przestrzeń nazw](microsoft-wrl-namespace.md)