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
ms.openlocfilehash: 0f4aeb3bc5b2ee0598cf9e7d3f572f1f0e5fb5f2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393181"
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

*a*<br/>
Odwołanie do **comptrref —** obiektu.

*b*<br/>
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

[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)<br/>
[ComPtrRef, klasa](../windows/comptrref-class.md)