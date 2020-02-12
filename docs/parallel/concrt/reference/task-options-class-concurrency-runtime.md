---
title: Klasa task_options (współbieżność środowiska wykonawczego)
ms.date: 11/04/2016
f1_keywords:
- ppltasks/concurrency::task_options
ms.assetid: f93d146b-70f7-46ec-8c2f-c33b8bb0af69
ms.openlocfilehash: 5f60a07d709a79f3ce4845c8fbd1c40cb2ee7328
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142544"
---
# <a name="task_options-class-concurrency-runtime"></a>Klasa task_options (współbieżność środowiska wykonawczego)

Reprezentuje dozwolone opcje tworzenia zadania

## <a name="syntax"></a>Składnia

```cpp
class task_options;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[task_options:: task_options, Konstruktor (środowisko uruchomieniowe współbieżności)](#ctor)|Przeciążone. Domyślna lista opcji tworzenia zadań|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[task_options:: get_cancellation_token, Metoda (środowisko uruchomieniowe współbieżności)](#get_cancellation_token)|Zwraca token anulowania|
|[task_options:: get_continuation_context, Metoda (środowisko uruchomieniowe współbieżności)](#get_continuation_context)|Zwraca kontekst kontynuacji|
|[task_options:: get_scheduler, Metoda (środowisko uruchomieniowe współbieżności)](#get_scheduler)|Zwraca harmonogram|
|[task_options:: has_cancellation_token, Metoda (środowisko uruchomieniowe współbieżności)](#has_cancellation_token)|Wskazuje, czy token anulowania został określony przez użytkownika|
|[task_options:: has_scheduler, Metoda (środowisko uruchomieniowe współbieżności)](#has_scheduler)|Wskazuje, czy harmonogram n został określony przez użytkownika|
|[task_options:: set_cancellation_token, Metoda (środowisko uruchomieniowe współbieżności)](#set_cancellation_token)|Ustawia dany token w opcjach|
|[task_options:: set_continuation_context, Metoda (środowisko uruchomieniowe współbieżności)](#set_continuation_context)|Ustawia dany kontekst kontynuacji w opcjach|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`task_options`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ppltasks. h

**Przestrzeń nazw:** współbieżność

## <a name="get_cancellation_token"></a>task_options:: get_cancellation_token, Metoda (środowisko uruchomieniowe współbieżności)

Zwraca token anulowania

```cpp
cancellation_token get_cancellation_token() const;
```

### <a name="return-value"></a>Wartość zwrócona

## <a name="get_continuation_context"></a>task_options:: get_continuation_context, Metoda (środowisko uruchomieniowe współbieżności)

Zwraca kontekst kontynuacji

```cpp
task_continuation_context get_continuation_context() const;
```

### <a name="return-value"></a>Wartość zwrócona

## <a name="get_scheduler"></a>task_options:: get_scheduler, Metoda (środowisko uruchomieniowe współbieżności)

Zwraca harmonogram

```cpp
scheduler_ptr get_scheduler() const;
```

### <a name="return-value"></a>Wartość zwrócona

## <a name="has_cancellation_token"></a>task_options:: has_cancellation_token, Metoda (środowisko uruchomieniowe współbieżności)

Wskazuje, czy token anulowania został określony przez użytkownika

```cpp
bool has_cancellation_token() const;
```

### <a name="return-value"></a>Wartość zwrócona

## <a name="has_scheduler"></a>task_options:: has_scheduler, Metoda (środowisko uruchomieniowe współbieżności)

Wskazuje, czy harmonogram n został określony przez użytkownika

```cpp
bool has_scheduler() const;
```

### <a name="return-value"></a>Wartość zwrócona

## <a name="set_cancellation_token"></a>task_options:: set_cancellation_token, Metoda (środowisko uruchomieniowe współbieżności)

Ustawia dany token w opcjach

```cpp
void set_cancellation_token(cancellation_token _Token);
```

### <a name="parameters"></a>Parametry

`_Token`

## <a name="set_continuation_context"></a>task_options:: set_continuation_context, Metoda (środowisko uruchomieniowe współbieżności)

Ustawia dany kontekst kontynuacji w opcjach

```cpp
void set_continuation_context(task_continuation_context _ContinuationContext);
```

### <a name="parameters"></a>Parametry

`_ContinuationContext`

## <a name="ctor"></a>task_options:: task_options, Konstruktor (środowisko uruchomieniowe współbieżności)

Domyślna lista opcji tworzenia zadań

```cpp
task_options();

task_options(
    cancellation_token _Token);

task_options(
    task_continuation_context _ContinuationContext);

task_options(
    cancellation_token _Token,
    task_continuation_context _ContinuationContext);

template<typename _SchedType>
task_options(
    std::shared_ptr<_SchedType> _Scheduler);

task_options(
    scheduler_interface& _Scheduler);

task_options(
    scheduler_ptr _Scheduler);

task_options(
    const task_options& _TaskOptions);
```

### <a name="parameters"></a>Parametry

`_SchedType`

`_Token`

`_ContinuationContext`

`_Scheduler`

`_TaskOptions`

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
