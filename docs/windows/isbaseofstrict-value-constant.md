---
title: IsBaseOfStrict::value, stała | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
dev_langs:
- C++
helpviewer_keywords:
- value constant
ms.assetid: 4a0cdab0-ba03-482b-babf-eeec519ba687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e7159e75b03c6440dfc5742de9f98d93da47d904
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583857"
---
# <a name="isbaseofstrictvalue-constant"></a>IsBaseOfStrict::value — Stała

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
static const bool value = __is_base_of(Base, Derived);
```

## <a name="remarks"></a>Uwagi

Wskazuje, czy jeden typ jest podstawą innego.

**wartość** jest **true** Jeśli typ `Base` jest klasą bazową typu `Derived`, w przeciwnym razie jest **false**.

## <a name="requirements"></a>Wymagania

**Nagłówek:** internal.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[IsBaseOfStrict, struktura](../windows/isbaseofstrict-structure.md)  
[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)