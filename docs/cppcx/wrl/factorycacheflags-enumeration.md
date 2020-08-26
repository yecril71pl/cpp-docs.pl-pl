---
title: FactoryCacheFlags — Wyliczenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
ms.openlocfilehash: 3381b2bcfcbf298270b547199ae614291855a2f7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843277"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags — Wyliczenie

Określa, czy obiekty fabryki są buforowane.

## <a name="syntax"></a>Składnia

```cpp
enum FactoryCacheFlags;
```

## <a name="remarks"></a>Uwagi

Domyślnie zasady buforowania fabryki są określane jako parametr szablonu [ModuleType](moduletype-enumeration.md) podczas tworzenia obiektu [modułu](module-class.md) . Aby zastąpić te zasady, określ wartość **FactoryCacheFlags** podczas tworzenia obiektu fabryki.

| Zasady | Opis |
|-|-|
|`FactoryCacheDefault`|`Module`Używane są zasady buforowania obiektu.|
|`FactoryCacheEnabled`|Włącza buforowanie fabryki niezależnie od `ModuleType` parametru szablonu, który jest używany do tworzenia `Module` obiektu.|
|`FactoryCacheDisabled`|Wyłącza buforowanie fabryki niezależnie od `ModuleType` parametru szablonu, który jest używany do tworzenia `Module` obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** implementuje. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="see-also"></a>Zobacz też

[Microsoft:: WRL, przestrzeń nazw](microsoft-wrl-namespace.md)
