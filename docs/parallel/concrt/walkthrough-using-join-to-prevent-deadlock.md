---
title: 'Przewodnik: Używanie, aby zapobiec zakleszczeniu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- preventing deadlock with joins [Concurrency Runtime]
- deadlock, preventing [Concurrency Runtime]
- non-greedy joins, example
- join class, example
ms.assetid: d791f697-bb93-463e-84bd-5df1651b7446
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45669b4838925ed671646ca1aad16a3fdbe6de77
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377282"
---
# <a name="walkthrough-using-join-to-prevent-deadlock"></a>Wskazówki: korzystanie ze złączy w celu zapobiegania zakleszczeniom

Ten temat używa problem ucztujących filozofów, aby zilustrować, jak używać [concurrency::join](../../parallel/concrt/reference/join-class.md) klasy w celu uniknięcia zakleszczenia w aplikacji. W przypadku aplikacji oprogramowania *zakleszczenia* występuje, gdy dwa lub więcej procesów każdego zasobu do przechowywania i wzajemnie poczekaj, aż inny proces zwolnić innego zasobu.

Problem ucztujących filozofów jest szczegółowy przykład ogólne zbiór problemów, które mogą wystąpić, gdy zestaw zasobów jest współużytkowana przez wiele procesów współbieżnych.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego instruktażu, przeczytaj następujące tematy:

- [Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)

- [Przewodnik: tworzenie aplikacji opartej o agentów](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)

- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)

- [Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)

##  <a name="top"></a> Sekcje

Ten przewodnik zawiera następujące sekcje:

- [Problem Ucztujących Filozofów](#problem)

- [Implementacja Naiwni](#deadlock)

- [Za pomocą, aby zapobiec zakleszczeniu](#solution)

##  <a name="problem"></a> Problem Ucztujących Filozofów

Problem ucztujących filozofów ilustruje, jak zakleszczenia odbywa się w aplikacji. W ten problem ucztujących pięć znajdują się w tabeli działanie. Każdy philosopher przełącza między myśl i pochłaniając. Każdy philosopher musi udostępnić chopstick sąsiada się po lewej stronie, a drugi chopstick z sąsiedniej po prawej stronie. Poniższa ilustracja przedstawia ten układ.

![Problem Ucztujących jadalni](../../parallel/concrt/media/dining_philosophersproblem.png "dining_philosophersproblem")

Do spożycia, philosopher musi zawierać dwa chopsticks. Jeśli każdy philosopher przechowuje tylko jedną chopstick i oczekuje na inną, następnie można jeść nie philosopher i nie pozbawi wszystkie.

[[Górnej](#top)]

##  <a name="deadlock"></a> Implementacja Naiwni

Poniższy przykład pokazuje implementację problem ucztujących filozofów naiwni. `philosopher` Klasy, która jest pochodną [concurrency::agent](../../parallel/concrt/reference/agent-class.md), umożliwia każdej philosopher działać niezależnie. W przykładzie użyto udostępnionej macierzy [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) obiekty do każdej `philosopher` wyłączny dostęp do pary chopsticks obiektu.

Do wykonania na ilustracji, powiązania `philosopher` klasa reprezentuje jeden philosopher. `int` Zmienna reprezentuje każdego chopstick. `critical_section` Obiekty służą jako właścicieli, na których chopsticks rest. `run` Metoda symuluje cyklu życia philosopher. `think` Metoda symuluje działanie myślenia i `eat` metoda symuluje pochłaniając czynność.

A `philosopher` obiektu blokuje zarówno `critical_section` obiektów, aby zasymulować usunięcie chopsticks od posiadaczy przed nią wywołuje `eat` metody. Po wywołaniu `eat`, `philosopher` zwraca chopsticks posiadaczom ustawiając `critical_section` obiektów z powrotem do stanu odblokowane.

`pickup_chopsticks` Metoda ilustruje, których może wystąpić zakleszczenia. Jeśli każdy `philosopher` obiekt uzyskuje dostęp do jednego z blokad, a następnie nie `philosopher` obiektu można kontynuować, ponieważ inne blokady jest kontrolowany przez inną `philosopher` obiektu.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

### <a name="code"></a>Kod

[!code-cpp[concrt-philosophers-deadlock#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_1.cpp)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `philosophers-deadlock.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc ucztujących deadlock.cpp**

[[Górnej](#top)]

##  <a name="solution"></a> Za pomocą, aby zapobiec zakleszczeniu

W tej sekcji pokazano, jak użyć buforów komunikatów oraz funkcje przekazywania komunikatów w celu wyeliminowania ryzyko zakleszczenia.

Powiązanie w tym przykładzie do przedstawionego wcześniej `philosopher` klasy zastępuje każdy `critical_section` obiektu za pomocą [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) obiektu i `join` obiektu. `join` Obiektu służy jako kryterium, które zapewniają chopsticks philosopher.

W tym przykładzie użyto `unbounded_buffer` klasy, ponieważ gdy obiekt docelowy otrzymuje komunikat z `unbounded_buffer` obiekt, komunikat zostanie usunięty z kolejki komunikatów. Dzięki temu `unbounded_buffer` obiekt, który przechowuje komunikat z informacją, że chopstick jest dostępny. `unbounded_buffer` Obiekt, który przechowuje żaden komunikat wskazuje, czy chopstick jest używany.

W tym przykładzie użyto niezachłanne `join` obiektu, ponieważ niezachłanne złączenia zapewnia każdego `philosopher` obiektu dostęp do obu chopsticks tylko wtedy, gdy oba `unbounded_buffer` obiekty zawierają wiadomość. Zachłanne złączenia nie uniemożliwiłyby zakleszczenia, ponieważ zachłanne złączenia akceptuje komunikaty, gdy tylko staną się dostępne. Zakleszczenie może wystąpić, jeśli jest to wszystko zachłanne `join` obiekty wyświetlony jeden z komunikatów, ale czekają na inne staną się dostępne.

Aby uzyskać więcej informacji na temat sprzężeń zachłanne i niezachłanne i różnice między różnymi typami buforu komunikatów, zobacz [bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md).

#### <a name="to-prevent-deadlock-in-this-example"></a>W celu uniknięcia zakleszczenia w tym przykładzie

1. Usuń następujący kod z przykładu.

[!code-cpp[concrt-philosophers-deadlock#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_2.cpp)]

1. Zmiana rodzaju `_left` i `_right` elementów członkowskich danych `philosopher` klasy `unbounded_buffer`.

[!code-cpp[concrt-philosophers-join#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_3.cpp)]

1. Modyfikowanie `philosopher` konstruktora, aby móc `unbounded_buffer` obiektów jako jego parametry.

[!code-cpp[concrt-philosophers-join#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_4.cpp)]

1. Modyfikowanie `pickup_chopsticks` metodę niezachłanne `join` obiekt, aby odbierać komunikaty z buforów komunikatów dla obu chopsticks.

[!code-cpp[concrt-philosophers-join#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_5.cpp)]

1. Modyfikowanie `putdown_chopsticks` metodę, aby zwolnić dostęp do chopsticks, wysyłając wiadomość do buforów komunikatów dla obu chopsticks.

[!code-cpp[concrt-philosophers-join#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_6.cpp)]

1. Modyfikowanie `run` metodę do przechowywania wyników `pickup_chopsticks` metody oraz przekazywanie tych wyników, aby `putdown_chopsticks` metody.

[!code-cpp[concrt-philosophers-join#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_7.cpp)]

1. Zmodyfikuj deklarację zmiennej `chopsticks` zmienną `wmain` funkcję, aby był tablicą o `unbounded_buffer` obiekty, przytrzymując każdy jeden komunikat.

[!code-cpp[concrt-philosophers-join#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_8.cpp)]

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniżej pokazano przykład ukończone, który używa niezachłanne `join` obiektów, aby wyeliminować ryzyko zakleszczenia.

### <a name="code"></a>Kod

[!code-cpp[concrt-philosophers-join#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_9.cpp)]

### <a name="comments"></a>Komentarze

Ten przykład generuje następujące dane wyjściowe.

```Output
aristotle ate 50 times.
descartes ate 50 times.
hobbes ate 50 times.
socrates ate 50 times.
plato ate 50 times.
```

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `philosophers-join.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc ucztujących join.cpp**

[[Górnej](#top)]

## <a name="see-also"></a>Zobacz też

[Środowisko uruchomieniowe współbieżności — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)<br/>
[Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)
