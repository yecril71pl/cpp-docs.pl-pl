---
title: ComPtr::operator -&gt; Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator->
dev_langs:
- C++
helpviewer_keywords:
- operator-> operator
ms.assetid: 7b7faefd-d1e4-4f31-a77d-17a42e0d6b6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 417fd11017f9f70ee8cc247898e23741488ae5e7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599991"
---
# <a name="comptroperator-gt-operator"></a>ComPtr::operator —&gt; — Operator

Pobiera wskaźnik do typu określonego przez parametr bieżącego szablonu.

## <a name="syntax"></a>Składnia

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do typu określonego przez nazwę typu bieżącego szablonu.

## <a name="remarks"></a>Uwagi

Ta funkcja pomocnika usuwa niepotrzebne obciążenie spowodowane użyciem STDMETHOD — makro. Ta funkcja sprawia, że `IUnknown` typy **prywatnej** zamiast **wirtualnego**.

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[ComPtr, klasa](../windows/comptr-class.md)