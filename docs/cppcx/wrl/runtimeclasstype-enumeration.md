---
title: RuntimeClassType — Wyliczenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 53f0172968c28762bb1305e274bbd47494cdaf4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213580"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType — Wyliczenie

Określa typ wystąpienia [RuntimeClass](runtimeclass-class.md) , które jest obsługiwane.

## <a name="syntax"></a>Składnia

```cpp
enum RuntimeClassType;
```

## <a name="members"></a>Members

### <a name="values"></a>Wartości

|Name (Nazwa)|Opis|
|----------|-----------------|
|`ClassicCom`|Klasyczna Klasa środowiska uruchomieniowego COM.|
|`Delegate`|Równoważne `ClassicCom`.|
|`InhibitFtmBase`|Wyłącza obsługę `FtmBase`, gdy `__WRL_CONFIGURATION_LEGACY__` nie jest zdefiniowany.|
|`InhibitWeakReference`|Wyłącza obsługę słabej referencji.|
|`WinRt`|Klasa środowisko wykonawcze systemu Windows.|
|`WinRtClassicComMix`|Kombinacja `WinRt` i `ClassicCom`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** implementuje. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)
