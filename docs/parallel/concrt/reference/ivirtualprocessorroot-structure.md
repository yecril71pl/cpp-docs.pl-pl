---
title: "Ivirtualprocessorroot — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Activate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Deactivate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::EnsureAllTasksVisible
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::GetId
dev_langs:
- C++
helpviewer_keywords:
- IVirtualProcessorRoot structure
ms.assetid: 5ef371b8-9e4f-4fef-bb0d-49099693dd2b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a385bc12d3add9dd445243794135083c7cc1b3c1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot — Struktura
Abstrakcja wątku sprzętu, na którym serwer proxy wątek może zostać uruchomiony.  
  
## <a name="syntax"></a>Składnia  
  
```
struct IVirtualProcessorRoot : public IExecutionResource;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IVirtualProcessorRoot::Activate](#activate)|Powoduje, że serwer proxy wątku skojarzoną z interfejsem kontekstu wykonywania `pContext` można uruchomić wykonywania w nim procesora wirtualnego.|  
|[IVirtualProcessorRoot::Deactivate](#deactivate)|Powoduje, że serwer proxy wątku aktualnie wykonywanych na tego procesora wirtualnego katalogu głównego, przestanie wysyłki kontekstu wykonywania. Wątek proxy zostanie wznowiona wykonywania na wywołanie `Activate` metody.|  
|[IVirtualProcessorRoot::EnsureAllTasksVisible](#ensurealltasksvisible)|Powoduje, że dane przechowywane w hierarchii pamięci poszczególnych procesorów, które stają się widoczne dla wszystkich procesorów w systemie. Gwarantuje, że ogranicznika całej pamięci zostało uruchomione na wszystkich procesorów przed metoda zwraca.|  
|[IVirtualProcessorRoot::GetId](#getid)|Zwraca unikatowy identyfikator dla elementu głównego procesora wirtualnego.|  
  
## <a name="remarks"></a>Uwagi  
 Każdy procesora wirtualnego katalogu głównego ma wykonanie skojarzonych zasobów. `IVirtualProcessorRoot` Dziedziczy interfejs [iexecutionresource —](iexecutionresource-structure.md) interfejsu. Wiele procesorów wirtualnych katalogów głównych mogą odpowiadać tej samej podstawowej wątku sprzętu.  
  
 Menedżer zasobów udziela procesorów wirtualnych katalogów głównych planiści w odpowiedzi na żądania zasobów. Harmonogram można użyć głównego procesora wirtualnego do wykonywania pracy aktywować go z kontekstu wykonywania.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [IExecutionResource](iexecutionresource-structure.md)  
  
 `IVirtualProcessorRoot`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrtrm.h  
  
 **Namespace:** współbieżności  
  
##  <a name="activate"></a>  IVirtualProcessorRoot::Activate — metoda  
 Powoduje, że serwer proxy wątku skojarzoną z interfejsem kontekstu wykonywania `pContext` można uruchomić wykonywania w nim procesora wirtualnego.  
  
```
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pContext`  
 Interfejs do kontekstu wykonywania, który będą wysyłane w przypadku tego procesora wirtualnego katalogu głównego.  
  
### <a name="remarks"></a>Uwagi  
 Menedżer zasobów będzie dostarczać wątku serwera proxy, jeśli jeszcze nie została skojarzona z interfejsem kontekstu wykonywania `pContext`  
  
 `Activate` Metody można użyć, można uruchomić wykonywania pracy na nowy katalog główny procesora wirtualnego zwrócony przez Menedżera zasobów lub serwera proxy wątku głównego procesora wirtualnego, który ma dezaktywowane lub ma dezaktywować wznowienia. Zobacz [IVirtualProcessorRoot::Deactivate](#deactivate) Aby uzyskać więcej informacji na temat dezaktywowania. Gdy wznawianie dezaktywowane procesora wirtualnego katalogu głównego, parametr `pContext` musi być taka sama jak parametru użytego do dezaktywowania głównego procesora wirtualnego.  
  
 Po aktywowaniu procesora wirtualnego katalogu głównego po raz pierwszy, pary kolejnych wywołań `Deactivate` i `Activate` mogą zastępować ze sobą. Oznacza to jest akceptowalne dla Menedżera zasobów do odbierania wywołanie `Activate` przed odbierze `Deactivate` miały do wywołania.  
  
 Po aktywowaniu procesora wirtualnego katalogu głównego, możesz sygnał Menedżera zasobów czy tego procesora wirtualnego katalogu głównego jest aktualnie zajęty z pracą. Jeśli Twoje harmonogramu nie można odnaleźć żadnej pracy można wykonać w tym folderze głównym, oczekuje się, aby wywołać `Deactivate` metody informowania Menedżera zasobów procesora wirtualnego katalogu głównego jest w stanie bezczynności. Menedżer zasobów używa tych danych do systemu równoważenia obciążenia.  
  
 `invalid_argument` wygenerowany, jeśli argument `pContext` ma wartość `NULL`.  
  
 `invalid_operation` wygenerowany, jeśli argument `pContext` nie reprezentuje kontekstu wykonywania, który został ostatnio wysłanych przez tego procesora wirtualnego katalogu głównego.  
  
 Działanie aktywacji procesora wirtualnego katalogu głównego zwiększa poziom subskrypcji źródłowej wątku sprzętu o jeden. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
##  <a name="deactivate"></a>  IVirtualProcessorRoot::Deactivate — metoda  
 Powoduje, że serwer proxy wątku aktualnie wykonywanych na tego procesora wirtualnego katalogu głównego, przestanie wysyłki kontekstu wykonywania. Wątek proxy zostanie wznowiona wykonywania na wywołanie `Activate` metody.  
  
```
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pContext`  
 Kontekst, który jest aktualnie wysyłane przez ten główny.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość logiczna. Wartość `true` wskazuje, że serwer proxy wątku zwrócony z `Deactivate` w odpowiedzi na wywołanie metody `Activate` metody. Wartość `false` wskazuje, że serwer proxy wątku zwrócony z metody w odpowiedzi na zdarzenia powiadomienia Menedżera zasobów. W trybie użytkownika schedulable (UMS) wątku harmonogramu to wskazuje, że elementy były wyświetlane na liście uzupełniania harmonogramu i harmonogramu jest wymagana do ich obsługi.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby tymczasowo zatrzymać wykonywania procesora wirtualnego katalogu głównego pracę, możesz znaleźć w harmonogramie użytkownika. Wywołanie `Deactivate` metody muszą pochodzić z poziomu `Dispatch` metodę kontekstu wykonywania, z ostatniego uaktywnienia głównego procesora wirtualnego. Innymi słowy, serwer proxy wątku wywoływania `Deactivate` metoda musi być jedną, która jest aktualnie wykonywany w katalogu głównym procesora wirtualnego. Wywołanie metody procesora wirtualnego katalogu głównego, nie wykonywana na może spowodować niezdefiniowane zachowanie.  
  
 Dezaktywowane procesora wirtualnego katalogu głównego może wznawiać wywołaniem `Activate` metodę z tego samego argumentu, który został przekazany do `Deactivate` metody. Harmonogram jest odpowiedzialny za zapewnienie, który odwołuje się do `Activate` i `Deactivate` metody są skojarzone, ale nie są one wymagane do odebrania w określonej kolejności. Resource Manager może obsługiwać odbieranie wywołania `Activate` metoda przed odbierze wywołanie `Deactivate` miały dla metody.  
  
 Jeśli awakens procesora wirtualnego katalogu głównego i wartość zwrotną z elementu `Deactivate` metody jest wartością `false`, harmonogram powinien zapytania listy uzupełniania UMS za pośrednictwem `IUMSCompletionList::GetUnblockNotifications` metody, działają na tych informacji, a następnie wywołać `Deactivate`metody ponownie. Powinny to być powtarzane do czasu `Deactivate` metoda zwraca wartość `true`.  
  
 `invalid_argument` wygenerowany, jeśli argument `pContext` ma wartość `NULL`.  
  
 `invalid_operation` jest generowany, jeśli główny procesorów wirtualnych nigdy nie został aktywowany, lub argumentu `pContext` nie reprezentuje kontekstu wykonywania, który został ostatnio wysłanych przez tego procesora wirtualnego katalogu głównego.  
  
 Czynność dezaktywowanie procesora wirtualnego katalogu głównego zmniejsza poziomu subskrypcji źródłowej wątku sprzętu przez jeden. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
##  <a name="ensurealltasksvisible"></a>  IVirtualProcessorRoot::EnsureAllTasksVisible — metoda  
 Powoduje, że dane przechowywane w hierarchii pamięci poszczególnych procesorów, które stają się widoczne dla wszystkich procesorów w systemie. Gwarantuje, że ogranicznika całej pamięci zostało uruchomione na wszystkich procesorów przed metoda zwraca.  
  
```
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pContext`  
 Kontekst, w którym jest obecnie wysyłany przez tego procesora wirtualnego katalogu głównego.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda mogą być przydatne, gdy chcesz synchronizować z dodaniem nowych zadań do harmonogramu dezaktywacji procesora wirtualnego katalogu głównego. Ze względu na wydajność może zadecydować o dodawanie elementów roboczych do Twojej harmonogramu bez wykonywania bariery pamięci, co oznacza dodane przez wątek wykonywania w jednym procesorze elementów roboczych nie są bezpośrednio widoczne dla wszystkich innych procesorów. Za pomocą tej metody w połączeniu z `Deactivate` metody można zapewnić, że Twoje harmonogramu nie dezaktywować jego procesorów wirtualnych katalogów głównych istnieją elementy robocze w kolekcji z harmonogramu.  
  
 Wywołanie `EnsureAllTasksVisibleThe` metody muszą pochodzić z poziomu `Dispatch` metodę kontekstu wykonywania, z ostatniego uaktywnienia głównego procesora wirtualnego. Innymi słowy, serwer proxy wątku wywoływania `EnsureAllTasksVisible` metoda musi być jedną, która jest aktualnie wykonywany w katalogu głównym procesora wirtualnego. Wywołanie metody procesora wirtualnego katalogu głównego, nie wykonywana na może spowodować niezdefiniowane zachowanie.  
  
 `invalid_argument` wygenerowany, jeśli argument `pContext` ma wartość `NULL`.  
  
 `invalid_operation` jest generowany, jeśli główny procesorów wirtualnych nigdy nie został aktywowany, lub argumentu `pContext` nie reprezentuje kontekstu wykonywania, który został ostatnio wysłanych przez tego procesora wirtualnego katalogu głównego.  
  
##  <a name="getid"></a>  IVirtualProcessorRoot::GetId — metoda  
 Zwraca unikatowy identyfikator dla elementu głównego procesora wirtualnego.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator liczby całkowitej.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
