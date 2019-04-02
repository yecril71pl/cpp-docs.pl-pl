---
title: InspectableClass — Makro
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: cedf395ae98a423e0335851327b5fdda1a4bc7d6
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787543"
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

## <a name="see-also"></a>Zobacz też

[RuntimeClass, klasa](runtimeclass-class.md)