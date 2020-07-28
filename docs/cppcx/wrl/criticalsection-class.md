---
title: CriticalSection — Klasa
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::cs_
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::IsValid
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::~CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::CriticalSection class
- Microsoft::WRL::Wrappers::CriticalSection::cs_ data member
- Microsoft::WRL::Wrappers::CriticalSection::IsValid method
- Microsoft::WRL::Wrappers::CriticalSection::Lock method
- Microsoft::WRL::Wrappers::CriticalSection::~CriticalSection, destructor
- Microsoft::WRL::Wrappers::CriticalSection::CriticalSection, constructor
- Microsoft::WRL::Wrappers::CriticalSection::TryLock method
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
ms.openlocfilehash: b95e512f89ee1ff32ca9f1bea51bce643d185a2e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220525"
---
# <a name="criticalsection-class"></a>CriticalSection — Klasa

Reprezentuje obiekt sekcji krytycznej.

## <a name="syntax"></a>Składnia

```cpp
class CriticalSection;
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructor"></a>Konstruktor

Nazwa                                                        | Opis
----------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[CriticalSection:: CriticalSection](#criticalsection)        | Inicjuje obiekt synchronizacji podobny do obiektu mutex, ale może być używany tylko przez wątki pojedynczego procesu.
[CriticalSection:: ~ CriticalSection](#tilde-criticalsection) | Deinicjalizuje i niszczy bieżący `CriticalSection` obiekt.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                 | Opis
------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------
[CriticalSection:: IsValid](#isvalid) | Wskazuje, czy bieżąca Sekcja krytyczna jest prawidłowa.
[CriticalSection:: Lock](#lock)       | Czeka na własność określonego obiektu sekcji krytycznej. Funkcja zwraca, gdy przydzielono wątek wywołujący własność.
[CriticalSection:: TryLock —](#trylock) | Próbuje wprowadzić sekcję krytyczną bez blokowania. Jeśli wywołanie powiedzie się, wątek wywołujący przejmuje własność sekcji krytycznej.

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

Nazwa                        | Opis
--------------------------- | ----------------------------------------
[CriticalSection:: cs_](#cs) | Deklaruje element członkowski danych sekcji krytycznej.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CriticalSection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers. h

**Przestrzeń nazw:** Microsoft:: WRL:: otoki

## <a name="criticalsectioncriticalsection"></a><a name="tilde-criticalsection"></a>CriticalSection:: ~ CriticalSection

Deinicjalizuje i niszczy bieżący `CriticalSection` obiekt.

```cpp
WRL_NOTHROW ~CriticalSection();
```

## <a name="criticalsectioncriticalsection"></a><a name="criticalsection"></a>CriticalSection:: CriticalSection

Inicjuje obiekt synchronizacji podobny do obiektu mutex, ale może być używany tylko przez wątki pojedynczego procesu.

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>Parametry

*spincount*<br/>
Liczba obrotów dla obiektu sekcji krytycznej. Wartość domyślna to 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat krytycznych sekcji i spincounts, zobacz `InitializeCriticalSectionAndSpinCount` funkcję w `Synchronization` sekcji interfejsu API systemu Windows zawiera.

## <a name="criticalsectioncs_"></a><a name="cs"></a>CriticalSection:: cs_

Deklaruje element członkowski danych sekcji krytycznej.

```cpp
CRITICAL_SECTION cs_;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski danych jest chroniony.

## <a name="criticalsectionisvalid"></a><a name="isvalid"></a>CriticalSection:: IsValid

Wskazuje, czy bieżąca Sekcja krytyczna jest prawidłowa.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Wartość zwracana

Domyślnie program zawsze zwraca wartość **`true`** .

## <a name="criticalsectionlock"></a><a name="lock"></a>CriticalSection:: Lock

Czeka na własność określonego obiektu sekcji krytycznej. Funkcja zwraca, gdy przydzielono wątek wywołujący własność.

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parametry

*Rejestr*<br/>
Obiekt sekcji krytycznej określony przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

Obiekt blokady, który może służyć do odblokowania bieżącej sekcji krytycznej.

### <a name="remarks"></a>Uwagi

Pierwsza `Lock` Funkcja ma wpływ na bieżący obiekt sekcji krytycznej. Druga `Lock` Funkcja ma wpływ na sekcję krytyczną określoną przez użytkownika.

## <a name="criticalsectiontrylock"></a><a name="trylock"></a>CriticalSection:: TryLock —

Próbuje wprowadzić sekcję krytyczną bez blokowania. Jeśli wywołanie powiedzie się, wątek wywołujący przejmuje własność sekcji krytycznej.

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parametry

*Rejestr*<br/>
Obiekt sekcji krytycznej określony przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera, jeśli Sekcja krytyczna została wprowadzona pomyślnie lub bieżący wątek jest już właścicielem sekcji krytycznej. Zero, jeśli inny wątek jest już właścicielem sekcji krytycznej.

### <a name="remarks"></a>Uwagi

Pierwsza `TryLock` Funkcja ma wpływ na bieżący obiekt sekcji krytycznej. Druga `TryLock` Funkcja ma wpływ na sekcję krytyczną określoną przez użytkownika.
