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
ms.openlocfilehash: e4c38a6e1f1a1c6f4beda43ff2c055b6070258b8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222670"
---
# <a name="reader_writer_lock-class"></a>reader_writer_lock — Klasa

Blokada modułu zapisywania czytnika z preferencjami dla programu zapisywania z użyciem tylko lokalnego. Blokada przydaje pierwszy dostęp (FIFO) do składników zapisywania i starves w ramach ciągłego ładowania modułów zapisujących.

## <a name="syntax"></a>Składnia

```cpp
class reader_writer_lock;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-classes"></a>Klasy publiczne

|Nazwa|Opis|
|----------|-----------------|
|[reader_writer_lock:: scoped_lock, Klasa](#scoped_lock_class)|Wyjątek bezpieczny RAII otoki, który może służyć do uzyskiwania `reader_writer_lock` obiektów Lock jako składnika zapisywania.|
|[reader_writer_lock:: scoped_lock_read, Klasa](#scoped_lock_read_class)|Wyjątek bezpieczny RAII otoki, który może służyć do uzyskiwania `reader_writer_lock` obiektów Lock jako czytelnik.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Klasa reader_writer_lock](#ctor)|Tworzy nowy `reader_writer_lock` obiekt.|
|[~ reader_writer_lock destruktor](#dtor)|Niszczy `reader_writer_lock` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[skręt](#lock)|Uzyskuje blokadę modułu odczytującego jako składnik zapisywania.|
|[lock_read](#lock_read)|Uzyskuje blokadę modułu odczytującego jako czytelnika. Jeśli istnieją moduły zapisujące, aktywni czytelnicy muszą czekać, aż zostaną wykonane. Czytelnik po prostu rejestruje zainteresowania w blokadzie i czeka na jego wydanie przez autorów.|
|[try_lock](#try_lock)|Próbuje uzyskać blokadę modułu zapisywania czytnika jako moduł zapisujący bez blokowania.|
|[try_lock_read](#try_lock_read)|Próbuje uzyskać blokadę modułu odczytującego czytnika jako czytnik bez blokowania.|
|[odblokowania](#unlock)|Odblokowuje blokadę modułu odczytującego na podstawie osoby, która ją zablokowała, czytelnik lub składnik zapisywania.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [struktury danych synchronizacji](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`reader_writer_lock`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="lock"></a><a name="lock"></a>skręt

Uzyskuje blokadę modułu odczytującego jako składnik zapisywania.

```cpp
void lock();
```

### <a name="remarks"></a>Uwagi

Często bezpieczniejsze jest wykorzystanie konstrukcji [scoped_lock](#scoped_lock_class) w celu uzyskania i zwolnienia `reader_writer_lock` obiektu jako składnika zapisywania w bezpieczny sposób.

Gdy moduł zapisujący próbuje uzyskać blokadę, wszystkie przyszłe czytelnicy będą blokować do momentu pomyślnego pozyskania i zwolnienia blokady. Ta blokada jest obciążona wkładami autorów i może zablokować dostęp czytelników w ramach ciągłego ładowania autorów.

Moduły zapisujące są połączone w łańcuch, dzięki czemu moduł zapisujący opuszcza blokadę zwalnia Następny składnik zapisywania w wierszu.

Jeśli blokada jest już zatrzymywana przez kontekst wywołujący, zostanie zgłoszony wyjątek [improper_lock](improper-lock-class.md) .

## <a name="lock_read"></a><a name="lock_read"></a>lock_read

Uzyskuje blokadę modułu odczytującego jako czytelnika. Jeśli istnieją moduły zapisujące, aktywni czytelnicy muszą czekać, aż zostaną wykonane. Czytelnik po prostu rejestruje zainteresowania w blokadzie i czeka na jego wydanie przez autorów.

```cpp
void lock_read();
```

### <a name="remarks"></a>Uwagi

Często bezpieczniejsze jest wykorzystanie konstrukcji [scoped_lock_read](#scoped_lock_read_class) , aby uzyskać i zwolnić `reader_writer_lock` obiekt jako czytelnik w bezpieczny sposób.

W przypadku, gdy wszyscy autorzy oczekują na blokadę, czytnik zaczeka, aż wszystkie moduły zapisujące w wierszu uzyskają i udostępnią blokadę. Ta blokada jest obciążona wkładami autorów i może zablokować dostęp czytelników w ramach ciągłego ładowania autorów.

## <a name="reader_writer_lock"></a><a name="ctor"></a>reader_writer_lock

Tworzy nowy `reader_writer_lock` obiekt.

```cpp
reader_writer_lock();
```

## <a name="reader_writer_lock"></a><a name="dtor"></a>~ reader_writer_lock

Niszczy `reader_writer_lock` obiekt.

```cpp
~reader_writer_lock();
```

### <a name="remarks"></a>Uwagi

Oczekuje się, że blokada nie jest już utrzymywana podczas działania destruktora. Zezwolenie na blokadę modułu zapisywania czytnika do destruktora z blokadą nadal ma wynik niezdefiniowanego zachowania.

## <a name="reader_writer_lockscoped_lock-class"></a><a name="scoped_lock_class"></a>reader_writer_lock:: scoped_lock, Klasa

Wyjątek bezpieczny RAII otoki, który może służyć do uzyskiwania `reader_writer_lock` obiektów Lock jako składnika zapisywania.

```cpp
class scoped_lock;
```

## <a name="scoped_lockscoped_lock"></a><a name="scoped_lock_ctor"></a>scoped_lock:: scoped_lock

Konstruuje `scoped_lock` obiekt i uzyskuje `reader_writer_lock` obiekt przekazaną w `_Reader_writer_lock` parametrze jako składnik zapisywania. Jeśli blokada jest utrzymywana przez inny wątek, to wywołanie zostanie zablokowane.

```cpp
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>Parametry

*_Reader_writer_lock*<br/>
`reader_writer_lock`Obiekt, który ma zostać przejęty jako składnik zapisywania.

## <a name="scoped_lockscoped_lock"></a><a name="scoped_lock_dtor"></a>scoped_lock:: ~ scoped_lock

Niszczy `reader_writer_lock` obiekt i zwalnia blokadę podaną w konstruktorze.

```cpp
~scoped_lock();
```

## <a name="reader_writer_lockscoped_lock_read-class"></a><a name="scoped_lock_read_class"></a>reader_writer_lock:: scoped_lock_read, Klasa

Wyjątek bezpieczny RAII otoki, który może służyć do uzyskiwania `reader_writer_lock` obiektów Lock jako czytelnik.

```cpp
class scoped_lock_read;
```

## <a name="scoped_lock_readscoped_lock_read"></a><a name="scoped_lock_read_ctor"></a>scoped_lock_read:: scoped_lock_read

Konstruuje `scoped_lock_read` obiekt i uzyskuje `reader_writer_lock` obiekt przekazaną w `_Reader_writer_lock` parametrze jako czytelnik. Jeśli blokada jest utrzymywana przez inny wątek jako składnik zapisywania lub istnieją oczekujące moduły zapisujące, to wywołanie zostanie zablokowane.

```cpp
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>Parametry

*_Reader_writer_lock*<br/>
`reader_writer_lock`Obiekt, który ma zostać przejęty jako czytelnik.

## <a name="a-namescoped_lock_read_dtor--reader_writer_lockscoped_lock_readscoped_lock_read-destructor"></a><a name="scoped_lock_read_dtor">reader_writer_lock:: scoped_lock_read:: ~ scoped_lock_read destruktor

Niszczy `scoped_lock_read` obiekt i zwalnia blokadę podaną w konstruktorze.

```cpp
~scoped_lock_read();
```

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Próbuje uzyskać blokadę modułu zapisywania czytnika jako moduł zapisujący bez blokowania.

### <a name="syntax"></a>Składnia

```cpp
bool try_lock();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli blokada została uzyskana, wartość **`true`** ; w przeciwnym razie wartość **`false`** .

## <a name="try_lock_read"></a><a name="try_lock_read"></a>try_lock_read

Próbuje uzyskać blokadę modułu odczytującego czytnika jako czytnik bez blokowania.

```cpp
bool try_lock_read();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli blokada została uzyskana, wartość **`true`** ; w przeciwnym razie wartość **`false`** .

## <a name="unlock"></a><a name="unlock"></a>odblokowania

Odblokowuje blokadę modułu odczytującego na podstawie osoby, która ją zablokowała, czytelnik lub składnik zapisywania.

```cpp
void unlock();
```

### <a name="remarks"></a>Uwagi

W przypadku, gdy wszyscy autorzy oczekują na blokadę, wydanie blokady zawsze przechodzi do następnego składnika zapisywania w kolejności FIFO. Ta blokada jest obciążona wkładami autorów i może zablokować dostęp czytelników w ramach ciągłego ładowania autorów.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Klasa critical_section](critical-section-class.md)
