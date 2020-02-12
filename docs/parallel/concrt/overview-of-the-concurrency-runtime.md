---
title: Omówienie współbieżności środowiska wykonawczego
ms.date: 11/19/2018
helpviewer_keywords:
- Concurrency Runtime, requirements
- Concurrency Runtime, architecture
- Concurrency Runtime, overview
- Concurrency Runtime, lambda expressions
ms.assetid: 56237d96-10b0-494a-9cb4-f5c5090436c5
ms.openlocfilehash: b50c943bb83c587ab4001556b1143f9d5f868a0b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142930"
---
# <a name="overview-of-the-concurrency-runtime"></a>Omówienie współbieżności środowiska wykonawczego

Ten dokument zawiera omówienie środowisko uruchomieniowe współbieżności. W tym artykule opisano zalety środowisko uruchomieniowe współbieżności, kiedy należy z niego korzystać i jak jego składniki współdziałają ze sobą oraz z systemem operacyjnym i aplikacjami.

## <a name="top"></a>Poszczególne

Ten dokument zawiera następujące sekcje:

- [Historia implementacji środowisko uruchomieniowe współbieżności](#dlls)

- [Dlaczego środowisko uruchomieniowe współbieżności jest ważne](#runtime)

- [Architektura](#architecture)

- [C++Wyrażenia lambda](#lambda)

- [Wymagania](#requirements)

## <a name="dlls"></a>Historia implementacji środowisko uruchomieniowe współbieżności

W programie Visual Studio 2010 do 2013 środowisko uruchomieniowe współbieżności został zawarty w pliku msvcr100. dll za pomocą msvcr120. dll.  Gdy w programie Visual Studio 2015 wystąpi Refaktoryzacja UCRT, Ta biblioteka DLL została Refaktoryzacja do trzech części:

- ucrtbase. dll — interfejs API języka C, dostarczany w systemie Windows 10 i usługi niskiego poziomu za pośrednictwem Windows Update-

- vcruntime140. dll — funkcje obsługi kompilatora i środowisko uruchomieniowe EH, dostarczane za pośrednictwem programu Visual Studio

- concrt140. dll — środowisko uruchomieniowe współbieżności dostarczone za pośrednictwem programu Visual Studio. Wymagane dla kontenerów równoległych i algorytmów, takich jak `concurrency::parallel_for`. Ponadto STL wymaga tej biblioteki DLL w systemie Windows XP do elementów pierwotnych synchronizacji, ponieważ system Windows XP nie ma zmiennych warunkowych.

W programie Visual Studio 2015 i nowszych Harmonogram zadań środowisko uruchomieniowe współbieżności nie jest już harmonogramem dla klasy zadania i powiązanych typów w ppltasks. h. Te typy używają teraz puli wątków systemu Windows w celu zapewnienia lepszej wydajności i współdziałania z podstawowymi synchronizacjami systemu Windows.

## <a name="runtime"></a>Dlaczego środowisko uruchomieniowe współbieżności jest ważne

Środowisko uruchomieniowe dla współbieżności zapewnia jednorodność i przewidywalność aplikacji i składników aplikacji, które działają jednocześnie. Dwa przykłady korzyści płynących z środowisko uruchomieniowe współbieżności to *wspólne planowanie zadań* i wzajemne *blokowanie*.

Środowisko uruchomieniowe współbieżności używa wspólnego harmonogramu zadań, który implementuje algorytm kradzieży pracy, aby efektywnie dystrybuować pracę między zasobami obliczeniowymi. Rozważmy na przykład aplikację, która ma dwa wątki, które są zarządzane przez to samo środowisko uruchomieniowe. Jeśli jeden wątek zakończy zaplanowane zadanie, może odciążać pracę od innego wątku. Ten mechanizm równoważy ogólne obciążenie aplikacji.

Środowisko uruchomieniowe współbieżności udostępnia również elementy podstawowe synchronizacji, które używają bloku blokowego do synchronizowania dostępu do zasobów. Rozważmy na przykład zadanie, które musi mieć wyłączny dostęp do zasobu udostępnionego. Dzięki zablokowaniu wspólnie środowisko uruchomieniowe może użyć pozostałej Quantum do wykonania kolejnego zadania, gdy pierwsze zadanie czeka na zasób. Ten mechanizm podwyższa maksymalne wykorzystanie zasobów obliczeniowych.

[[Top](#top)]

## <a name="architecture"></a>Będąc

Środowisko uruchomieniowe współbieżności jest podzielony na cztery składniki: Biblioteka równoległych wzorców (PPL), Biblioteka agentów asynchronicznych, Harmonogram zadań i Menedżer zasobów. Te składniki znajdują się między systemem operacyjnym a aplikacjami. Na poniższej ilustracji przedstawiono, jak składniki środowisko uruchomieniowe współbieżności współdziałają między systemem operacyjnym a aplikacjami:

**Architektura środowisko uruchomieniowe współbieżności**

![Architektura środowisko uruchomieniowe współbieżności](../../parallel/concrt/media/concurrencyrun.png "Architektura środowisko uruchomieniowe współbieżności")

> [!IMPORTANT]
> Składniki Harmonogram zadań i Menedżer zasobów nie są dostępne z poziomu aplikacji platforma uniwersalna systemu Windows (platformy UWP) lub w przypadku używania klasy Task lub innych typów w ppltasks. h.

Środowisko uruchomieniowe współbieżności jest wysoce do *redagowania*, czyli można połączyć istniejące funkcje, aby wykonać więcej czynności. Środowisko uruchomieniowe współbieżności składa wiele funkcji, takich jak algorytmy równoległe, od składników niższego poziomu.

Środowisko uruchomieniowe współbieżności udostępnia również elementy podstawowe synchronizacji, które używają bloku blokowego do synchronizowania dostępu do zasobów. Aby uzyskać więcej informacji na temat tych elementów pierwotnych synchronizacji, zobacz [struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md).

Poniższe sekcje zawierają krótkie omówienie elementów dostarczanych przez poszczególne składniki i kiedy ich używać.

### <a name="parallel-patterns-library"></a>Biblioteka równoległych wzorców

Biblioteka równoległych wzorców (PPL) zawiera kontenery ogólnego przeznaczenia i algorytmy umożliwiające wykonywanie współbieżności. PPL umożliwia bezwzględne *równoległość danych* przez dostarczanie algorytmów równoległych, które dystrybuują obliczenia dla kolekcji lub zestawów danych w ramach zasobów obliczeniowych. Umożliwia również *równoległość zadań* , dostarczając obiekty zadań, które dystrybuują wiele niezależnych operacji w ramach zasobów obliczeniowych.

Biblioteka wzorców równoległych jest używana w przypadku lokalnego obliczenia, które może korzystać z wykonywania równoległego. Można na przykład użyć algorytmu [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) , aby przekształcić istniejącą pętlę `for` w celu równoległego działania.

Aby uzyskać więcej informacji na temat biblioteki równoległych wzorców, zobacz [Biblioteka wzorców równoległych (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md).

### <a name="asynchronous-agents-library"></a>Biblioteki agentów asynchronicznych

Biblioteka agentów asynchronicznych (lub tylko *Biblioteka agentów*) udostępnia model programowania oparty na aktorze i umożliwia przekazywanie interfejsów w celu uzyskania szczegółowych zadań przepływu danych i potokowych. Agenci asynchroniczni umożliwiają wydajne korzystanie z opóźnienia przez wykonywanie pracy, ponieważ inne składniki oczekują na dane.

Biblioteka agentów jest używana, gdy istnieje wiele jednostek, które komunikują się ze sobą asynchronicznie. Na przykład można utworzyć agenta, który odczytuje dane z pliku lub połączenia sieciowego, a następnie używa interfejsów przekazywania komunikatów do wysyłania tych danych do innego agenta.

Aby uzyskać więcej informacji na temat biblioteki Agents, zobacz [Biblioteka agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md).

### <a name="task-scheduler"></a>Harmonogram zadań

Harmonogram zadań planuje i koordynuje zadania w czasie wykonywania. Harmonogram zadań jest wspólna i używa algorytmu kradzieży pracy w celu osiągnięcia maksymalnego użycia zasobów przetwarzania.

Środowisko uruchomieniowe współbieżności udostępnia domyślny harmonogram, dzięki czemu nie trzeba zarządzać szczegółami infrastruktury. Aby jednak spełnić wymagania dotyczące jakości aplikacji, możesz również podać własne zasady planowania lub skojarzyć określone harmonogramy z określonymi zadaniami.

Aby uzyskać więcej informacji na temat Harmonogram zadań, zobacz [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

### <a name="resource-manager"></a>Resource Manager

Rolą Menedżer zasobów jest zarządzanie zasobami obliczeniowymi, takimi jak procesory i pamięć. Menedżer zasobów reaguje na obciążenia, gdy zmieniają się w czasie wykonywania przez przypisanie zasobów do miejsca, w którym mogą być najbardziej efektywne.

Menedżer zasobów służy jako Abstrakcja zasobów obliczeniowych i przede wszystkim współdziała z Harmonogram zadań. Mimo że można użyć Menedżer zasobów, aby dostosować wydajność bibliotek i aplikacji, zazwyczaj używasz funkcji udostępnianych przez bibliotekę wzorców równoległych, bibliotekę agentów i Harmonogram zadań. Te biblioteki używają Menedżer zasobów do dynamicznego zrównoważenia zasobów w miarę zmiany obciążeń.

[[Top](#top)]

## <a name="lambda"></a>C++ Wyrażenia lambda

Wiele typów i algorytmów, które są zdefiniowane przez środowisko uruchomieniowe współbieżności są implementowane jako C++ szablony. Niektóre z tych typów i algorytmów przyjmują jako parametry procedurę wykonującą prace. Ten parametr może być funkcją lambda, obiektem funkcji lub wskaźnikiem funkcji. Te jednostki są również nazywane *funkcjami roboczymi* lub *procedurami roboczymi*.

Wyrażenia lambda są ważną nową funkcją języka C++ wizualnego, ponieważ zapewniają zwięzły sposób definiowania funkcji roboczych do przetwarzania równoległego. Obiekty funkcji i wskaźniki funkcji umożliwiają używanie środowisko uruchomieniowe współbieżności z istniejącym kodem. Zaleca się jednak używanie wyrażeń lambda podczas pisania nowego kodu ze względu na bezpieczeństwo i korzyści płynące z zapewnienia bezpieczeństwa.

Poniższy przykład porównuje składnię funkcji lambda, obiektów funkcyjnych i wskaźników funkcji w wielu wywołaniach do algorytmu [concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) . Każde wywołanie `parallel_for_each` używa innej techniki do obliczenia kwadratu każdego elementu w obiekcie [std:: Array](../../standard-library/array-class-stl.md) .

[!code-cpp[concrt-comparing-work-functions#1](../../parallel/concrt/codesnippet/cpp/overview-of-the-concurrency-runtime_1.cpp)]

**Dane wyjściowe**

```Output
1
256
6561
65536
390625
```

Aby uzyskać więcej informacji na temat funkcji C++lambda w, zobacz [lambda Expressions](../../cpp/lambda-expressions-in-cpp.md).

[[Top](#top)]

## <a name="requirements"></a>Wymagania

W poniższej tabeli przedstawiono pliki nagłówka, które są skojarzone z poszczególnymi składnikami środowisko uruchomieniowe współbieżności:

|Składnik|Pliki nagłówkowe|
|---------------|------------------|
|Biblioteka równoległych wzorców (PLL)|ppl.h<br /><br /> concurrent_queue.h<br /><br /> concurrent_vector.h|
|Biblioteki agentów asynchronicznych|Agenci. h|
|Harmonogram zadań|concrt.h|
|Resource Manager|concrtrm.h|

Środowisko uruchomieniowe współbieżności jest zadeklarowana w przestrzeni nazw [współbieżności](../../parallel/concrt/reference/concurrency-namespace.md) . (Można również użyć [współbieżności](../../parallel/concrt/reference/concurrency-namespace.md), który jest aliasem dla tej przestrzeni nazw). Przestrzeń nazw `concurrency::details` obsługuje strukturę środowisko uruchomieniowe współbieżności i nie jest przeznaczona do użycia bezpośrednio w kodzie.

Środowisko uruchomieniowe współbieżności jest udostępniana jako część biblioteki środowiska uruchomieniowego języka C (CRT). Aby uzyskać więcej informacji na temat sposobu tworzenia aplikacji korzystającej z CRT, zobacz [funkcje biblioteki CRT](../../c-runtime-library/crt-library-features.md).

[[Top](#top)]
