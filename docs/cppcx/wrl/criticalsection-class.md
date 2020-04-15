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
ms.openlocfilehash: 5deb89e795d1886ca316886ae1ea260ce1f36fd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372588"
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
[CriticalSekcja::CriticalSekcja](#criticalsection)        | Inicjuje obiekt synchronizacji, który jest podobny do obiektu mutex, ale może być używany tylko przez wątki pojedynczego procesu.
[CriticalSekcja::~CriticalSekcja](#tilde-criticalsection) | Deinitializes i niszczy `CriticalSection` bieżący obiekt.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                 | Opis
------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------
[CriticalSection::IsValid](#isvalid) | Wskazuje, czy bieżąca sekcja krytyczna jest prawidłowa.
[CriticalSekcja::Zablokuj](#lock)       | Czeka na własność określonego obiektu sekcji krytycznej. Funkcja zwraca, gdy wątek wywołujący jest przyznawana własność.
[CriticalSekcja::TryLock](#trylock) | Próbuje wprowadzić sekcję krytyczną bez blokowania. Jeśli wywołanie zakończy się pomyślnie, wątek wywołujący przejmuje odpowiedzialność za sekcję krytyczną.

### <a name="protected-data-members"></a>Członkowie chronionych danych

Nazwa                        | Opis
--------------------------- | ----------------------------------------
[CriticalSection::cs_](#cs) | Deklaruje element członkowski danych sekcji krytycznej.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CriticalSection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Obszar nazw:** Microsoft::WRL::Otoki

## <a name="criticalsectioncriticalsection"></a><a name="tilde-criticalsection"></a>CriticalSekcja::~CriticalSekcja

Deinitializes i niszczy `CriticalSection` bieżący obiekt.

```cpp
WRL_NOTHROW ~CriticalSection();
```

## <a name="criticalsectioncriticalsection"></a><a name="criticalsection"></a>CriticalSekcja::CriticalSekcja

Inicjuje obiekt synchronizacji, który jest podobny do obiektu mutex, ale może być używany tylko przez wątki pojedynczego procesu.

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>Parametry

*spincount*<br/>
Liczba obrotów dla obiektu przekroju krytycznego. Wartość domyślna to 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat krytycznych `InitializeCriticalSectionAndSpinCount` sekcji i `Synchronization` spincounts, zobacz funkcję w sekcji documenation interfejsu API systemu Windows.

## <a name="criticalsectioncs_"></a><a name="cs"></a>CriticalSection::cs_

Deklaruje element członkowski danych sekcji krytycznej.

```cpp
CRITICAL_SECTION cs_;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski danych jest chroniony.

## <a name="criticalsectionisvalid"></a><a name="isvalid"></a>CriticalSection::IsValid

Wskazuje, czy bieżąca sekcja krytyczna jest prawidłowa.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Wartość zwracana

Domyślnie zawsze zwraca **wartość true**.

## <a name="criticalsectionlock"></a><a name="lock"></a>CriticalSekcja::Zablokuj

Czeka na własność określonego obiektu sekcji krytycznej. Funkcja zwraca, gdy wątek wywołujący jest przyznawana własność.

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parametry

*Cs*<br/>
Obiekt sekcji krytycznej określony przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

Obiekt blokady, który może służyć do odblokowania bieżącej sekcji krytycznej.

### <a name="remarks"></a>Uwagi

Pierwsza `Lock` funkcja wpływa na bieżący obiekt sekcji krytycznej. Druga `Lock` funkcja ma wpływ na sekcję krytyczną określoną przez użytkownika.

## <a name="criticalsectiontrylock"></a><a name="trylock"></a>CriticalSekcja::TryLock

Próbuje wprowadzić sekcję krytyczną bez blokowania. Jeśli wywołanie zakończy się pomyślnie, wątek wywołujący przejmuje odpowiedzialność za sekcję krytyczną.

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parametry

*Cs*<br/>
Obiekt sekcji krytycznej określony przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

Wartość niezerowa, jeśli sekcja krytyczna została pomyślnie wprowadzona lub bieżący wątek jest już właścicielem sekcji krytycznej. Zero, jeśli inny wątek jest już właścicielem sekcji krytycznej.

### <a name="remarks"></a>Uwagi

Pierwsza `TryLock` funkcja wpływa na bieżący obiekt sekcji krytycznej. Druga `TryLock` funkcja ma wpływ na sekcję krytyczną określoną przez użytkownika.
