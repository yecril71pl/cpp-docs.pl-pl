---
title: HStringReference::Operator =, Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
dev_langs:
- C++
ms.assetid: ea100ed3-e566-4c9e-b6a8-f296088dea9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7045229cc15304a88253f97e1ad3c9f171f139a0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597131"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator= Operator

Przenosi wartość innego **HStringReference** obiekt do bieżącego **HStringReference** obiektu.

## <a name="syntax"></a>Składnia

```cpp
HStringReference& operator=(HStringReference&& other) throw()  
```

### <a name="parameters"></a>Parametry

*other*  
Istniejące **HStringReference** obiektu.

## <a name="remarks"></a>Uwagi

Wartość istniejącego *innych* obiekt jest kopiowany do bieżącego **HStringReference** obiektu, a następnie *innych* niszczony jest obiekt.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[HStringReference, klasa](../windows/hstringreference-class.md)