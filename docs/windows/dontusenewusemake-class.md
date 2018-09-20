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
ms.openlocfilehash: dc2b2f03cfbd488de8358b2e4b123716efcbfe15
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431312"
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

[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)<br/>
[Make, funkcja](../windows/make-function.md)