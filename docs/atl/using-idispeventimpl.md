---
title: Przy użyciu IDispEventImpl (ATL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- IDispEventImpl
dev_langs:
- C++
helpviewer_keywords:
- IDispEventImpl class, using
ms.assetid: 82d53b61-9d0d-45c5-aff9-2fafa468a9ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 520d1129234a26ff6eb4c402154969ad7e166211
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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

