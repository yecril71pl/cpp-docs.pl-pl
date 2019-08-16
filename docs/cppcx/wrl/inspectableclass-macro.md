---
title: InspectableClass — Makro
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: ee2a76edb967923a03ce6720b4163baf1cc48c32
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500474"
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

**Obszaru** Microsoft:: WRL

## <a name="see-also"></a>Zobacz także

[RuntimeClass, klasa](runtimeclass-class.md)