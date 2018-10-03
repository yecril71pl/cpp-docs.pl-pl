---
title: Criticalsection — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::cs_
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::IsValid
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::~CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::CriticalSection class
- Microsoft::WRL::Wrappers::CriticalSection::cs_ data member
- Microsoft::WRL::Wrappers::CriticalSection::IsValid method
- Microsoft::WRL::Wrappers::CriticalSection::Lock method
- Microsoft::WRL::Wrappers::CriticalSection::~CriticalSection, destructor
- Microsoft::WRL::Wrappers::CriticalSection::CriticalSection, constructor
- Microsoft::WRL::Wrappers::CriticalSection::TryLock method
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 67ca6e8eab90e1e97a3ab8aacd46616dbcbf2d0e
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234726"
---
# <a name="criticalsection-class"></a>CriticalSection — Klasa

Reprezentuje obiekt sekcję krytyczną.

## <a name="syntax"></a>Składnia

```cpp
class CriticalSection;
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructor"></a>Konstruktor

Nazwa                                                        | Opis
----------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[CriticalSection::CriticalSection](#criticalsection)        | Inicjuje obiekt synchronizacji, który jest podobny do obiektu mutex, ale mogą być używane przez wątki tylko pojedynczego procesu.
[CriticalSection:: ~ CriticalSection](#tilde-criticalsection) | Wyłącza i niszczy bieżącego `CriticalSection` obiektu.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                 | Opis
------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------
[CriticalSection::IsValid](#isvalid) | Wskazuje, czy bieżąca sekcja krytycznego jest prawidłowa.
[CriticalSection::Lock](#lock)       | Czeka na własność obiektu określona sekcja krytycznego. Funkcja zwróci, jeśli wątek wywołujący udzielono prawa własności.
[CriticalSection::TryLock](#trylock) | Próbuje wprowadzić sekcję krytyczną bez blokowania. Jeśli wywołanie zakończy się pomyślnie, wątek wywołujący przejmuje na własność sekcję krytyczną.

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

Nazwa                        | Opis
--------------------------- | ----------------------------------------
[CriticalSection::cs_](#cs) | Deklaruje element członkowski danych sekcję krytyczną.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CriticalSection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="tilde-criticalsection"></a>CriticalSection:: ~ CriticalSection

Wyłącza i niszczy bieżącego `CriticalSection` obiektu.

```cpp
WRL_NOTHROW ~CriticalSection();
```

## <a name="criticalsection"></a>CriticalSection::CriticalSection

Inicjuje obiekt synchronizacji, który jest podobny do obiektu mutex, ale mogą być używane przez wątki tylko pojedynczego procesu.

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>Parametry

*spincount*<br/>
Liczba obiektów sekcję krytyczną pokrętła. Wartość domyślna to 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat sekcje krytyczne i spincounts zobacz `InitializeCriticalSectionAndSpinCount` działa w programach `Synchronization` sekcji zawiera interfejs API Windows.

## <a name="cs"></a>CriticalSection::cs_

Deklaruje element członkowski danych sekcję krytyczną.

```cpp
CRITICAL_SECTION cs_;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski danych jest chroniona.

## <a name="isvalid"></a>CriticalSection::IsValid

Wskazuje, czy bieżąca sekcja krytycznego jest prawidłowa.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Wartość zwracana

Domyślnie zwraca zawsze `true`.

## <a name="lock"></a>CriticalSection::Lock

Czeka na własność obiektu określona sekcja krytycznego. Funkcja zwróci, jeśli wątek wywołujący udzielono prawa własności.

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parametry

*CS*<br/>
Obiekt sekcję krytyczną określonych przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

Obiekt blokady, który może służyć do odblokowania bieżąca sekcja krytycznego.

### <a name="remarks"></a>Uwagi

Pierwszy `Lock` funkcji ma wpływ na bieżący obiekt sekcję krytyczną. Drugi `Lock` funkcji ma wpływ na sekcję krytyczną określonych przez użytkownika.

## <a name="trylock"></a>CriticalSection::TryLock

Próbuje wprowadzić sekcję krytyczną bez blokowania. Jeśli wywołanie zakończy się pomyślnie, wątek wywołujący przejmuje na własność sekcję krytyczną.

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parametry

*CS*<br/>
Obiekt sekcję krytyczną określonych przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli pomyślnie podano sekcję krytyczną lub bieżący wątek jest już właścicielem sekcję krytyczną. Zero, jeśli inny wątek jest już właścicielem sekcję krytyczną.

### <a name="remarks"></a>Uwagi

Pierwszy `TryLock` funkcji ma wpływ na bieżący obiekt sekcję krytyczną. Drugi `TryLock` funkcji ma wpływ na sekcję krytyczną określonych przez użytkownika.
