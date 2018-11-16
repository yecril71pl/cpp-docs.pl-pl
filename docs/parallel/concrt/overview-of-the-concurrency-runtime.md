---
title: Omówienie współbieżności środowiska wykonawczego
ms.date: 07/20/2018
helpviewer_keywords:
- Concurrency Runtime, requirements
- Concurrency Runtime, architecture
- Concurrency Runtime, overview
- Concurrency Runtime, lambda expressions
ms.assetid: 56237d96-10b0-494a-9cb4-f5c5090436c5
ms.openlocfilehash: dab4860bcc69780fa6a6390e2ef111216642637a
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693660"
---
# <a name="overview-of-the-concurrency-runtime"></a>Omówienie współbieżności środowiska wykonawczego

Ten dokument zawiera omówienie współbieżności środowiska wykonawczego. Opisuje korzyści ze współbieżności środowiska wykonawczego, kiedy go używać, i sposobu jego składniki interakcji ze sobą oraz z systemu operacyjnego i aplikacji.

##  <a name="top"></a> Sekcje

Ten dokument zawiera następujące sekcje:

- [Historia wdrożenia środowiska uruchomieniowego współbieżności](#dlls)

- [Dlaczego współbieżność środowiska wykonawczego jest ważna](#runtime)

- [Architektura](#architecture)

- [Wyrażenie C++ Lambda](#lambda)

- [Wymagania](#requirements)

## <a name="dlls"></a> Historia wdrożenia środowiska uruchomieniowego współbieżności

W Visual Studio 2010, 2013 r środowisko uruchomieniowe współbieżności została włączona w pliku msvcr100.dll za pośrednictwem msvcr120.dll.  Refaktoryzacja UCRT wystąpienia w programie Visual Studio 2015, że biblioteki DLL został zrefaktoryzowany do trzech części:

- ucrtbase.dll — interfejs API języka C, dostarczana z systemem Windows 10 i obsługiwanych niskiego poziomu aktualizacji — za pośrednictwem Windows

- biblioteki vcruntime140.dll — kompilator obsługuje funkcje i środowisko uruchomieniowe EH, dostarczane za pośrednictwem programu Visual Studio

- concrt140.dll — w środowisku uruchomieniowym współbieżności: dostarczane za pośrednictwem programu Visual Studio. Wymagane dla równoległe kontenery oraz algorytmów, takich jak `concurrency::parallel_for`. Ponadto STL wymaga w podstawowych synchronizacji zasilania, tę bibliotekę DLL w systemie Windows XP, ponieważ Windows XP nie ma zmiennych warunków.

W programie Visual Studio 2015 i nowszych harmonogram zadań środowisko uruchomieniowe współbieżności nie jest już harmonogram dla zadania klasy i powiązanych typów ppltasks.h. Te typy teraz używać Windows ThreadPool gwarantujące wysoką wydajność i współdziałanie z podstawowych synchronizacji Windows.

##  <a name="runtime"></a> Dlaczego współbieżność środowiska wykonawczego jest ważna

Współbieżność środowiska wykonawczego zapewnia zgodność i stabilności na aplikacje i składniki aplikacji, które są uruchamiane jednocześnie. Są dwa przykłady korzyści zapewnianych przez środowisko uruchomieniowe współbieżności *planowania zadań w zakresie współpracy* i *blokowanie współpracy*.

Środowisko uruchomieniowe współbieżności używa harmonogramu zadań współpracy, który implementuje określony algorytm kradzież pracy umożliwiająca efektywną dystrybucję pracy między zasobami obliczeniowymi. Na przykład rozważmy aplikację, która ma dwa wątki, które są jednocześnie zarządzane przez tego samego środowiska uruchomieniowego. Jeśli jeden wątek kończy jego zaplanowanego zadania, jego odciążania pracy z innego wątku. Ten mechanizm równoważy całkowitego obciążenia aplikacji.

Środowisko uruchomieniowe współbieżności także podstawowych synchronizacji, które używają blokowanie współpracy do synchronizowania dostępu do zasobów. Rozważmy na przykład zadanie, które musi mieć wyłącznego dostępu do zasobu udostępnionego. Blokując wspólne, środowisko uruchomieniowe umożliwia pozostałe quantum wykonać inne zadanie, ponieważ pierwsze zadanie czeka na zasób. Ten mechanizm promuje maksymalne użycie zasobów obliczeniowych.

[[Górnej](#top)]

##  <a name="architecture"></a> Architektura

Współbieżność środowiska wykonawczego jest dzielony na cztery składniki: Biblioteka równoległych wzorców (PPL), bibliotekę asynchronicznych agentów, harmonogram zadań i Menedżera zasobów. Te składniki znajdują się między systemem operacyjnym i aplikacjami. Na poniższej ilustracji przedstawiono sposób interakcji składników środowiska uruchomieniowego współbieżności między systemem operacyjnym i aplikacjami:

**Architektura środowiska uruchomieniowego współbieżności**

![Architektura środowiska uruchomieniowego współbieżności](../../parallel/concrt/media/concurrencyrun.png "concurrencyrun")

> [!IMPORTANT]
>  Składniki harmonogramu zadań i Menedżera zasobów nie są dostępne z poziomu aplikacji uniwersalnych platformy Windows (UWP) podczas korzystania z funkcji klasy zadania lub inne typy w ppltasks.h.

Współbieżność środowiska wykonawczego jest wysoce *konfigurowalna*, oznacza to, że można połączyć istniejące funkcje, aby robić więcej. Środowisko uruchomieniowe współbieżności komponuje się wiele funkcji, takich jak algorytmów równoległych, z składniki niższego poziomu.

Środowisko uruchomieniowe współbieżności także podstawowych synchronizacji, które używają blokowanie współpracy do synchronizowania dostępu do zasobów. Aby uzyskać więcej informacji na temat tych wartości pierwotnych synchronizacji, zobacz [struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md).

Poniższe sekcje zawierają krótki przegląd zawiera poszczególne składniki i kiedy go używać.

### <a name="parallel-patterns-library"></a>Biblioteka równoległych wzorców

Biblioteka równoległych wzorców (PPL) zapewnia kontenery ogólnego przeznaczenia i algorytmy umożliwiające wykonywanie równoległość drobnoziarnistą. Włącza PPL *równoległości danych imperatywne* , zapewniając równoległe algorytmy, które rozpowszechniają obliczeń na kolekcje lub zestawy danych i zasobów obliczeniowych. Umożliwia ona także *równoległość zadań* , zapewniając obiektów zadań, które rozpowszechniają wielu niezależnych operacji zasobów obliczeniowych.

Biblioteka równoległych wzorców należy użyć w przypadku lokalnie udostępniać funkcje obliczeń, który może być korzystne przetwarzania równoległego. Na przykład, można użyć [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytmu, aby przekształcić istniejącą `for` pętli, która będzie działać równolegle.

Aby uzyskać więcej informacji na temat biblioteki wzorców równoległych, zobacz [biblioteki wzorców równoległych (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md).

### <a name="asynchronous-agents-library"></a>Biblioteki agentów asynchronicznych

Bibliotekę asynchronicznych agentów (lub po prostu *biblioteki agentów*) zapewnia model programowania oparty na aktora i komunikat, przekazując interfejsów gruboziarnistych przepływu danych i przetwarzanie potokowe zadania. Agenci asynchroniczni umożliwiają wykonywanie wydajne korzystanie z opóźnieniem, wykonując pracę, zgodnie z innymi składnikami czekać na dane.

Biblioteka agentów należy użyć, jeśli masz wiele jednostek, które komunikują się ze sobą asynchronicznie. Na przykład można utworzyć agenta, który odczytuje dane z pliku lub połączenie sieciowe, a następnie używa przekazywania interfejsów komunikatów do wysyłania danych do innego agenta.

Aby uzyskać więcej informacji na temat biblioteki agentów, zobacz [bibliotekę asynchronicznych agentów](../../parallel/concrt/asynchronous-agents-library.md).

### <a name="task-scheduler"></a>Harmonogram zadań

Harmonogram zadań planuje i koordynuje zadania w czasie wykonywania. Harmonogram zadań jest wspólne i używa algorytmu kradzież pracy do osiągnięcia maksymalnego użycia przetwarzania zasobów.

Środowisko uruchomieniowe współbieżności zawiera domyślnego harmonogramu, tak, aby nie trzeba zarządzać szczegóły infrastruktury. Jednak aby zaspokoić potrzeby jakości aplikacji, możesz także podać własne planowania zasad lub skojarz określonych harmonogramów z określonych zadań.

Aby uzyskać więcej informacji na temat harmonogramu zadań, zobacz [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

### <a name="resource-manager"></a>Menedżer zasobów

Rola Menedżera zasobów jest zarządzać zasobów obliczeniowych, takich jak procesory i pamięć. Menedżera zasobów odpowiada obciążeń w miarę jak ulegają zmianom w czasie wykonywania przez przydzielanie zasobów do której może być najbardziej efektywne.

Menedżer zasobów służy jako abstrakcję za pośrednictwem zasobów obliczeniowych i przede wszystkim współdziała z harmonogramu zadań. Chociaż usługi Resource Manager można używać w celu dostrajania wydajności aplikacji i bibliotek, używa się zazwyczaj funkcje, które są dostarczane przez biblioteki wzorców równoległych, biblioteka agentów i harmonogramu zadań. Te biblioteki umożliwia dynamicznie ponowne zrównoważenie zasobów zmiany obciążenia usługi Resource Manager.

[[Górnej](#top)]

##  <a name="lambda"></a> Wyrażenie C++ Lambda

Wiele typów i algorytmy, które są zdefiniowane w czasie wykonywania współbieżności są implementowane jako szablonów języka C++. Wykonać niektóre z tych typów i algorytmy jako parametr procedury, który wykonuje pracę. Ten parametr może być funkcją lambda, obiekt funkcji lub wskaźnik funkcji. Te jednostki są również nazywane *funkcji pracy* lub *pracy procedury*.

Wyrażenia lambda są ważne nowej funkcji języka Visual C++, ponieważ zapewniają one zwięzły sposób definiowania funkcji pracy do przetwarzania równoległego. Obiektów funkcyjnych i funkcji wskaźniki umożliwiają korzystanie ze środowiska uruchomieniowego współbieżności przy użyciu istniejącego kodu. Jednak firma Microsoft zaleca użycie wyrażeń lambda, kiedy piszesz nowy kod ze względu na bezpieczeństwo i wydajność korzyści, które zapewniają.

W poniższym przykładzie porównano Składnia funkcji lambda, obiektów funkcyjnych i wskaźników funkcji w wielu wywołaniach do [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytmu. Każde wywołanie `parallel_for_each` wykorzystuje różne techniki do obliczenia kwadrat każdego elementu w [std::array](../../standard-library/array-class-stl.md) obiektu.

[!code-cpp[concrt-comparing-work-functions#1](../../parallel/concrt/codesnippet/cpp/overview-of-the-concurrency-runtime_1.cpp)]

**Output**

```Output
1
256
6561
65536
390625
```

Aby uzyskać więcej informacji na temat funkcji lambda w języku C++, zobacz [wyrażeń Lambda](../../cpp/lambda-expressions-in-cpp.md).

[[Górnej](#top)]

##  <a name="requirements"></a> Wymagania

W poniższej tabeli przedstawiono pliki nagłówkowe, które są skojarzone z każdego składnika środowiska uruchomieniowego współbieżności:

|Składnik|Pliki nagłówkowe|
|---------------|------------------|
|Biblioteka równoległych wzorców (PLL)|ppl.h<br /><br /> concurrent_queue.h<br /><br /> concurrent_vector.h|
|Biblioteki agentów asynchronicznych|Agents.h|
|Harmonogram zadań|concrt.h|
|Menedżer zasobów|concrtrm.h|

Współbieżność środowiska wykonawczego jest zadeklarowana w [współbieżności](../../parallel/concrt/reference/concurrency-namespace.md) przestrzeni nazw. (Możesz również użyć [współbieżności](../../parallel/concrt/reference/concurrency-namespace.md), która jest aliasem dla tej przestrzeni nazw.) `concurrency::details` Przestrzeń nazw obsługuje współbieżność środowiska wykonawczego framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.

Współbieżność środowiska wykonawczego jest dostarczany jako część z biblioteki środowiska uruchomieniowego C (CRT). Aby uzyskać więcej informacji na temat tworzenia aplikacji, która używa CRT, zobacz [funkcje biblioteki CRT](../../c-runtime-library/crt-library-features.md).

[[Górnej](#top)]

