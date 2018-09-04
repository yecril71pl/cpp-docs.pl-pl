---
title: ComPtrRef::operator! = — Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator!=
dev_langs:
- C++
ms.assetid: ab3093cc-6fbd-4039-890a-6df1cde992b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 97a0f98044e18ec6eff1f1b99e9c9178b711e040
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596026"
---
# <a name="comptrrefoperator-operator"></a>ComPtrRef::operator!= Operator

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)  
);

bool operator!=(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator!=(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>Parametry

*a*  
Odwołanie do **comptrref —** obiektu.

*b*  
Odwołanie do innego **comptrref —** obiekt lub wskaźnik do obiektu anonimowego (`void*`).

## <a name="return-value"></a>Wartość zwracana

Pierwszy plony operator **true** Jeśli obiekt *a* nie jest równa obiektu *b*; w przeciwnym razie **false**.

Operatory drugi i trzeci uzyskanie **true** Jeśli obiekt *a* nie jest równa **nullptr**; w przeciwnym razie **false**.

Operatory czwarty i piąty uzyskanie **true** Jeśli obiekt *a* nie jest równa obiektu *b*; w przeciwnym razie **false**.

## <a name="remarks"></a>Uwagi

Wskazuje, czy dwa **comptrref —** obiekty nie są równe.

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)  
[ComPtrRef, klasa](../windows/comptrref-class.md)