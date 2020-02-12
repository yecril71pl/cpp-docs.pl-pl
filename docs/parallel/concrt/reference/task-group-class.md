---
title: task_group — Klasa
ms.date: 07/20/2018
f1_keywords:
- task_group
- PPL/concurrency::task_group
- PPL/concurrency::task_group::task_group
helpviewer_keywords:
- task_group class
ms.openlocfilehash: 60c147f38ddc3936f47aea0cfd1ab1548b382441
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142566"
---
# <a name="task_group-class"></a>task_group — Klasa

Klasa `task_group` reprezentuje kolekcję równoległych zadań, które mogą być oczekiwane lub anulowane.

## <a name="syntax"></a>Składnia

```cpp
class task_group;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[task_group](#ctor)|Przeciążone. Tworzy nowy obiekt `task_group`.|
|[~ task_group destruktor](#dtor)|Niszczy obiekt `task_group`. Oczekiwane jest wywołanie metody `wait` lub `run_and_wait` w obiekcie przed wykonaniem destruktora, chyba że destruktor jest wykonywany jako wynik odwinięcia stosu z powodu wyjątku.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Anuluj](#cancel)|W ramach tej grupy zadań najlepszym etapem jest próba anulowania poddrzewa pracy z odblokowanym dostępem. Każde zadanie zaplanowane w grupie zadań zostanie anulowane przechodniie, jeśli jest to możliwe.|
|[is_canceling](#is_canceling)|Informuje obiekt wywołujący niezależnie od tego, czy grupa zadań jest obecnie w pośrodku anulowania. Nie musi to oznaczać, że metoda `cancel` została wywołana w obiekcie `task_group` (mimo że na pewno ta metoda jest zgodna z `true`). Może tak być, że obiekt `task_group` wykonuje wbudowaną, a grupa zadań została anulowana w drzewie roboczym. W takich przypadkach, w których środowisko uruchomieniowe może ustalić przed czasem, gdy anulowanie będzie przepływać przez ten obiekt `task_group`, `true` również zostanie zwrócone.|
|[wykonane](#run)|Przeciążone. Planuje zadanie na obiekcie `task_group`. Jeśli obiekt `task_handle` jest przenoszona jako parametr do `run`, obiekt wywołujący jest odpowiedzialny za zarządzanie okresem istnienia obiektu `task_handle`. Wersja metody, która pobiera odwołanie do obiektu funkcji jako parametr, obejmuje alokację sterty wewnątrz środowiska uruchomieniowego, co może być wykonane mniej dobrze niż przy użyciu wersji, która pobiera odwołanie do obiektu `task_handle`. Wersja, która przyjmuje parametr `_Placement` powoduje, że zadanie zostanie rozdzielone na wykonanie w lokalizacji określonej przez ten parametr.|
|[run_and_wait](#run_and_wait)|Przeciążone. Planuje uruchamianie zadania w sposób wbudowany w kontekście wywołania z pomocą obiektu `task_group` w celu uzyskania pełnej obsługi anulowania. Funkcja czeka, aż wszystkie prace na obiekcie `task_group` zostaną zakończone lub anulowane. Jeśli obiekt `task_handle` jest przenoszona jako parametr do `run_and_wait`, obiekt wywołujący jest odpowiedzialny za zarządzanie okresem istnienia obiektu `task_handle`.|
|[trwa](#wait)|Czeka, aż wszystkie prace na obiekcie `task_group` zostaną zakończone lub anulowane.|

## <a name="remarks"></a>Uwagi

W przeciwieństwie do mocno ograniczonej klasy `structured_task_group`, Klasa `task_group` jest znacznie bardziej ogólna konstrukcja. Nie ma żadnych ograniczeń opisanych przez [structured_task_group](structured-task-group-class.md). obiekty `task_group` mogą być bezpiecznie używane między wątkami i wykorzystane w sposób niezależny. Wadą konstrukcji `task_group` jest to, że może nie działać, a także konstrukcja `structured_task_group` dla zadań, które wykonują niewielkie ilości pracy.

Aby uzyskać więcej informacji, zobacz [równoległość zadań](../task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`task_group`

## <a name="requirements"></a>Wymagania

**Nagłówek:** PPL. h

**Przestrzeń nazw:** współbieżność

## <a name="cancel"></a>Anuluj

W ramach tej grupy zadań najlepszym etapem jest próba anulowania poddrzewa pracy z odblokowanym dostępem. Każde zadanie zaplanowane w grupie zadań zostanie anulowane przechodniie, jeśli jest to możliwe.

```cpp
void cancel();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [anulowania](../cancellation-in-the-ppl.md).

## <a name="is_canceling"></a>is_canceling

Informuje obiekt wywołujący niezależnie od tego, czy grupa zadań jest obecnie w pośrodku anulowania. Nie musi to oznaczać, że metoda `cancel` została wywołana w obiekcie `task_group` (mimo że na pewno ta metoda jest zgodna z `true`). Może tak być, że obiekt `task_group` wykonuje wbudowaną, a grupa zadań została anulowana w drzewie roboczym. W takich przypadkach, w których środowisko uruchomieniowe może ustalić przed czasem, gdy anulowanie będzie przepływać przez ten obiekt `task_group`, `true` również zostanie zwrócone.

```cpp
bool is_canceling();
```

### <a name="return-value"></a>Wartość zwrócona

Wskazanie, czy `task_group` obiektu znajduje się w pośrodku anulowania (lub jest to wkrótce zagwarantowane).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [anulowania](../cancellation-in-the-ppl.md).

## <a name="run"></a>wykonane

Planuje zadanie na obiekcie `task_group`. Jeśli obiekt `task_handle` jest przenoszona jako parametr do `run`, obiekt wywołujący jest odpowiedzialny za zarządzanie okresem istnienia obiektu `task_handle`. Wersja metody, która pobiera odwołanie do obiektu funkcji jako parametr, obejmuje alokację sterty wewnątrz środowiska uruchomieniowego, co może być wykonane mniej dobrze niż przy użyciu wersji, która pobiera odwołanie do obiektu `task_handle`. Wersja, która przyjmuje parametr `_Placement` powoduje, że zadanie zostanie rozdzielone na wykonanie w lokalizacji określonej przez ten parametr.

```cpp
template<
   typename _Function
>
void run(
   const _Function& _Func
);

template<
   typename _Function
>
void run(
   const _Function& _Func,
   location& _Placement
);

template<
   typename _Function
>
void run(
   task_handle<_Function>& _Task_handle
);

template<
   typename _Function
>
void run(
   task_handle<_Function>& _Task_handle,
   location& _Placement
);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ obiektu funkcji, który zostanie wywołany w celu wykonania treści uchwytu zadania.

*_Func*<br/>
Funkcja, która zostanie wywołana w celu wywołania treści zadania. Może to być wyrażenie lambda lub inny obiekt, który obsługuje wersję operatora wywołania funkcji z sygnaturą `void operator()()`.

*_Placement*<br/>
Odwołanie do lokalizacji, w której należy wykonać zadanie reprezentowane przez parametr `_Func`.

*_Task_handle*<br/>
Dojście do zaplanowanych zadań. Należy zauważyć, że obiekt wywołujący odpowiada za okres istnienia tego obiektu. Środowisko uruchomieniowe będzie nadal oczekiwać na żywo do momentu wywołania metody `wait` lub `run_and_wait` w tym obiekcie `task_group`.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe planuje uruchomienie podanej funkcji roboczej w późniejszym czasie, która może być po powrocie funkcji wywołującej. Ta metoda używa obiektu [task_handle](task-handle-class.md) do przechowywania kopii podanej funkcji służbowej. W związku z tym wszelkie zmiany stanu, które występują w obiekcie funkcji przekazywanym do tej metody, nie będą wyświetlane w kopii tego obiektu funkcji. Ponadto należy się upewnić, że okres istnienia wszystkich obiektów przekazywanych przez wskaźnik lub przez odwołanie do funkcji służbowej pozostanie ważny do momentu, gdy funkcja pracy zwróci wartość.

Jeśli `task_group` destruktory jako wynik odwinięcia stosu z wyjątku, nie ma potrzeby zagwarantowania, że wywołanie zostało wykonane do metody `wait` lub `run_and_wait`. W takim przypadku destruktor zostanie odpowiednio anulowany i poczeka na zakończenie zadania reprezentowanego przez `_Task_handle` parametr.

Metoda zgłasza wyjątek [invalid_multiple_scheduling](invalid-multiple-scheduling-class.md) , jeśli uchwyt zadania określony przez parametr `_Task_handle` został już zaplanowany do obiektu grupy zadań za pośrednictwem metody `run` i nie istnieje wywołanie wywołujące do metody `wait` lub `run_and_wait` w tej grupie zadań.

## <a name="run_and_wait"></a>run_and_wait

Planuje uruchamianie zadania w sposób wbudowany w kontekście wywołania z pomocą obiektu `task_group` w celu uzyskania pełnej obsługi anulowania. Funkcja czeka, aż wszystkie prace na obiekcie `task_group` zostaną zakończone lub anulowane. Jeśli obiekt `task_handle` jest przenoszona jako parametr do `run_and_wait`, obiekt wywołujący jest odpowiedzialny za zarządzanie okresem istnienia obiektu `task_handle`.

```cpp
template<
   class _Function
>
task_group_status run_and_wait(
   task_handle<_Function>& _Task_handle
);

template<
   class _Function
>
task_group_status run_and_wait(
   const _Function& _Func
);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ obiektu funkcji, który zostanie wywołany, aby wykonać treść zadania.

*_Task_handle*<br/>
Dojście do zadania, które zostanie uruchomione w tekście w kontekście wywołującym. Należy zauważyć, że obiekt wywołujący odpowiada za okres istnienia tego obiektu. Środowisko uruchomieniowe będzie nadal oczekiwać na żywo do momentu zakończenia wykonywania metody `run_and_wait`.

*_Func*<br/>
Funkcja, która zostanie wywołana w celu wywołania treści pracy. Może to być wyrażenie lambda lub inny obiekt, który obsługuje wersję operatora wywołania funkcji z sygnaturą `void operator()()`.

### <a name="return-value"></a>Wartość zwrócona

Wskazanie, czy oczekiwano oczekiwania, czy grupa zadań została anulowana z powodu jawnej operacji anulowania lub zgłaszania wyjątku z jednego z jego zadań. Aby uzyskać więcej informacji, zobacz [task_group_status](concurrency-namespace-enums.md#task_group_status).

### <a name="remarks"></a>Uwagi

Należy zauważyć, że co najmniej jedno z zadań zaplanowanych do tego obiektu `task_group` może zostać wykonane w tekście w kontekście wywołującym.

Jeśli co najmniej jedno z zadań zaplanowanych do tego obiektu `task_group` zgłosi wyjątek, środowisko uruchomieniowe wybierze jeden z tych wyjątków i propaguje go z wywołania metody `run_and_wait`.

Po powrocie z metody `run_and_wait` na obiekcie `task_group` środowisko uruchomieniowe resetuje obiekt do stanu czystego, gdzie można go ponownie użyć. Obejmuje to przypadek, w którym obiekt `task_group` został anulowany.

W niewyjątkowej ścieżce wykonywania użytkownik ma mandat do wywołania tej metody lub metody `wait` przed wykonaniem destruktora `task_group`.

## <a name="ctor"></a>task_group

Tworzy nowy obiekt `task_group`.

```cpp
task_group();

task_group(
   cancellation_token _CancellationToken
);
```

### <a name="parameters"></a>Parametry

*_CancellationToken*<br/>
Token anulowania, który ma zostać skojarzony z tą grupą zadań. Po anulowaniu tokenu grupa zadań zostanie anulowana.

### <a name="remarks"></a>Uwagi

Konstruktor, który pobiera token anulowania, tworzy `task_group`, który zostanie anulowany, gdy źródło skojarzone z tokenem zostanie anulowane. Dostarczenie jawnego tokenu anulowania spowoduje również wyodrębnienie tej grupy zadań z uczestnictwa w niejawnym anulowaniu z grupy nadrzędnej z innym tokenem lub bez tokenu.

## <a name="dtor"></a>~ task_group

Niszczy obiekt `task_group`. Oczekiwane jest wywołanie metody `wait` lub `run_and_wait` w obiekcie przed wykonaniem destruktora, chyba że destruktor jest wykonywany jako wynik odwinięcia stosu z powodu wyjątku.

```cpp
~task_group();
```

### <a name="remarks"></a>Uwagi

Jeśli destruktor działa w wyniku normalnego wykonywania (na przykład nie powoduje odwinięcia stosu z powodu wyjątku) i nie wywołano `wait` ani `run_and_wait` metod, destruktor może zgłosić wyjątek [missing_wait](missing-wait-class.md) .

## <a name="wait"></a>trwa

Czeka, aż wszystkie prace na obiekcie `task_group` zostaną zakończone lub anulowane.

```cpp
task_group_status wait();
```

### <a name="return-value"></a>Wartość zwrócona

Wskazanie, czy oczekiwano oczekiwania, czy grupa zadań została anulowana z powodu jawnej operacji anulowania lub zgłaszania wyjątku z jednego z jego zadań. Aby uzyskać więcej informacji, zobacz [task_group_status](concurrency-namespace-enums.md#task_group_status).

### <a name="remarks"></a>Uwagi

Należy zauważyć, że co najmniej jedno z zadań zaplanowanych do tego obiektu `task_group` może zostać wykonane w tekście w kontekście wywołującym.

Jeśli co najmniej jedno z zadań zaplanowanych do tego obiektu `task_group` zgłosi wyjątek, środowisko uruchomieniowe wybierze jeden z tych wyjątków i propaguje go z wywołania metody `wait`.

Wywołanie `wait` na obiekcie `task_group` powoduje zresetowanie go do stanu czystego, w którym można go ponownie użyć. Obejmuje to przypadek, w którym obiekt `task_group` został anulowany.

W niewyjątkowej ścieżce wykonywania użytkownik ma mandat do wywołania tej metody lub metody `run_and_wait` przed wykonaniem destruktora `task_group`.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[structured_task_group, klasa](structured-task-group-class.md)<br/>
[task_handle, klasa](task-handle-class.md)
