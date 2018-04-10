---
title: Przy użyciu IDispEventSimpleImpl (ATL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDispEventSimpleImpl
dev_langs:
- C++
helpviewer_keywords:
- IDispEventSimpleImpl class, using
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ed21c862d61686e86efd684a6e88795e4b7bbe51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-idispeventsimpleimpl"></a>Przy użyciu IDispEventSimpleImpl
Korzystając z `IDispEventSimpleImpl` do obsługi zdarzeń, konieczne będzie:  
  
-   Pochodzi z klasy [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md).  
  
-   Dodaj mapę obiekt sink zdarzenia do swojej klasy.  
  
-   Zdefiniuj [_ATL_FUNC_INFO](../atl/reference/atl-func-info-structure.md) struktury zawierająca opis zdarzenia.  
  
-   Dodawanie wpisów do event sink mapy przy użyciu [SINK_ENTRY_INFO](reference/composite-control-macros.md#sink_entry_info) makra.  
  
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
  
 [!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventsimpleimpl_1.h)]  
  
 Wszystkie informacje z biblioteki typów faktycznie używana w tym przykładzie jest CLSID Word **aplikacji** obiekt i uzyskanie identyfikatora IID **ApplicationEvents** interfejsu. Te informacje jest używana tylko w czasie kompilacji.  
  
 Poniższy kod zostanie wyświetlony w Simple.h. Odpowiedni kod jest odnotowany odpowiednimi komentarzami:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/cpp/using-idispeventsimpleimpl_2.h)]  
  
 Poniższy kod jest Simple.cpp:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/cpp/using-idispeventsimpleimpl_3.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa zdarzeń](../atl/event-handling-and-atl.md)   
 [Przykładowe ATLEventHandling](../visual-cpp-samples.md)

