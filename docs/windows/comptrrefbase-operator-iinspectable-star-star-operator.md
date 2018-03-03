---
title: "ComPtrRefBase::operator IInspectable ** — Operator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable**
dev_langs:
- C++
helpviewer_keywords:
- operator IInspectable** operator
ms.assetid: 06ac1051-606c-449b-a566-cac78ca53762
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d83580537a81b1c75f44e32e6aa43b2b014c8373
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="comptrrefbaseoperator-iinspectable-operator"></a>ComPtrRefBase::operator IInspectable** Operator

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
operator IInspectable**() const;
```

## <a name="remarks"></a>Uwagi

Rzutuje bieżącego [ptr_ — element](../windows/comptrrefbase-ptr-data-member.md) elementu członkowskiego danych do wskaźnik do a wskaźnik do interfejsie IInspectable.

Wystąpił błąd są emitowane, jeśli bieżący comptrrefbase — nie pochodzi od IInspectable.

To rzutowanie jest dostępna tylko wtedy, gdy **&#95; &#95; WRL_CLASSIC_COM &#95; &#95;**  jest zdefiniowany.

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Microsoft::wrl:: details —

## <a name="see-also"></a>Zobacz też

[Comptrrefbase — klasa](../windows/comptrrefbase-class.md)   
[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)