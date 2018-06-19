---
title: Agenci asynchroniczni | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- asynchronous agents
- agents [Concurrency Runtime]
ms.assetid: 6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8649ebe0451e4352b27989563a1a0918afcb5a01
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687982"
---
# <a name="asynchronous-agents"></a>Agenci asynchroniczni
*Asynchroniczne agenta* (lub po prostu *agenta*) to składnik aplikacji asynchronicznie współpracuje z innymi czynnikami rozwiązać większych zadań. Agenta można traktować jako zadanie, które ma ustawione cyklu życia. Na przykład jeden agent może odczytać danych z urządzenia wejścia/wyjścia (na przykład klawiatura, plik na dysku lub połączenie sieciowe) i innego agenta może wykonać akcję na tych danych po jej udostępnieniu. Pierwszy agent używa przekazywanie komunikatów do agenta drugiego informuje, że dostępnych jest więcej danych. Współbieżność środowiska wykonawczego harmonogram zadań zapewnia mechanizm wydajne umożliwiające agentów zablokować, a także uzyskanie wspólnie bez konieczności wywłaszczanie mniej wydajne.  
  

 Biblioteki agentów definiuje [concurrency::agent](../../parallel/concrt/reference/agent-class.md) klasy do reprezentowania asynchroniczne agenta. `agent` jest klasą abstrakcyjną, która deklaruje metody wirtualnej [concurrency::agent::run](reference/agent-class.md#run). `run` Metoda wykonuje zadanie, które jest wykonywane przez agenta. Ponieważ `run` jest abstrakcyjna, musisz zaimplementować tę metodę w każdej klasie, z której pochodzi od `agent`.  
  
## <a name="agent-life-cycle"></a>Cykl życia agenta  
 Agenci mają ustawione cyklu życia. [Concurrency::agent_status](reference/concurrency-namespace-enums.md#agent_status) wyliczenie definiuje różne stany agenta. Na rysunku poniżej przedstawiono diagram stanu pokazującego postęp agentów z jednego stanu do innego. Na tej ilustracji linia ciągła reprezentują metody, które można wywołać z poziomu aplikacji; Wiersze przerywana reprezentują metod, które są wywoływane ze środowiska uruchomieniowego.  
  
 ![Diagram stanu agenta](../../parallel/concrt/media/agentstate.png "agentstate")  
  
 W poniższej tabeli opisano każdy stan w `agent_status` wyliczenia.  
  
|Stan agenta.|Opis|  
|-----------------|-----------------|  
|`agent_created`|Agent nie zostało zaplanowane do wykonania.|  
|`agent_runnable`|Środowisko wykonawcze jest planowanie agent do wykonania.|  
|`agent_started`|Agent został uruchomiony i działa.|  
|`agent_done`|Zakończono agenta.|  
|`agent_canceled`|Agent została anulowana, zanim pojawił się `started` stanu.|  
  
 `agent_created` początkowy stan agenta jest `agent_runnable` i `agent_started` są aktywne stany i `agent_done` i `agent_canceled` terminali Stany.  
  
 Użyj [concurrency::agent::status](reference/agent-class.md#status) metodę, aby pobrać bieżący stan `agent` obiektu. Mimo że `status` metoda jest bezpieczne współbieżności, stan agenta można zmienić w czasie `status` zwraca metody. Agent może być na przykład w `agent_started` stanu podczas wywoływania `status` metody, ale przeniesiony do `agent_done` stanu tuż po `status` zwraca metody.  

  
## <a name="methods-and-features"></a>Metody i funkcje  
 W poniższej tabeli przedstawiono niektóre ważne metody, które należą do `agent` klasy. Aby uzyskać więcej informacji o wszystkich `agent` metody klasy, zobacz [agenta klasy](../../parallel/concrt/reference/agent-class.md).  
  
|Metoda|Opis|  
|------------|-----------------|  
|[start](reference/agent-class.md#start)|Harmonogramy `agent` obiektu do wykonania i ustawia ją na `agent_runnable` stanu.|  
|[run](reference/agent-class.md#run)|Wykonuje zadanie, które ma być wykonywane przez `agent` obiektu.|  
|[Gotowe](reference/agent-class.md#done)|Przenosi agentowi `agent_done` stanu.|  
|[cancel](../../parallel/concrt/cancellation-in-the-ppl.md#cancel)|Jeśli agent nie został uruchomiony, ta metoda powoduje anulowanie wykonywania agenta i ustawia ją na `agent_canceled` stanu.|  
|[status](reference/agent-class.md#status)|Pobiera bieżący stan `agent` obiektu.|  
|[oczekiwania](reference/agent-class.md#wait)|Czeka na `agent` obiekt, aby wprowadzić `agent_done` lub `agent_canceled` stanu.|  
|[wait_for_all](reference/agent-class.md#wait_for_all)|Czeka na wszystkie podane `agent` obiektów, aby wprowadzić `agent_done` lub `agent_canceled` stanu.|  
|[wait_for_one](reference/agent-class.md#wait_for_one)|Oczekuje na co najmniej jeden z dostarczonego `agent` obiektów, aby wprowadzić `agent_done` lub `agent_canceled` stanu.|  
  
 Po utworzeniu obiektu agenta należy wywołać [concurrency::agent::start](reference/agent-class.md#start) metody do zaplanowania jej wykonanie. Wywołania środowiska uruchomieniowego `run` metody po planuje agenta i ustawia ją na `agent_runnable` stanu.  
  
 Środowisko uruchomieniowe nie zarządza wyjątki, które są generowane przez agentów asynchronicznych. Aby uzyskać więcej informacji na temat obsługi wyjątków i agentów zobacz [obsługi wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
## <a name="example"></a>Przykład  
 Na przykład, który przedstawia sposób tworzenia podstawowej aplikacji opartej o agentów, zobacz [wskazówki: tworzenie aplikacji opartej o agentów](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)

