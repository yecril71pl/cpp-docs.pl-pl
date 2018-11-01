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
ms.openlocfilehash: 5f358dbc61fc39928e877dbc3673a8b9f51917eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582519"
---
# <a name="taskcontinuationcontext-class"></a>task_continuation_context — Klasa

`task_continuation_context` Klasy pozwala określić, gdzie chcesz kontynuacji do wykonania. Ta jest przydatna tylko używanie tej klasy z aplikacji środowiska wykonawczego Windows. W przypadku aplikacji innych niż Windows Runtime Kontekst wykonywania kontynuacji zadania jest ustalony w czasie wykonywania i nie można konfigurować.

## <a name="syntax"></a>Składnia

```
class task_continuation_context : public details::_ContextCallback;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get_current_winrt_context](#get_current_winrt_context)|Zwraca obiekt kontekstu kontynuacji zadania, który reprezentuje bieżący kontekst wątku winrt.|
|[use_arbitrary](#use_arbitrary)|Tworzy kontekst kontynuacji zadania, co pozwala środowisko uruchomieniowe może wybierać kontekst wykonania dla kontynuacji.|
|[use_current](#use_current)|Zwraca obiekt kontekstu kontynuacji zadania, który reprezentuje bieżący kontekst wykonywania.|
|[use_default](#use_default)|Tworzy domyślny kontekst kontynuacji zadania.|
|[use_synchronous_execution](#use_synchronous_execution)|Zwraca obiekt kontekstu kontynuacji zadania, który reprezentuje Kontekst wykonywania synchronicznych.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`_ContextCallback`

`task_continuation_context`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ppltasks.h

**Namespace:** współbieżności

## <a name="get_current_winrt_context"></a> get_current_winrt_context

Zwraca obiekt kontekstu kontynuacji zadania, który reprezentuje bieżący kontekst wątku WinRT.

## <a name="syntax"></a>Składnia

```
static task_continuation_context get_current_winrt_context();
```

## <a name="return-value"></a>Wartość zwracana

Bieżący kontekst wątku środowiska wykonawczego Windows. Zwraca pusty task_continuation_context, jeśli wywołano z kontekstu innych niż Windows Runtime.

## <a name="remarks"></a>Uwagi

`get_current_winrt_context` Metoda przechwytuje kontekst wątku środowiska uruchomieniowego Windows obiektu wywołującego. Zwraca pustego kontekstu do wywoływania innego niż Windows Runtime.

Wartość zwrócona przez obiekt `get_current_winrt_context` może służyć do wskazania, kontynuacja powinna zostać wykonana w modelu typu apartment w kontekście przechwyconym (STA vs MTA), niezależnie od tego, czy zadanie poprzedzające jest rozpoznające. Rozpoznające zadanie jest zadaniem, które dekoduje środowiska uruchomieniowego Windows `IAsyncInfo` interfejs lub klasę task, która wywodzi się z takiego zadania.

Ta metoda jest podobna do `use_current` metody, ale jest również dostępny do kodu natywnego języka C++ bez C + +/ CX rozszerzenie obsługi. Służy ona używana przez zaawansowanych użytkowników pisania C + +/ CX niezależny od kodu biblioteki dla natywnych i wywołań środowiska wykonawczego Windows. Jeśli nie potrzebujesz tej funkcji, firma Microsoft zaleca `use_current` metody, która jest dostępna tylko dla C + +/ CX klientów.

##  <a name="use_arbitrary"></a> use_arbitrary —

Tworzy kontekst kontynuacji zadania, co pozwala środowisko uruchomieniowe może wybierać kontekst wykonania dla kontynuacji.

```
static task_continuation_context use_arbitrary();
```

### <a name="return-value"></a>Wartość zwracana

Kontekst kontynuacji zadania, który reprezentuje dowolne miejsce.

### <a name="remarks"></a>Uwagi

Gdy używany jest ten kontekst kontynuacji, kontynuacja będzie wykonywana w kontekście wybranym przez środowisko wykonawcze, nawet jeśli zadanie poprzedzające jest rozpoznające.

`use_arbitrary` można wyłączyć to zachowanie domyślne dla kontynuacji w zadaniu rozpoznawania komórki utworzonym w STA.

Ta metoda jest dostępna tylko dla aplikacji środowiska wykonawczego Windows.

##  <a name="use_current"></a> use_current —

Zwraca obiekt kontekstu kontynuacji zadania, który reprezentuje bieżący kontekst wykonywania.

```
static task_continuation_context use_current();
```

### <a name="return-value"></a>Wartość zwracana

Bieżący kontekst wykonywania.

### <a name="remarks"></a>Uwagi

Ta metoda przechwytuje kontekst środowiska wykonawczego Windows obiektu wywołującego tak, aby kontynuacje mogły być wykonywane we właściwej komórce.

Wartość zwrócona przez obiekt `use_current` może służyć do wskazania środowiska uruchomieniowego, że kontynuacja powinna zostać wykonana w kontekście przechwyconym (STA vs MTA) niezależnie od tego, czy zadanie poprzedzające rozpoznające. Rozpoznające zadanie jest zadaniem, które dekoduje środowiska uruchomieniowego Windows `IAsyncInfo` interfejs lub klasę task, która wywodzi się z takiego zadania.

Ta metoda jest dostępna tylko dla aplikacji środowiska wykonawczego Windows.

##  <a name="use_default"></a> use_default —

Tworzy domyślny kontekst kontynuacji zadania.

```
static task_continuation_context use_default();
```

### <a name="return-value"></a>Wartość zwracana

Domyślny kontekst kontynuacji.

### <a name="remarks"></a>Uwagi

W przeciwnym razie Określ kontekst kontynuacji po wywołaniu, używany jest kontekst domyślny `then` metody. W aplikacji Windows, Windows 7 i poniżej, a także aplikacji pulpitu w systemie Windows 8 lub nowszym środowisko wykonawcze określa, gdzie będzie wykonywać zadania kontynuacji. Jednak w aplikacji środowiska wykonawczego Windows domyślny kontekst kontynuacji dla kontynuacji w zadaniu rozpoznającym komórkę jest komórka gdzie `then` jest wywoływana.

Rozpoznające zadanie jest zadaniem, które dekoduje środowiska uruchomieniowego Windows `IAsyncInfo` interfejs lub klasę task, która wywodzi się z takiego zadania. W związku z tym jeśli zaplanujesz kontynuację w zadaniu rozpoznającym komórkę w STA środowiska wykonawczego Windows, kontynuacja zostanie wykonana w tej komórce STA.

Kontynuacja na zadaniu apartamentu będzie wykonywany w kontekście wybranym przez środowisko wykonawcze.

## <a name="use_synchronous_execution"></a> task_continuation_context::use_synchronous_execution

Zwraca obiekt kontekstu kontynuacji zadania, który reprezentuje Kontekst wykonywania synchronicznych.

## <a name="syntax"></a>Składnia

```
static task_continuation_context use_synchronous_execution();
```

## <a name="return-value"></a>Wartość zwracana

Kontekst wykonywania synchronicznych.

## <a name="remarks"></a>Uwagi

`use_synchronous_execution` Metoda wymusza zadanie kontynuacji, aby były uruchamiane synchronicznie w kontekście, co powoduje zakończenia jej zadania poprzedzającego.

Jeśli zadanie poprzedzające została już zakończona, gdy jest dołączony kontynuacji, kontynuacja jest uruchamiana synchronicznie w kontekście, który dołącza kontynuacji.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
