---
title: Operator ComPtrRefBase::operator IInspectable ** | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 4683305b9f7f396168bd9404f6f2501502db3d01
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645025"
---
# <a name="comptrrefbaseoperator-iinspectable-operator"></a>ComPtrRefBase::operator IInspectable\* \* — Operator

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
operator IInspectable**() const;
```

## <a name="remarks"></a>Uwagi

Rzutuje bieżącego [ptr_ — element](../windows/comptrrefbase-ptr-data-member.md) element członkowski danych do wskaźnik do a wskaźnik do `IInspectable` interfejsu.

Błąd jest emitowane, jeśli bieżący **comptrrefbase —** nie pochodzi od `IInspectable`.

To rzutowanie jest dostępna tylko wtedy, gdy `__WRL_CLASSIC_COM__` jest zdefiniowana.

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też
[Comptrrefbase — klasa](../windows/comptrrefbase-class.md)   
[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)