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
ms.openlocfilehash: f7df639a879bad7af1b4de401460ff298e466c78
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215819"
---
# <a name="critical_section-class"></a>critical_section — Klasa

Niewspółpracujący obiekt mutex, który jest jawnie świadomy środowisko uruchomieniowe współbieżności.

## <a name="syntax"></a>Składnia

```cpp
class critical_section;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`native_handle_type`|Odwołanie do `critical_section` obiektu.|

### <a name="public-classes"></a>Klasy publiczne

|Nazwa|Opis|
|----------|-----------------|
|[critical_section:: scoped_lock, Klasa](#critical_section__scoped_lock_class)|Wyjątek z bezpiecznym otoką RAII dla `critical_section` obiektu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[critical_section](#ctor)|Tworzy nową sekcję krytyczną.|
|[~ critical_section destruktor](#dtor)|Niszczy sekcję krytyczną.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[skręt](#lock)|Uzyskuje tę sekcję krytyczną.|
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

## <a name="critical_section"></a><a name="ctor"></a>critical_section

Tworzy nową sekcję krytyczną.

```cpp
critical_section();
```

## <a name="critical_section"></a><a name="dtor"></a>~ critical_section

Niszczy sekcję krytyczną.

```cpp
~critical_section();
```

### <a name="remarks"></a>Uwagi

Oczekuje się, że blokada nie jest już utrzymywana podczas działania destruktora. Umożliwienie sekcji krytycznej do destruktora z blokadą nadal ma wynik niezdefiniowanego zachowania.

## <a name="lock"></a><a name="lock"></a>skręt

Uzyskuje tę sekcję krytyczną.

```cpp
void lock();
```

### <a name="remarks"></a>Uwagi

Często bezpieczniejsze jest wykorzystanie konstrukcji [scoped_lock](#critical_section__scoped_lock_class) do uzyskiwania i zwalniania `critical_section` obiektu w ramach wyjątku bezpieczny sposób.

Jeśli blokada jest już zatrzymywana przez kontekst wywołujący, zostanie zgłoszony wyjątek [improper_lock](improper-lock-class.md) .

## <a name="native_handle"></a><a name="native_handle"></a>native_handle

Zwraca uchwyt macierzysty specyficzny dla platformy (jeśli taki istnieje).

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do sekcji krytycznej.

### <a name="remarks"></a>Uwagi

`critical_section`Obiekt nie jest skojarzony z uchwytem natywnym specyficznym dla platformy dla systemu operacyjnego Windows. Metoda po prostu zwraca odwołanie do samego obiektu.

## <a name="critical_sectionscoped_lock-class"></a><a name="critical_section__scoped_lock_class"></a>critical_section:: scoped_lock, Klasa

Wyjątek z bezpiecznym otoką RAII dla `critical_section` obiektu.

```cpp
class scoped_lock;
```

## <a name="scoped_lockscoped_lock"></a><a name="critical_section__scoped_lock_ctor"></a>scoped_lock:: scoped_lock

Konstruuje `scoped_lock` obiekt i uzyskuje obiekt, który `critical_section` przeszedł do `_Critical_section` parametru. Jeśli Sekcja krytyczna jest przechowywana przez inny wątek, to wywołanie zostanie zablokowane.

```cpp
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```

### <a name="parameters"></a>Parametry

*_Critical_section*<br/>
Sekcja krytyczna do zablokowania.

## <a name="scoped_lockscoped_lock"></a><a name="critical_section__scoped_lock_dtor"></a>scoped_lock:: ~ scoped_lock

Niszczy `scoped_lock` obiekt i zwalnia sekcję krytyczną podaną w konstruktorze.

```cpp
~scoped_lock();
```

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Próbuje uzyskać blokadę bez blokowania.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli blokada została uzyskana, wartość **`true`** ; w przeciwnym razie wartość **`false`** .

## <a name="try_lock_for"></a><a name="try_lock_for"></a>try_lock_for

Próbuje uzyskać blokadę bez blokowania przez określoną liczbę milisekund.

```cpp
bool try_lock_for(unsigned int _Timeout);
```

### <a name="parameters"></a>Parametry

*_Timeout*<br/>
Liczba milisekund oczekiwania przed upływem limitu czasu.

### <a name="return-value"></a>Wartość zwracana

Jeśli blokada została uzyskana, wartość **`true`** ; w przeciwnym razie wartość **`false`** .

## <a name="unlock"></a><a name="unlock"></a>odblokowania

Odblokowuje sekcję krytyczną.

```cpp
void unlock();
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Klasa reader_writer_lock](reader-writer-lock-class.md)
