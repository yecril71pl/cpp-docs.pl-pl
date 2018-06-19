---
title: Obsługa Podsumowanie zdarzeń ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handling, implementing
ms.assetid: e8b47ef0-0bdc-47ff-9dd6-34df11dde9a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a938bd072ea8df30e64cce28fbf0709f08547d28
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356525"
---
# <a name="atl-event-handling-summary"></a>Podsumowanie obsługi zdarzenia ATL
Ogólnie rzecz biorąc Obsługa zdarzeń COM jest procesem stosunkowo proste. Istnieją trzy główne kroki:  
  
-   Implementowanie interfejsu zdarzenia na obiekt.  
  
-   Zalecamy źródła zdarzeń obiektu chce odbierać zdarzenia.  
  
-   Unadvise źródła zdarzeń, gdy obiekt nie będzie już potrzebował do odbierania zdarzeń.  
  
## <a name="implementing-the-interface"></a>Implementowanie interfejsu  
 Istnieją cztery główne sposoby implementowania interfejsu za pomocą ATL.  
  
|Pochodzi od|Odpowiednie dla typu interfejsu|Wymaga wdrożenia wszystkich metod *|Wymaga biblioteki typów w czasie wykonywania|  
|-----------------|---------------------------------|---------------------------------------------|-----------------------------------------|  
|Interfejs|Vtable|Tak|Nie|  
|[IDispatchImpl](../atl/reference/idispatchimpl-class.md)|Podwójny|Tak|Tak|  
|[IDispEventImpl](../atl/reference/idispeventimpl-class.md)|Dispinterface|Nie|Tak|  
|[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|Dispinterface|Nie|Nie|  
  
 \* Podczas korzystania z klasy obsługi ATL, nigdy nie należy do implementacji **IUnknown** lub `IDispatch` metody ręcznie.  
  
## <a name="advising-and-unadvising-the-event-source"></a>Udzielanie porad i Unadvising źródła zdarzeń  
 Istnieją trzy sposoby udzielanie porad i unadvising źródło zdarzeń przy użyciu ATL.  
  
|Zalecamy, funkcja|Unadvise — funkcja|Najbardziej odpowiednie do użycia z programem|Wymaga do śledzenia pliku cookie|Komentarze|  
|---------------------|-----------------------|--------------------------------|---------------------------------------------|--------------|  

|[AtlAdvise](reference/connection-point-global-functions.md#atladvise), [CComPtrBase::Advise](../atl/reference/ccomptrbase-class.md#advise)|[AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise)| Vtable lub podwójne interfejsy | Tak | `AtlAdvise` jest funkcją globalną ATL. `CComPtrBase::Advise` jest używany przez [CComPtr](../atl/reference/ccomptr-class.md) i [CComQIPtr](../atl/reference/ccomqiptr-class.md). |  

|[IDispEventSimpleImpl::DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise)|[IDispEventSimpleImpl::DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise)|[IDispEventImpl](../atl/reference/idispeventimpl-class.md) lub [ IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)| Nie | Parametry mniej niż `AtlAdvise` od klasy podstawowej jest więcej pracy. |  
|[CComCompositeControl::AdviseSinkMap(TRUE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|[CComCompositeControl::AdviseSinkMap(FALSE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)| Formanty ActiveX w formanty złożone | Nie | `CComCompositeControl::AdviseSinkMap` z informacją o tym wszystkie wpisy sink zdarzeń mapy. Taką samą funkcję unadvises wpisów. Ta metoda jest wywoływana automatycznie przez `CComCompositeControl` klasy. |  
|[CAxDialogImpl::AdviseSinkMap(TRUE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|[CAxDialogImpl::AdviseSinkMap(FALSE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)| Formanty ActiveX w oknie dialogowym | Nie | `CAxDialogImpl::AdviseSinkMap` zaleceniem i unadvises wszystkich kontrolek ActiveX w zasobu okna dialogowego. Odbywa się to automatycznie dla Ciebie. |  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa zdarzeń](../atl/event-handling-and-atl.md)   
 [Obsługa interfejsu IDispEventImpl](../atl/supporting-idispeventimpl.md)

