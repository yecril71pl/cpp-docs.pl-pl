---
title: SyncLockWithStatusT — Klasa
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT class
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT, constructor
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
ms.openlocfilehash: 4b7dbe8ae1648e4185a9eb1e1142df4a3869aa2f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216547"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT — Klasa

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <typename SyncTraits>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>Parametry

*SyncTraits*<br/>
Typ, który może przyjmować lub udostępniać prawa własności do zasobu.

## <a name="remarks"></a>Uwagi

Reprezentuje typ, który może przyjmować lub udostępniać prawa własności do zasobu.

`SyncLockWithStatusT`Klasa jest używana do implementowania klas [mutex](mutex-class.md) i [semaforów](semaphore-class.md) .

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                             | Opis
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT:: SyncLockWithStatusT](#synclockwithstatust) | Inicjuje nowe wystąpienie klasy `SyncLockWithStatusT`.

### <a name="protected-constructors"></a>Konstruktory chronione

Nazwa                                                             | Opis
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT:: SyncLockWithStatusT](#synclockwithstatust) | Inicjuje nowe wystąpienie klasy `SyncLockWithStatusT`.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                         | Opis
-------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT:: GetStatus](#getstatus) | Pobiera stan oczekiwania bieżącego `SyncLockWithStatusT` obiektu.
[SyncLockWithStatusT:: IsLocked](#islocked)   | Wskazuje, czy bieżący `SyncLockWithStatusT` obiekt jest właścicielem zasobu, czyli `SyncLockWithStatusT` obiekt jest *zablokowany*.

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

Nazwa                                    | Opis
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT:: status_](#status) | Przechowuje wynik bazowej operacji oczekiwania po operacji blokowania na obiekcie opartym na bieżącym `SyncLockWithStatusT` obiekcie.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers. h

**Przestrzeń nazw:** Microsoft:: WRL:: otoki::D etails

## <a name="synclockwithstatustgetstatus"></a><a name="getstatus"></a>SyncLockWithStatusT:: GetStatus

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>Wartość zwracana

Wynik operacji oczekiwania na obiekcie, który jest oparty na `SyncLockWithStatusT` klasie, takiej jak [mutex](mutex-class.md) lub [semafor](semaphore-class.md). Zero (0) oznacza, że operacja oczekiwania zwróciła stan sygnalizujący; w przeciwnym razie Wystąpił inny stan, na przykład limit czasu, który upłynął.

### <a name="remarks"></a>Uwagi

Pobiera stan oczekiwania bieżącego `SyncLockWithStatusT` obiektu.

Funkcja GetStatus () Pobiera wartość bazowego elementu członkowskiego danych [status_](#status) . Gdy obiekt oparty na `SyncLockWithStatusT` klasie wykonuje operację blokowania, obiekt najpierw czeka na udostępnienie obiektu. Wynik tej operacji oczekiwania jest przechowywany w `status_` elemencie członkowskim danych. Możliwe wartości `status_` elementu członkowskiego danych są zwracanymi wartościami operacji oczekiwania. Aby uzyskać więcej informacji, zobacz wartości zwracane [`WaitForSingleObjectEx`](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobjectex) funkcji.

## <a name="synclockwithstatustislocked"></a><a name="islocked"></a>SyncLockWithStatusT:: IsLocked

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>Uwagi

Wskazuje, czy bieżący `SyncLockWithStatusT` obiekt jest właścicielem zasobu, czyli `SyncLockWithStatusT` obiekt jest *zablokowany*.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli `SyncLockWithStatusT` obiekt jest zablokowany; w przeciwnym razie, **`false`** .

## <a name="synclockwithstatuststatus_"></a><a name="status"></a>SyncLockWithStatusT:: status_

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
DWORD status_;
```

### <a name="remarks"></a>Uwagi

Przechowuje wynik bazowej operacji oczekiwania po operacji blokowania na obiekcie opartym na bieżącym `SyncLockWithStatusT` obiekcie.

## <a name="synclockwithstatustsynclockwithstatust"></a><a name="synclockwithstatust"></a>SyncLockWithStatusT:: SyncLockWithStatusT

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
SyncLockWithStatusT(
   _Inout_ SyncLockWithStatusT&& other
);

explicit SyncLockWithStatusT(
   typename SyncTraits::Type sync,
   DWORD status
);
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
Rvalue odwołanie do innego `SyncLockWithStatusT` obiektu.

*synchronizacji*<br/>
Odwołanie do innego `SyncLockWithStatusT` obiektu.

*Stany*<br/>
Wartość elementu członkowskiego danych [status_](#status) *innego* parametru lub parametru *synchronizacji* .

### <a name="remarks"></a>Uwagi

Inicjuje nowe wystąpienie klasy `SyncLockWithStatusT`.

Pierwszy Konstruktor inicjuje bieżący `SyncLockWithStatusT` obiekt z innego `SyncLockWithStatusT` określonego przez parametr *inny*, a następnie unieważnia inny `SyncLockWithStatusT` obiekt. Drugi Konstruktor jest **`protected`** i inicjuje bieżący `SyncLockWithStatusT` obiekt w nieprawidłowym stanie.
