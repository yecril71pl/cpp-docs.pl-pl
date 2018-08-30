---
title: Archetyp procesu roboczego | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: fd9e665a83db3b824e03eb960baf54f296d15d4f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204857"
---
# <a name="worker-archetype"></a>Archetyp procesu roboczego
Klasy, które są zgodne z *procesu roboczego* archetype zapewniają kodu do elementów roboczych procesu w kolejce puli wątków.  
  
 **Implementacja**  
  
 Aby zaimplementować klasę zgodnych z tym archetype, klasy, należy podać następujące funkcje:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Initialize](#initialize)|Wywoływana w celu zainicjowania obiektu proces roboczy, zanim wszystkie żądania są przekazywane do [Execute](#execute).|  
|[Execute](#execute)|Wywołuje się, by przetworzyć elementu roboczego.|  
|[Terminate](#terminate)|Wywoływana na uninitialize obiektu procesu roboczego po przejściu wszystkich żądań do [Execute](#execute).|  
  
|Element TypeDef|Opis|  
|-------------|-----------------|  
|[RequestType](#requesttype)|Element typedef dla typu elementu roboczego, które mogą być przetwarzane przez klasę procesu roboczego.|  
  
 Typowa *procesu roboczego* klasy wygląda następująco:  
  
 [!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]  
  
 **Istniejących implementacji**  
  
 Te klasy są zgodne z tym archetype:  
  
|Class|Opis|  
|-----------|-----------------|  
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|Odbiera żądania z puli wątków i przekazuje je do obiektu procesu roboczego, który jest tworzona i niszczona dla każdego żądania.|  
  
 **Użyj**  
  
 Te parametry szablonu spodziewać się klasy, która ma być zgodna z ten archetype:  
  
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
 *Żądanie*  
 Element roboczy do przetworzenia. Element roboczy jest taki sam jak `RequestType`.  
  
 *pvWorkerParam*  
 Parametru niestandardowego, zrozumiałym dla klasy procesu roboczego. Również są przekazywane do `WorkerArchetype::Initialize` i `Terminate`.  
  
 *pOverlapped*  
 Wskaźnik do [OVERLAPPED](/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) struktura używana do tworzenia kolejek na pracy, dla których elementy znajdują się w kolejce.  
  
## <a name="initialize"></a> WorkerArchetype::Initialize
Wywoływana w celu zainicjowania obiektu proces roboczy, zanim wszystkie żądania są przekazywane do `WorkerArchetype::Execute`.  
```
BOOL Initialize(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>Parametry  
 *pvParam*  
 Parametru niestandardowego, zrozumiałym dla klasy procesu roboczego. Również są przekazywane do `WorkerArchetype::Terminate` i `WorkerArchetype::Execute`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.  
  
## <a name="requesttype"></a> WorkerArchetype::RequestType
Element typedef dla typu elementu roboczego, które mogą być przetwarzane przez klasę procesu roboczego.  
  
```  
typedef MyRequestType RequestType;    
```  
  
### <a name="remarks"></a>Uwagi  
 Ten typ musi być używany jako pierwszy parametr `WorkerArchetype::Execute` i musi być w stanie rzutowany do i z typu ULONG_PTR.  
  
## <a name="terminate"></a> WorkerArchetype::Terminate
Wywoływana na uninitialize obiektu procesu roboczego po przejściu wszystkich żądań do `WorkerArchetype::Execute`).  
    
``` 
void Terminate(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>Parametry  
 *pvParam*  
 Parametru niestandardowego, zrozumiałym dla klasy procesu roboczego. Również są przekazywane do `WorkerArchetype::Initialize` i `WorkerArchetype::Execute`.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../../atl/active-template-library-atl-concepts.md)   
 [Składniki ATL COM pulpitu](../../atl/atl-com-desktop-components.md)



