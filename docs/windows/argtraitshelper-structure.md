---
title: Argtraitshelper — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
dev_langs:
- C++
helpviewer_keywords:
- ArgTraitsHelper structure
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 314853b103d74bd7907fb665b806f386ed7bd44e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397472"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper — Struktura

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template<typename TDelegateInterface>
struct ArgTraitsHelper;
```

### <a name="parameters"></a>Parametry

*TDelegateInterface*<br/>
Interfejs delegata.

## <a name="remarks"></a>Uwagi

Pomaga zdefiniować typowe cechy argumenty delegata.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`methodType`|Synonim dla `decltype(&TDelegateInterface::Invoke)`.|
|`Traits`|Synonim dla `ArgTraits<methodType>`.|

### <a name="public-constants"></a>Publiczne stałe

|Nazwa|Opis|
|----------|-----------------|
|[ArgTraitsHelper::args, stała](../windows/argtraitshelper-args-constant.md)|Pomaga [ArgTraits::args](../windows/argtraits-args-constant.md) liczbę parametrów bądź na bieżąco z `Invoke` metodę interfejsu delegata.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ArgTraitsHelper`

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)