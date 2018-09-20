---
title: InspectableClass, makro | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
dev_langs:
- C++
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a20815972f595a15097a057537d6cb5cdca4fb4b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408339"
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
Jedną z [TrustLevel](https://msdn.microsoft.com/library/br224625.aspx) wyliczonych wartości.

## <a name="remarks"></a>Uwagi

**InspectableClass** makra mogą służyć tylko z typów środowiska wykonawczego Windows.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[RuntimeClass, klasa](../windows/runtimeclass-class.md)