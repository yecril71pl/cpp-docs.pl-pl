---
title: CriticalSectionTraits::Unlock, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 8fb382f5-6eda-407e-9673-71d77bda4962
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5babc5c14baae474409cd364af31b70549fcefe5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413019"
---
# <a name="criticalsectiontraitsunlock-method"></a>CriticalSectionTraits::Unlock — Metoda

Specjalizuje się `CriticalSection` szablonu, tak że obsługuje uwalniający własności obiektu określona sekcja krytycznego.

## <a name="syntax"></a>Składnia

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>Parametry

*CS*<br/>
Wskaźnik do obiektu sekcję krytyczną.

## <a name="remarks"></a>Uwagi

`Type` Modyfikator jest zdefiniowany jako `typedef CRITICAL_SECTION* Type;`.

Aby uzyskać więcej informacji, zobacz **funkcja LeaveCriticalSection** w **funkcji synchronizacji** części dokumentacji interfejsu API Windows.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>Zobacz też

[CriticalSectionTraits, struktura](../windows/criticalsectiontraits-structure.md)