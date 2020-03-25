---
title: FactoryCacheFlags — Wyliczenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
ms.openlocfilehash: 250c8c8e7ade72bd1a9cd63f0b515774058f0723
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214009"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags — Wyliczenie

Określa, czy obiekty fabryki są buforowane.

## <a name="syntax"></a>Składnia

```cpp
enum FactoryCacheFlags;
```

## <a name="remarks"></a>Uwagi

Domyślnie zasady buforowania fabryki są określane jako parametr szablonu [ModuleType](moduletype-enumeration.md) podczas tworzenia obiektu [modułu](module-class.md) . Aby zastąpić te zasady, określ wartość **FactoryCacheFlags** podczas tworzenia obiektu fabryki.

|||
|-|-|
|`FactoryCacheDefault`|Używane są zasady buforowania obiektu `Module`.|
|`FactoryCacheEnabled`|Włącza buforowanie fabryki niezależnie od parametru `ModuleType` szablonu, który jest używany do tworzenia obiektu `Module`.|
|`FactoryCacheDisabled`|Wyłącza buforowanie fabryki niezależnie od parametru `ModuleType` szablonu, który jest używany do tworzenia obiektu `Module`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** implementuje. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)
