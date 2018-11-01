---
title: FactoryCacheFlags — Wyliczenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
ms.openlocfilehash: 8320563991981f7a49d4775a2bad9c487124d907
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595653"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags — Wyliczenie

Określa, czy obiekty są buforowane.

## <a name="syntax"></a>Składnia

```cpp
enum FactoryCacheFlags;
```

## <a name="remarks"></a>Uwagi

Domyślnie fabryki zasady buforowania jest określony jako [ModuleType](../windows/moduletype-enumeration.md) parametru szablonu podczas tworzenia [modułu](../windows/module-class.md) obiektu. Aby zastąpić te zasady, należy określić **FactoryCacheFlags** wartości podczas tworzenia obiektu fabryki.

|||
|-|-|
|`FactoryCacheDefault`|Zasady buforowania `Module` obiekt jest używany.|
|`FactoryCacheEnabled`|Włącza buforowanie fabryki, niezależnie od wartości `ModuleType` parametr szablonu, który jest używany do tworzenia `Module` obiektu.|
|`FactoryCacheDisabled`|Wyłącza buforowanie fabryki, niezależnie od wartości `ModuleType` parametr szablonu, który jest używany do tworzenia `Module` obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)