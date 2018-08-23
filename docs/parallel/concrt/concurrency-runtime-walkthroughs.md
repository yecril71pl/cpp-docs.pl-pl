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
ms.openlocfilehash: 19de73a99384d8cea0f9f594b5a1a214f8aaaf22
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2018
ms.locfileid: "42465260"
---
# <a name="concurrency-runtime-walkthroughs"></a>Współbieżność środowiska wykonawczego — Wskazówki
Oparte na scenariuszach tematy w tej sekcji pokazano, jak używać wielu funkcji środowiska uruchomieniowego współbieżności.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przewodnik: łączenie za pomocą zadań i żądań XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)  
 Ilustruje sposób używania [IXMLHTTPRequest2](/previous-versions/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2) i [IXMLHTTPRequest2Callback](/previous-versions/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2callback) interfejsów oraz zadań wysyłać żądania HTTP GET i POST do usługi sieci web w aplikacji platformy uniwersalnej Windows (UWP).  
  
 [Przewodnik: tworzenie aplikacji opartej o agentów](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)  
 W tym artykule opisano sposób tworzenia podstawowych aplikacji opartej o agentów.  
  
 [Przewodnik: tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)  
 Pokazuje, jak tworzyć aplikacje oparte na agentach, oparte na przepływ danych, a nie na przepływ sterowania.  
  
 [Przewodnik: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)  
 Pokazuje, jak utworzyć sieć bloki komunikatów asynchronicznych, wykonujących przetwarzanie obrazu.  
  
 [Przewodnik: wdrażanie przyszłych operacji](../../parallel/concrt/walkthrough-implementing-futures.md)  
 Pokazuje, jak asynchroniczne obliczenia wartości do późniejszego użycia.  
  
 [Przewodnik: korzystanie ze złączy w celu zapobiegania zakleszczeniom](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)  
 Używa problem ucztujących filozofów, aby zilustrować, jak używać [concurrency::join](../../parallel/concrt/reference/join-class.md) klasy w celu uniknięcia zakleszczenia w aplikacji.  
  
 [Przewodnik: usuwanie pracy z wątku interfejs użytkownika](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)  
 Pokazuje, jak poprawić wydajność aplikacji MFC, który rysuje fraktalowy Mandelbrot.  
  
 [Przewodnik: korzystanie ze środowiska uruchomieniowego współbieżności w aplikacji z możliwością korzystania z COM](../../parallel/concrt/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application.md)  
 Pokazuje sposób korzystania ze współbieżności środowiska wykonawczego w aplikacji, która używa Component Object Model (COM).  
  
 [Przewodnik: adaptacja istniejącego kodu do potrzeb zadań lekkich](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)  
 Pokazuje, jak dostosować istniejący kod, który używa interfejsu API Windows do tworzenia i wykonywanie wątku w celu użycia lekkiego zadania.  
  
 [Przewodnik: tworzenie niestandardowego bloku komunikatów](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)  
 W tym artykule opisano sposób tworzenia komunikatów niestandardowy typ bloku, które porządkuje przychodzące wiadomości według priorytetu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)  
 Wprowadza platformy programowania współbieżnego dla języka Visual C++.

