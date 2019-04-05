---
title: FactoryCacheFlags — Wyliczenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
ms.openlocfilehash: 8cf4af2ac0b4557fc6b175b84c47f83dd8a6e4ba
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037448"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags — Wyliczenie

Określa, czy obiekty są buforowane.

## <a name="syntax"></a>Składnia

```cpp
enum FactoryCacheFlags;
```

## <a name="remarks"></a>Uwagi

Domyślnie fabryki zasady buforowania jest określony jako [ModuleType](moduletype-enumeration.md) parametru szablonu podczas tworzenia [modułu](module-class.md) obiektu. Aby zastąpić te zasady, należy określić **FactoryCacheFlags** wartości podczas tworzenia obiektu fabryki.

|||
|-|-|
|`FactoryCacheDefault`|Zasady buforowania `Module` obiekt jest używany.|
|`FactoryCacheEnabled`|Włącza buforowanie fabryki, niezależnie od wartości `ModuleType` parametr szablonu, który jest używany do tworzenia `Module` obiektu.|
|`FactoryCacheDisabled`|Wyłącza buforowanie fabryki, niezależnie od wartości `ModuleType` parametr szablonu, który jest używany do tworzenia `Module` obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL — Przestrzeń nazw](microsoft-wrl-namespace.md)