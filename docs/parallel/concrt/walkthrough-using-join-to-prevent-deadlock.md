---
title: 'Wskazówki: korzystanie ze złączy w celu zapobiegania zakleszczeniom'
ms.date: 04/25/2019
helpviewer_keywords:
- preventing deadlock with joins [Concurrency Runtime]
- deadlock, preventing [Concurrency Runtime]
- non-greedy joins, example
- join class, example
ms.assetid: d791f697-bb93-463e-84bd-5df1651b7446
ms.openlocfilehash: 4df83e944552fd6c0d2482efa72883d87cd45f8c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140654"
---
# <a name="walkthrough-using-join-to-prevent-deadlock"></a>Wskazówki: korzystanie ze złączy w celu zapobiegania zakleszczeniom

W tym temacie jest używany problem rekomendowanych lokali ucztujących, który ilustruje sposób używania klasy [concurrency:: join](../../parallel/concrt/reference/join-class.md) w celu zapobiegania zakleszczeniom w aplikacji. W aplikacji oprogramowania *zakleszczenie* występuje, gdy co najmniej dwa procesy przechowują zasób i wzajemnie czekają na inny proces zwolnienia innego zasobu.

Problem z rekomendowanych lokali ucztujących to konkretny przykład ogólnego zestawu problemów, które mogą wystąpić, gdy zestaw zasobów jest współużytkowany przez wiele współbieżnych procesów.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego instruktażu zapoznaj się z następującymi tematami:

- [Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)

- [Przewodnik: tworzenie aplikacji opartej o agentów](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)

- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)

- [Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)

## <a name="top"></a>Poszczególne

Ten Instruktaż zawiera następujące sekcje:

- [Problem z rekomendowanych lokali ucztujących](#problem)

- [Implementacja algorytmie](#deadlock)

- [Używanie sprzężenia w celu zapobiegania zakleszczeniom](#solution)

## <a name="problem"></a>Problem z rekomendowanych lokali ucztujących

Problem z rekomendowanych lokali ucztujących ilustruje, jak zakleszczenie występuje w aplikacji. W tym problemie pięć ucztujących znajduje się w postaci okrągłej tabeli. Każdy Philosopher alternatywy między myśliją i jedzenia. Każdy Philosopher musi udostępnić Chopstick z sąsiadem po lewej stronie, a inne Chopstick z sąsiadem z prawej strony. Na poniższej ilustracji przedstawiono ten układ.

![Problem z rekomendowanych lokali ucztujących](../../parallel/concrt/media/dining_philosophersproblem.png "Problem ucztujących filozofów")

Do Eat, Philosopher musi przechowywać dwie Chopsticks. Jeśli każdy Philosopher ma tylko jeden Chopstick i oczekuje na inny, a następnie Philosopher nie może być Eat i wszystkie zablokować dostęp.

[[Top](#top)]

## <a name="deadlock"></a>Implementacja algorytmie

W poniższym przykładzie przedstawiono implementację algorytmie problemu ucztujących rekomendowanych lokali. Klasa `philosopher`, która wynika z [współbieżności:: Agent](../../parallel/concrt/reference/agent-class.md), umożliwia każdemu Philosopher działania niezależnie. W przykładzie zastosowano współdzieloną tablicę obiektów [concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) , aby nadać każdemu obiektowi `philosopher`emu wyłączny dostęp do pary Chopsticks.

Aby powiązać implementację z ilustracją, Klasa `philosopher` reprezentuje jeden Philosopher. Zmienna `int` reprezentuje każdy Chopstick. Obiekty `critical_section` stanowią posiadaczy Chopsticks. Metoda `run` symuluje życie Philosopher. Metoda `think` symuluje czynność działania, a metoda `eat` symuluje działanie jedzenia.

Obiekt `philosopher` blokuje obydwie `critical_section` obiekty w celu symulowania usuwania Chopsticks z posiadaczy przed wywołaniem metody `eat`. Po wywołaniu `eat`obiekt `philosopher` zwróci Chopsticks do posiadaczy przez ustawienie obiektów `critical_section` z powrotem do stanu odblokowany.

Metoda `pickup_chopsticks` ilustruje, gdzie może wystąpić zakleszczenie. Jeśli każdy `philosopher` obiektu uzyska dostęp do jednego z blokad, nie będzie można kontynuować `philosopher` obiektu, ponieważ inne blokady są kontrolowane przez inny obiekt `philosopher`.

### <a name="example"></a>Przykład

[!code-cpp[concrt-philosophers-deadlock#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_1.cpp)]

### <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `philosophers-deadlock.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **CL. exe/EHsc Philosophers-Deadlock. cpp**

[[Top](#top)]

## <a name="solution"></a>Używanie sprzężenia w celu zapobiegania zakleszczeniom

W tej sekcji pokazano, jak używać buforów komunikatów i funkcji przekazywania komunikatów, aby wyeliminować prawdopodobieństwo zakleszczenia.

Aby powiązać ten przykład do wcześniejszego, Klasa `philosopher` zastępuje każdy obiekt `critical_section` przy użyciu obiektu [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) i obiektu `join`. Obiekt `join` służy jako arbiter, który dostarcza Chopsticks do Philosopher.

Ten przykład używa klasy `unbounded_buffer`, ponieważ gdy obiekt docelowy otrzymuje komunikat z obiektu `unbounded_buffer`, komunikat zostanie usunięty z kolejki komunikatów. Dzięki temu obiekt `unbounded_buffer`, który przechowuje komunikat wskazujący, że Chopstick jest dostępny. Obiekt `unbounded_buffer`, który nie zawiera żadnego komunikatu wskazuje, że jest używany Chopstick.

W tym przykładzie używa obiektu niezachłanne `join`, ponieważ sprzężenie inne niż zachłanne powoduje, że każdy obiekt `philosopher` ma dostęp do obu Chopsticks tylko wtedy, gdy oba obiekty `unbounded_buffer` zawierają komunikat. Zachłanne Join nie zapobiega zakleszczeniu, ponieważ sprzężenie zachłanne akceptuje komunikaty zaraz po ich udostępnieniu. Zakleszczenie może wystąpić, jeśli wszystkie obiekty zachłanne `join` będą odbierać jeden z komunikatów, ale czekają na to, aby pozostałe elementy były dostępne.

Aby uzyskać więcej informacji na temat sprzężeń zachłanne i innych niż zachłanne, a różnice między różnymi typami buforów komunikatów, zobacz [asynchroniczne bloki komunikatów](../../parallel/concrt/asynchronous-message-blocks.md).

### <a name="to-prevent-deadlock-in-this-example"></a>W celu uniknięcia zakleszczenia w tym przykładzie

1. Usuń Poniższy kod z przykładu.

[!code-cpp[concrt-philosophers-deadlock#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_2.cpp)]

1. Zmień typ `_left` i `_right` członków danych klasy `philosopher` na `unbounded_buffer`.

[!code-cpp[concrt-philosophers-join#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_3.cpp)]

1. Zmodyfikuj konstruktora `philosopher`, aby `unbounded_buffer` obiekty jako parametry.

[!code-cpp[concrt-philosophers-join#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_4.cpp)]

1. Zmodyfikuj metodę `pickup_chopsticks`, aby użyć obiektu niezachłanne `join` do odbierania komunikatów z buforów komunikatów dla obu Chopsticks.

[!code-cpp[concrt-philosophers-join#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_5.cpp)]

1. Zmodyfikuj metodę `putdown_chopsticks`, aby zwolnić dostęp do Chopsticks, wysyłając komunikat do buforów komunikatów dla obu Chopsticks.

[!code-cpp[concrt-philosophers-join#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_6.cpp)]

1. Zmodyfikuj metodę `run`, aby przechowywać wyniki metody `pickup_chopsticks` i przekazać te wyniki do metody `putdown_chopsticks`.

[!code-cpp[concrt-philosophers-join#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_7.cpp)]

1. Zmodyfikuj deklarację zmiennej `chopsticks` w funkcji `wmain`, aby była tablicą `unbounded_buffer` obiektów, które zawierają jeden komunikat.

[!code-cpp[concrt-philosophers-join#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_8.cpp)]

### <a name="description"></a>Opis

Poniżej przedstawiono zakończono przykład, który używa obiektów zachłanne `join`, aby wyeliminować ryzyko zakleszczenia.

### <a name="example"></a>Przykład

[!code-cpp[concrt-philosophers-join#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_9.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
aristotle ate 50 times.
descartes ate 50 times.
hobbes ate 50 times.
socrates ate 50 times.
plato ate 50 times.
```

### <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `philosophers-join.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **CL. exe/EHsc Philosophers-Join. cpp**

[[Top](#top)]

## <a name="see-also"></a>Zobacz też

[Środowisko uruchomieniowe współbieżności — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)<br/>
[Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)
