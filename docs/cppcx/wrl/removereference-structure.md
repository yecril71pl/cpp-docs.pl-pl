---
title: RemoveReference — Struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RemoveReference
helpviewer_keywords:
- RemoveReference structure
ms.assetid: 43ff91bb-815a-440e-b9fb-7dcbb7c863af
ms.openlocfilehash: 342980ac9a7cae8a98ffd0f367c666487e34e5de
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59021621"
---
# <a name="removereference-structure"></a>RemoveReference — Struktura

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template<class T>
struct RemoveReference;

template<class T>
struct RemoveReference<T&>;

template<class T>
struct RemoveReference<T&&>;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa.

## <a name="remarks"></a>Uwagi

Usuwa odwołanie lub odwołaniem rvalue cech od parametru szablonu określonej klasy.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`Type`|Synonim dla parametru szablonu klasy.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`RemoveReference`

## <a name="requirements"></a>Wymagania

**Nagłówek:** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL::Details, przestrzeń nazw](microsoft-wrl-details-namespace.md)