---
title: lock_guard, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
dev_langs:
- C++
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f53732fee62906da19a5771c8598cce51fc6331
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953761"
---
# <a name="lockguard-class"></a>lock_guard — Klasa

Reprezentuje szablon, który można utworzyć wystąpienia, aby utworzyć obiekt, którego destruktor odblokowuje `mutex`.

## <a name="syntax"></a>Składnia

```cpp
template <class Mutex>
class lock_guard;
```

## <a name="remarks"></a>Uwagi

Argument szablonu `Mutex` należy nazywać *typu obiektu mutex*.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`lock_guard::mutex_type`|Synonim dla argumentu szablonu `Mutex`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock_guard](#lock_guard)|Konstruuje `lock_guard` obiektu.|
|[lock_guard:: ~ lock_guard — destruktor](#dtorlock_guard_destructor)|Odblokowuje `mutex` który został przekazany do konstruktora.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<mutex >

**Namespace:** standardowe

## <a name="lock_guard"></a>  lock_guard::lock_guard — Konstruktor

Konstruuje `lock_guard` obiektu.

```cpp
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```

### <a name="parameters"></a>Parametry

*Mtx* A *typu obiektu mutex* obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje obiekt typu `lock_guard` i blokady *Mtx*. Jeśli *Mtx* nie jest elementu mutex cyklicznego musi być odblokowany po wywołaniu tego konstruktora.

Drugi Konstruktor nie blokuje *Mtx*. *Mtx* musi być zablokowane, gdy ten konstruktor jest wywoływany. Konstruktor wyrzuca bez wyjątków.

## <a name="dtorlock_guard_destructor"></a>  lock_guard:: ~ lock_guard — destruktor

Odblokowuje `mutex` który został przekazany do konstruktora.

```cpp
~lock_guard() noexcept;
```

### <a name="remarks"></a>Uwagi

Jeśli `mutex` nie istnieje, po uruchomieniu destruktora, zachowanie jest niezdefiniowane.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
