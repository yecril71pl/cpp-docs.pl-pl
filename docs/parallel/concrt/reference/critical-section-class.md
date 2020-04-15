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
ms.openlocfilehash: 24f96282a7728c6db6e0b05d36406f15383913f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372680"
---
# <a name="critical_section-class"></a>critical_section — Klasa

Obiekt mutex nieprzywrotowy, który jest jawnie świadomy środowiska wykonawczego współbieżności.

## <a name="syntax"></a>Składnia

```cpp
class critical_section;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|`native_handle_type`|Odwołanie do `critical_section` obiektu.|

### <a name="public-classes"></a>Klasy publiczne

|Nazwa|Opis|
|----------|-----------------|
|[critical_section::klasa scoped_lock](#critical_section__scoped_lock_class)|Wyjątek bezpieczne otoki RAII dla `critical_section` obiektu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[critical_section](#ctor)|Tworzy nową sekcję krytyczną.|
|[~critical_section Destruktor](#dtor)|Niszczy sekcję krytyczną.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock](#lock)|Przejmuje tę sekcję krytyczną.|
|[native_handle](#native_handle)|Zwraca dojście natywne specyficzne dla platformy, jeśli istnieje.|
|[try_lock](#try_lock)|Próbuje uzyskać blokadę bez blokowania.|
|[try_lock_for](#try_lock_for)|Próbuje uzyskać blokadę bez blokowania dla określonej liczby milisekund.|
|[Odblokować](#unlock)|Odblokowuje sekcję krytyczną.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Struktura danych synchronizacji](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`critical_section`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Przestrzeń nazw:** współbieżność

## <a name="critical_section"></a><a name="ctor"></a>Critical_section

Tworzy nową sekcję krytyczną.

```cpp
critical_section();
```

## <a name="critical_section"></a><a name="dtor"></a>~critical_section

Niszczy sekcję krytyczną.

```cpp
~critical_section();
```

### <a name="remarks"></a>Uwagi

Oczekuje się, że blokada nie jest już utrzymywana podczas pracy destruktora. Zezwalając sekcji krytycznej do destrukcji z blokady nadal przechowywane wyniki w niezdefiniowanym zachowaniu.

## <a name="lock"></a><a name="lock"></a>Blokady

Przejmuje tę sekcję krytyczną.

```cpp
void lock();
```

### <a name="remarks"></a>Uwagi

Często bezpieczniej jest korzystać z [konstrukcji scoped_lock,](#critical_section__scoped_lock_class) aby `critical_section` nabyć i zwolnić obiekt w sposób bezpieczny wyjątek.

Jeśli blokada jest już w posiadaniu kontekstu wywołującego, zostanie zgłoszony wyjątek [improper_lock.](improper-lock-class.md)

## <a name="native_handle"></a><a name="native_handle"></a>native_handle

Zwraca dojście natywne specyficzne dla platformy, jeśli istnieje.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do sekcji krytycznej.

### <a name="remarks"></a>Uwagi

Obiekt `critical_section` nie jest skojarzony z dojściem macierzystym dla systemu operacyjnego Windows specyficznym dla platformy. Metoda po prostu zwraca odwołanie do samego obiektu.

## <a name="critical_sectionscoped_lock-class"></a><a name="critical_section__scoped_lock_class"></a>critical_section::klasa scoped_lock

Wyjątek bezpieczne otoki RAII dla `critical_section` obiektu.

```cpp
class scoped_lock;
```

## <a name="scoped_lockscoped_lock"></a><a name="critical_section__scoped_lock_ctor"></a>scoped_lock::scoped_lock

Konstruuje `scoped_lock` obiekt i `critical_section` uzyskuje obiekt `_Critical_section` przekazany w parametrze. Jeśli sekcja krytyczna jest utrzymywana przez inny wątek, to wywołanie zostanie zablokowane.

```cpp
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```

### <a name="parameters"></a>Parametry

*_Critical_section*<br/>
Sekcja krytyczna do zablokowania.

## <a name="scoped_lockscoped_lock"></a><a name="critical_section__scoped_lock_dtor"></a>scoped_lock::~scoped_lock

Niszczy `scoped_lock` obiekt i zwalnia sekcji krytycznej dostarczonej w jego konstruktora.

```cpp
~scoped_lock();
```

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Próbuje uzyskać blokadę bez blokowania.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli blokada została nabyta, wartość **true**; w przeciwnym razie wartość **false**.

## <a name="try_lock_for"></a><a name="try_lock_for"></a>try_lock_for

Próbuje uzyskać blokadę bez blokowania dla określonej liczby milisekund.

```cpp
bool try_lock_for(unsigned int _Timeout);
```

### <a name="parameters"></a>Parametry

*_Timeout*<br/>
Liczba milisekund do oczekiwania przed przesuniem czasu.

### <a name="return-value"></a>Wartość zwracana

Jeśli blokada została nabyta, wartość **true**; w przeciwnym razie wartość **false**.

## <a name="unlock"></a><a name="unlock"></a>Odblokować

Odblokowuje sekcję krytyczną.

```cpp
void unlock();
```

## <a name="see-also"></a>Zobacz też

[współbieżność Obszar nazw](concurrency-namespace.md)<br/>
[Klasa reader_writer_lock](reader-writer-lock-class.md)
