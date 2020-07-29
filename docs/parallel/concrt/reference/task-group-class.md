---
title: task_group — Klasa
ms.date: 07/20/2018
f1_keywords:
- task_group
- PPL/concurrency::task_group
- PPL/concurrency::task_group::task_group
helpviewer_keywords:
- task_group class
ms.openlocfilehash: 4d11a7fc25d95884418a3062721df75cc11be520
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224958"
---
# <a name="task_group-class"></a>task_group — Klasa

`task_group`Klasa reprezentuje kolekcję równoległych zadań, które mogą być oczekiwane lub anulowane.

## <a name="syntax"></a>Składnia

```cpp
class task_group;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[task_group](#ctor)|Przeciążone. Tworzy nowy `task_group` obiekt.|
|[~ task_group destruktor](#dtor)|Niszczy `task_group` obiekt. Oczekiwane jest wywołanie `wait` `run_and_wait` metody lub obiektu przed wykonaniem destruktora, chyba że destruktor jest wykonywany jako wynik odwinięcia stosu z powodu wyjątku.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Anuluj](#cancel)|W ramach tej grupy zadań najlepszym etapem jest próba anulowania poddrzewa pracy z odblokowanym dostępem. Każde zadanie zaplanowane w grupie zadań zostanie anulowane przechodniie, jeśli jest to możliwe.|
|[is_canceling](#is_canceling)|Informuje obiekt wywołujący niezależnie od tego, czy grupa zadań jest obecnie w pośrodku anulowania. Nie musi to oznaczać, że `cancel` Metoda została wywołana na `task_group` obiekcie (mimo że na pewno kwalifikuje się ta metoda do zwrócenia **`true`** ). Może tak być, że `task_group` obiekt wykonuje wbudowaną, a grupa zadań została anulowana w drzewie roboczym. W takich przypadkach, w których środowisko uruchomieniowe może ustalić przed czasem, gdy anulowanie będzie przepływać przez ten `task_group` obiekt, **`true`** również zostanie zwrócone.|
|[wykonane](#run)|Przeciążone. Planuje zadanie na `task_group` obiekcie. Jeśli `task_handle` obiekt jest przekazaniem jako parametr do `run` , obiekt wywołujący jest odpowiedzialny za zarządzanie okresem istnienia `task_handle` obiektu. Wersja metody, która pobiera odwołanie do obiektu funkcji jako parametr, obejmuje alokację sterty wewnątrz środowiska uruchomieniowego, co może być wykonane mniej dobrze niż przy użyciu wersji, która pobiera odwołanie do `task_handle` obiektu. Wersja, która pobiera parametr `_Placement` powoduje, że zadanie jest rozdzielone na wykonanie w lokalizacji określonej przez ten parametr.|
|[run_and_wait](#run_and_wait)|Przeciążone. Planuje uruchamianie zadania w sposób wbudowany w kontekście wywoływania przy użyciu `task_group` obiektu do obsługi pełnego anulowania. Funkcja czeka, aż wszystkie prace na obiekcie zostaną `task_group` zakończone lub anulowane. Jeśli `task_handle` obiekt jest przekazaniem jako parametr do `run_and_wait` , obiekt wywołujący jest odpowiedzialny za zarządzanie okresem istnienia `task_handle` obiektu.|
|[trwa](#wait)|Czeka, aż wszystkie prace na `task_group` obiekcie zostaną zakończone lub anulowane.|

## <a name="remarks"></a>Uwagi

W przeciwieństwie do mocno ograniczonej `structured_task_group` klasy Klasa `task_group` jest znacznie bardziej ogólna konstrukcja. Nie ma żadnych ograniczeń opisanych przez [structured_task_group](structured-task-group-class.md). `task_group`obiekty mogą być bezpiecznie używane między wątkami i wykorzystane w sposób niezależny. Wadą `task_group` konstrukcji jest to, że może nie działać, a także `structured_task_group` konstrukcja dla zadań, które wykonują niewielkie ilości pracy.

Aby uzyskać więcej informacji, zobacz [równoległość zadań](../task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`task_group`

## <a name="requirements"></a>Wymagania

**Nagłówek:** PPL. h

**Przestrzeń nazw:** współbieżność

## <a name="cancel"></a><a name="cancel"></a>Anuluj

W ramach tej grupy zadań najlepszym etapem jest próba anulowania poddrzewa pracy z odblokowanym dostępem. Każde zadanie zaplanowane w grupie zadań zostanie anulowane przechodniie, jeśli jest to możliwe.

```cpp
void cancel();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [anulowania](../cancellation-in-the-ppl.md).

## <a name="is_canceling"></a><a name="is_canceling"></a>is_canceling

Informuje obiekt wywołujący niezależnie od tego, czy grupa zadań jest obecnie w pośrodku anulowania. Nie musi to oznaczać, że `cancel` Metoda została wywołana na `task_group` obiekcie (mimo że na pewno kwalifikuje się ta metoda do zwrócenia **`true`** ). Może tak być, że `task_group` obiekt wykonuje wbudowaną, a grupa zadań została anulowana w drzewie roboczym. W takich przypadkach, w których środowisko uruchomieniowe może ustalić przed czasem, gdy anulowanie będzie przepływać przez ten `task_group` obiekt, **`true`** również zostanie zwrócone.

```cpp
bool is_canceling();
```

### <a name="return-value"></a>Wartość zwracana

Wskazanie, czy `task_group` obiekt znajduje się w pośrodku anulowania (lub ma być wkrótce zagwarantowany).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [anulowania](../cancellation-in-the-ppl.md).

## <a name="run"></a><a name="run"></a>wykonane

Planuje zadanie na `task_group` obiekcie. Jeśli `task_handle` obiekt jest przekazaniem jako parametr do `run` , obiekt wywołujący jest odpowiedzialny za zarządzanie okresem istnienia `task_handle` obiektu. Wersja metody, która pobiera odwołanie do obiektu funkcji jako parametr, obejmuje alokację sterty wewnątrz środowiska uruchomieniowego, co może być wykonane mniej dobrze niż przy użyciu wersji, która pobiera odwołanie do `task_handle` obiektu. Wersja, która pobiera parametr `_Placement` powoduje, że zadanie jest rozdzielone na wykonanie w lokalizacji określonej przez ten parametr.

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
Funkcja, która zostanie wywołana w celu wywołania treści zadania. Może to być wyrażenie lambda lub inny obiekt, który obsługuje wersję operatora wywołania funkcji z podpisem `void operator()()` .

*_Placement*<br/>
Odwołanie do lokalizacji, w której ma zostać wykonane zadanie reprezentowane przez `_Func` parametr.

*_Task_handle*<br/>
Dojście do zaplanowanych zadań. Należy zauważyć, że obiekt wywołujący odpowiada za okres istnienia tego obiektu. Środowisko uruchomieniowe będzie nadal oczekiwać na żywo do momentu `wait` `run_and_wait` wywołania metody lub dla tego `task_group` obiektu.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe planuje uruchomienie podanej funkcji roboczej w późniejszym czasie, która może być po powrocie funkcji wywołującej. Ta metoda używa obiektu [task_handle](task-handle-class.md) do przechowywania kopii podanej funkcji służbowej. W związku z tym wszelkie zmiany stanu, które występują w obiekcie funkcji przekazywanym do tej metody, nie będą wyświetlane w kopii tego obiektu funkcji. Ponadto należy się upewnić, że okres istnienia wszystkich obiektów przekazywanych przez wskaźnik lub przez odwołanie do funkcji służbowej pozostanie ważny do momentu, gdy funkcja pracy zwróci wartość.

Jeśli `task_group` destruktory jako wynik odwinięcia stosu z wyjątku, nie ma potrzeby zagwarantowania, że wywołanie zostało wykonane do `wait` `run_and_wait` metody lub. W takim przypadku destruktor zostanie odpowiednio anulowany i poczeka na ukończenie zadania reprezentowanego przez `_Task_handle` parametr.

Metoda zgłasza wyjątek [invalid_multiple_scheduling](invalid-multiple-scheduling-class.md) , jeśli dojście zadania przekazanego przez `_Task_handle` parametr został już zaplanowany do obiektu grupy zadań za pośrednictwem `run` metody i nie istnieje wywołanie wywołujące do `wait` `run_and_wait` metody lub dla tej grupy zadań.

## <a name="run_and_wait"></a><a name="run_and_wait"></a>run_and_wait

Planuje uruchamianie zadania w sposób wbudowany w kontekście wywoływania przy użyciu `task_group` obiektu do obsługi pełnego anulowania. Funkcja czeka, aż wszystkie prace na obiekcie zostaną `task_group` zakończone lub anulowane. Jeśli `task_handle` obiekt jest przekazaniem jako parametr do `run_and_wait` , obiekt wywołujący jest odpowiedzialny za zarządzanie okresem istnienia `task_handle` obiektu.

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
Dojście do zadania, które zostanie uruchomione w tekście w kontekście wywołującym. Należy zauważyć, że obiekt wywołujący odpowiada za okres istnienia tego obiektu. Środowisko uruchomieniowe będzie nadal oczekiwać na żywo do momentu `run_and_wait` zakończenia wykonywania metody.

*_Func*<br/>
Funkcja, która zostanie wywołana w celu wywołania treści pracy. Może to być wyrażenie lambda lub inny obiekt, który obsługuje wersję operatora wywołania funkcji z podpisem `void operator()()` .

### <a name="return-value"></a>Wartość zwracana

Wskazanie, czy oczekiwano oczekiwania, czy grupa zadań została anulowana z powodu jawnej operacji anulowania lub zgłaszania wyjątku z jednego z jego zadań. Aby uzyskać więcej informacji, zobacz [task_group_status](concurrency-namespace-enums.md#task_group_status).

### <a name="remarks"></a>Uwagi

Należy zauważyć, że co najmniej jedno z zadań zaplanowanych do tego `task_group` obiektu może zostać wykonane w tekście w kontekście wywołującym.

Jeśli co najmniej jedno z zadań zaplanowanych dla tego `task_group` obiektu zgłasza wyjątek, środowisko uruchomieniowe wybierze jeden z tych wyjątków, a następnie propaguje go z wywołania `run_and_wait` metody.

Po powrocie z `run_and_wait` metody na `task_group` obiekcie środowisko uruchomieniowe resetuje obiekt do stanu czystego, gdzie można go ponownie użyć. Obejmuje to przypadek, w którym `task_group` obiekt został anulowany.

W niewyjątkowej ścieżce wykonywania użytkownik ma mandat do wywołania tej metody lub `wait` metody przed destruktorem `task_group` wykonywanym.

## <a name="task_group"></a><a name="ctor"></a>task_group

Tworzy nowy `task_group` obiekt.

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

Konstruktor, który pobiera token anulowania `task_group` , tworzy, który zostanie anulowany, gdy źródło skojarzone z tokenem zostanie anulowane. Dostarczenie jawnego tokenu anulowania spowoduje również wyodrębnienie tej grupy zadań z uczestnictwa w niejawnym anulowaniu z grupy nadrzędnej z innym tokenem lub bez tokenu.

## <a name="task_group"></a><a name="dtor"></a>~ task_group

Niszczy `task_group` obiekt. Oczekiwane jest wywołanie `wait` `run_and_wait` metody lub obiektu przed wykonaniem destruktora, chyba że destruktor jest wykonywany jako wynik odwinięcia stosu z powodu wyjątku.

```cpp
~task_group();
```

### <a name="remarks"></a>Uwagi

Jeśli destruktor działa jako wynik normalnego wykonywania (na przykład nie powoduje odwinięcia stosu ze względu na wyjątek), a metody i nie `wait` `run_and_wait` zostały wywołane, destruktor może zgłosić wyjątek [missing_wait](missing-wait-class.md) .

## <a name="wait"></a><a name="wait"></a>trwa

Czeka, aż wszystkie prace na `task_group` obiekcie zostaną zakończone lub anulowane.

```cpp
task_group_status wait();
```

### <a name="return-value"></a>Wartość zwracana

Wskazanie, czy oczekiwano oczekiwania, czy grupa zadań została anulowana z powodu jawnej operacji anulowania lub zgłaszania wyjątku z jednego z jego zadań. Aby uzyskać więcej informacji, zobacz [task_group_status](concurrency-namespace-enums.md#task_group_status).

### <a name="remarks"></a>Uwagi

Należy zauważyć, że co najmniej jedno z zadań zaplanowanych do tego `task_group` obiektu może zostać wykonane w tekście w kontekście wywołującym.

Jeśli co najmniej jedno z zadań zaplanowanych dla tego `task_group` obiektu zgłasza wyjątek, środowisko uruchomieniowe wybierze jeden z tych wyjątków, a następnie propaguje go z wywołania `wait` metody.

Wywołanie `wait` na `task_group` obiekcie powoduje zresetowanie go do stanu czystego, w którym można go ponownie użyć. Obejmuje to przypadek, w którym `task_group` obiekt został anulowany.

W niewyjątkowej ścieżce wykonywania użytkownik ma mandat do wywołania tej metody lub `run_and_wait` metody przed destruktorem `task_group` wykonywanym.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Klasa structured_task_group](structured-task-group-class.md)<br/>
[Klasa task_handle](task-handle-class.md)
