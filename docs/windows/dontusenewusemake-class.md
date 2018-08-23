---
title: Dontusenewusemake — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
dev_langs:
- C++
helpviewer_keywords:
- DontUseNewUseMake class
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6ce3e391ac0da93ed7571a95ce328a5260a8dd44
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593610"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake — Klasa

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>Uwagi

Zapobiega za pomocą operatora **nowe** w `RuntimeClass`. W związku z tym, należy użyć [funkcji](../windows/make-function.md) zamiast tego.

## <a name="members"></a>Elementy członkowskie

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[DontUseNewUseMake::operator nowy operator](../windows/dontusenewusemake-operator-new-operator.md)|Przeciążenia operatora **nowe** i zapobiega używana w `RuntimeClass`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`DontUseNewUseMake`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)  
[Make, funkcja](../windows/make-function.md)