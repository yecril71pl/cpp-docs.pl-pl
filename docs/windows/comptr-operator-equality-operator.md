---
title: ComPtr::operator == — Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator==
dev_langs:
- C++
ms.assetid: 6a26e936-29d4-4b7d-b44a-7c575ad07509
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 24ca52eccc814b82e5f9bdd6ddac6458fb5992fe
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607139"
---
# <a name="comptroperator-operator"></a>ComPtr::operator== Operator

Wskazuje, czy dwa **ComPtr** obiekty są sobie równe.

## <a name="syntax"></a>Składnia

```cpp
bool operator==(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator==(
   const ComPtr<T>& a,
   decltype(__nullptr)  
);

bool operator==(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>Parametry

*a*  
Odwołanie do **ComPtr** obiektu.

*b*  
Odwołanie do innego **ComPtr** obiektu.

## <a name="return-value"></a>Wartość zwracana

Pierwszy plony operator **true** Jeśli obiekt *a* jest równy obiektowi *b*; w przeciwnym razie **false**.

Operatory drugi i trzeci uzyskanie **true** Jeśli obiekt *a* jest równa **nullptr**; w przeciwnym razie **false**.

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)  
[ComPtr, klasa](../windows/comptr-class.md)