---
title: lock_guard — Klasa
ms.date: 11/04/2016
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
ms.openlocfilehash: f59860c3aaa9ef7458fe5e30b85b119dede52c72
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453857"
---
# <a name="lockguard-class"></a>lock_guard — Klasa

Reprezentuje szablon, który może być skonkretyzowany do utworzenia obiektu, którego destruktor odblokowuje `mutex`.

## <a name="syntax"></a>Składnia

```cpp
template <class Mutex>
class lock_guard;
```

## <a name="remarks"></a>Uwagi

Argument `Mutex` szablonu musi mieć nazwę *typu muteksu*.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`lock_guard::mutex_type`|Synonim argumentu `Mutex`szablonu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock_guard](#lock_guard)|Konstruuje `lock_guard` obiekt.|
|[lock_guard:: ~ lock_guard, destruktor](#dtorlock_guard_destructor)|Odblokowuje `mutex` , który został przesłany do konstruktora.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> mutex

**Przestrzeń nazw:** std

## <a name="lock_guard"></a>lock_guard:: lock_guard — Konstruktor

Konstruuje `lock_guard` obiekt.

```cpp
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```

### <a name="parameters"></a>Parametry

*MTX*\
Obiekt *typu mutex* .

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje obiekt typu `lock_guard` i blokuje *MTX*. Jeśli *MTX* nie jest cyklicznym obiektem mutex, musi być odblokowany, gdy ten konstruktor jest wywoływany.

Drugi Konstruktor nie blokuje *MTX*. *MTX* musi być zablokowany, gdy ten konstruktor jest wywoływany. Konstruktor nie zgłasza wyjątków.

## <a name="dtorlock_guard_destructor"></a>lock_guard:: ~ lock_guard, destruktor

Odblokowuje `mutex` , który został przesłany do konstruktora.

```cpp
~lock_guard() noexcept;
```

### <a name="remarks"></a>Uwagi

`mutex` Jeśli nie istnieje w trakcie działania destruktora, zachowanie jest niezdefiniowane.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
