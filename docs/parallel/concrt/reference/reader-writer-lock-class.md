---
title: reader_writer_lock — Klasa
ms.date: 11/04/2016
f1_keywords:
- reader_writer_lock
- CONCRT/concurrency::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock_read
- CONCRT/concurrency::reader_writer_lock::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::lock
- CONCRT/concurrency::reader_writer_lock::lock_read
- CONCRT/concurrency::reader_writer_lock::try_lock
- CONCRT/concurrency::reader_writer_lock::try_lock_read
- CONCRT/concurrency::reader_writer_lock::unlock
helpviewer_keywords:
- reader_writer_lock class
ms.assetid: 91a59cd2-ca05-4b74-8398-d826d9f86736
ms.openlocfilehash: 13b44387f3e9489090ec31345fe4347ff5f205ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376241"
---
# <a name="reader_writer_lock-class"></a>reader_writer_lock — Klasa

Blokada czytnika i modułu zapisującego oparta na preferencjach modułu zapisującego z lokalnym tylko się obraca. Blokada udziela pierwszy w - pierwszy out (FIFO) dostęp do pisarzy i głoduje czytelników pod ciągłym obciążeniem pisarzy.

## <a name="syntax"></a>Składnia

```cpp
class reader_writer_lock;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-classes"></a>Klasy publiczne

|Nazwa|Opis|
|----------|-----------------|
|[reader_writer_lock::klasa scoped_lock](#scoped_lock_class)|Wyjątek bezpieczne otoki RAII, które `reader_writer_lock` mogą służyć do uzyskiwania obiektów blokady jako moduł zapisujący.|
|[reader_writer_lock::klasa scoped_lock_read](#scoped_lock_read_class)|Wyjątek bezpieczne otoki RAII, które `reader_writer_lock` mogą służyć do nabycia obiektów blokady jako czytnik.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Klasa reader_writer_lock](#ctor)|Konstruuje `reader_writer_lock` nowy obiekt.|
|[~reader_writer_lock Destruktor](#dtor)|Niszczy `reader_writer_lock` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock](#lock)|Uzyskuje blokadę czytnika-pisarza jako moduł zapisujący.|
|[lock_read](#lock_read)|Uzyskuje blokadę czytnika-moduł zapisujący jako czytnik. Jeśli są autorzy, aktywni czytelnicy muszą czekać, aż zostaną wykonane. Czytelnik po prostu rejestruje zainteresowanie blokadą i czeka na pisarzy, aby go zwolnić.|
|[try_lock](#try_lock)|Próbuje uzyskać blokadę czytnika-pisarza jako moduł zapisujący bez blokowania.|
|[try_lock_read](#try_lock_read)|Próbuje uzyskać blokadę czytnika-modułu zapisującego jako czytnik bez blokowania.|
|[Odblokować](#unlock)|Odblokowuje blokadę czytnika-pisarza w oparciu o to, kto ją zablokował, czytelnik lub pisarz.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Struktura danych synchronizacji](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`reader_writer_lock`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Przestrzeń nazw:** współbieżność

## <a name="lock"></a><a name="lock"></a>Blokady

Uzyskuje blokadę czytnika-pisarza jako moduł zapisujący.

```cpp
void lock();
```

### <a name="remarks"></a>Uwagi

Często bezpieczniej jest korzystać z [konstrukcji scoped_lock](#scoped_lock_class) do `reader_writer_lock` nabycia i wydania obiektu jako modułu zapisującego w sposób bezpieczny wyjątek.

Po writer próbuje uzyskać blokadę, wszelkie przyszłych czytelników będzie blokować, dopóki autorzy pomyślnie nabyte i wydany blokady. Ten zamek jest stronniczy wobec pisarzy i może głodować czytelników pod ciągłym obciążeniem pisarzy.

Moduły zapisujące są przykuty tak, aby moduł zapisujący wychodzący z blokady zwalnia następnego modułu zapisującego w wierszu.

Jeśli blokada jest już w posiadaniu kontekstu wywołującego, zostanie zgłoszony wyjątek [improper_lock.](improper-lock-class.md)

## <a name="lock_read"></a><a name="lock_read"></a>lock_read

Uzyskuje blokadę czytnika-moduł zapisujący jako czytnik. Jeśli są autorzy, aktywni czytelnicy muszą czekać, aż zostaną wykonane. Czytelnik po prostu rejestruje zainteresowanie blokadą i czeka na pisarzy, aby go zwolnić.

```cpp
void lock_read();
```

### <a name="remarks"></a>Uwagi

Często bezpieczniej jest wykorzystać [konstrukcję scoped_lock_read](#scoped_lock_read_class) do nabycia `reader_writer_lock` i wydania obiektu jako czytnika w sposób bezpieczny jako wyjątek.

Jeśli na blokadzie czekają autorzy, czytnik będzie czekać, aż wszyscy autorzy w kolejce nabyli i zwolnili blokadę. Ten zamek jest stronniczy wobec pisarzy i może głodować czytelników pod ciągłym obciążeniem pisarzy.

## <a name="reader_writer_lock"></a><a name="ctor"></a>Reader_writer_lock

Konstruuje `reader_writer_lock` nowy obiekt.

```cpp
reader_writer_lock();
```

## <a name="reader_writer_lock"></a><a name="dtor"></a>~reader_writer_lock

Niszczy `reader_writer_lock` obiekt.

```cpp
~reader_writer_lock();
```

### <a name="remarks"></a>Uwagi

Oczekuje się, że blokada nie jest już utrzymywana podczas pracy destruktora. Zezwalając blokady modułu zapisującego czytnika do niszczenia z blokady nadal przechowywane wyniki w niezdefiniowanym zachowaniu.

## <a name="reader_writer_lockscoped_lock-class"></a><a name="scoped_lock_class"></a>reader_writer_lock::klasa scoped_lock

Wyjątek bezpieczne otoki RAII, które `reader_writer_lock` mogą służyć do uzyskiwania obiektów blokady jako moduł zapisujący.

```cpp
class scoped_lock;
```

## <a name="scoped_lockscoped_lock"></a><a name="scoped_lock_ctor"></a>scoped_lock::scoped_lock

Konstruuje `scoped_lock` obiekt i `reader_writer_lock` uzyskuje obiekt `_Reader_writer_lock` przekazany w parametrze jako moduł zapisujący. Jeśli blokada jest utrzymywana przez inny wątek, to wywołanie zostanie zablokowane.

```cpp
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>Parametry

*_Reader_writer_lock*<br/>
Obiekt `reader_writer_lock` do nabycia jako moduł zapisujący.

## <a name="scoped_lockscoped_lock"></a><a name="scoped_lock_dtor"></a>scoped_lock::~scoped_lock

Niszczy `reader_writer_lock` obiekt i zwalnia blokadę dostarczoną w jego konstruktorze.

```cpp
~scoped_lock();
```

## <a name="reader_writer_lockscoped_lock_read-class"></a><a name="scoped_lock_read_class"></a>reader_writer_lock::klasa scoped_lock_read

Wyjątek bezpieczne otoki RAII, które `reader_writer_lock` mogą służyć do nabycia obiektów blokady jako czytnik.

```cpp
class scoped_lock_read;
```

## <a name="scoped_lock_readscoped_lock_read"></a><a name="scoped_lock_read_ctor"></a>scoped_lock_read::scoped_lock_read

Konstruuje `scoped_lock_read` obiekt i `reader_writer_lock` uzyskuje obiekt `_Reader_writer_lock` przekazany w parametrze jako czytnik. Jeśli blokada jest utrzymywana przez inny wątek jako moduł zapisujący lub istnieją oczekujące moduły zapisu, to wywołanie zostanie zablokowane.

```cpp
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>Parametry

*_Reader_writer_lock*<br/>
Obiekt `reader_writer_lock` do nabycia jako czytnik.

## <a name="a-namescoped_lock_read_dtor--reader_writer_lockscoped_lock_readscoped_lock_read-destructor"></a><a name="scoped_lock_read_dtor">reader_writer_lock::scoped_lock_read::~scoped_lock_read Destruktor

Niszczy `scoped_lock_read` obiekt i zwalnia blokadę dostarczoną w jego konstruktorze.

```cpp
~scoped_lock_read();
```

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Próbuje uzyskać blokadę czytnika-pisarza jako moduł zapisujący bez blokowania.

### <a name="syntax"></a>Składnia

```cpp
bool try_lock();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli blokada została nabyta, wartość **true**; w przeciwnym razie wartość **false**.

## <a name="try_lock_read"></a><a name="try_lock_read"></a>try_lock_read

Próbuje uzyskać blokadę czytnika-modułu zapisującego jako czytnik bez blokowania.

```cpp
bool try_lock_read();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli blokada została nabyta, wartość **true**; w przeciwnym razie wartość **false**.

## <a name="unlock"></a><a name="unlock"></a>Odblokować

Odblokowuje blokadę czytnika-pisarza w oparciu o to, kto ją zablokował, czytelnik lub pisarz.

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

Jeśli istnieją autorzy czekają na blokadę, wydanie blokady zawsze przejdzie do następnego modułu zapisującego w kolejności FIFO. Ten zamek jest stronniczy wobec pisarzy i może głodować czytelników pod ciągłym obciążeniem pisarzy.

## <a name="see-also"></a>Zobacz też

[współbieżność Obszar nazw](concurrency-namespace.md)<br/>
[Klasa critical_section](critical-section-class.md)
