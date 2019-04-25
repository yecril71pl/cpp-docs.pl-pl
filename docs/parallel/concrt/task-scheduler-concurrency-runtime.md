---
title: Harmonogram zadań (współbieżność środowiska wykonawczego)
ms.date: 11/04/2016
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
ms.openlocfilehash: c5d37d320344d2ebf83be2c939f5a7372d4af306
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180059"
---
# <a name="task-scheduler-concurrency-runtime"></a>Harmonogram zadań (współbieżność środowiska wykonawczego)

W tematach w tej części dokumentacji opisano ważne funkcje harmonogram zadań środowiska uruchomieniowego współbieżności. Harmonogram zadań jest przydatne, gdy chcesz dostrojenie wydajności usługi istniejący kod, który używa środowiska uruchomieniowego współbieżności.

> [!IMPORTANT]
>  Harmonogram zadań nie jest dostępna z aplikacji platformy uniwersalnej Windows (UWP). Aby uzyskać więcej informacji, zobacz [tworzenie operacji asynchronicznych w języku C++ dla aplikacji platformy UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).
>
>  W programie Visual Studio 2015 i nowszych [concurrency::task](../../parallel/concrt/reference/task-class.md) klas i typów powiązanych w ppltasks.h użyć puli wątków Windows jako ich harmonogram. Ten temat dotyczy nie jest już na typy, które są zdefiniowane w ppltasks.h. Algorytmy równoległe, takie jak parallel_for w dalszym ciągu używać środowiska uruchomieniowego współbieżności jako domyślnego harmonogramu.

> [!TIP]
>  Środowisko uruchomieniowe współbieżności zawiera domyślnego harmonogramu, a w związku z tym nie należy utworzyć w aplikacji. Ponieważ Harmonogram zadań ułatwia dostrajania wydajności aplikacji, zalecamy rozpoczęcie od [biblioteki wzorców równoległych (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) lub [bibliotekę asynchronicznych agentów](../../parallel/concrt/asynchronous-agents-library.md) przypadku jesteś nowym użytkownikiem w czasie wykonywania współbieżności.

Harmonogram zadań planuje i koordynuje zadania w czasie wykonywania. A *zadań* jest jednostką pracy, który wykonuje określone zadanie. Zadania zazwyczaj można uruchomić równolegle z innymi zadaniami. Pracę wykonywaną przez elementy grupy zadań, algorytmy równoległe i agentów asynchronicznych należą do nich zadania.

Harmonogram zadań zarządza szczegółowe informacje, które są powiązane z efektywne planowanie zadań na komputerach, które mają wiele zasobów obliczeniowych. Harmonogram zadań również korzysta z najnowszych funkcji systemu operacyjnego. W związku z tym aplikacje, które używają środowiska uruchomieniowego współbieżności automatycznie skalować i poprawić na sprzęcie, który wzrosły możliwości.

[Porównanie z modelami współbieżności inne](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md) opisano różnice między mechanizmy planowania preemptive i współpracy. Harmonogram zadań używa planowania współpracy i algorytmu kradzież pracy wraz z preemptive Harmonogram systemu operacyjnego do osiągnięcia maksymalnego użycia przetwarzania zasobów.

Środowisko uruchomieniowe współbieżności zawiera domyślnego harmonogramu, tak, aby nie trzeba zarządzać szczegóły infrastruktury. Dlatego należy zwykle nie należy używać harmonogramu zadań bezpośrednio. Jednak aby zaspokoić potrzeby jakości aplikacji, można użyć harmonogramu zadań, podać własne planowania zasad lub skojarz transfery danych z określonych zadań. Na przykład załóżmy, że masz równoległego sortowanie procedury, która nie skalować poza cztery procesory. Możesz użyć *zasad harmonogramu* utworzyć harmonogram, który generuje nie więcej niż cztery współbieżnych zadań. Uruchamianie procedury sortowania na ten harmonogram umożliwia innych aktywnych harmonogramów wszelkie pozostałe zasoby przetwarzania.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Wystąpienia harmonogramu](../../parallel/concrt/scheduler-instances.md)|W tym artykule opisano wystąpienia harmonogramu i sposobu używania `concurrency::Scheduler` i `concurrency::CurrentScheduler` klasy, aby zarządzać nimi. Wystąpienia harmonogramu należy użyć skojarzyć zasady planowania jawne za pomocą określonych rodzajów obciążeń.|
|[Zasady harmonogramu](../../parallel/concrt/scheduler-policies.md)|W tym artykule opisano rolę zasad harmonogramu. Gdy użytkownik chce kontrolować strategii, używany w harmonogramie podczas zarządzania zadaniami za pomocą zasad harmonogramu.|
|[Grupy harmonogramu](../../parallel/concrt/schedule-groups.md)|W tym artykule opisano rolę harmonogramu grupy. Użyj grupy harmonogramu, gdy na przykład wymagają wysokiego stopnia miejscowość spośród zadań, gdy grupa powiązanych zadań korzystają z wykonywane w tym samym węźle procesora.|
|[Zadania lekkie](../../parallel/concrt/lightweight-tasks.md)|W tym artykule opisano rolę lekkie zadanie. Zadania lekkie są przydatne, gdy dostosowanie istniejącego kodu do planowania funkcji środowiska uruchomieniowego współbieżności.|
|[Konteksty](../../parallel/concrt/contexts.md)|Zawiera opis roli kontekstach `concurrency::wait` funkcji i `concurrency::Context` klasy. W przypadku konieczności sprawowania kontroli nad po kontekstów block odblokowania i uzyskanie lub jeśli chcesz włączyć nadsubskrypcję w aplikacji, należy użyć tej funkcji.|
|[Funkcje zarządzania pamięcią](../../parallel/concrt/memory-management-functions.md)|W tym artykule opisano `concurrency::Alloc` i `concurrency::Free` funkcji. Te funkcje można zwiększyć wydajność pamięci, przez przydzielanie i zwalnianie pamięci w sposób współbieżnych.|
|[Porównywanie z innymi modelami współbieżności](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|W tym artykule opisano różnice między mechanizmy planowania preemptive i współpracy.|
|[Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Opisuje sposób używania różnych równoległych wzorców, na przykład algorytmów równoległych w aplikacjach.|
|[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)|W tym artykule opisano, jak używać agentów asynchronicznych w aplikacjach.|
|[Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)|W tym artykule opisano środowisko uruchomieniowe współbieżności, upraszczający Programowanie równoległe i zawiera linki do powiązanych tematów.|
