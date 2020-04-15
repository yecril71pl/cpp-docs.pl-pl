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
ms.openlocfilehash: 6d4ba08ab1884e8584b0e98e931d2d63cdac5aec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371252"
---
# <a name="mutextraits-structure"></a>MutexTraits — Struktura

Definiuje wspólne cechy klasy [Mutex.](mutex-class.md)

## <a name="syntax"></a>Składnia

```cpp
struct MutexTraits : HANDLENullTraits;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

Nazwa                           | Opis
------------------------------ | ------------------------------------------------
[MutexTraits::Odblokuj](#unlock) | Zwalnia wyłączną kontrolę nad zasobem udostępnionym.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`HANDLENullTraits`

`MutexTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Obszar nazw:** Microsoft::WRL::Otoki::HandleTraits

## <a name="mutextraitsunlock-method"></a><a name="unlock"></a>MutexTraits::Metoda odblokowywania

Zwalnia wyłączną kontrolę nad zasobem udostępnionym.

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Dojście do obiektu mutex.
