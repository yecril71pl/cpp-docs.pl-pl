---
title: ComPtrRefBase::operator IInspectable ** — Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable**
dev_langs:
- C++
helpviewer_keywords:
- operator IInspectable** operator
ms.assetid: 06ac1051-606c-449b-a566-cac78ca53762
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e337f6bbc92718c839fc2bd12c9df9f0caa5d5aa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883462"
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

To rzutowanie jest dostępna tylko wtedy, gdy **&#95; &#95;WRL_CLASSIC_COM&#95; &#95;** jest zdefiniowany.

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Microsoft::wrl:: details —

## <a name="see-also"></a>Zobacz też

[Comptrrefbase — klasa](../windows/comptrrefbase-class.md)   
[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)