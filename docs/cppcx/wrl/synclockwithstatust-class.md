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
ms.openlocfilehash: 77bcb8336e4650de7ed01a067fa1bdd7ec0ba3e8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374267"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT — Klasa

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

## <a name="syntax"></a>Składnia

```cpp
template <typename SyncTraits>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>Parametry

*SyncTraits (SyncTraits)*<br/>
Typ, który może przejąć wyłączną lub współwłasność zasobu.

## <a name="remarks"></a>Uwagi

Reprezentuje typ, który może przejąć wyłączną lub współwłasność zasobu.

Klasa `SyncLockWithStatusT` jest używana do implementowania [mutex](mutex-class.md) i [Semaphore](semaphore-class.md) klasy.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                             | Opis
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT::SyncLockWithStatusT](#synclockwithstatust) | Inicjuje nowe wystąpienie klasy `SyncLockWithStatusT`.

### <a name="protected-constructors"></a>Konstruktory chronione

Nazwa                                                             | Opis
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT::SyncLockWithStatusT](#synclockwithstatust) | Inicjuje nowe wystąpienie klasy `SyncLockWithStatusT`.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                         | Opis
-------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT::GetStatus](#getstatus) | Pobiera stan oczekiwania bieżącego `SyncLockWithStatusT` obiektu.
[SyncLockWithStatusT::Jest zablokowany](#islocked)   | Wskazuje, czy `SyncLockWithStatusT` bieżący obiekt jest właścicielem zasobu; oznacza to, `SyncLockWithStatusT` że obiekt jest *zablokowany*.

### <a name="protected-data-members"></a>Członkowie chronionych danych

Nazwa                                    | Opis
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT::status_](#status) | Przechowuje wynik podstawowej operacji oczekiwania po operacji blokady `SyncLockWithStatusT` na obiekcie na podstawie bieżącego obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Obszar nazw:** Microsoft::WRL::Otoki::Details

## <a name="synclockwithstatustgetstatus"></a><a name="getstatus"></a>SyncLockWithStatusT::GetStatus

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>Wartość zwracana

Wynik operacji oczekiwania na obiekcie, który `SyncLockWithStatusT` jest oparty na klasie, takich jak [Mutex](mutex-class.md) lub [Semaphore](semaphore-class.md). Zero (0) wskazuje, że operacja oczekiwania zwróciła stan sygnalizowany; w przeciwnym razie wystąpił inny stan, taki jak limit czasu.

### <a name="remarks"></a>Uwagi

Pobiera stan oczekiwania bieżącego `SyncLockWithStatusT` obiektu.

Funkcja GetStatus() pobiera wartość elementu członkowskiego [status_](#status) danych. Gdy obiekt oparty `SyncLockWithStatusT` na klasie wykonuje operację blokady, obiekt najpierw czeka, aż obiekt stanie się dostępny. Wynik tej operacji oczekiwania jest `status_` przechowywany w elementów członkowskich danych. Możliwe wartości elementu `status_` członkowskiego danych są zwracane wartości operacji oczekiwania. Aby uzyskać więcej informacji, zobacz `WaitForSingleObjectEx()` zwracane wartości funkcji w bibliotece MSDN.

## <a name="synclockwithstatustislocked"></a><a name="islocked"></a>SyncLockWithStatusT::Jest zablokowany

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>Uwagi

Wskazuje, czy `SyncLockWithStatusT` bieżący obiekt jest właścicielem zasobu; oznacza to, `SyncLockWithStatusT` że obiekt jest *zablokowany*.

### <a name="return-value"></a>Wartość zwracana

**true,** `SyncLockWithStatusT` jeśli obiekt jest zablokowany; w przeciwnym razie **false**.

## <a name="synclockwithstatuststatus_"></a><a name="status"></a>SyncLockWithStatusT::status_

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
DWORD status_;
```

### <a name="remarks"></a>Uwagi

Przechowuje wynik podstawowej operacji oczekiwania po operacji blokady `SyncLockWithStatusT` na obiekcie na podstawie bieżącego obiektu.

## <a name="synclockwithstatustsynclockwithstatust"></a><a name="synclockwithstatust"></a>SyncLockWithStatusT::SyncLockWithStatusT

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

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

*Innych*<br/>
Odwołanie rvalue do `SyncLockWithStatusT` innego obiektu.

*synchronizacja*<br/>
Odwołanie do `SyncLockWithStatusT` innego obiektu.

*Stan*<br/>
Wartość [status_](#status) elementu członkowskiego danych *innego* parametru lub parametru *synchronizacji.*

### <a name="remarks"></a>Uwagi

Inicjuje nowe wystąpienie klasy `SyncLockWithStatusT`.

Pierwszy `SyncLockWithStatusT` konstruktor inicjuje bieżący obiekt z innego `SyncLockWithStatusT` określonego przez parametr *inny*, a następnie unieważnia inny `SyncLockWithStatusT` obiekt. Drugi konstruktor `protected`jest i inicjuje bieżący `SyncLockWithStatusT` obiekt do nieprawidłowego stanu.
