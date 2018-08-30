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
ms.openlocfilehash: 9b85a10c68b7379f0e59bf859b3d8badf7413195
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208344"
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

*runtimeClassName*  
Pełna tekstowa Nazwa klasy runtime.

*trustLevel*  
Jedną z [TrustLevel](https://msdn.microsoft.com/library/br224625.aspx) wyliczonych wartości.

## <a name="remarks"></a>Uwagi

**InspectableClass** makra mogą służyć tylko z typów środowiska wykonawczego Windows.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[RuntimeClass, klasa](../windows/runtimeclass-class.md)