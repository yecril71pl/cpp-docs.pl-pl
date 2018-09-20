---
title: WeakReference::DecrementStrongReference, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
dev_langs:
- C++
helpviewer_keywords:
- DecrementStrongReference method
ms.assetid: 97d70d9f-41b8-4f8d-a6fa-4137cc4f9029
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9a73608bd2faa8de2c5e23eff84290e7dd5fae11
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417192"
---
# <a name="weakreferencedecrementstrongreference-method"></a>WeakReference::DecrementStrongReference — Metoda

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
ULONG DecrementStrongReference();
```

## <a name="remarks"></a>Uwagi

Dekrementuje silne odwołanie zliczane bieżącego **WeakReference** obiektu.

Gdy liczba silne odwołanie staje się zerem, silne odwołanie jest ustawiona na **nullptr**.

## <a name="return-value"></a>Wartość zwracana

Liczba wraz z przydzielaniem silne odwołanie.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[Weakreference — klasa](../windows/weakreference-class1.md)<br/>
[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)