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
ms.openlocfilehash: 5cca5d20b89df97e27529d656e9a6553fd8a1820
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="structuredtaskgroup-class"></a>structured_task_group — Klasa
`structured_task_group` Klasa reprezentuje kolekcję uporządkowany równoległych pracy. Można dodać do kolejki na poszczególnych zadań równoległych `structured_task_group` przy użyciu `task_handle` obiekty i zaczekaj na ich zakończenie lub kliknij przycisk Anuluj grupy zadań przed ich zakończeniem wykonywania, która spowoduje przerwanie wszystkich zadań, które nie zostały uruchomione wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```
class structured_task_group;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[structured_task_group](#ctor)|Przeciążone. Tworzy nową `structured_task_group` obiektu.|  
|[~ structured_task_group — destruktor](#dtor)|Niszczy `structured_task_group` obiektu. Powinny wywoływać albo `wait` lub `run_and_wait` metody dla obiekt przed wykonaniem destruktor, chyba że destruktor jest wykonywany w stosu rozwinięcia z powodu wyjątku.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[cancel](#cancel)|Sprawia, że starań, podjęto próbę anulowania poddrzewa pracy umieszczone w tej grupy zadań. Każdego zadania zaplanowane w grupie zadań będzie pobrać anulowane Przechodnie Jeśli to możliwe.|  
|[is_canceling](#is_canceling)|Informuje o wywołującego czy grupy zadań jest obecnie pośrodku anulowania. To nie musi oznaczać, że `cancel` wywołano metodę na `structured_task_group` obiektu (chociaż takie pewnością kwalifikuje się tę metodę, aby zwrócić `true`). Mogło stanowić przypadek który `structured_task_group` obiektu wykonuje wbudowanego i dalsze grupy zadań się w drzewie pracy zostało anulowane. W przypadkach, takich jak te where środowiska uruchomieniowego można określić czas, który anulowania będzie przechodził przez to `structured_task_group` obiektu `true` zostaną zwrócone, jak również.|  
|[run](#run)|Przeciążone. Zaplanowane zadanie na `structured_task_group` obiektu. Obiekt wywołujący zarządza czasem istnienia `task_handle` przekazano obiekt `_Task_handle` parametru. Wersja, która przyjmuje parametr `_Placement` powoduje można ukierunkowane pod kątem wykonywania w lokalizacji określonej przez parametr tego zadania.|  
|[run_and_wait](#run_and_wait)|Przeciążone. Zaplanowane zadania do wykonania wbudowanej w kontekście wywoływania przy pomocy `structured_task_group` obiektu pełne anulowania obsługi. Jeśli `task_handle` obiekt został przekazany jako parametr `run_and_wait`, element wywołujący jest odpowiedzialny za zarządzanie okres istnienia `task_handle` obiektu. Funkcja następnie czeka, aż wszystkie działają na `structured_task_group` obiektu została ukończona lub zostało anulowane.|  
|[oczekiwania](#wait)|Czeka, aż wszystkie działają na `structured_task_group` zostało zakończone lub została anulowana.|  
  
## <a name="remarks"></a>Uwagi  
 Istnieje szereg ograniczeń poważny dotyczącymi użycia `structured_task_group` obiektu w celu uzyskania wydajności:  
  
-   Pojedynczy `structured_task_group` przez wiele wątków nie można użyć obiektu. Wszystkie operacje na `structured_task_group` obiekt musi zostać wykonana przez wątek, który utworzył obiekt. Dwa wyjątki od tej reguły są funkcje Członkowskie `cancel` i `is_canceling`. Obiekt nie może znajdować się na liście przechwytywania wyrażenia lambda i można używać w ramach zadania, chyba że zadanie używa jednej z operacji anulowania.  
  
-   Wszystkie zadania zaplanowane do `structured_task_group` zaplanowane za pośrednictwem obiektu `task_handle` obiekty, które należy jawnie zarządzać okres istnienia.  
  
-   Wiele grup można używać tylko w kolejności absolutnie zagnieżdżonych. Jeśli dwa `structured_task_group` obiekty są zadeklarowane, drugi został zadeklarowany (wewnętrzny jeden) muszą destruct przed dowolnej metody, z wyjątkiem `cancel` lub `is_canceling` jest wywoływana na pierwszą (jeden zewnętrzny). Ten warunek jest spełniony, w przypadku po prostu deklarowanie wielu `structured_task_group` obiektów w tym samym lub funkcjonalnie zagnieżdżonych zakresów, a także w przypadku zadania, które zostało umieszczone w kolejce do `structured_task_group` za pośrednictwem `run` lub `run_and_wait` metody.  
  
-   W odróżnieniu od ogólnych `task_group` klasy wszystkich stanów w `structured_task_group` klasy są końcowego. Po w kolejce zadań do grupy i czas potrzebny na ich zakończenie, nie można używać tej samej grupie ponownie.  
  
 Aby uzyskać więcej informacji, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `structured_task_group`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ppl.h  
  
 **Namespace:** współbieżności  
  
##  <a name="cancel"></a> Anuluj 

 Sprawia, że starań, podjęto próbę anulowania poddrzewa pracy umieszczone w tej grupy zadań. Każdego zadania zaplanowane w grupie zadań będzie pobrać anulowane Przechodnie Jeśli to możliwe.  
  
```
void cancel();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [anulowania](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).  
  
##  <a name="is_canceling"></a> is_canceling 

 Informuje o wywołującego czy grupy zadań jest obecnie pośrodku anulowania. To nie musi oznaczać, że `cancel` wywołano metodę na `structured_task_group` obiektu (chociaż takie pewnością kwalifikuje się tę metodę, aby zwrócić `true`). Mogło stanowić przypadek który `structured_task_group` obiektu wykonuje wbudowanego i dalsze grupy zadań się w drzewie pracy zostało anulowane. W przypadkach, takich jak te where środowiska uruchomieniowego można określić czas, który anulowania będzie przechodził przez to `structured_task_group` obiektu `true` zostaną zwrócone, jak również.  
  
```
bool is_canceling();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskazuje, czy `structured_task_group` obiektu jest pośrodku anulowania (lub może być wkrótce).  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [anulowania](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).  
  
##  <a name="run"></a> Uruchom 

 Zaplanowane zadanie na `structured_task_group` obiektu. Obiekt wywołujący zarządza czasem istnienia `task_handle` przekazano obiekt `_Task_handle` parametru. Wersja, która przyjmuje parametr `_Placement` powoduje można ukierunkowane pod kątem wykonywania w lokalizacji określonej przez parametr tego zadania.  
  
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
 `_Function`  
 Typ obiektu funkcji, który zostanie wywołany, można wykonać treści dojścia zadań.  
  
 `_Task_handle`  
 Dojście do pracy zaplanowane. Należy pamiętać, że wywołującego odpowiada za okres istnienia tego obiektu. Środowisko uruchomieniowe będą w dalszym ciągu będzie się na żywo do momentu `wait` lub `run_and_wait` metoda została wywołana dla tego `structured_task_group` obiektu.  
  
 `_Placement`  
 Odwołanie do lokalizacji, w którym zadanie reprezentowany przez `_Task_handle` parametr powinien zostać wykonany.  
  
### <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe tworzona jest kopia funkcji pracy, który jest przekazywany do tej metody. Wszelkie zmiany stanu, które występują w obiekcie funkcji, które można przekazać do tej metody nie będą widoczne w kopii tego obiektu funkcji.  
  
 Jeśli `structured_task_group` destructs wyniku stosu odwijanie od wyjątek, nie trzeba zagwarantować, że nawiązano połączenie jako `wait` lub `run_and_wait` metody. W takim przypadku destruktor odpowiednio spowoduje anulowanie i poczekaj, aż zadanie reprezentowany przez `_Task_handle` parametr, aby zakończyć.  
  
 Zgłasza wyjątek [invalid_multiple_scheduling —](invalid-multiple-scheduling-class.md) wyjątek, jeśli zadanie obsługi podana przez `_Task_handle` parametru zostało już zaplanowane na obiektu grupy zadań za pomocą `run` — metoda i nie było żadnych pośredniczące wywołania albo `wait` lub `run_and_wait` metody dla tej grupy zadań.  
  
##  <a name="run_and_wait"></a> run_and_wait 

 Zaplanowane zadania do wykonania wbudowanej w kontekście wywoływania przy pomocy `structured_task_group` obiektu pełne anulowania obsługi. Jeśli `task_handle` obiekt został przekazany jako parametr `run_and_wait`, element wywołujący jest odpowiedzialny za zarządzanie okres istnienia `task_handle` obiektu. Funkcja następnie czeka, aż wszystkie działają na `structured_task_group` obiektu została ukończona lub zostało anulowane.  
  
```
template<class _Function>
task_group_status run_and_wait(task_handle<_Function>& _Task_handle);

template<class _Function>
task_group_status run_and_wait(const _Function& _Func);
```  
  
### <a name="parameters"></a>Parametry  
 `_Function`  
 Typ obiektu funkcji, który zostanie wywołany, można wykonać zadania.  
  
 `_Task_handle`  
 Dojście do zadania, które zostanie uruchomione wbudowanego Kontekst wywołania. Należy pamiętać, że wywołującego odpowiada za okres istnienia tego obiektu. Środowisko uruchomieniowe będą w dalszym ciągu będzie się na żywo do `run_and_wait` metoda kończy działanie.  
  
 `_Func`  
 Funkcję, która będzie wywoływana w celu wywołania jednostkę pracy. Może to być wyrażenie lambda lub inny obiekt, który obsługuje wersję operator wywołania funkcji z podpisem `void operator()()`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskazanie, czy zostały spełnione czas oczekiwania lub grupy zadań została anulowana z powodu operacji anulowania jawne lub wyjątek z jednego z jego zadań podrzędnych. Aby uzyskać więcej informacji, zobacz [task_group_status —](concurrency-namespace-enums.md)  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, jednego lub więcej zadań zaplanowanych do tego `structured_task_group` obiektu wbudowanego może być wykonywany na kontekst wywołania.  
  
 Jeśli co najmniej jednego zadania zaplanowane do tego `structured_task_group` obiektu zgłasza wyjątek, środowisko uruchomieniowe będzie wybierz jeden taki wyjątek jego wybieranie i propagację go poza wywołanie `run_and_wait` metody.  
  
 Po powrocie z tej funkcji `structured_task_group` obiekt jest rozpatrywany w stanie końcowym i nie powinna być używana. Należy pamiętać, że użycie po `run_and_wait` metoda zwraca spowoduje niezdefiniowane zachowanie.  
  
 W ścieżce innym kodem wykonywania masz upoważnienia do albo ta metoda jest wywoływana lub `wait` metody przed destruktor `structured_task_group` wykonuje.  
  
##  <a name="ctor"></a> structured_task_group — 

 Tworzy nową `structured_task_group` obiektu.  
  
```
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```  
  
### <a name="parameters"></a>Parametry  
 `_CancellationToken`  
 Token anulowania do skojarzenia z tym strukturalne grupy zadań. Grupy zadań strukturalnych zostanie anulowane po anulowaniu tokenu.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor, który pobiera token anulowania tworzy `structured_task_group` będzie można anulować po anulowaniu źródła skojarzone z tokenem. Także dostarczanie token anulowania jawne izoluje tej grupy zadań strukturalnych z uczestnictwa w niejawnych anulowania z nadrzędnej grupy o inny token lub nie tokenu.  
  
##  <a name="dtor"></a> ~ structured_task_group — 

 Niszczy `structured_task_group` obiektu. Powinny wywoływać albo `wait` lub `run_and_wait` metody dla obiekt przed wykonaniem destruktor, chyba że destruktor jest wykonywany w stosu rozwinięcia z powodu wyjątku.  
  
```
~structured_task_group();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli destruktor jest uruchamiana w wyniku normalnego wykonywania (na przykład nie odwijanie stosu z powodu wyjątku), a nie `wait` ani `run_and_wait` wywołaniu metody, destruktor może zgłaszać [missing_wait —](missing-wait-class.md) wyjątek.  
  
##  <a name="wait"></a> oczekiwania 

 Czeka, aż wszystkie działają na `structured_task_group` zostało zakończone lub została anulowana.  
  
```
task_group_status wait();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskazanie, czy zostały spełnione czas oczekiwania lub grupy zadań została anulowana z powodu operacji anulowania jawne lub wyjątek z jednego z jego zadań podrzędnych. Aby uzyskać więcej informacji, zobacz [task_group_status —](concurrency-namespace-enums.md)  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, jednego lub więcej zadań zaplanowanych do tego `structured_task_group` obiektu wbudowanego może być wykonywany na kontekst wywołania.  
  
 Jeśli co najmniej jednego zadania zaplanowane do tego `structured_task_group` obiektu zgłasza wyjątek, środowisko uruchomieniowe będzie wybierz jeden taki wyjątek jego wybieranie i propagację go poza wywołanie `wait` metody.  
  
 Po powrocie z tej funkcji `structured_task_group` obiekt jest rozpatrywany w stanie końcowym i nie powinna być używana. Należy pamiętać, że użycie po `wait` metoda zwraca spowoduje niezdefiniowane zachowanie.  
  
 W ścieżce innym kodem wykonywania masz upoważnienia do albo ta metoda jest wywoływana lub `run_and_wait` metody przed destruktor `structured_task_group` wykonuje.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [task_group — klasa](task-group-class.md)   
 [task_handle, klasa](task-handle-class.md)
