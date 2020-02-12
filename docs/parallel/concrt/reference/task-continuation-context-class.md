---
title: task_continuation_context — Klasa
ms.date: 11/04/2016
f1_keywords:
- task_continuation_context
- PPLTASKS/concurrency::task_continuation_context
- PPLTASKS/concurrency::task_continuation_context::get_current_winrt_context
- PPLTASKS/concurrency::task_continuation_context::use_arbitrary
- PPLTASKS/concurrency::task_continuation_context::use_current
- PPLTASKS/concurrency::task_continuation_context::use_default
- PPLTASKS/concurrency::task_continuation_context::use_synchronous_execution
helpviewer_keywords:
- task_continuation_context class
ms.assetid: 1fb5a76a-3682-45c2-a615-8b6b527741f0
ms.openlocfilehash: ae8ac425f035839cdddc0b19f4f40d3b6369202a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142576"
---
# <a name="task_continuation_context-class"></a>task_continuation_context — Klasa

Klasa `task_continuation_context` pozwala określić, gdzie mają być kontynuowane. Jest to przydatne tylko w przypadku używania tej klasy z poziomu aplikacji środowisko wykonawcze systemu Windows. W przypadku aplikacji innych niż środowisko wykonawcze systemu Windows kontekst wykonywania kontynuacji zadania jest określany przez środowisko uruchomieniowe i nie można go konfigurować.

## <a name="syntax"></a>Składnia

```cpp
class task_continuation_context : public details::_ContextCallback;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[get_current_winrt_context](#get_current_winrt_context)|Zwraca obiekt kontekstu kontynuacji zadania, który reprezentuje bieżący kontekst wątku WinRT.|
|[use_arbitrary](#use_arbitrary)|Tworzy kontekst kontynuacji zadania, który umożliwia środowisko uruchomieniowe Wybieranie kontekstu wykonywania w celu kontynuacji.|
|[use_current](#use_current)|Zwraca obiekt kontekstu kontynuacji zadania, który reprezentuje bieżący kontekst wykonania.|
|[use_default](#use_default)|Tworzy domyślny kontekst kontynuacji zadania.|
|[use_synchronous_execution](#use_synchronous_execution)|Zwraca obiekt kontekstu kontynuacji zadania, który reprezentuje kontekst wykonania synchronicznego.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_ContextCallback`

`task_continuation_context`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ppltasks. h

**Przestrzeń nazw:** współbieżność

## <a name="get_current_winrt_context"></a>get_current_winrt_context

Zwraca obiekt kontekstu kontynuacji zadania, który reprezentuje bieżący kontekst wątku WinRT.

### <a name="syntax"></a>Składnia

```cpp
static task_continuation_context get_current_winrt_context();
```

### <a name="return-value"></a>Wartość zwrócona

Bieżący kontekst wątku środowisko wykonawcze systemu Windows. Zwraca puste task_continuation_context, jeśli wywołano z kontekstu nieśrodowisko wykonawcze systemu Windowsowego.

### <a name="remarks"></a>Uwagi

Metoda `get_current_winrt_context` przechwytuje kontekst wątku środowisko wykonawcze systemu Windows obiektu wywołującego. Zwraca pusty kontekst do obiektów wywołujących innych niż środowisko wykonawcze systemu Windows.

Wartość zwracana przez `get_current_winrt_context` może służyć do wskazania, że środowisko uruchomieniowe powinno być wykonywane w modelu apartamentu przechwyconego kontekstu (STA vs MTA), bez względu na to, czy zadanie poprzedzające jest oparte na komórce. Zadanie z obsługą apartamentu to zadanie, które odpakuje środowisko wykonawcze systemu Windows interfejs `IAsyncInfo`, lub zadanie, które jest z tego zadania podrzędnego.

Ta metoda jest podobna do metody `use_current`, ale jest również dostępna dla kodu natywnego C++ bez C++obsługi rozszerzenia/CX. Jest ona przeznaczona do użycia przez zaawansowanych użytkowników, C++pisząc kod biblioteki/CX-agnostic zarówno dla obiektów wywołujących natywnych, jak i środowisko wykonawcze systemu Windows. Jeśli ta funkcja jest niezbędna, zalecamy metodę `use_current`, która jest dostępna tylko dla C++klientów/CX.

## <a name="use_arbitrary"></a>use_arbitrary

Tworzy kontekst kontynuacji zadania, który umożliwia środowisko uruchomieniowe Wybieranie kontekstu wykonywania w celu kontynuacji.

### <a name="syntax"></a>Składnia

```cpp
static task_continuation_context use_arbitrary();
```

### <a name="return-value"></a>Wartość zwrócona

Kontekst kontynuacji zadania, który reprezentuje arbitralną lokalizację.

### <a name="remarks"></a>Uwagi

Gdy jest używany ten kontekst kontynuacji, kontynuacja będzie wykonywana w kontekście wybranym przez środowisko uruchomieniowe, nawet jeśli zadanie poprzedzające jest zgodne z komórkami.

`use_arbitrary` można użyć, aby wyłączyć domyślne zachowanie dla kontynuacji w zadaniu typu Apartment, które zostało utworzone w STA.

Ta metoda jest dostępna tylko dla aplikacji środowisko wykonawcze systemu Windows.

## <a name="use_current"></a>use_current

Zwraca obiekt kontekstu kontynuacji zadania, który reprezentuje bieżący kontekst wykonania.

```cpp
static task_continuation_context use_current();
```

### <a name="return-value"></a>Wartość zwrócona

Bieżący kontekst wykonania.

### <a name="remarks"></a>Uwagi

Ta metoda przechwytuje kontekst środowisko wykonawcze systemu Windows obiektu wywołującego, aby kontynuacje mogły być wykonywane w odpowiedniej apartamentie.

Wartość zwracana przez `use_current` może służyć do wskazania, że środowisko uruchomieniowe powinno zostać wykonane w przechwyconym kontekście (STA vs MTA), niezależnie od tego, czy zadanie poprzedzające jest zgodne z komórkami. Zadanie z obsługą apartamentu to zadanie, które odpakuje środowisko wykonawcze systemu Windows interfejs `IAsyncInfo`, lub zadanie, które jest z tego zadania podrzędnego.

Ta metoda jest dostępna tylko dla aplikacji środowisko wykonawcze systemu Windows.

## <a name="use_default"></a>use_default

Tworzy domyślny kontekst kontynuacji zadania.

```cpp
static task_continuation_context use_default();
```

### <a name="return-value"></a>Wartość zwrócona

Domyślny kontekst kontynuacji.

### <a name="remarks"></a>Uwagi

Domyślny kontekst jest używany, jeśli nie określisz kontekstu kontynuacji podczas wywoływania metody `then`. W aplikacjach systemu Windows dla systemu Windows 7 i nowszych, a także aplikacji klasycznych w systemie Windows 8 lub nowszym, środowisko uruchomieniowe określa, gdzie będą wykonywane kontynuacje zadań. Jednak w aplikacji środowisko wykonawcze systemu Windows domyślny kontekst kontynuacji dla kontynuacji w zadaniu typu Apartment jest obiektem komórkowym, w którym `then` jest wywoływana.

Zadanie z obsługą apartamentu to zadanie, które odpakuje środowisko wykonawcze systemu Windows interfejs `IAsyncInfo`, lub zadanie, które jest z tego zadania podrzędnego. W związku z tym w przypadku zaplanowania kontynuacji w zadaniu typu Apartment w środowisko wykonawcze systemu Windows STA, kontynuacja zostanie wykonana w tym STA.

Kontynuacja w zadaniu niezależnym od apartamentu zostanie wykonana w kontekście wybranym przez środowisko uruchomieniowe.

## <a name="use_synchronous_execution"></a>task_continuation_context:: use_synchronous_execution

Zwraca obiekt kontekstu kontynuacji zadania, który reprezentuje kontekst wykonania synchronicznego.

### <a name="syntax"></a>Składnia

```cpp
static task_continuation_context use_synchronous_execution();
```

### <a name="return-value"></a>Wartość zwrócona

Kontekst wykonywania synchronicznego.

### <a name="remarks"></a>Uwagi

Metoda `use_synchronous_execution` wymusza, aby zadanie kontynuacji zostało uruchomione synchronicznie w kontekście, co powoduje ukończenie zadania poprzedzającego.

Jeśli zadanie poprzedzające zostało już zakończone po dołączeniu kontynuacji, kontynuacja przebiega synchronicznie w kontekście, który dołącza kontynuację.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
