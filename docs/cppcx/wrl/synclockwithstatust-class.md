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
ms.openlocfilehash: 1c9c0805834a59d10a559bfc2b6da0f10e2fe160
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787484"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT — Klasa

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <typename SyncTraits>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>Parametry

*SyncTraits*<br/>
Typ, który może zająć wyłączne lub współużytkować własność zasobu.

## <a name="remarks"></a>Uwagi

Reprezentuje typ, który może zająć wyłączne lub współużytkować własność zasobu.

`SyncLockWithStatusT` Klasa jest używana do zaimplementowania [Mutex](mutex-class.md) i [semafora](semaphore-class.md) klasy.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                             | Opis
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT::SyncLockWithStatusT](#synclockwithstatust) | Inicjuje nowe wystąpienie klasy `SyncLockWithStatusT` klasy.

### <a name="protected-constructors"></a>Konstruktory chronione

Nazwa                                                             | Opis
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT::SyncLockWithStatusT](#synclockwithstatust) | Inicjuje nowe wystąpienie klasy `SyncLockWithStatusT` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                         | Opis
-------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT::GetStatus](#getstatus) | Pobiera stan oczekiwania bieżącego `SyncLockWithStatusT` obiektu.
[SyncLockWithStatusT::IsLocked](#islocked)   | Wskazuje, czy bieżący `SyncLockWithStatusT` obiekt posiada zasób; czyli, `SyncLockWithStatusT` obiekt jest *zablokowane*.

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

Nazwa                                    | Opis
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT::status_](#status) | Zawiera wynik podstawowych operacji oczekiwania po operacji blokadę na obiekcie na podstawie bieżącego `SyncLockWithStatusT` obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="getstatus"></a>SyncLockWithStatusT::GetStatus

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>Wartość zwracana

Wynik operacji oczekiwania na obiekt, który jest oparty na `SyncLockWithStatusT` klasy, takie jak [Mutex](mutex-class.md) lub [semafora](semaphore-class.md). Zero (0) oznacza, że operacji oczekiwania zwrócone sygnalizowanego stanu; w przeciwnym razie inny stan wystąpił, takie jak wartość limitu czasu, który upłynął.

### <a name="remarks"></a>Uwagi

Pobiera stan oczekiwania bieżącego `SyncLockWithStatusT` obiektu.

Funkcja GetStatus() pobiera wartości elementu bazowego [status_ — element](#status) element członkowski danych. Gdy obiekt jest oparty na `SyncLockWithStatusT` klasy wykonuje operację blokady, obiekt najpierw czeka na udostępnienie obiektu. Wynikiem tej operacji oczekiwania są przechowywane w `status_` element członkowski danych. Możliwe wartości `status_` element członkowski danych są zwracane wartości operacji oczekiwania. Aby uzyskać więcej informacji, zobacz wartości zwracanych metody `WaitForSingleObjectEx()` funkcji w bibliotece MSDN.

## <a name="islocked"></a>SyncLockWithStatusT::IsLocked

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>Uwagi

Wskazuje, czy bieżący `SyncLockWithStatusT` obiekt posiada zasób; czyli, `SyncLockWithStatusT` obiekt jest *zablokowane*.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `SyncLockWithStatusT` obiektu jest zablokowany; w przeciwnym razie **false**.

## <a name="status"></a>SyncLockWithStatusT::status_

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
DWORD status_;
```

### <a name="remarks"></a>Uwagi

Zawiera wynik podstawowych operacji oczekiwania po operacji blokadę na obiekcie na podstawie bieżącego `SyncLockWithStatusT` obiektu.

## <a name="synclockwithstatust"></a>SyncLockWithStatusT::SyncLockWithStatusT

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

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

*other*<br/>
Odwołanie rvalue, do innego `SyncLockWithStatusT` obiektu.

*sync*<br/>
Odwołanie do innego `SyncLockWithStatusT` obiektu.

*status*<br/>
Wartość [status_ — element](#status) element członkowski danych *innych* parametru lub *synchronizacji* parametru.

### <a name="remarks"></a>Uwagi

Inicjuje nowe wystąpienie klasy `SyncLockWithStatusT` klasy.

Pierwszy Konstruktor inicjuje bieżące `SyncLockWithStatusT` obiektu z innego `SyncLockWithStatusT` określony przez parametr *innych*, a następnie unieważnia innych `SyncLockWithStatusT` obiektu. Drugi Konstruktor jest `protected`i inicjuje bieżące `SyncLockWithStatusT` obiektu nieprawidłowym stanie.