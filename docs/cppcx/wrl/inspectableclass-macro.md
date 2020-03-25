---
title: InspectableClass — Makro
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: 755a8f58ffc290d73d6060b0b0924905ecbf6028
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213879"
---
# <a name="inspectableclass-macro"></a>InspectableClass — Makro

Ustawia nazwę klasy środowiska uruchomieniowego i poziom zaufania.

## <a name="syntax"></a>Składnia

```cpp
InspectableClass(
   runtimeClassName,
   trustLevel)
```

### <a name="parameters"></a>Parametry

*runtimeClassName*<br/>
Pełna nazwa tekstowa klasy środowiska uruchomieniowego.

*trustLevel*<br/>
Jedna z [TrustLevel](/windows/win32/api/inspectable/ne-inspectable-trustlevel) wartości.

## <a name="remarks"></a>Uwagi

Makro **InspectableClass** może być używane tylko z typami środowisko wykonawcze systemu Windows.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implementuje. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="see-also"></a>Zobacz też

[RuntimeClass, klasa](runtimeclass-class.md)
