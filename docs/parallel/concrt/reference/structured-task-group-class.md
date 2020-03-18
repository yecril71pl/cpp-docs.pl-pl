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
ms.openlocfilehash: 93dd79b755f79dcb4857c1b1c4856362b0bd45dd
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422130"
---
# <a name="structured_task_group-class"></a>structured_task_group — Klasa

Klasa `structured_task_group` reprezentuje wysoce strukturalną kolekcję równoległych zadań. Można kolejkować poszczególne równoległe zadania do `structured_task_group` przy użyciu obiektów `task_handle` i poczekać na ich zakończenie lub anulować grupę zadań przed zakończeniem wykonywania, co spowoduje przerwanie wszystkich zadań, które nie rozpoczęły wykonania.

## <a name="syntax"></a>Składnia

```cpp
class structured_task_group;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[structured_task_group](#ctor)|Przeciążone. Tworzy nowy obiekt `structured_task_group`.|
|[~ structured_task_group destruktor](#dtor)|Niszczy obiekt `structured_task_group`. Oczekiwane jest wywołanie metody `wait` lub `run_and_wait` w obiekcie przed wykonaniem destruktora, chyba że destruktor jest wykonywany jako wynik odwinięcia stosu z powodu wyjątku.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Anuluj](#cancel)|W ramach tej grupy zadań najlepszym etapem jest próba anulowania poddrzewa pracy z odblokowanym dostępem. Każde zadanie zaplanowane w grupie zadań zostanie anulowane przechodniie, jeśli jest to możliwe.|
|[is_canceling](#is_canceling)|Informuje obiekt wywołujący niezależnie od tego, czy grupa zadań jest obecnie w pośrodku anulowania. Nie musi to oznaczać, że metoda `cancel` została wywołana w obiekcie `structured_task_group` (chociaż na pewno ta metoda ma **wartość "true"** ). Może tak być, że obiekt `structured_task_group` wykonuje wbudowaną, a grupa zadań została anulowana w drzewie roboczym. W takich przypadkach, w których środowisko uruchomieniowe może ustalić przed czasem, gdy anulowanie będzie przepływać przez ten obiekt `structured_task_group`, zwraca **wartość true** .|
|[wykonane](#run)|Przeciążone. Planuje zadanie na obiekcie `structured_task_group`. Obiekt wywołujący zarządza okresem istnienia obiektu `task_handle` przekazaną w parametrze `_Task_handle`. Wersja, która przyjmuje parametr `_Placement` powoduje, że zadanie zostanie rozdzielone na wykonanie w lokalizacji określonej przez ten parametr.|
|[run_and_wait](#run_and_wait)|Przeciążone. Planuje uruchamianie zadania w sposób wbudowany w kontekście wywołania z pomocą obiektu `structured_task_group` w celu uzyskania pełnej obsługi anulowania. Jeśli obiekt `task_handle` jest przenoszona jako parametr do `run_and_wait`, obiekt wywołujący jest odpowiedzialny za zarządzanie okresem istnienia obiektu `task_handle`. Funkcja czeka, aż wszystkie prace na obiekcie `structured_task_group` zostaną zakończone lub anulowane.|
|[trwa](#wait)|Czeka, aż cała operacja w `structured_task_group` zostanie zakończona lub zostanie anulowana.|

## <a name="remarks"></a>Uwagi

Istnieje wiele poważnych ograniczeń dotyczących użycia obiektu `structured_task_group` w celu uzyskania wydajności:

- Jeden obiekt `structured_task_group` nie może być używany przez wiele wątków. Wszystkie operacje na obiekcie `structured_task_group` muszą być wykonywane przez wątek, który utworzył obiekt. Dwa wyjątki od tej reguły są funkcjami składowymi `cancel` i `is_canceling`. Obiekt nie może znajdować się na liście przechwytywania wyrażenia lambda i być używany w ramach zadania, chyba że zadanie używa jednej z operacji anulowania.

- Wszystkie zadania zaplanowane do `structured_task_group` obiektu są planowane przy użyciu obiektów `task_handle`, które należy jawnie zarządzać okresem istnienia.

- Wielu grup można używać tylko w Jednowierszowo zagnieżdżonej kolejności. Jeśli są zadeklarowane dwa obiekty `structured_task_group`, drugi zadeklarowany (wewnętrzny) musi być destruktorem, zanim jakakolwiek metoda z wyjątkiem `cancel` lub `is_canceling` jest wywoływana w pierwszym (zewnętrznym). Ten stan ma wartość true w obu przypadkach po prostu deklarując wiele obiektów `structured_task_group` w ramach tych samych lub funkcjonalnie zagnieżdżonych zakresów, jak również w przypadku zadania, które zostało umieszczone w kolejce do `structured_task_group` za pomocą metody `run` lub `run_and_wait`.

- W przeciwieństwie do ogólnej klasy `task_group` wszystkie stany w klasie `structured_task_group` są ostateczne. Po przypisaniu do grupy zadań w kolejce i zaczekaniu na ich zakończenie nie można ponownie używać tej samej grupy.

Aby uzyskać więcej informacji, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`structured_task_group`

## <a name="requirements"></a>Wymagania

**Nagłówek:** PPL. h

**Przestrzeń nazw:** współbieżność

## <a name="cancel"></a>Anuluj

W ramach tej grupy zadań najlepszym etapem jest próba anulowania poddrzewa pracy z odblokowanym dostępem. Każde zadanie zaplanowane w grupie zadań zostanie anulowane przechodniie, jeśli jest to możliwe.

```cpp
void cancel();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [anulowania](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="is_canceling"></a>is_canceling

Informuje obiekt wywołujący niezależnie od tego, czy grupa zadań jest obecnie w pośrodku anulowania. Nie musi to oznaczać, że metoda `cancel` została wywołana w obiekcie `structured_task_group` (chociaż na pewno ta metoda ma **wartość "true"** ). Może tak być, że obiekt `structured_task_group` wykonuje wbudowaną, a grupa zadań została anulowana w drzewie roboczym. W takich przypadkach, w których środowisko uruchomieniowe może ustalić przed czasem, gdy anulowanie będzie przepływać przez ten obiekt `structured_task_group`, zwraca **wartość true** .

```cpp
bool is_canceling();
```

### <a name="return-value"></a>Wartość zwrócona

Wskazanie, czy `structured_task_group` obiektu znajduje się w pośrodku anulowania (lub jest to wkrótce zagwarantowane).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [anulowania](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="run"></a>wykonane

Planuje zadanie na obiekcie `structured_task_group`. Obiekt wywołujący zarządza okresem istnienia obiektu `task_handle` przekazaną w parametrze `_Task_handle`. Wersja, która przyjmuje parametr `_Placement` powoduje, że zadanie zostanie rozdzielone na wykonanie w lokalizacji określonej przez ten parametr.

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
Dojście do zaplanowanych zadań. Należy zauważyć, że obiekt wywołujący odpowiada za okres istnienia tego obiektu. Środowisko uruchomieniowe będzie nadal oczekiwać na żywo do momentu wywołania metody `wait` lub `run_and_wait` w tym obiekcie `structured_task_group`.

*_Placement*<br/>
Odwołanie do lokalizacji, w której należy wykonać zadanie reprezentowane przez parametr `_Task_handle`.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe tworzy kopię funkcji pracy przekazanej do tej metody. Wszelkie zmiany stanu, które występują w obiekcie funkcji przekazywanym do tej metody nie będą wyświetlane w kopii tego obiektu funkcji.

Jeśli `structured_task_group` destruktory jako wynik odwinięcia stosu z wyjątku, nie ma potrzeby zagwarantowania, że wywołanie zostało wykonane do metody `wait` lub `run_and_wait`. W takim przypadku destruktor zostanie odpowiednio anulowany i poczeka na zakończenie zadania reprezentowanego przez `_Task_handle` parametr.

Zgłasza wyjątek [invalid_multiple_scheduling](invalid-multiple-scheduling-class.md) , jeśli uchwyt zadania określony przez parametr `_Task_handle` został już zaplanowany do obiektu grupy zadań za pośrednictwem metody `run` i nie wystąpiło wywołanie wywołujące do metody `wait` lub `run_and_wait` w tej grupie zadań.

## <a name="run_and_wait"></a>run_and_wait

Planuje uruchamianie zadania w sposób wbudowany w kontekście wywołania z pomocą obiektu `structured_task_group` w celu uzyskania pełnej obsługi anulowania. Jeśli obiekt `task_handle` jest przenoszona jako parametr do `run_and_wait`, obiekt wywołujący jest odpowiedzialny za zarządzanie okresem istnienia obiektu `task_handle`. Funkcja czeka, aż wszystkie prace na obiekcie `structured_task_group` zostaną zakończone lub anulowane.

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
Dojście do zadania, które zostanie uruchomione w tekście w kontekście wywołującym. Należy zauważyć, że obiekt wywołujący odpowiada za okres istnienia tego obiektu. Środowisko uruchomieniowe będzie nadal oczekiwać na żywo do momentu zakończenia wykonywania metody `run_and_wait`.

*_Func*<br/>
Funkcja, która zostanie wywołana w celu wywołania treści pracy. Może to być obiekt lambda lub inny, który obsługuje wersję operatora wywołania funkcji z sygnaturą `void operator()()`.

### <a name="return-value"></a>Wartość zwrócona

Wskazanie, czy oczekiwano oczekiwania, czy grupa zadań została anulowana z powodu jawnej operacji anulowania lub zgłaszania wyjątku z jednego z jego zadań. Aby uzyskać więcej informacji, zobacz [task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>Uwagi

Należy zauważyć, że co najmniej jedno z zadań zaplanowanych do tego obiektu `structured_task_group` może zostać wykonane w tekście w kontekście wywołującym.

Jeśli co najmniej jedno z zadań zaplanowanych do tego obiektu `structured_task_group` zgłosi wyjątek, środowisko uruchomieniowe wybierze jeden z tych wyjątków i propaguje go z wywołania metody `run_and_wait`.

Po powrocie tej funkcji obiekt `structured_task_group` jest brany pod uwagę w stanie końcowym i nie powinien być używany. Należy zauważyć, że użycie po zwracaniu metody `run_and_wait` spowoduje niezdefiniowane zachowanie.

W niewyjątkowej ścieżce wykonywania użytkownik ma mandat do wywołania tej metody lub metody `wait` przed wykonaniem destruktora `structured_task_group`.

## <a name="ctor"></a>structured_task_group

Tworzy nowy obiekt `structured_task_group`.

```cpp
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```

### <a name="parameters"></a>Parametry

*_CancellationToken*<br/>
Token anulowania do skojarzenia z tą strukturalną grupą zadań. Grupa zadań ze strukturą zostanie anulowana po anulowaniu tokenu.

### <a name="remarks"></a>Uwagi

Konstruktor, który pobiera token anulowania, tworzy `structured_task_group`, który zostanie anulowany, gdy źródło skojarzone z tokenem zostanie anulowane. Dostarczenie jawnego tokenu anulowania spowoduje również odizolowanie tej strukturalnej grupy zadań od uczestnictwa w niejawnym anulowaniu z grupy nadrzędnej z innym tokenem lub bez tokenu.

## <a name="dtor"></a>~ structured_task_group

Niszczy obiekt `structured_task_group`. Oczekiwane jest wywołanie metody `wait` lub `run_and_wait` w obiekcie przed wykonaniem destruktora, chyba że destruktor jest wykonywany jako wynik odwinięcia stosu z powodu wyjątku.

```cpp
~structured_task_group();
```

### <a name="remarks"></a>Uwagi

Jeśli destruktor działa w wyniku normalnego wykonywania (na przykład nie powoduje odwinięcia stosu z powodu wyjątku) i nie wywołano `wait` ani `run_and_wait` metod, destruktor może zgłosić wyjątek [missing_wait](missing-wait-class.md) .

## <a name="wait"></a>trwa

Czeka, aż cała operacja w `structured_task_group` zostanie zakończona lub zostanie anulowana.

```cpp
task_group_status wait();
```

### <a name="return-value"></a>Wartość zwrócona

Wskazanie, czy oczekiwano oczekiwania, czy grupa zadań została anulowana z powodu jawnej operacji anulowania lub zgłaszania wyjątku z jednego z jego zadań. Aby uzyskać więcej informacji, zobacz [task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>Uwagi

Należy zauważyć, że co najmniej jedno z zadań zaplanowanych do tego obiektu `structured_task_group` może zostać wykonane w tekście w kontekście wywołującym.

Jeśli co najmniej jedno z zadań zaplanowanych do tego obiektu `structured_task_group` zgłosi wyjątek, środowisko uruchomieniowe wybierze jeden z tych wyjątków i propaguje go z wywołania metody `wait`.

Po powrocie tej funkcji obiekt `structured_task_group` jest brany pod uwagę w stanie końcowym i nie powinien być używany. Należy zauważyć, że użycie po zwracaniu metody `wait` spowoduje niezdefiniowane zachowanie.

W niewyjątkowej ścieżce wykonywania użytkownik ma mandat do wywołania tej metody lub metody `run_and_wait` przed wykonaniem destruktora `structured_task_group`.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[task_group, klasa](task-group-class.md)<br/>
[task_handle, klasa](task-handle-class.md)
