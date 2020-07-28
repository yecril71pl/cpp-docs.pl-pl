---
title: CriticalSectionTraits — Struktura
ms.date: 09/26/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock method
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
ms.openlocfilehash: 3573cad21734a97629cbc12b76d73b99024cbc2f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220512"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits — Struktura

Wyspecjalizowano `CriticalSection` obiekt do obsługi nieprawidłowej sekcji krytycznej lub funkcji w celu wydania sekcji krytycznej.

## <a name="syntax"></a>Składnia

```
struct CriticalSectionTraits;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

Nazwa   | Opis
------ | -----------------------------------------------------------------------------------------------------------------
`Type` | A **`typedef`** , który definiuje wskaźnik do sekcji krytycznej. `Type`jest zdefiniowane jako `typedef CRITICAL_SECTION* Type;` .

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                       | Opis
---------------------------------------------------------- | -----------------
[CriticalSectionTraits:: GetInvalidValue —](#getinvalidvalue) | `CriticalSection`Określa szablon w taki sposób, aby szablon był zawsze nieprawidłowy.
[CriticalSectionTraits:: Unlock](#unlock)                   | Specjalizacja `CriticalSection` szablonu, aby obsługiwał możliwość zwalniania własności określonego obiektu sekcji krytycznej.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CriticalSectionTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers. h

**Przestrzeń nazw:** Microsoft:: WRL:: otoki:: HandleTraits

## <a name="criticalsectiontraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>CriticalSectionTraits:: GetInvalidValue —

`CriticalSection`Określa szablon w taki sposób, aby szablon był zawsze nieprawidłowy.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wskaźnik do nieprawidłowej sekcji krytycznej.

### <a name="remarks"></a>Uwagi

`Type`Modyfikator jest zdefiniowany jako `typedef CRITICAL_SECTION* Type;` .

## <a name="criticalsectiontraitsunlock"></a><a name="unlock"></a>CriticalSectionTraits:: Unlock

Specjalizacja `CriticalSection` szablonu, aby obsługiwał możliwość zwalniania własności określonego obiektu sekcji krytycznej.

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>Parametry

*Rejestr*<br/>
Wskaźnik do obiektu sekcji krytycznej.

### <a name="remarks"></a>Uwagi

`Type`Modyfikator jest zdefiniowany jako `typedef CRITICAL_SECTION* Type;` .

Aby uzyskać więcej informacji, zobacz **Funkcja LeaveCriticalSection** w sekcji **funkcje synchronizacji** dokumentacji interfejsu API systemu Windows.
