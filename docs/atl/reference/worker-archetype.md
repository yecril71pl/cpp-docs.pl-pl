---
title: Proces roboczy Archetype | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cee9df0b137655fe66e68c189de756f15233a94d
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34255981"
---
# <a name="worker-archetype"></a>Archetype procesu roboczego
Klasy, które odpowiadają *procesu roboczego* archetype Podaj kod do elementów roboczych procesu umieszczonych w kolejce na puli wątków.  
  
 **Implementacja**  
  
 Aby zaimplementować klasę zgodne z tym archetype, klasa podać następujące funkcje:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Initialize](#initialize)|Wywoływana w celu zainicjowania obiektu proces roboczy, zanim wszystkie żądania są przekazywane do [Execute](#execute).|  
|[Wykonanie](#execute)|Wywołuje się, by przetworzyć elementu roboczego.|  
|[Zakończenie](#terminate)|O nazwie uninitialize obiektu procesu roboczego po przejściu do wszystkich żądań [Execute](#execute).|  
  
|Element TypeDef|Opis|  
|-------------|-----------------|  
|[RequestType](#requesttype)|Element typedef dla typu elementu roboczego, które mogą być przetwarzane przez klasę procesu roboczego.|  
  
 Typowe *procesu roboczego* klasy wygląda następująco:  
  
 [!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]  
  
 **Istniejącymi implementacjami**  
  
 Te klasy są zgodne z tym archetype:  
  
|Class|Opis|  
|-----------|-----------------|  
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|Odbiera żądania z puli wątków i przekazuje je do obiektu procesu roboczego, które jest tworzone i niszczone dla każdego żądania.|  
  
 **Użyj**  
  
 Te parametry szablonu spodziewać się klasy, która ma być zgodna z tym archetype:  
  
|Nazwa parametru|Używane przez|  
|--------------------|-------------|  
|*Proces roboczy*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|  
|*Proces roboczy*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlutil.h  
  
## <a name="execute"></a>WorkerArchetype::Execute
Wywołuje się, by przetworzyć elementu roboczego.  
  
  
  
```  
void Execute(
    RequestType request,  
    void* pvWorkerParam,  
    OVERLAPPED* pOverlapped);
```  
  
#### <a name="parameters"></a>Parametry  
 `request`  
 Element roboczy do przetworzenia. Element roboczy jest taki sam typ jak `RequestType`.  
  
 `pvWorkerParam`  
 Niestandardowy parametr zrozumiałe dla klasy procesu roboczego. Również przekazany do `WorkerArchetype::Initialize` i `Terminate`.  
  
 `pOverlapped`  
 Wskaźnik do [OVERLAPPED](http://msdn.microsoft.com/library/windows/desktop/ms684342) struktury używane do tworzenia kolejek w pracy, dla których elementów umieszczonych w kolejce.  
  
## <a name="initialize"></a> WorkerArchetype::Initialize
Wywoływana w celu zainicjowania obiektu proces roboczy, zanim wszystkie żądania są przekazywane do `WorkerArchetype::Execute`.  
```
BOOL Initialize(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>Parametry  
 `pvParam`  
 Niestandardowy parametr zrozumiałe dla klasy procesu roboczego. Również przekazany do `WorkerArchetype::Terminate` i `WorkerArchetype::Execute`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia **FALSE** w przypadku awarii.  
  
## <a name="requesttype"></a> WorkerArchetype::RequestType
Element typedef dla typu elementu roboczego, które mogą być przetwarzane przez klasę procesu roboczego.  
  
```  
typedef MyRequestType RequestType;    
```  
  
### <a name="remarks"></a>Uwagi  
 Ten typ musi być używany jako pierwszy parametr `WorkerArchetype::Execute` i musi być w stanie trwa rzutowania z typu ULONG_PTR i.  
  
## <a name="terminate"></a> WorkerArchetype::Terminate
O nazwie uninitialize obiektu procesu roboczego po przejściu do wszystkich żądań `WorkerArchetype::Execute`).  
    
``` 
void Terminate(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>Parametry  
 `pvParam`  
 Niestandardowy parametr zrozumiałe dla klasy procesu roboczego. Również przekazany do `WorkerArchetype::Initialize` i `WorkerArchetype::Execute`.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../../atl/active-template-library-atl-concepts.md)   
 [Składniki ATL COM pulpitu](../../atl/atl-com-desktop-components.md)



