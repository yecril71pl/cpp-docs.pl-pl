---
title: critical_section — Klasa
ms.date: 11/04/2016
f1_keywords:
- critical_section
- CONCRT/concurrency::critical_section
- CONCRT/concurrency::critical_section::critical_section::scoped_lock Class
- CONCRT/concurrency::critical_section::critical_section
- CONCRT/concurrency::critical_section::lock
- CONCRT/concurrency::critical_section::native_handle
- CONCRT/concurrency::critical_section::try_lock
- CONCRT/concurrency::critical_section::try_lock_for
- CONCRT/concurrency::critical_section::unlock
helpviewer_keywords:
- critical_section class
ms.assetid: fa3c89d6-be5d-4d1b-bddb-8232814e6cf6
ms.openlocfilehash: aef3ae6100133374cb89098f118c447effafd840
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143087"
---
# <a name="critical_section-class"></a>critical_section — Klasa

Niewspółpracujący obiekt mutex, który jest jawnie świadomy środowisko uruchomieniowe współbieżności.

## <a name="syntax"></a>Składnia

```cpp
class critical_section;
```

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name (Nazwa)|Opis|
|----------|-----------------|
|`native_handle_type`|Odwołanie do obiektu `critical_section`.|

### <a name="public-classes"></a>Klasy publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[critical_section:: scoped_lock, Klasa](#critical_section__scoped_lock_class)|Wyjątek RAII bezpiecznie dla obiektu `critical_section`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[critical_section](#ctor)|Tworzy nową sekcję krytyczną.|
|[~ critical_section destruktor](#dtor)|Niszczy sekcję krytyczną.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[lock](#lock)|Uzyskuje tę sekcję krytyczną.|
|[native_handle](#native_handle)|Zwraca uchwyt macierzysty specyficzny dla platformy (jeśli taki istnieje).|
|[try_lock](#try_lock)|Próbuje uzyskać blokadę bez blokowania.|
|[try_lock_for](#try_lock_for)|Próbuje uzyskać blokadę bez blokowania przez określoną liczbę milisekund.|
|[odblokowania](#unlock)|Odblokowuje sekcję krytyczną.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [struktury danych synchronizacji](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`critical_section`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>critical_section

Tworzy nową sekcję krytyczną.

```cpp
critical_section();
```

## <a name="dtor"></a>~ critical_section

Niszczy sekcję krytyczną.

```cpp
~critical_section();
```

### <a name="remarks"></a>Uwagi

Oczekuje się, że blokada nie jest już utrzymywana podczas działania destruktora. Umożliwienie sekcji krytycznej do destruktora z blokadą nadal ma wynik niezdefiniowanego zachowania.

## <a name="lock"></a>skręt

Uzyskuje tę sekcję krytyczną.

```cpp
void lock();
```

### <a name="remarks"></a>Uwagi

Często bezpieczniejsze jest wykorzystanie konstrukcji [scoped_lock](#critical_section__scoped_lock_class) do uzyskania i zwolnienia obiektu `critical_section` w bezpieczny sposób.

Jeśli blokada jest już zatrzymywana przez kontekst wywołujący, zostanie zgłoszony wyjątek [improper_lock](improper-lock-class.md) .

## <a name="native_handle"></a>native_handle

Zwraca uchwyt macierzysty specyficzny dla platformy (jeśli taki istnieje).

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do sekcji krytycznej.

### <a name="remarks"></a>Uwagi

Obiekt `critical_section` nie jest skojarzony z uchwytem natywnym specyficznym dla platformy dla systemu operacyjnego Windows. Metoda po prostu zwraca odwołanie do samego obiektu.

## <a name="critical_section__scoped_lock_class"></a>critical_section:: scoped_lock, Klasa

Wyjątek RAII bezpiecznie dla obiektu `critical_section`.

```cpp
class scoped_lock;
```

## <a name="critical_section__scoped_lock_ctor"></a>scoped_lock:: scoped_lock

Konstruuje obiekt `scoped_lock` i uzyskuje obiekt `critical_section` przesłany w parametrze `_Critical_section`. Jeśli Sekcja krytyczna jest przechowywana przez inny wątek, to wywołanie zostanie zablokowane.

```cpp
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```

### <a name="parameters"></a>Parametry

*_Critical_section*<br/>
Sekcja krytyczna do zablokowania.

## <a name="critical_section__scoped_lock_dtor"></a>scoped_lock:: ~ scoped_lock

Niszczy obiekt `scoped_lock` i zwalnia sekcję krytyczną dostarczoną w konstruktorze.

```cpp
~scoped_lock();
```

## <a name="try_lock"></a>try_lock

Próbuje uzyskać blokadę bez blokowania.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Wartość zwrócona

W przypadku pozyskania blokady wartość **true**; w przeciwnym razie wartość **false**.

## <a name="try_lock_for"></a>try_lock_for

Próbuje uzyskać blokadę bez blokowania przez określoną liczbę milisekund.

```cpp
bool try_lock_for(unsigned int _Timeout);
```

### <a name="parameters"></a>Parametry

*_Timeout*<br/>
Liczba milisekund oczekiwania przed upływem limitu czasu.

### <a name="return-value"></a>Wartość zwrócona

W przypadku pozyskania blokady wartość **true**; w przeciwnym razie wartość **false**.

## <a name="unlock"></a>odblokowania

Odblokowuje sekcję krytyczną.

```cpp
void unlock();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[reader_writer_lock, klasa](reader-writer-lock-class.md)
