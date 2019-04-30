---
title: InspectableClass — Makro
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: 9d194f5a87ac4a142301bc896cb3ed172f119473
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398199"
---
# <a name="inspectableclass-macro"></a>InspectableClass — Makro

Ustawia poziom nazwy i zaufania klasy środowiska uruchomieniowego.

## <a name="syntax"></a>Składnia

```cpp
InspectableClass(
   runtimeClassName,
   trustLevel)
```

### <a name="parameters"></a>Parametry

*runtimeClassName*<br/>
Pełna tekstowa Nazwa klasy runtime.

*trustLevel*<br/>
Jedną z [TrustLevel](/windows/desktop/api/inspectable/ne-inspectable-trustlevel) wyliczonych wartości.

## <a name="remarks"></a>Uwagi

**InspectableClass** makra mogą służyć tylko z typów środowiska wykonawczego Windows.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz także

[RuntimeClass, klasa](runtimeclass-class.md)