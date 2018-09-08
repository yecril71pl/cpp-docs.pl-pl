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
ms.openlocfilehash: 5e096d21699d4e6218bbadedcd1cc0bcc65f92f2
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108192"
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

*Mtx*<br/>
A *typu obiektu mutex* obiektu.

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
