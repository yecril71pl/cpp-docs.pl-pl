---
title: structured_task_group — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- structured_task_group
- PPL/concurrency::structured_task_group
- PPL/concurrency::structured_task_group::structured_task_group
- PPL/concurrency::structured_task_group::cancel
- PPL/concurrency::structured_task_group::is_canceling
- PPL/concurrency::structured_task_group::run
- PPL/concurrency::structured_task_group::run_and_wait
- PPL/concurrency::structured_task_group::wait
dev_langs:
- C++
helpviewer_keywords:
- structured_task_group class
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9e87ebd4523b5211c94955b5bec7905ed848946
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161687"
---
# <a name="structuredtaskgroup-class"></a>structured_task_group — Klasa

`structured_task_group` Klasa reprezentuje uporządkowany zbiór równoległą pracę. Można kolejkować pojedynczych zadań równoległych `structured_task_group` przy użyciu `task_handle` obiekty i zaczekaj na ich zakończenie lub anulować grupę zadań zanim została zakończona, wykonywania, co spowoduje przerwanie wszystkich zadań, które nie zostały rozpoczęte wykonywanie.

## <a name="syntax"></a>Składnia

```
class structured_task_group;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[structured_task_group](#ctor)|Przeciążone. Tworzy nowy `structured_task_group` obiektu.|
|[~ structured_task_group — destruktor](#dtor)|Niszczy `structured_task_group` obiektu. Powinny wywoływać albo `wait` lub `run_and_wait` metody na obiekcie przed wykonaniem destruktora, chyba że destruktor jest wykonywany na odwijanie stosu z powodu wyjątku.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[cancel](#cancel)|Stara podjęto próbę anulowania poddrzewie pracy na tej grupy zadań. Każde zadanie zaplanowane w grupie zadań będzie uzyskać anulowane przechodni, jeśli jest to możliwe.|
|[is_canceling](#is_canceling)|Informuje obiekt wywołujący, czy grupa zadań jest obecnie w środku anulowania. Musi to oznaczać, że `cancel` metoda została wywołana na `structured_task_group` obiektu (mimo że takie kwalifikuje się bez obaw tę metodę, aby zwrócić **true**). Może być tak, `structured_task_group` obiektu jest wykonywana i wbudowana i grupy zadań, który jest dalsze się w drzewie pracy zostało anulowane. W przypadkach, takich jak tych usług, środowisko uruchomieniowe można określić anulowania będą przepływać przez to wcześniej `structured_task_group` obiektu **true** zostanie zwrócona, jak również.|
|[run](#run)|Przeciążone. Planuje zadanie na `structured_task_group` obiektu. Obiekt wywołujący zarządza czasem istnienia `task_handle` obiekt przekazany w `_Task_handle` parametru. Wersja, która przyjmuje parametr `_Placement` powoduje ukierunkowane wykonywania w lokalizacji określonej przez parametr tego zadania.|
|[run_and_wait](#run_and_wait)|Przeciążone. Planuje zadania do uruchomienia wbudowanego w kontekście wywoływania przy pomocy `structured_task_group` obiekt do obsługi pełnego anulowania. Jeśli `task_handle` obiekt jest przekazywany jako parametr do `run_and_wait`, obiekt wywołujący jest odpowiedzialny za zarządzanie okresem istnienia `task_handle` obiektu. Funkcja następnie czeka, aż wszystkie pracować nad `structured_task_group` obiektu zostało ukończone lub zostało anulowane.|
|[Czekaj](#wait)|Czeka, aż wszystkie pracować nad `structured_task_group` zostało zakończone lub zostało anulowane.|

## <a name="remarks"></a>Uwagi

Kilka poważnych ograniczeniami użycia `structured_task_group` obiektu w celu uzyskania wydajności:

- Pojedynczy `structured_task_group` obiektu nie można używać w wielu wątkach. Wszystkie operacje na `structured_task_group` obiektu muszą być wykonywane przez wątek, który utworzył obiekt. Dwa wyjątki od tej reguły są funkcje elementów członkowskich `cancel` i `is_canceling`. Obiekt nie może być na liście przechwytywania wyrażenia lambda i można używać w ramach zadania, chyba że używa jednej z operacji anulowania zadania.

- Wszystkie zadania zaplanowane do `structured_task_group` obiektu są planowane za pośrednictwem `task_handle` którego musi jawnie zarządzać okresem istnienia obiektów.

- Wiele grup można używać tylko w kolejności absolutnie zagnieżdżonych. Jeśli dwa `structured_task_group` obiekty są deklarowane, drugi deklarowanej (jeden wewnętrzny) musi niszczenia przed każdą metodę, z wyjątkiem `cancel` lub `is_canceling` jest wywoływana w pierwszy z nich (jeden zewnętrzny). Ten stan jest prawdziwe w przypadku po prostu deklarowania wielu `structured_task_group` obiektów w ramach tej samej lub funkcjonalnie zagnieżdżonych zakresów, a także w przypadku zadania, które zostało umieszczone w kolejce do `structured_task_group` za pośrednictwem `run` lub `run_and_wait` metody.

- W przeciwieństwie do ogólnych `task_group` klasy wszystkie stany w `structured_task_group` jest klasa. Gdy w kolejce zadań do grupy, a czas potrzebny na ich zakończenie, nie można używać tej samej grupie ponownie.

Aby uzyskać więcej informacji, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`structured_task_group`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ppl.h

**Namespace:** współbieżności

##  <a name="cancel"></a> Anuluj

Stara podjęto próbę anulowania poddrzewie pracy na tej grupy zadań. Każde zadanie zaplanowane w grupie zadań będzie uzyskać anulowane przechodni, jeśli jest to możliwe.

```
void cancel();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [anulowania](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

##  <a name="is_canceling"></a> is_canceling —

Informuje obiekt wywołujący, czy grupa zadań jest obecnie w środku anulowania. Musi to oznaczać, że `cancel` metoda została wywołana na `structured_task_group` obiektu (mimo że takie kwalifikuje się bez obaw tę metodę, aby zwrócić **true**). Może być tak, `structured_task_group` obiektu jest wykonywana i wbudowana i grupy zadań, który jest dalsze się w drzewie pracy zostało anulowane. W przypadkach, takich jak tych usług, środowisko uruchomieniowe można określić anulowania będą przepływać przez to wcześniej `structured_task_group` obiektu **true** zostanie zwrócona, jak również.

```
bool is_canceling();
```

### <a name="return-value"></a>Wartość zwracana

Wskazanie, czy `structured_task_group` obiekt jest w środku anulowania (lub może być wkrótce).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [anulowania](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

##  <a name="run"></a> Uruchom

Planuje zadanie na `structured_task_group` obiektu. Obiekt wywołujący zarządza czasem istnienia `task_handle` obiekt przekazany w `_Task_handle` parametru. Wersja, która przyjmuje parametr `_Placement` powoduje ukierunkowane wykonywania w lokalizacji określonej przez parametr tego zadania.

```
template<class _Function>
void run(
    task_handle<_Function>& _Task_handle);

template<class _Function>
void run(
    task_handle<_Function>& _Task_handle,
    location& _Placement);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ obiektu funkcji, która będzie wywoływana w celu wykonania treści obsługi zadań.

*_Task_handle*<br/>
Dojście do pracy, zaplanowane. Należy pamiętać, że obiekt wywołujący odpowiada za okres istnienia tego obiektu. Środowisko uruchomieniowe będzie w dalszym ciągu będzie się na żywo do momentu `wait` lub `run_and_wait` na ten zostanie wywołana metoda `structured_task_group` obiektu.

*_Umieszczenia.*<br/>
Odwołanie do lokalizacji, w którym zadanie jest reprezentowane przez `_Task_handle` parametr powinien zostać wykonany.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe tworzy kopię ta funkcja pracy, które przechodzą do tej metody. Wszelkie zmiany stanu, które występują w obiekt funkcji, które przechodzą do tej metody nie będą widoczne w swoją kopię tego obiektu funkcji.

Jeśli `structured_task_group` destructs wyniku odwijanie z wyjątku stosu, nie trzeba gwarantuje, że nawiązano połączenie na `wait` lub `run_and_wait` metody. W tym przypadku destruktor zostanie odpowiednio Anuluj i poczekaj, aż zadanie reprezentowany przez `_Task_handle` parametr w celu ukończenia.

Zgłasza [invalid_multiple_scheduling —](invalid-multiple-scheduling-class.md) wyjątek, jeśli zadanie obsługi przez `_Task_handle` parametru została zaplanowana na obiekt grupy zadań, za pośrednictwem `run` metody i nie było żadnych interwencyjnego wywołania albo `wait` lub `run_and_wait` metody dla tej grupy zadań.

##  <a name="run_and_wait"></a> run_and_wait —

Planuje zadania do uruchomienia wbudowanego w kontekście wywoływania przy pomocy `structured_task_group` obiekt do obsługi pełnego anulowania. Jeśli `task_handle` obiekt jest przekazywany jako parametr do `run_and_wait`, obiekt wywołujący jest odpowiedzialny za zarządzanie okresem istnienia `task_handle` obiektu. Funkcja następnie czeka, aż wszystkie pracować nad `structured_task_group` obiektu zostało ukończone lub zostało anulowane.

```
template<class _Function>
task_group_status run_and_wait(task_handle<_Function>& _Task_handle);

template<class _Function>
task_group_status run_and_wait(const _Function& _Func);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ obiektu funkcji, która zostanie wywołany, można wykonać zadania.

*_Task_handle*<br/>
Dojście do zadania, które jest uruchamiane wbudowane Kontekst wywołania. Należy pamiętać, że obiekt wywołujący odpowiada za okres istnienia tego obiektu. Środowisko uruchomieniowe będzie w dalszym ciągu będzie się na żywo do momentu `run_and_wait` metoda kończy działanie.

*_Func*<br/>
Funkcja, która zostanie wywołana w celu wywołania jednostkę pracy. Może to być wyrażenie lambda lub inny obiekt, który obsługuje wersję operator wywołania funkcji z podpisem `void operator()()`.

### <a name="return-value"></a>Wartość zwracana

Wskazanie, czy czas oczekiwania był zadawalający lub grupy zadań zostało anulowane z powodu operacji anulowania jawne lub wyjątek z jednego z jego zadań podrzędnych. Aby uzyskać więcej informacji, zobacz [task_group_status —](concurrency-namespace-enums.md)

### <a name="remarks"></a>Uwagi

Należy pamiętać, jednego lub więcej zadań zaplanowanych do tego `structured_task_group` obiektu może zostać wykonany wbudowane na kontekst wywołania.

Jeśli co najmniej jednego zadania zaplanowane do tego `structured_task_group` obiektu zgłasza wyjątek, środowisko uruchomieniowe zaznaczy jeden taki wyjątek, jego zalety i propagowanie go poza wywołanie `run_and_wait` metody.

Po powrocie z tej funkcji `structured_task_group` obiekt jest uważana za stan końcowy i nie powinna być używana. Należy pamiętać, że wykorzystanie po `run_and_wait` metoda zwraca wartość, spowoduje niezdefiniowane zachowanie.

W ścieżce niewyjątkowego wykonywania masz upoważnienia do obu tę metodę należy wywołać lub `wait` metody przed destruktor `structured_task_group` wykonuje.

##  <a name="ctor"></a> structured_task_group

Tworzy nowy `structured_task_group` obiektu.

```
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```

### <a name="parameters"></a>Parametry

*_CancellationToken*<br/>
Token anulowania do skojarzenia z tą grupą zadania strukturalne. Grupy wykonujący zadania strukturalne zostanie anulowane, gdy token zostanie anulowany.

### <a name="remarks"></a>Uwagi

Konstruktor, który pobiera token anulowania, tworzy `structured_task_group` , zostanie anulowane, gdy źródło skojarzone z tokenem zostało anulowane. Również zapewnienie token anulowania jawne izoluje tej grupy wykonujący zadania strukturalne z uczestnictwa w anulowanie niejawne z grupy nadrzędnej z inny token lub brak tokenu.

##  <a name="dtor"></a> ~ structured_task_group

Niszczy `structured_task_group` obiektu. Powinny wywoływać albo `wait` lub `run_and_wait` metody na obiekcie przed wykonaniem destruktora, chyba że destruktor jest wykonywany na odwijanie stosu z powodu wyjątku.

```
~structured_task_group();
```

### <a name="remarks"></a>Uwagi

Jeśli destruktor jest uruchomiony w wyniku normalnego wykonania (na przykład nie odwijanie stosu ze względu na wyjątek), a żaden z nich nie `wait` ani `run_and_wait` wywołaniu metody, destruktor może zgłaszać [missing_wait —](missing-wait-class.md) wyjątek.

##  <a name="wait"></a> Czekaj

Czeka, aż wszystkie pracować nad `structured_task_group` zostało zakończone lub zostało anulowane.

```
task_group_status wait();
```

### <a name="return-value"></a>Wartość zwracana

Wskazanie, czy czas oczekiwania był zadawalający lub grupy zadań zostało anulowane z powodu operacji anulowania jawne lub wyjątek z jednego z jego zadań podrzędnych. Aby uzyskać więcej informacji, zobacz [task_group_status —](concurrency-namespace-enums.md)

### <a name="remarks"></a>Uwagi

Należy pamiętać, jednego lub więcej zadań zaplanowanych do tego `structured_task_group` obiektu może zostać wykonany wbudowane na kontekst wywołania.

Jeśli co najmniej jednego zadania zaplanowane do tego `structured_task_group` obiektu zgłasza wyjątek, środowisko uruchomieniowe zaznaczy jeden taki wyjątek, jego zalety i propagowanie go poza wywołanie `wait` metody.

Po powrocie z tej funkcji `structured_task_group` obiekt jest uważana za stan końcowy i nie powinna być używana. Należy pamiętać, że wykorzystanie po `wait` metoda zwraca wartość, spowoduje niezdefiniowane zachowanie.

W ścieżce niewyjątkowego wykonywania masz upoważnienia do obu tę metodę należy wywołać lub `run_and_wait` metody przed destruktor `structured_task_group` wykonuje.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[task_group — klasa](task-group-class.md)<br/>
[task_handle, klasa](task-handle-class.md)
