---
title: Srwlocksharedtraits — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
dev_langs:
- C++
helpviewer_keywords:
- SRWLockSharedTraits structure
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 50bcfc728a2f228e4fa8444fe41cc25c3ff449a2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602249"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits — Struktura

W tym artykule opisano typowe cechy `SRWLock` klasy w trybie blokady udostępniania.

## <a name="syntax"></a>Składnia

```cpp
struct SRWLockSharedTraits;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`Type`|Synonim dla wskaźnika do [SRWLOCK](../windows/srwlock-class.md) klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[SRWLockSharedTraits::GetInvalidValue, metoda](../windows/srwlocksharedtraits-getinvalidvalue-method.md)|Pobiera **srwlocksharedtraits —** obiekt, który zawsze jest nieprawidłowy.|
|[SRWLockSharedTraits::Unlock, metoda](../windows/srwlocksharedtraits-unlock-method.md)|Zwalnia wyłączną kontrolę określonego `SRWLock` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SRWLockSharedTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Wrappers::HandleTraits, przestrzeń nazw](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)