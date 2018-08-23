---
title: SemaphoreTraits::Unlock, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 4e0ea808-b70d-43f7-81ef-998c3b34e3a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e993c58ea6fc84e0b4001b488632858e5251d67b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583974"
---
# <a name="semaphoretraitsunlock-method"></a>SemaphoreTraits::Unlock — Metoda

Kontrola wersji zasobu udostępnionego.

## <a name="syntax"></a>Składnia

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Parametry

*h*  
Dojście do **semafora** obiektu.

## <a name="remarks"></a>Uwagi

W przypadku operacji odblokowania kończy się niepowodzeniem, **Unlock()** emituje komunikat o błędzie wskazujący przyczynę błędu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>Zobacz też

[SemaphoreTraits, struktura](../windows/semaphoretraits-structure.md)