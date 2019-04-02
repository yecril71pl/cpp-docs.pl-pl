---
title: MutexTraits — Struktura
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::MutexTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock method
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
ms.openlocfilehash: 9bc4071e5699610a664cbf01ca3e7d36d7effc5e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787226"
---
# <a name="mutextraits-structure"></a>MutexTraits — Struktura

Definiuje typowe cechy [Mutex](mutex-class.md) klasy.

## <a name="syntax"></a>Składnia

```cpp
struct MutexTraits : HANDLENullTraits;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

Nazwa                           | Opis
------------------------------ | ------------------------------------------------
[MutexTraits::Unlock](#unlock) | Zwalnia wyłączną kontrolę zasobu udostępnionego.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`HANDLENullTraits`

`MutexTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="unlock"></a>MutexTraits::Unlock, metoda

Zwalnia wyłączną kontrolę zasobu udostępnionego.

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Uchwytu do obiektu mutex.
