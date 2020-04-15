---
title: lock_guard — Klasa
ms.date: 11/04/2016
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
ms.openlocfilehash: 989c1e368e95fc0009f0c3f1c71af0bdba20609d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351717"
---
# <a name="lock_guard-class"></a>lock_guard — Klasa

Reprezentuje szablon, który można utworzyć w celu utworzenia obiektu, `mutex`którego destruktor odblokowuje plik .

## <a name="syntax"></a>Składnia

```cpp
template <class Mutex>
class lock_guard;
```

## <a name="remarks"></a>Uwagi

Argument `Mutex` szablonu musi nadać nazwę *typowi obiektu mutex*.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|`lock_guard::mutex_type`|Synonim argumentu `Mutex`szablonu .|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock_guard](#lock_guard)|Konstruuje `lock_guard` obiekt.|
|[lock_guard::~lock_guard Destruktor](#dtorlock_guard_destructor)|Odblokowuje `mutex` to, które zostało przekazane do konstruktora.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<mutex>

**Przestrzeń nazw:** std

## <a name="lock_guardlock_guard-constructor"></a><a name="lock_guard"></a>lock_guard::lock_guard konstruktor

Konstruuje `lock_guard` obiekt.

```cpp
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```

### <a name="parameters"></a>Parametry

*Mtx*\
Obiekt *typu mutex.*

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor konstruuje `lock_guard` obiekt typu i blokuje *Mtx*. Jeśli *Mtx* nie jest cyklicznym mutex, musi być odblokowany, gdy ten konstruktor jest wywoływany.

Drugi konstruktor nie blokuje *Mtx*. *Mtx* musi być zablokowany, gdy ten konstruktor jest wywoływany. Konstruktor zgłasza żadnych wyjątków.

## <a name="lock_guardlock_guard-destructor"></a><a name="dtorlock_guard_destructor"></a>lock_guard::~lock_guard Destruktor

Odblokowuje `mutex` to, które zostało przekazane do konstruktora.

```cpp
~lock_guard() noexcept;
```

### <a name="remarks"></a>Uwagi

Jeśli `mutex` nie istnieje, gdy destruktor działa, zachowanie jest niezdefiniowane.

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<>mutex](../standard-library/mutex.md)
