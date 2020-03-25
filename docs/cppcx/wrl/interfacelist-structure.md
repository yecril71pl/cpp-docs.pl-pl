---
title: InterfaceList — Struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
ms.openlocfilehash: 7fd06f71bc4d8097366dc0e87d7ff92c5a12a790
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213866"
---
# <a name="interfacelist-structure"></a>InterfaceList — Struktura

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <typename T, typename U>
struct InterfaceList;
```

### <a name="parameters"></a>Parametry

*&*<br/>
Nazwa interfejsu; Pierwszy interfejs na liście cyklicznej.

*'T*<br/>
Nazwa interfejsu; Pozostałe interfejsy na liście cyklicznej.

## <a name="remarks"></a>Uwagi

Służy do tworzenia cyklicznej listy interfejsów.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name (Nazwa)|Opis|
|----------|-----------------|
|`FirstT`|Synonim dla parametru szablonu *T*.|
|`RestT`|Synonim dla parametru szablonu *U*.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`InterfaceList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implementuje. h

**Przestrzeń nazw:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](microsoft-wrl-details-namespace.md)
