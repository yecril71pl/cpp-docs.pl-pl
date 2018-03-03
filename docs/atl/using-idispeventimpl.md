---
title: "Przy użyciu IDispEventImpl (ATL) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDispEventImpl
dev_langs:
- C++
helpviewer_keywords:
- IDispEventImpl class, using
ms.assetid: 82d53b61-9d0d-45c5-aff9-2fafa468a9ca
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f787fac05e95fff8a974692c3e6fca24561ed222
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-idispeventimpl"></a>Przy użyciu IDispEventImpl
Korzystając z `IDispEventImpl` do obsługi zdarzeń, konieczne będzie:  
  
-   Pochodzi z klasy [IDispEventImpl](../atl/reference/idispeventimpl-class.md).  
  
-   Dodaj mapę obiekt sink zdarzenia do swojej klasy.  
  
-   Dodawanie wpisów do event sink mapy przy użyciu [SINK_ENTRY](reference/composite-control-macros.md#sink_entry) lub [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex) makra.  
  
-   Implementuje metody, że jesteś zainteresowany obsługi.  
  
-   Powiadomienia i unadvise źródło zdarzenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób obsługi **DocumentChange** zdarzenia wywoływane przez Word **aplikacji** obiektu. To zdarzenie jest definiowane jako metodę na **ApplicationEvents** dispinterface.  
  
 Przykładem jest z [próbki ATLEventHandling](../visual-cpp-samples.md).  
  
 `[`  
  
 `uuid(000209F7-0000-0000-C000-000000000046),`  
  
 `hidden`  
  
 `]`  
  
 `dispinterface ApplicationEvents {`  
  
 `properties:`  
  
 `methods:`  
  
 `[id(0x00000001), restricted, hidden]`  
  
 `void Startup();`  
  
 `[id(0x00000002)]`  
  
 `void Quit();`  
  
 `[id(0x00000003)]`  
  
 `void DocumentChange();`  
  
 `};`  
  
 W przykładzie użyto `#import` generuje pliki wymaganego nagłówka z biblioteki typów dla programu Word. Jeśli chcesz użyć tego przykładu z innymi wersjami programu Word, należy określić poprawną mso pliku dll. Na przykład pakiet Office 2000 zawiera mso9.dll i OfficeXP zapewnia mso.dll. Ten kod jest uproszczone z stdafx.h:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventimpl_1.h)]  
  
 Poniższy kod zostanie wyświetlony w NotSoSimple.h. Odpowiedni kod jest odnotowany odpowiednimi komentarzami:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#2](../atl/codesnippet/cpp/using-idispeventimpl_2.h)]  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa zdarzeń](../atl/event-handling-and-atl.md)   
 [Przykładowe ATLEventHandling](../visual-cpp-samples.md)

