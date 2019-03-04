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
ms.openlocfilehash: f334b159ae39f48006a135c6e36d413b737a7344
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260949"
---
# <a name="criticalsection-class"></a>critical_section — Klasa

Mutex nie obsługującą, które jest jawnie świadome współbieżności środowiska wykonawczego.

## <a name="syntax"></a>Składnia

```
class critical_section;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`native_handle_type`|Odwołanie do `critical_section` obiektu.|

### <a name="public-classes"></a>Publiczne klasy

|Nazwa|Opis|
|----------|-----------------|
|[critical_section::scoped_lock — klasa](#critical_section__scoped_lock_class)|Wyjątek bezpieczne otoka RAII na `critical_section` obiektu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[critical_section —](#ctor)|Tworzy nową sekcję krytyczną.|
|[~ critical_section — destruktor](#dtor)|Niszczy sekcję krytyczną.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[lock](#lock)|Uzyskuje w tej sekcji krytycznych.|
|[native_handle](#native_handle)|Zwraca określonego dojścia natywnego platformy, jeśli taka istnieje.|
|[try_lock](#try_lock)|Próbuje uzyskać blokady bez blokowania.|
|[try_lock_for](#try_lock_for)|Próbuje uzyskać blokady bez blokowania określoną liczbę milisekund.|
|[unlock](#unlock)|Odblokowuje sekcję krytyczną.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [struktury danych synchronizacji](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`critical_section`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności

##  <a name="ctor"></a> critical_section —

Tworzy nową sekcję krytyczną.

```
critical_section();
```

##  <a name="dtor"></a> ~ critical_section

Niszczy sekcję krytyczną.

```
~critical_section();
```

### <a name="remarks"></a>Uwagi

Oczekuje się, że blokada nie jest już przechowywany po uruchomieniu destruktora. Nadal umożliwiając sekcję krytyczną do niszczenia przy użyciu blokady przechowywane wyniki w niezdefiniowane zachowanie.

##  <a name="lock"></a> Blokady

Uzyskuje w tej sekcji krytycznych.

```
void lock();
```

### <a name="remarks"></a>Uwagi

Często jest to bezpieczniejsze korzystanie z [scoped_lock](#critical_section__scoped_lock_class) konstrukcji nabywania i zwolnij `critical_section` obiektu wyjątku bezpieczny sposób.

Jeśli blokada jest już używana przez kontekst wywołania [improper_lock —](improper-lock-class.md) zostanie zgłoszony wyjątek.

##  <a name="native_handle"></a> native_handle —

Zwraca określonego dojścia natywnego platformy, jeśli taka istnieje.

```
native_handle_type native_handle();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do sekcji krytycznych.

### <a name="remarks"></a>Uwagi

Element `critical_section` obiektu nie jest skojarzony z platform określonych natywnych dojście systemu operacyjnego Windows. Metoda po prostu zwraca odwołanie do samego obiektu.

##  <a name="critical_section__scoped_lock_class"></a>  critical_section::scoped_lock — klasa

Wyjątek bezpieczne otoka RAII na `critical_section` obiektu.

```
class scoped_lock;
```

##  <a name="critical_section__scoped_lock_ctor"></a> scoped_lock::scoped_lock

Konstruuje `scoped_lock` obiektu i uzyskuje `critical_section` obiekt przekazany w `_Critical_section` parametru. Jeśli sekcja krytycznego są przechowywane przez inny wątek, to wywołanie spowoduje zablokowanie.

```
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```

### <a name="parameters"></a>Parametry

*_Critical_section*<br/>
Sekcję krytyczną, można zablokować.

##  <a name="critical_section__scoped_lock_dtor"></a> scoped_lock:: ~ scoped_lock

Niszczy `scoped_lock` obiektu i zwalnia sekcję krytyczną, podana w jego konstruktorze.

```
~scoped_lock();
```

##  <a name="try_lock"></a> try_lock —

Próbuje uzyskać blokady bez blokowania.

```
bool try_lock();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli blokada została uzyskana, wartość **true**; w przeciwnym razie wartość **false**.

##  <a name="try_lock_for"></a> try_lock_for —

Próbuje uzyskać blokady bez blokowania określoną liczbę milisekund.

```
bool try_lock_for(unsigned int _Timeout);
```

### <a name="parameters"></a>Parametry

*_Limit czasu*<br/>
Liczba milisekund oczekiwania przed przekroczeniem limitu czasu.

### <a name="return-value"></a>Wartość zwracana

Jeśli blokada została uzyskana, wartość **true**; w przeciwnym razie wartość **false**.

##  <a name="unlock"></a> Odblokowywanie

Odblokowuje sekcję krytyczną.

```
void unlock();
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[reader_writer_lock, klasa](reader-writer-lock-class.md)
