---
title: Runtimeclasstype — wyliczenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a3358455755ec4c00ebea85fc13fe0022c7b6697
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595457"
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