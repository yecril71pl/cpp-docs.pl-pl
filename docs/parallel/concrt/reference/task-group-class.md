`task_group` Klasa reprezentuje kolekcję równoległych pracy, które mogą być obsługiwane lub anulowane.  
  
## <a name="syntax"></a>Składnia  
  
```  
class task_group;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[task_group](#ctor)|Przeciążone. Tworzy nową `task_group` obiektu.|  
|[~ task_group — destruktor](#dtor)|Niszczy `task_group` obiektu. Powinny wywoływać albo `wait` lub `run_and_wait` metody dla obiekt przed wykonaniem destruktor, chyba że destruktor jest wykonywany w wyniku odwijanie z powodu wyjątku stosu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[cancel](#cancel)|Sprawia, że starań, podjęto próbę anulowania poddrzewa pracy umieszczone w tej grupy zadań. Każdego zadania zaplanowane w grupie zadań będzie pobrać anulowane Przechodnie Jeśli to możliwe.|  
|[is_canceling](#is_canceling)|Informuje o wywołującego czy grupy zadań jest obecnie pośrodku anulowania. To nie musi oznaczać, że `cancel` wywołano metodę na `task_group` obiektu (chociaż takie pewnością kwalifikuje się tę metodę, aby zwrócić `true`). Mogło stanowić przypadek który `task_group` obiektu wykonuje wbudowanego i dalsze grupy zadań się w drzewie pracy zostało anulowane. W przypadkach, takich jak te where środowiska uruchomieniowego można określić czas, który anulowania będzie przechodził przez to `task_group` obiektu `true` zostaną zwrócone, jak również.|  
|[run](#run)|Przeciążone. Zaplanowane zadanie na `task_group` obiektu. Jeśli `task_handle` obiekt został przekazany jako parametr `run`, element wywołujący jest odpowiedzialny za zarządzanie okres istnienia `task_handle` obiektu. Także mniej niż przy użyciu wersji, która przyjmuje odwołanie do wykonania wersji metody, która przyjmuje odwołanie do obiektu funkcji jako parametr obejmuje Alokacja sterty wewnątrz środowiska uruchomieniowego, które mogą być `task_handle` obiektu. Wersja, która przyjmuje parametr `_Placement` powoduje można ukierunkowane pod kątem wykonywania w lokalizacji określonej przez parametr tego zadania.|  
|[run_and_wait](#run_and_wait)|Przeciążone. Zaplanowane zadania do wykonania wbudowanej w kontekście wywoływania przy pomocy `task_group` obiektu pełne anulowania obsługi. Funkcja następnie czeka, aż wszystkie działają na `task_group` obiektu została ukończona lub zostało anulowane. Jeśli `task_handle` obiekt został przekazany jako parametr `run_and_wait`, element wywołujący jest odpowiedzialny za zarządzanie okres istnienia `task_handle` obiektu.|  
|[oczekiwania](#wait)|Czeka, aż wszystkie działają na `task_group` obiektu została ukończona lub zostało anulowane.|  
  
## <a name="remarks"></a>Uwagi  
 W odróżnieniu od znacznie ograniczone `structured_task_group` klasy `task_group` klasy jest bardziej ogólne konstrukcji. Nie ma żadnych ograniczeń opisanego przez [structured_task_group —](structured-task-group-class.md). `task_group` bezpiecznie obiektów mogą być używane przez wątki i użyte w sposób dowolnych. Wadą `task_group` konstrukcja jest mogą nie działać, jak również `structured_task_group` skonstruować dla zadania, które wykonują niewielkich ilości pracy.  
  
 Aby uzyskać więcej informacji, zobacz [równoległość zadań](../task-parallelism-concurrency-runtime.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `task_group`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ppl.h  
  
 **Namespace:** współbieżności  
  
##  <a name="cancel"></a> Anuluj 

 Sprawia, że starań, podjęto próbę anulowania poddrzewa pracy umieszczone w tej grupy zadań. Każdego zadania zaplanowane w grupie zadań będzie pobrać anulowane Przechodnie Jeśli to możliwe.  
  
```  
void cancel();  
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [anulowania](../cancellation-in-the-ppl.md).  
  
##  <a name="is_canceling"></a> is_canceling 

 Informuje o wywołującego czy grupy zadań jest obecnie pośrodku anulowania. To nie musi oznaczać, że `cancel` wywołano metodę na `task_group` obiektu (chociaż takie pewnością kwalifikuje się tę metodę, aby zwrócić `true`). Mogło stanowić przypadek który `task_group` obiektu wykonuje wbudowanego i dalsze grupy zadań się w drzewie pracy zostało anulowane. W przypadkach, takich jak te where środowiska uruchomieniowego można określić czas, który anulowania będzie przechodził przez to `task_group` obiektu `true` zostaną zwrócone, jak również.  
  
```  
bool is_canceling();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskazuje, czy `task_group` obiektu jest pośrodku anulowania (lub może być wkrótce).  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [anulowania](../cancellation-in-the-ppl.md).  
  
##  <a name="run"></a> Uruchom 

 Zaplanowane zadanie na `task_group` obiektu. Jeśli `task_handle` obiekt został przekazany jako parametr `run`, element wywołujący jest odpowiedzialny za zarządzanie okres istnienia `task_handle` obiektu. Także mniej niż przy użyciu wersji, która przyjmuje odwołanie do wykonania wersji metody, która przyjmuje odwołanie do obiektu funkcji jako parametr obejmuje Alokacja sterty wewnątrz środowiska uruchomieniowego, które mogą być `task_handle` obiektu. Wersja, która przyjmuje parametr `_Placement` powoduje można ukierunkowane pod kątem wykonywania w lokalizacji określonej przez parametr tego zadania.  
  
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
 `_Function`  
 Typ obiektu funkcji, który zostanie wywołany, można wykonać treści dojścia zadań.  
  
 `_Func`  
 Funkcja, która będzie wywoływana w celu wywołania treści zadania. Może to być wyrażenie lambda lub inny obiekt, który obsługuje wersję operator wywołania funkcji z podpisem `void operator()()`.  
  
 `_Placement`  
 Odwołanie do lokalizacji, w którym zadanie reprezentowany przez `_Func` parametr powinien zostać wykonany.  
  
 `_Task_handle`  
 Dojście do pracy zaplanowane. Należy pamiętać, że wywołującego odpowiada za okres istnienia tego obiektu. Środowisko uruchomieniowe będą w dalszym ciągu będzie się na żywo do momentu `wait` lub `run_and_wait` metoda została wywołana dla tego `task_group` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe planuje określona funkcja pracy do uruchomienia w późniejszym czasie, który może być po powrocie z funkcji wywołującej. Ta metoda używa [task_handle](task-handle-class.md) obiekt, aby pomieścić kopię określona funkcja pracy. W związku z tym wszelkie zmiany stanu, które występują w obiekcie funkcji, które można przekazać do tej metody nie będą widoczne w kopii tego obiektu funkcji. Ponadto upewnij się, że okres istnienia obiektów przekazywane przez wskaźnik lub odwołanie do funkcji pracy ważność dopóki funkcja pracy.  
  
 Jeśli `task_group` destructs wyniku stosu odwijanie od wyjątek, nie trzeba zagwarantować, że nawiązano połączenie jako `wait` lub `run_and_wait` metody. W takim przypadku destruktor odpowiednio spowoduje anulowanie i poczekaj, aż zadanie reprezentowany przez `_Task_handle` parametr, aby zakończyć.  
  
 Metoda zgłasza [invalid_multiple_scheduling —](invalid-multiple-scheduling-class.md) wyjątek, jeśli zadanie obsługi danego przez `_Task_handle` parametru zostało już zaplanowane na obiektu grupy zadań za pomocą `run` — metoda i że została nie aktywne wywołania jako `wait` lub `run_and_wait` metody dla tej grupy zadań.  
  
##  <a name="run_and_wait"></a> run_and_wait 

 Zaplanowane zadania do wykonania wbudowanej w kontekście wywoływania przy pomocy `task_group` obiektu pełne anulowania obsługi. Funkcja następnie czeka, aż wszystkie działają na `task_group` obiektu została ukończona lub zostało anulowane. Jeśli `task_handle` obiekt został przekazany jako parametr `run_and_wait`, element wywołujący jest odpowiedzialny za zarządzanie okres istnienia `task_handle` obiektu.  
  
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
 `_Function`  
 Typ obiektu funkcji, które będą wywoływane w celu wykonania treści zadania.  
  
 `_Task_handle`  
 Dojście do zadania, które zostanie uruchomione wbudowanego Kontekst wywołania. Należy pamiętać, że wywołującego odpowiada za okres istnienia tego obiektu. Środowisko uruchomieniowe będą w dalszym ciągu będzie się na żywo do `run_and_wait` metoda kończy działanie.  
  
 `_Func`  
 Funkcję, która będzie wywoływana w celu wywołania jednostkę pracy. Może to być wyrażenie lambda lub inny obiekt, który obsługuje wersję operator wywołania funkcji z podpisem `void operator()()`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskazanie, czy zostały spełnione czas oczekiwania lub grupy zadań została anulowana z powodu operacji anulowania jawne lub wyjątek z jednego z jego zadań podrzędnych. Aby uzyskać więcej informacji, zobacz [task_group_status —](concurrency-namespace-enums.md#task_group_status).  

  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, jednego lub więcej zadań zaplanowanych do tego `task_group` obiektu wbudowanego może być wykonywany na kontekst wywołania.  
  
 Jeśli co najmniej jednego zadania zaplanowane do tego `task_group` obiektu zgłasza wyjątek, środowisko uruchomieniowe będzie wybierz jeden taki wyjątek jego wybieranie i propagację go poza wywołanie `run_and_wait` metody.  
  
 Po powrocie z `run_and_wait` metoda `task_group` obiektu środowiska wykonawczego resetuje obiektu do stanu czystego, w którym można ponownie. W tym przypadku gdzie `task_group` obiektu została anulowana.  
  
 W ścieżce innym kodem wykonywania masz upoważnienia do albo ta metoda jest wywoływana lub `wait` metody przed destruktor `task_group` wykonuje.  
  
##  <a name="ctor"></a> task_group — 

 Tworzy nową `task_group` obiektu.  
  
```  
task_group();  
  
task_group(  
   cancellation_token _CancellationToken  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_CancellationToken`  
 Token anulowania do skojarzenia z tą grupą zadań. Grupy zadań zostanie anulowane po anulowaniu tokenu.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor, który pobiera token anulowania tworzy `task_group` będzie można anulować po anulowaniu źródła skojarzone z tokenem. Także dostarczanie token anulowania jawne izoluje tej grupy zadań z uczestnictwa w niejawnych anulowania z nadrzędnej grupy o inny token lub nie tokenu.  
  
##  <a name="dtor"></a> ~ task_group — 

 Niszczy `task_group` obiektu. Powinny wywoływać albo `wait` lub `run_and_wait` metody dla obiekt przed wykonaniem destruktor, chyba że destruktor jest wykonywany w wyniku odwijanie z powodu wyjątku stosu.  
  
```  
~task_group();  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli destruktor jest uruchamiana w wyniku normalnego wykonywania (na przykład nie odwijanie stosu z powodu wyjątku), a nie `wait` ani `run_and_wait` wywołaniu metody, destruktor może zgłaszać [missing_wait —](missing-wait-class.md) wyjątek.  
  
##  <a name="wait"></a> oczekiwania 

 Czeka, aż wszystkie działają na `task_group` obiektu została ukończona lub zostało anulowane.  
  
```  
task_group_status wait();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskazanie, czy zostały spełnione czas oczekiwania lub grupy zadań została anulowana z powodu operacji anulowania jawne lub wyjątek z jednego z jego zadań podrzędnych. Aby uzyskać więcej informacji, zobacz [task_group_status —](concurrency-namespace-enums.md#task_group_status).  

  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, jednego lub więcej zadań zaplanowanych do tego `task_group` obiektu wbudowanego może być wykonywany na kontekst wywołania.  
  
 Jeśli co najmniej jednego zadania zaplanowane do tego `task_group` obiektu zgłasza wyjątek, środowisko uruchomieniowe będzie wybierz jeden taki wyjątek jego wybieranie i propagację go poza wywołanie `wait` metody.  
  
 Wywoływanie `wait` na `task_group` obiektu Ponadto resetuje go do stanu czystego, w którym można ponownie. W tym przypadku gdzie `task_group` obiektu została anulowana.  
  
 W ścieżce innym kodem wykonywania masz upoważnienia do albo ta metoda jest wywoływana lub `run_and_wait` metody przed destruktor `task_group` wykonuje.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [structured_task_group — klasa](structured-task-group-class.md)   
 [task_handle, klasa](task-handle-class.md)