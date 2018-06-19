---
title: Zadania harmonogramu (współbieżność środowiska wykonawczego) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- oversubscription [Concurrency Runtime]
- task scheduler [Concurrency Runtime], oversubscription
- schedule groups [Concurrency Runtime]
- task scheduler [Concurrency Runtime], lightweight tasks
- task scheduler [Concurrency Runtime]
- lightweight tasks [Concurrency Runtime]
- task scheduler [Concurrency Runtime], scheduler policies
- task scheduler [Concurrency Runtime], schedule groups
- wait function [Concurrency Runtime]
- task scheduler [Concurrency Runtime], scheduler instances
- scheduler instances [Concurrency Runtime]
- scheduler policies [Concurrency Runtime]
- task scheduler [Concurrency Runtime], wait function
ms.assetid: 9aba278c-e0c9-4ede-b7c6-fedf7a365d90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b76aaa0310e9f481ea65a0ab0600a0e3ae6aed7c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689324"
---
# <a name="task-scheduler-concurrency-runtime"></a>Harmonogram zadań (współbieżność środowiska wykonawczego)
W tematach w tej części dokumentacji opisano ważne funkcje harmonogram zadań współbieżności środowiska wykonawczego. Harmonogram zadań jest przydatne, gdy chcesz dostrojenie wydajności istniejący kod, który korzysta ze współbieżności środowiska wykonawczego.  
  
> [!IMPORTANT]
>  Harmonogram zadań nie jest dostępny z poziomu aplikacji systemu Windows platformy Uniwersalnej. Aby uzyskać więcej informacji, zobacz [tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).  
>   
>  W programie Visual Studio 2015 lub nowszego oraz [concurrency::task](../../parallel/concrt/reference/task-class.md) klasy i powiązanych typów z ppltasks.h Użyj puli wątków systemu Windows jako ich harmonogramu. W tym temacie nie ma już zastosowania do typów, które są zdefiniowane w ppltasks.h. Algorytmy równoległe, takich jak parallel_for w dalszym ciągu korzystać ze współbieżności środowiska wykonawczego jako domyślnego harmonogramu.  
  
> [!TIP]
>  Współbieżność środowiska wykonawczego zapewnia harmonogram domyślny, i dlatego nie trzeba utworzyć w aplikacji. Harmonogram zadań ułatwia dostrojenie wydajności aplikacji, dlatego zaleca się uruchamiania z [równoległych biblioteki wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md) lub [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) w przypadku jesteś nowym użytkownikiem współbieżności środowiska wykonawczego.  
  
 Harmonogram zadań harmonogramy i koordynuje zadań w czasie wykonywania. A *zadań* jest jednostka pracy, który wykonuje określone zadanie. Zadania można są zazwyczaj uruchamiane równolegle z innymi zadaniami. Pracy, które jest wykonywane przez elementy grupy zadań, algorytmy równoległe i agentów asynchronicznych należą do nich zadań.  
  
 Harmonogram zadań zarządza szczegółowe informacje, które są powiązane z efektywne planowanie zadań na komputerach, które mają wiele zasobów obliczeniowych. Harmonogram zadań używa także najnowsze funkcje systemu operacyjnego. W związku z tym aplikacje korzystające ze współbieżności środowiska wykonawczego automatycznie skalować i poprawić na sprzęcie, który daje szereg nowych możliwości.  
  
 [Porównywanie z modelami współbieżności inne](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md) opisano różnice między mechanizmy planowania cenią sobie wcześniejsze i współpracy. Harmonogram zadań używa współpracy planowania i algorytmu kradzież pracy oraz cenią sobie wcześniejsze Harmonogram systemu operacyjnego do osiągnięcia maksymalnego użycia przetwarzania zasobów.  
  
 Współbieżność środowiska wykonawczego zawiera harmonogram domyślny, dzięki czemu nie trzeba zarządzać szczegóły infrastruktury. W związku z tym należy zwykle nie należy używać harmonogram zadań bezpośrednio. Jednak aby spełnić wymagania jakości aplikacji, można użyć harmonogramu zadań, aby podać własne planowania planiści zasad lub kojarzenie z określonych zadań. Na przykład załóżmy, że masz równoległego sortowanie procedury, która nie obsługuje więcej niż cztery procesory. Można użyć *zasad harmonogramu* można utworzyć harmonogramu, która generuje nie więcej niż cztery równoczesnych zadań. Uruchamianie procedury sortowania na ten harmonogram umożliwia inne aktywne planiści wszelkie pozostałe zasoby przetwarzania.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wystąpienia harmonogramu](../../parallel/concrt/scheduler-instances.md)|W tym artykule opisano wystąpienia harmonogramu i sposobu użycia `concurrency::Scheduler` i `concurrency::CurrentScheduler` klasy do zarządzania nimi. Wystąpienia harmonogramu należy użyć, jeśli chcesz skojarzyć z określonych rodzajów obciążeń jawne zasadami planowania.|  
|[Zasady harmonogramu](../../parallel/concrt/scheduler-policies.md)|Zawiera opis roli zasad harmonogramu. Jeśli chcesz kontrolować strategii, używany w harmonogramie podczas zarządzania zadania przy użyciu zasad harmonogramu.|  
|[Grupy harmonogramu](../../parallel/concrt/schedule-groups.md)|Zawiera opis roli grup harmonogramu. Grupy harmonogramu Użyj, jeśli wymagane jest wysoki stopień miejscowości spośród zadań, na przykład, gdy grupa powiązanych zadań korzystać z wykonania na tym samym węźle procesora.|  
|[Zadania lekkie](../../parallel/concrt/lightweight-tasks.md)|Zawiera opis roli lekkie zadań. Zadania lekkie jest przydatna w przypadku dostosowania istniejącego kodu do korzystania z funkcji planowania programu współbieżności środowiska wykonawczego.|  
|[Konteksty](../../parallel/concrt/contexts.md)|Zawiera opis roli kontekstów, `concurrency::wait` funkcji i `concurrency::Context` klasy. Tej funkcji należy używać wtedy, gdy będziesz potrzebować kontrolę nad po kontekstów zablokować odblokować i uzyskanie lub jeśli chcesz włączyć nadsubskrypcji w aplikacji.|  
|[Funkcje zarządzania pamięcią](../../parallel/concrt/memory-management-functions.md)|W tym artykule opisano `concurrency::Alloc` i `concurrency::Free` funkcji. Te funkcje umożliwiają poprawę wydajności pamięci przydzielając i zwolnić pamięć, w sposób współbieżnych.|  
|[Porównywanie z innymi modelami współbieżności](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|W tym artykule opisano różnice między mechanizmy planowania cenią sobie wcześniejsze i współpracy.|  
|[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Informacje dotyczące używania różnych równoległych wzorców, na przykład algorytmy równoległe w aplikacji.|  
|[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)|Opisuje sposób korzystania z agentów asynchronicznych w aplikacjach użytkownika.|  
|[Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)|W tym artykule opisano współbieżność środowiska wykonawczego, co upraszcza Programowanie równoległe i zawiera linki do powiązanych tematów.|

