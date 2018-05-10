---
title: Omówienie współbieżności środowiska wykonawczego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Concurrency Runtime, requirements
- Concurrency Runtime, architecture
- Concurrency Runtime, overview
- Concurrency Runtime, lambda expressions
ms.assetid: 56237d96-10b0-494a-9cb4-f5c5090436c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 67f0497f600cf5d528b2c41601b7a02c08771861
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="overview-of-the-concurrency-runtime"></a>Omówienie współbieżności środowiska wykonawczego
Ten dokument zawiera omówienie współbieżności środowiska wykonawczego. Opisuje korzyści ze współbieżności środowiska wykonawczego, kiedy należy używać go i interakcje jego składniki ze sobą i z systemu operacyjnego i aplikacji.  
  
> [!IMPORTANT]
>  W programie Visual Studio 2015 lub nowszego oraz harmonogram zadań współbieżności środowiska wykonawczego nie jest już harmonogram dla zadania klasy i powiązanych typów z ppltasks.h. Te typy teraz używać pozostawiło Windows lepszą wydajność i współdziałanie z elementów podstawowych synchronizacji systemu Windows. Algorytmy równoległe, takich jak parallel_for w dalszym ciągu korzystać z harmonogramu zadań współbieżności środowiska wykonawczego.  
  
##  <a name="top"></a> Sekcje  
 Ten dokument zawiera następujące sekcje:  
  
-   [Dlaczego jest ważne w środowisku uruchomieniowym na potrzeby współbieżności](#runtime)  
  
-   [Architektura](#architecture)  
  
-   [Wyrażenia Lambda w języku C++](#lambda)  
  
-   [Wymagania](#requirements)  
  
##  <a name="runtime"></a> Dlaczego jest ważne w środowisku uruchomieniowym na potrzeby współbieżności  
 Środowisko uruchomieniowe dla współbieżności zapewnia jednolitość i przewidywalności do aplikacji i składników aplikacji, które są uruchamiane jednocześnie. Są dwa przykłady korzyści ze współbieżności środowiska wykonawczego *Planowanie zadań współpracy* i *współpracy blokuje*.  
  
 Współbieżność środowiska wykonawczego używa harmonogramu zadań współpracy implementujący algorytmu kradzież pracy umożliwiająca efektywną dystrybucję pracy między zasobów obliczeniowych. Rozważmy na przykład aplikacja, która ma dwa wątki zarządzanych zarówno przez tego samego środowiska wykonawczego. Jeśli jeden wątek zakończy działanie jego zaplanowanego zadania, jego odciążania pracy z innego wątku. Ten mechanizm równoważy obciążenie ogólną aplikacji.  
  
 Współbieżność środowiska wykonawczego także elementy podstawowe synchronizacji używających współpracy blokuje synchronizujący dostęp do zasobów. Rozważmy na przykład zadań, która wymaga wyłącznego dostępu do zasobu udostępnionego. Blokując wspólnie, środowisko uruchomieniowe umożliwia pozostałych quantum wykonywanie innego zadania jako pierwsze zadanie czeka na zasób. Ten mechanizm wspiera maksymalnego użycia zasobów obliczeniowych.  
  
 [[Górnej](#top)]  
  
##  <a name="architecture"></a> Architektura  
 Współbieżność środowiska wykonawczego jest podzielony na cztery składniki: Biblioteka równoległych wzorców (PLL), biblioteki agentów asynchronicznych harmonogramu zadań i Menedżera zasobów. Te składniki znajdują się między systemu operacyjnego i aplikacji. Na poniższej ilustracji przedstawiono składniki współbieżność środowiska wykonawczego interakcje między systemu operacyjnego i aplikacji:  
  
 **Architektura wykonywania równoczesnego**  
  
 ![Architektura wykonywania równoczesnego](../../parallel/concrt/media/concurrencyrun.png "concurrencyrun")  
  
> [!IMPORTANT]
>  Składniki harmonogramu zadań i Menedżera zasobów nie są dostępne z poziomu aplikacji uniwersalnych platformy systemu Windows (UWP) lub użyj klasy zadania lub innych typów w ppltasks.h.  
  
 Współbieżność środowiska wykonawczego jest wysoce *zezwala na składanie*, oznacza to, można połączyć istniejące funkcje do innych. Współbieżność środowiska wykonawczego Redaguj wiele funkcji, takich jak algorytmy równoległe z składniki niższego poziomu.  
  
 Współbieżność środowiska wykonawczego także elementy podstawowe synchronizacji używających współpracy blokuje synchronizujący dostęp do zasobów. Aby uzyskać więcej informacji o tych podstawowych synchronizacji, zobacz [struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md).  
  
 Poniższe sekcje zawierają krótkie omówienie poszczególnych składników zapewnia i kiedy należy używać go.  
  
### <a name="parallel-patterns-library"></a>Biblioteka równoległych wzorców  
 Biblioteka równoległych wzorców (PLL) umożliwia kontenery ogólnego przeznaczenia i algorytmów w celu wykonania szczegółowych równoległości. Umożliwia PPL *równoległość danych konieczne* zapewniając algorytmów równoległych rozpowszechniają obliczenia na kolekcje lub zestawy danych zasobów obliczeniowych. Umożliwia również *równoległość zadań* zapewniając obiektów zadań, które rozpowszechniają wiele operacji niezależnych zasobów obliczeniowych.  
  
 Biblioteka równoległych wzorców należy użyć w przypadku lokalnego obliczeń, który może korzystać z przetwarzania równoległego. Na przykład można użyć [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytm przekształcania istniejące `for` pętli do działania równoległe.  
  
 Aby uzyskać więcej informacji na temat Biblioteka równoległych wzorców, zobacz [równoległych biblioteki wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md).  
  
### <a name="asynchronous-agents-library"></a>Biblioteki agentów asynchronicznych  
 Biblioteki agentów asynchronicznych (lub po prostu *biblioteki agentów*) zapewnia model programowania na podstawie aktora i komunikat przekazywanie interfejsy coarse-grained przepływu danych i przetwarzanie potokowe zadania. Agenci asynchroniczni umożliwiają wykorzystują produktywności opóźnienia, wykonując pracę, zgodnie z innymi składnikami, poczekaj na danych.  
  
 Biblioteki agentów należy użyć, jeśli masz wiele jednostek, które komunikują się ze sobą asynchronicznie. Na przykład można utworzyć agenta, która odczytuje dane z pliku lub połączenie sieciowe, a następnie używa przekazywania interfejsy komunikatów do wysyłania danych do innego agenta.  
  
 Aby uzyskać więcej informacji na temat biblioteki agentów, zobacz [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md).  
  
### <a name="task-scheduler"></a>Harmonogram zadań  
 Harmonogram zadań harmonogramy i koordynuje zadań w czasie wykonywania. Harmonogram zadań jest współpracy i używa algorytmu kradzież pracy do osiągnięcia maksymalnego użycia przetwarzania zasobów.  
  
 Współbieżność środowiska wykonawczego zawiera harmonogram domyślny, dzięki czemu nie trzeba zarządzać szczegóły infrastruktury. Jednak aby spełnić wymagania jakości aplikacji, można też podać własne planowania zasad lub kojarzenia określonych transfery danych z określonych zadań.  
  
 Aby uzyskać więcej informacji na temat harmonogramu zadań, zobacz [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
### <a name="resource-manager"></a>Menedżer zasobów  
 Rola Menedżera zasobów jest aby zarządzać zasobów obliczeniowych, takich jak procesory i pamięć. Ich zmiana w czasie wykonywania przez przydzielanie zasobów, do których może być najbardziej skutecznych Resource Manager odpowiada obciążeń.  
  
 Menedżer zasobów służy jako abstrakcji za pośrednictwem zasobów obliczeniowych i głównie współdziała z harmonogramu zadań. Chociaż Menedżer zasobów umożliwia dostrojenie wydajności bibliotek i aplikacji, używane są zwykle funkcjonalności zapewnianej przez Biblioteka równoległych wzorców, biblioteka agentów i harmonogram zadań. Te biblioteki dynamicznie ponowne zrównoważenie zasobów zmienić obciążeń przy użyciu Menedżera zasobów.  
  
 [[Górnej](#top)]  
  
##  <a name="lambda"></a> Wyrażenia Lambda w języku C++  
 Wiele typów i algorytmy, które są zdefiniowane przez współbieżności środowiska wykonawczego są zaimplementowane jako szablonów języka C++. Wykonać niektóre z tych typów i algorytmy jako parametr procedury, która wykonuje pracę. Ten parametr może być funkcją lambda, obiekt funkcji lub wskaźnik funkcji. Te jednostki są również nazywane *funkcji pracy* lub *pracy procedury*.  
  
 Wyrażenia lambda są ważne nowej funkcji języka Visual C++, ponieważ udostępniają one zwięzły sposób definiowania funkcji pracy w celu równoległego przetwarzania. Obiekty funkcji i wskaźniki funkcji umożliwiają korzystanie ze współbieżności środowiska wykonawczego z istniejącego kodu. Jednak zaleca się użycie wyrażeń lambda, gdy pisanie nowego kodu ze względu na bezpieczeństwo i wydajność korzyści, które zapewniają.  
  
 Poniższy przykład porównuje Składnia funkcji lambda, obiekty funkcji i wskaźniki funkcji w wielu wywołań [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytmu. Każde wywołanie `parallel_for_each` używa do obliczenia wartości kwadratu każdego elementu w różnych technik [std::array](../../standard-library/array-class-stl.md) obiektu.  
  
 [!code-cpp[concrt-comparing-work-functions#1](../../parallel/concrt/codesnippet/cpp/overview-of-the-concurrency-runtime_1.cpp)]  
  
 **Output**  
  
```Output  
1  
256  
6561  
65536  
390625  
```  
  
 Aby uzyskać więcej informacji na temat funkcji lambda w języku C++, zobacz [wyrażenia Lambda](../../cpp/lambda-expressions-in-cpp.md).  
  
 [[Górnej](#top)]  
  
##  <a name="requirements"></a> Wymagania  
 W poniższej tabeli przedstawiono pliki nagłówkowe, które są skojarzone z każdego składnika współbieżności środowiska wykonawczego:  
  
|Składnik|Pliki nagłówkowe|  
|---------------|------------------|  
|Biblioteka równoległych wzorców (PLL)|ppl.h<br /><br /> concurrent_queue.h<br /><br /> concurrent_vector.h|  
|Biblioteki agentów asynchronicznych|Agents.h|  
|Harmonogram zadań|concrt.h|  
|Menedżer zasobów|concrtrm.h|  
  
 Współbieżność środowiska wykonawczego jest zadeklarowana w [współbieżności](../../parallel/concrt/reference/concurrency-namespace.md) przestrzeni nazw. (Można również użyć [współbieżności](../../parallel/concrt/reference/concurrency-namespace.md), która jest alias dla tego obszaru nazw.) `concurrency::details` Przestrzeń nazw obsługuje framework współbieżność środowiska wykonawczego i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
 Współbieżność środowiska wykonawczego jest dostarczane jako część C Runtime Library (CRT). Aby uzyskać więcej informacji na temat sposobu tworzenia aplikacji, która używa CRT, zobacz [Biblioteka CRT — funkcje](../../c-runtime-library/crt-library-features.md).  
  
 [[Górnej](#top)]



