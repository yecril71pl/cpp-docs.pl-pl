---
title: Współbieżność środowiska wykonawczego — wskazówki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- walkthroughs [Concurrency Runtime]
- Concurrency Runtime, walkthroughs
ms.assetid: 7374c5e9-54eb-44bf-9ed9-5e190cfd290b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05e50530bf1c7aa401a7422a0119f004e30234a9
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686636"
---
# <a name="concurrency-runtime-walkthroughs"></a>Współbieżność środowiska wykonawczego — Wskazówki
Oparta na scenariuszu tematy w tej sekcji przedstawiono sposoby używania wielu funkcji współbieżności środowiska wykonawczego.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przewodnik: łączenie za pomocą zadań i żądań XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)  
 Przedstawia sposób użycia [IXMLHTTPRequest2](http://msdn.microsoft.com/en-us/bbc11c4a-aecf-4d6d-8275-3e852e309908) i [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/en-us/aa4b3f4c-6e28-458b-be25-6cce8865fc71) interfejsy wraz z zadań do wysyłania żądań HTTP GET i POST do usługi sieci web w aplikacji Windows platformy Uniwersalnej.  
  
 [Przewodnik: tworzenie aplikacji opartej o agentów](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)  
 Opisuje sposób tworzenia podstawowej aplikacji opartej o agentów.  
  
 [Przewodnik: tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)  
 Przedstawia sposób tworzenia aplikacji opartych na agenta, które są oparte na przepływu danych, a nie na przepływu sterowania.  
  
 [Przewodnik: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)  
 Pokazuje, jak utworzyć sieć bloki komunikatów asynchronicznych, które przetwarzania obrazu.  
  
 [Przewodnik: wdrażanie przyszłych operacji](../../parallel/concrt/walkthrough-implementing-futures.md)  
 Przedstawia sposób asynchronicznie obliczać wartości do późniejszego użycia.  
  
 [Przewodnik: korzystanie ze złączy w celu zapobiegania zakleszczeniom](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)  
 Używa lokali problem philosophers ilustrujący sposób użycia [concurrency::join](../../parallel/concrt/reference/join-class.md) klasę, aby zapobiec zakleszczenie w aplikacji.  
  
 [Przewodnik: usuwanie pracy z wątku interfejs użytkownika](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)  
 Pokazuje, jak poprawić wydajność aplikacji MFC rysującą fraktalowy Mandelbrot.  
  
 [Przewodnik: korzystanie ze środowiska uruchomieniowego współbieżności w aplikacji z możliwością korzystania z COM](../../parallel/concrt/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application.md)  
 Przedstawiono sposób korzystania ze współbieżności środowiska wykonawczego w aplikacji korzystającej z modelu obiektu składników (COM).  
  
 [Przewodnik: adaptacja istniejącego kodu do potrzeb zadań lekkich](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)  
 Pokazuje, jak adaptacja istniejącego kodu, który używa interfejsu API systemu Windows do tworzenia i wykonywania wątku w celu użyć zadania lekkie.  
  
 [Przewodnik: tworzenie niestandardowego bloku komunikatów](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)  
 Opisuje sposób tworzenia niestandardowego komunikatu typ bloku, któremu porządkuje komunikaty przychodzące według priorytetu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)  
 Wprowadza równoczesnych Architektura programowania w języku Visual C++.

