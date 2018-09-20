---
title: Interfacelist — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
dev_langs:
- C++
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7ce497c621f116c4755e8b47d148e24a9043b46b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374753"
---
# <a name="interfacelist-structure"></a>InterfaceList — Struktura

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <
   typename T,
   typename U
>
struct InterfaceList;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Nazwa interfejsu; Pierwszy interfejs na liście cykliczne.

*U*<br/>
Nazwa interfejsu; pozostałe interfejsy na liście cykliczne.

## <a name="remarks"></a>Uwagi

Użyty do utworzenia cyklicznego listę interfejsów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`FirstT`|Synonim dla parametru szablonu *T*.|
|`RestT`|Synonim dla parametru szablonu *U*.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`InterfaceList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)