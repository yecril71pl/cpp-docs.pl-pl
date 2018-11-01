---
title: task_group — Klasa
ms.date: 07/20/2018
f1_keywords:
- task_group
- PPL/concurrency::task_group
- PPL/concurrency::task_group::task_group
helpviewer_keywords:
- task_group class
ms.openlocfilehash: 1ba7251afca80c561bd8861968c35e3242c1507a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588854"
---
# <a name="taskgroup-class"></a>task_group — Klasa

`task_group` Klasa reprezentuje kolekcję równoległą pracę, która może być oczekiwany lub anulowane.

## <a name="syntax"></a>Składnia

```
class task_group;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[task_group](#ctor)|Przeciążone. Tworzy nowy `task_group` obiektu.|
|[~ task_group — destruktor](#dtor)|Niszczy `task_group` obiektu. Powinny wywoływać jednego z tych `wait` lub `run_and_wait` metody na obiekcie przed wykonaniem destruktora, chyba że destruktor jest wykonywany w wyniku odwijanie ze względu na wyjątek stosu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[cancel](#cancel)|Stara podjęto próbę anulowania poddrzewie pracy na tej grupy zadań. Każde zadanie zaplanowane w grupie zadań będzie uzyskać anulowane przechodni, jeśli jest to możliwe.|
|[is_canceling](#is_canceling)|Informuje obiekt wywołujący, czy grupa zadań jest obecnie w środku anulowania. Musi to oznaczać, że `cancel` metoda została wywołana na `task_group` obiektu (mimo że takie kwalifikuje się bez obaw tę metodę, aby zwrócić `true`). Może być tak, `task_group` obiektu jest wykonywana i wbudowana i grupy zadań, który jest dalsze się w drzewie pracy zostało anulowane. W przypadkach, takich jak tych usług, środowisko uruchomieniowe można określić anulowania będą przepływać przez to wcześniej `task_group` obiektu `true` zostanie zwrócona, jak również.|
|[run](#run)|Przeciążone. Planuje zadanie na `task_group` obiektu. Jeśli `task_handle` obiekt jest przekazywany jako parametr do `run`, obiekt wywołujący jest odpowiedzialny za zarządzanie okresem istnienia `task_handle` obiektu. Wersja metody, która przyjmuje odwołanie do obiektu funkcyjnego, ponieważ parametr obejmuje Alokacja sterty wewnątrz środowiska uruchomieniowego, które mogą być wykonać dobrze, mniej niż wersja, która przyjmuje odwołanie do `task_handle` obiektu. Wersja, która przyjmuje parametr `_Placement` powoduje ukierunkowane wykonywania w lokalizacji określonej przez parametr tego zadania.|
|[run_and_wait](#run_and_wait)|Przeciążone. Planuje zadania do uruchomienia wbudowanego w kontekście wywoływania przy pomocy `task_group` obiekt do obsługi pełnego anulowania. Funkcja następnie czeka, aż wszystkie pracować nad `task_group` obiektu zostało ukończone lub zostało anulowane. Jeśli `task_handle` obiekt jest przekazywany jako parametr do `run_and_wait`, obiekt wywołujący jest odpowiedzialny za zarządzanie okresem istnienia `task_handle` obiektu.|
|[Czekaj](#wait)|Czeka, aż wszystkie pracować nad `task_group` obiektu zostało ukończone lub zostało anulowane.|

## <a name="remarks"></a>Uwagi

W przeciwieństwie do silnie ograniczeniami `structured_task_group` klasy `task_group` klasa jest znacznie bardziej ogólne konstrukcji. Go nie ma żadnych ograniczeń, opisane przez [structured_task_group](structured-task-group-class.md). `task_group` obiekty mogą bezpiecznie używane w wątkach i wykorzystywane w dowolny sposób. Wadą `task_group` konstrukcja jest, że nie można wykonać, jak również `structured_task_group` konstruowania dla zadań, które wykonują niewielką ilość pracy.

Aby uzyskać więcej informacji, zobacz [równoległość zadań](../task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`task_group`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ppl.h

**Namespace:** współbieżności

##  <a name="cancel"></a> Anuluj

Stara podjęto próbę anulowania poddrzewie pracy na tej grupy zadań. Każde zadanie zaplanowane w grupie zadań będzie uzyskać anulowane przechodni, jeśli jest to możliwe.

```
void cancel();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [anulowania](../cancellation-in-the-ppl.md).

##  <a name="is_canceling"></a> is_canceling —

Informuje obiekt wywołujący, czy grupa zadań jest obecnie w środku anulowania. Musi to oznaczać, że `cancel` metoda została wywołana na `task_group` obiektu (mimo że takie kwalifikuje się bez obaw tę metodę, aby zwrócić `true`). Może być tak, `task_group` obiektu jest wykonywana i wbudowana i grupy zadań, który jest dalsze się w drzewie pracy zostało anulowane. W przypadkach, takich jak tych usług, środowisko uruchomieniowe można określić anulowania będą przepływać przez to wcześniej `task_group` obiektu `true` zostanie zwrócona, jak również.

```
bool is_canceling();
```

### <a name="return-value"></a>Wartość zwracana

Wskazanie, czy `task_group` obiekt jest w środku anulowania (lub może być wkrótce).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [anulowania](../cancellation-in-the-ppl.md).

##  <a name="run"></a> Uruchom

Planuje zadanie na `task_group` obiektu. Jeśli `task_handle` obiekt jest przekazywany jako parametr do `run`, obiekt wywołujący jest odpowiedzialny za zarządzanie okresem istnienia `task_handle` obiektu. Wersja metody, która przyjmuje odwołanie do obiektu funkcyjnego, ponieważ parametr obejmuje Alokacja sterty wewnątrz środowiska uruchomieniowego, które mogą być wykonać dobrze, mniej niż wersja, która przyjmuje odwołanie do `task_handle` obiektu. Wersja, która przyjmuje parametr `_Placement` powoduje ukierunkowane wykonywania w lokalizacji określonej przez parametr tego zadania.

```
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
Typ obiektu funkcji, która będzie wywoływana w celu wykonania treści obsługi zadań.

*_Func*<br/>
Funkcja, która zostanie wywołana w celu wywołania treści zadania. Może to być wyrażenie lambda lub inny obiekt, który obsługuje wersję operator wywołania funkcji z podpisem `void operator()()`.

*_Umieszczenia.*<br/>
Odwołanie do lokalizacji, w którym zadanie jest reprezentowane przez `_Func` parametr powinien zostać wykonany.

*_Task_handle*<br/>
Dojście do pracy, zaplanowane. Należy pamiętać, że obiekt wywołujący odpowiada za okres istnienia tego obiektu. Środowisko uruchomieniowe będzie w dalszym ciągu będzie się na żywo do momentu `wait` lub `run_and_wait` na ten zostanie wywołana metoda `task_group` obiektu.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe planuje podana funkcja pracy do uruchamiania w późniejszym czasie, który może być po powrocie funkcji wywołującej. Ta metoda używa [task_handle](task-handle-class.md) obiekt, aby przechowywać kopię podana funkcja pracy. W związku z tym wszelkie zmiany stanu, które występują w obiekt funkcji, które przechodzą do tej metody nie pojawi się w kopii tego obiektu funkcji. Ponadto upewnij się, okres istnienia obiektów przekazywane przez wskaźnik lub odwołanie do funkcji pracy pozostają ważne, dopóki ta funkcja pracy zwróci.

Jeśli `task_group` destructs wyniku odwijanie z wyjątku stosu, nie trzeba gwarantuje, że nawiązano połączenie na `wait` lub `run_and_wait` metody. W tym przypadku destruktor zostanie odpowiednio Anuluj i poczekaj, aż zadanie reprezentowany przez `_Task_handle` parametr w celu ukończenia.

Metoda zgłasza [invalid_multiple_scheduling —](invalid-multiple-scheduling-class.md) wyjątek, jeśli zadanie obsługi przez `_Task_handle` parametru została zaplanowana na obiekt grupy zadań, za pośrednictwem `run` metody i że została nie Wywołanie interwencyjne na `wait` lub `run_and_wait` metody dla tej grupy zadań.

##  <a name="run_and_wait"></a> run_and_wait —

Planuje zadania do uruchomienia wbudowanego w kontekście wywoływania przy pomocy `task_group` obiekt do obsługi pełnego anulowania. Funkcja następnie czeka, aż wszystkie pracować nad `task_group` obiektu zostało ukończone lub zostało anulowane. Jeśli `task_handle` obiekt jest przekazywany jako parametr do `run_and_wait`, obiekt wywołujący jest odpowiedzialny za zarządzanie okresem istnienia `task_handle` obiektu.

```
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
Typ obiektu funkcji, która będzie wywoływana w celu wykonania treści zadania.

*_Task_handle*<br/>
Dojście do zadania, które jest uruchamiane wbudowane Kontekst wywołania. Należy pamiętać, że obiekt wywołujący odpowiada za okres istnienia tego obiektu. Środowisko uruchomieniowe będzie w dalszym ciągu będzie się na żywo do momentu `run_and_wait` metoda kończy działanie.

*_Func*<br/>
Funkcja, która zostanie wywołana w celu wywołania jednostkę pracy. Może to być wyrażenie lambda lub inny obiekt, który obsługuje wersję operator wywołania funkcji z podpisem `void operator()()`.

### <a name="return-value"></a>Wartość zwracana

Wskazanie, czy czas oczekiwania był zadawalający lub grupy zadań zostało anulowane z powodu operacji anulowania jawne lub wyjątek z jednego z jego zadań podrzędnych. Aby uzyskać więcej informacji, zobacz [task_group_status —](concurrency-namespace-enums.md#task_group_status).

### <a name="remarks"></a>Uwagi

Należy pamiętać, jednego lub więcej zadań zaplanowanych do tego `task_group` obiektu może zostać wykonany wbudowane na kontekst wywołania.

Jeśli co najmniej jednego zadania zaplanowane do tego `task_group` obiektu zgłasza wyjątek, środowisko uruchomieniowe zaznaczy jeden taki wyjątek, jego zalety i propagowanie go poza wywołanie `run_and_wait` metody.

Po powrocie z `run_and_wait` metody `task_group` obiektu, środowisko uruchomieniowe przywraca obiekt stanu czystego, gdzie może zostać użyte. W tym przypadku gdzie `task_group` obiektu zostało anulowane.

W ścieżce niewyjątkowego wykonywania masz upoważnienia do obu tę metodę należy wywołać lub `wait` metody przed destruktor `task_group` wykonuje.

##  <a name="ctor"></a> task_group —

Tworzy nowy `task_group` obiektu.

```
task_group();

task_group(
   cancellation_token _CancellationToken
);
```

### <a name="parameters"></a>Parametry

*_CancellationToken*<br/>
Token anulowania do skojarzenia z tą grupą zadań. Grupy zadań zostanie anulowane, gdy token zostanie anulowany.

### <a name="remarks"></a>Uwagi

Konstruktor, który pobiera token anulowania, tworzy `task_group` , zostanie anulowane, gdy źródło skojarzone z tokenem zostało anulowane. Również zapewnienie token anulowania jawne izoluje ta grupa zadaniowa z uczestnictwa w anulowanie niejawne z grupy nadrzędnej z inny token lub brak tokenu.

##  <a name="dtor"></a> ~ task_group

Niszczy `task_group` obiektu. Powinny wywoływać jednego z tych `wait` lub `run_and_wait` metody na obiekcie przed wykonaniem destruktora, chyba że destruktor jest wykonywany w wyniku odwijanie ze względu na wyjątek stosu.

```
~task_group();
```

### <a name="remarks"></a>Uwagi

Jeśli destruktor jest uruchomiony w wyniku normalnego wykonania (na przykład nie odwijanie stosu ze względu na wyjątek), a żaden z nich nie `wait` ani `run_and_wait` wywołaniu metody, destruktor może zgłaszać [missing_wait —](missing-wait-class.md) wyjątek.

##  <a name="wait"></a> Czekaj

Czeka, aż wszystkie pracować nad `task_group` obiektu zostało ukończone lub zostało anulowane.

```
task_group_status wait();
```

### <a name="return-value"></a>Wartość zwracana

Wskazanie, czy czas oczekiwania był zadawalający lub grupy zadań zostało anulowane z powodu operacji anulowania jawne lub wyjątek z jednego z jego zadań podrzędnych. Aby uzyskać więcej informacji, zobacz [task_group_status —](concurrency-namespace-enums.md#task_group_status).

### <a name="remarks"></a>Uwagi

Należy pamiętać, jednego lub więcej zadań zaplanowanych do tego `task_group` obiektu może zostać wykonany wbudowane na kontekst wywołania.

Jeśli co najmniej jednego zadania zaplanowane do tego `task_group` obiektu zgłasza wyjątek, środowisko uruchomieniowe zaznaczy jeden taki wyjątek, jego zalety i propagowanie go poza wywołanie `wait` metody.

Wywoływanie `wait` na `task_group` obiektu Ponadto resetuje go do stanu czystego, gdzie może zostać użyte. W tym przypadku gdzie `task_group` obiektu zostało anulowane.

W ścieżce niewyjątkowego wykonywania masz upoważnienia do obu tę metodę należy wywołać lub `run_and_wait` metody przed destruktor `task_group` wykonuje.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[structured_task_group, klasa](structured-task-group-class.md)<br/>
[task_handle, klasa](task-handle-class.md)