---
title: "Współbieżność środowiska wykonawczego — wskazówki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- walkthroughs [Concurrency Runtime]
- Concurrency Runtime, walkthroughs
ms.assetid: 7374c5e9-54eb-44bf-9ed9-5e190cfd290b
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 42eae02b1eb789ea1333a8333e2f947457f87a41
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="concurrency-runtime-walkthroughs"></a>Współbieżność środowiska wykonawczego — Wskazówki
Oparta na scenariuszu tematy w tej sekcji przedstawiono sposoby używania wielu funkcji współbieżności środowiska wykonawczego.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wskazówki: Łączenie za pomocą zadań i żądań XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)  
 Przedstawia sposób użycia [IXMLHTTPRequest2](http://msdn.microsoft.com/en-us/bbc11c4a-aecf-4d6d-8275-3e852e309908) i [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/en-us/aa4b3f4c-6e28-458b-be25-6cce8865fc71) interfejsy wraz z zadań do wysyłania żądań HTTP GET i POST do usługi sieci web w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji.  
  
 [Wskazówki: Tworzenie aplikacji opartej o agentów](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)  
 Opisuje sposób tworzenia podstawowej aplikacji opartej o agentów.  
  
 [Wskazówki: Tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)  
 Przedstawia sposób tworzenia aplikacji opartych na agenta, które są oparte na przepływu danych, a nie na przepływu sterowania.  
  
 [Wskazówki: Tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)  
 Pokazuje, jak utworzyć sieć bloki komunikatów asynchronicznych, które przetwarzania obrazu.  
  
 [Wskazówki: Wdrażanie przyszłych operacji](../../parallel/concrt/walkthrough-implementing-futures.md)  
 Przedstawia sposób asynchronicznie obliczać wartości do późniejszego użycia.  
  
 [Wskazówki: Używanie w celu zapobiegania zakleszczeniom](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)  
 Używa lokali problem philosophers ilustrujący sposób użycia [concurrency::join](../../parallel/concrt/reference/join-class.md) klasę, aby zapobiec zakleszczenie w aplikacji.  
  
 [Wskazówki: Usuwanie pracy z wątku interfejsu użytkownika](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)  
 Pokazuje, jak poprawić wydajność aplikacji MFC rysującą fraktalowy Mandelbrot.  
  
 [Wskazówki: Korzystanie ze współbieżności środowiska wykonawczego w aplikacji z obsługą COM](../../parallel/concrt/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application.md)  
 Przedstawiono sposób korzystania ze współbieżności środowiska wykonawczego w aplikacji korzystającej z modelu obiektu składników (COM).  
  
 [Wskazówki: Adaptacja istniejącego kodu do potrzeb zadań lekkich](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)  
 Pokazuje, jak adaptacja istniejącego kodu, który używa interfejsu API systemu Windows do tworzenia i wykonywania wątku w celu użyć zadania lekkie.  
  
 [Wskazówki: Tworzenie niestandardowego bloku komunikatów](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)  
 Opisuje sposób tworzenia niestandardowego komunikatu typ bloku, któremu porządkuje komunikaty przychodzące według priorytetu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Współbieżność środowiska wykonawczego](../../parallel/concrt/concurrency-runtime.md)  
 Wprowadza równoczesnych Architektura programowania w języku Visual C++.

