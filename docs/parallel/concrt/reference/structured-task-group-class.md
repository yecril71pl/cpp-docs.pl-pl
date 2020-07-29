---
title: structured_task_group — Klasa
ms.date: 11/04/2016
f1_keywords:
- structured_task_group
- PPL/concurrency::structured_task_group
- PPL/concurrency::structured_task_group::structured_task_group
- PPL/concurrency::structured_task_group::cancel
- PPL/concurrency::structured_task_group::is_canceling
- PPL/concurrency::structured_task_group::run
- PPL/concurrency::structured_task_group::run_and_wait
- PPL/concurrency::structured_task_group::wait
helpviewer_keywords:
- structured_task_group class
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
ms.openlocfilehash: 44fd2a42f4c98a569e985449f0c55102a9cbc3a6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231679"
---
# <a name="structured_task_group-class"></a>structured_task_group — Klasa

`structured_task_group`Klasa reprezentuje wysoce strukturalną kolekcję równoległych zadań. Można kolejkować poszczególne równoległe zadania do `structured_task_group` obiektów przy użyciu `task_handle` i zaczekać na ich zakończenie lub anulować grupę zadań przed zakończeniem wykonywania, co spowoduje przerwanie wszystkich zadań, które nie rozpoczęły wykonania.

## <a name="syntax"></a>Składnia

```cpp
class structured_task_group;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[structured_task_group](#ctor)|Przeciążone. Tworzy nowy `structured_task_group` obiekt.|
|[~ structured_task_group destruktor](#dtor)|Niszczy `structured_task_group` obiekt. Oczekiwane jest wywołanie `wait` `run_and_wait` metody lub dla obiektu przed wykonaniem destruktora, chyba że destruktor jest wykonywany jako wynik odwinięcia stosu z powodu wyjątku.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Anuluj](#cancel)|W ramach tej grupy zadań najlepszym etapem jest próba anulowania poddrzewa pracy z odblokowanym dostępem. Każde zadanie zaplanowane w grupie zadań zostanie anulowane przechodniie, jeśli jest to możliwe.|
|[is_canceling](#is_canceling)|Informuje obiekt wywołujący niezależnie od tego, czy grupa zadań jest obecnie w pośrodku anulowania. Nie musi to oznaczać, że `cancel` Metoda została wywołana na `structured_task_group` obiekcie (mimo że na pewno kwalifikuje się ta metoda do zwrócenia **`true`** ). Może tak być, że `structured_task_group` obiekt wykonuje wbudowaną, a grupa zadań została anulowana w drzewie roboczym. W takich przypadkach, w których środowisko uruchomieniowe może ustalić przed czasem, gdy anulowanie będzie przepływać przez ten `structured_task_group` obiekt, **`true`** również zostanie zwrócone.|
|[wykonane](#run)|Przeciążone. Planuje zadanie na `structured_task_group` obiekcie. Obiekt wywołujący zarządza okresem istnienia `task_handle` obiektu przesłanego w `_Task_handle` parametrze. Wersja, która przyjmuje parametr powoduje, że zadanie jest rozdzielone na `_Placement` wykonanie w lokalizacji określonej przez ten parametr.|
|[run_and_wait](#run_and_wait)|Przeciążone. Planuje uruchamianie zadania w sposób wbudowany w kontekście wywoływania przy użyciu `structured_task_group` obiektu do obsługi pełnego anulowania. Jeśli `task_handle` obiekt jest przekazaniem jako parametr do `run_and_wait` , obiekt wywołujący jest odpowiedzialny za zarządzanie okresem istnienia `task_handle` obiektu. Funkcja czeka, aż wszystkie prace na obiekcie zostaną `structured_task_group` zakończone lub anulowane.|
|[trwa](#wait)|Czeka, aż wszystkie prace na stronie `structured_task_group` zostały ukończone lub anulowane.|

## <a name="remarks"></a>Uwagi

Istnieje wiele poważnych ograniczeń dotyczących użycia `structured_task_group` obiektu w celu uzyskania wydajności:

- `structured_task_group`Nie można użyć pojedynczego obiektu przez wiele wątków. Wszystkie operacje na `structured_task_group` obiekcie muszą być wykonywane przez wątek, który utworzył obiekt. Dwa wyjątki od tej reguły są funkcjami składowymi `cancel` i `is_canceling` . Obiekt nie może znajdować się na liście przechwytywania wyrażenia lambda i być używany w ramach zadania, chyba że zadanie używa jednej z operacji anulowania.

- Wszystkie zadania zaplanowane do `structured_task_group` obiektu są planowane przy użyciu `task_handle` obiektów, które muszą jawnie zarządzać okresem istnienia.

- Wielu grup można używać tylko w Jednowierszowo zagnieżdżonej kolejności. Jeśli `structured_task_group` są zadeklarowane dwa obiekty, druga zadeklarowana (wewnętrzna) musi być destruktorem przed każdą metodą z wyjątkiem `cancel` lub `is_canceling` jest wywoływana na pierwszej z nich (zewnętrzny). Ten warunek ma wartość true w obu przypadkach po prostu deklarując wiele `structured_task_group` obiektów w obrębie tych samych lub funkcjonalnie zagnieżdżonych zakresów, jak również w przypadku zadania, które zostało umieszczone w kolejce `structured_task_group` przy `run` użyciu `run_and_wait` metod lub.

- W przeciwieństwie do `task_group` klasy ogólnej, wszystkie stany w `structured_task_group` klasie są ostateczne. Po przypisaniu do grupy zadań w kolejce i zaczekaniu na ich zakończenie nie można ponownie używać tej samej grupy.

Aby uzyskać więcej informacji, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`structured_task_group`

## <a name="requirements"></a>Wymagania

**Nagłówek:** PPL. h

**Przestrzeń nazw:** współbieżność

## <a name="cancel"></a><a name="cancel"></a>Anuluj

W ramach tej grupy zadań najlepszym etapem jest próba anulowania poddrzewa pracy z odblokowanym dostępem. Każde zadanie zaplanowane w grupie zadań zostanie anulowane przechodniie, jeśli jest to możliwe.

```cpp
void cancel();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [anulowania](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="is_canceling"></a><a name="is_canceling"></a>is_canceling

Informuje obiekt wywołujący niezależnie od tego, czy grupa zadań jest obecnie w pośrodku anulowania. Nie musi to oznaczać, że `cancel` Metoda została wywołana na `structured_task_group` obiekcie (mimo że na pewno kwalifikuje się ta metoda do zwrócenia **`true`** ). Może tak być, że `structured_task_group` obiekt wykonuje wbudowaną, a grupa zadań została anulowana w drzewie roboczym. W takich przypadkach, w których środowisko uruchomieniowe może ustalić przed czasem, gdy anulowanie będzie przepływać przez ten `structured_task_group` obiekt, **`true`** również zostanie zwrócone.

```cpp
bool is_canceling();
```

### <a name="return-value"></a>Wartość zwracana

Wskazanie, czy `structured_task_group` obiekt znajduje się w pośrodku anulowania (lub ma być wkrótce zagwarantowany).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [anulowania](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="run"></a><a name="run"></a>wykonane

Planuje zadanie na `structured_task_group` obiekcie. Obiekt wywołujący zarządza okresem istnienia `task_handle` obiektu przesłanego w `_Task_handle` parametrze. Wersja, która przyjmuje parametr powoduje, że zadanie jest rozdzielone na `_Placement` wykonanie w lokalizacji określonej przez ten parametr.

```cpp
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
Typ obiektu funkcji, który zostanie wywołany w celu wykonania treści uchwytu zadania.

*_Task_handle*<br/>
Dojście do zaplanowanych zadań. Należy zauważyć, że obiekt wywołujący odpowiada za okres istnienia tego obiektu. Środowisko uruchomieniowe będzie nadal oczekiwać na żywo do momentu `wait` `run_and_wait` wywołania metody lub dla tego `structured_task_group` obiektu.

*_Placement*<br/>
Odwołanie do lokalizacji, w której ma zostać wykonane zadanie reprezentowane przez `_Task_handle` parametr.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe tworzy kopię funkcji pracy przekazanej do tej metody. Wszelkie zmiany stanu, które występują w obiekcie funkcji przekazywanym do tej metody nie będą wyświetlane w kopii tego obiektu funkcji.

Jeśli `structured_task_group` destruktory jako wynik odwinięcia stosu z wyjątku, nie ma potrzeby zagwarantowania, że wywołanie zostało wykonane do `wait` `run_and_wait` metody lub. W takim przypadku destruktor zostanie odpowiednio anulowany i poczeka na ukończenie zadania reprezentowanego przez `_Task_handle` parametr.

Zgłasza wyjątek [invalid_multiple_scheduling](invalid-multiple-scheduling-class.md) , jeśli dojście zadania przekazanego przez `_Task_handle` parametr został już zaplanowany do obiektu grupy zadań za pośrednictwem `run` metody i nie istnieje wywołanie wywołujące do `wait` `run_and_wait` metody lub dla tej grupy zadań.

## <a name="run_and_wait"></a><a name="run_and_wait"></a>run_and_wait

Planuje uruchamianie zadania w sposób wbudowany w kontekście wywoływania przy użyciu `structured_task_group` obiektu do obsługi pełnego anulowania. Jeśli `task_handle` obiekt jest przekazaniem jako parametr do `run_and_wait` , obiekt wywołujący jest odpowiedzialny za zarządzanie okresem istnienia `task_handle` obiektu. Funkcja czeka, aż wszystkie prace na obiekcie zostaną `structured_task_group` zakończone lub anulowane.

```cpp
template<class _Function>
task_group_status run_and_wait(task_handle<_Function>& _Task_handle);

template<class _Function>
task_group_status run_and_wait(const _Function& _Func);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ obiektu funkcji, który zostanie wywołany w celu wykonania zadania.

*_Task_handle*<br/>
Dojście do zadania, które zostanie uruchomione w tekście w kontekście wywołującym. Należy zauważyć, że obiekt wywołujący odpowiada za okres istnienia tego obiektu. Środowisko uruchomieniowe będzie nadal oczekiwać na żywo do momentu `run_and_wait` zakończenia wykonywania metody.

*_Func*<br/>
Funkcja, która zostanie wywołana w celu wywołania treści pracy. Może to być obiekt lambda lub inny, który obsługuje wersję operatora wywołania funkcji z podpisem `void operator()()` .

### <a name="return-value"></a>Wartość zwracana

Wskazanie, czy oczekiwano oczekiwania, czy grupa zadań została anulowana z powodu jawnej operacji anulowania lub zgłaszania wyjątku z jednego z jego zadań. Aby uzyskać więcej informacji, zobacz [task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>Uwagi

Należy zauważyć, że co najmniej jedno z zadań zaplanowanych do tego `structured_task_group` obiektu może zostać wykonane w tekście w kontekście wywołującym.

Jeśli co najmniej jedno z zadań zaplanowanych dla tego `structured_task_group` obiektu zgłasza wyjątek, środowisko uruchomieniowe wybierze jeden z tych wyjątków, a następnie propaguje go z wywołania `run_and_wait` metody.

Po powrocie tej funkcji `structured_task_group` obiekt jest brany pod uwagę w stanie końcowym i nie powinien być używany. Należy zauważyć, że użycie po `run_and_wait` zwracaniu metody spowoduje niezdefiniowane zachowanie.

W niewyjątkowej ścieżce wykonywania użytkownik ma mandat do wywołania tej metody lub `wait` metody przed destruktorem `structured_task_group` wykonywanym.

## <a name="structured_task_group"></a><a name="ctor"></a>structured_task_group

Tworzy nowy `structured_task_group` obiekt.

```cpp
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```

### <a name="parameters"></a>Parametry

*_CancellationToken*<br/>
Token anulowania do skojarzenia z tą strukturalną grupą zadań. Grupa zadań ze strukturą zostanie anulowana po anulowaniu tokenu.

### <a name="remarks"></a>Uwagi

Konstruktor, który pobiera token anulowania `structured_task_group` , tworzy, który zostanie anulowany, gdy źródło skojarzone z tokenem zostanie anulowane. Dostarczenie jawnego tokenu anulowania spowoduje również odizolowanie tej strukturalnej grupy zadań od uczestnictwa w niejawnym anulowaniu z grupy nadrzędnej z innym tokenem lub bez tokenu.

## <a name="structured_task_group"></a><a name="dtor"></a>~ structured_task_group

Niszczy `structured_task_group` obiekt. Oczekiwane jest wywołanie `wait` `run_and_wait` metody lub dla obiektu przed wykonaniem destruktora, chyba że destruktor jest wykonywany jako wynik odwinięcia stosu z powodu wyjątku.

```cpp
~structured_task_group();
```

### <a name="remarks"></a>Uwagi

Jeśli destruktor działa jako wynik normalnego wykonywania (na przykład nie powoduje odwinięcia stosu ze względu na wyjątek), a metody i nie `wait` `run_and_wait` zostały wywołane, destruktor może zgłosić wyjątek [missing_wait](missing-wait-class.md) .

## <a name="wait"></a><a name="wait"></a>trwa

Czeka, aż wszystkie prace na stronie `structured_task_group` zostały ukończone lub anulowane.

```cpp
task_group_status wait();
```

### <a name="return-value"></a>Wartość zwracana

Wskazanie, czy oczekiwano oczekiwania, czy grupa zadań została anulowana z powodu jawnej operacji anulowania lub zgłaszania wyjątku z jednego z jego zadań. Aby uzyskać więcej informacji, zobacz [task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>Uwagi

Należy zauważyć, że co najmniej jedno z zadań zaplanowanych do tego `structured_task_group` obiektu może zostać wykonane w tekście w kontekście wywołującym.

Jeśli co najmniej jedno z zadań zaplanowanych dla tego `structured_task_group` obiektu zgłasza wyjątek, środowisko uruchomieniowe wybierze jeden z tych wyjątków, a następnie propaguje go z wywołania `wait` metody.

Po powrocie tej funkcji `structured_task_group` obiekt jest brany pod uwagę w stanie końcowym i nie powinien być używany. Należy zauważyć, że użycie po `wait` zwracaniu metody spowoduje niezdefiniowane zachowanie.

W niewyjątkowej ścieżce wykonywania użytkownik ma mandat do wywołania tej metody lub `run_and_wait` metody przed destruktorem `structured_task_group` wykonywanym.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Klasa task_group](task-group-class.md)<br/>
[Klasa task_handle](task-handle-class.md)
