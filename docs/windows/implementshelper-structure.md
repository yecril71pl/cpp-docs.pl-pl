---
title: Implementshelper — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
dev_langs:
- C++
helpviewer_keywords:
- ImplementsHelper structure
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bcacfb8d5cd6d15cf9ca5f9f5bb8e937119dc863
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691577"
---
# <a name="implementshelper-structure"></a>ImplementsHelper — Struktura

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <
   typename RuntimeClassFlagsT,
   typename ILst,
   bool IsDelegateToClass
>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>Parametry

*RuntimeClassFlagsT*  
Pola flagi, które określa co najmniej jeden [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) modułów wyliczających.

*IList*  
Lista identyfikatorów interfejsu.

*IsDelegateToClass*  
Określ **true** Jeśli bieżące wystąpienie `Implements` będąca klasą bazową identyfikator pierwszego interfejsu w *IList*; w przeciwnym razie **false**.

## <a name="remarks"></a>Uwagi

Pomaga wdrożyć [implementuje](../windows/implements-structure.md) struktury.

Ten szablon przechodzi przez listę interfejsów i dodaje je w klasach bazowych, jak i informacje niezbędne do umożliwienia `QueryInterface`.

## <a name="members"></a>Elementy członkowskie

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ImplementsHelper`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)