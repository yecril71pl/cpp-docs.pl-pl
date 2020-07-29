---
title: 'Wskazówki: korzystanie ze złączy w celu zapobiegania zakleszczeniom'
ms.date: 04/25/2019
helpviewer_keywords:
- preventing deadlock with joins [Concurrency Runtime]
- deadlock, preventing [Concurrency Runtime]
- non-greedy joins, example
- join class, example
ms.assetid: d791f697-bb93-463e-84bd-5df1651b7446
ms.openlocfilehash: 5bdd6cd81051d224714dd66d4604cbdec4ddb552
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217886"
---
# <a name="walkthrough-using-join-to-prevent-deadlock"></a>Wskazówki: korzystanie ze złączy w celu zapobiegania zakleszczeniom

W tym temacie jest używany problem rekomendowanych lokali ucztujących, który ilustruje sposób używania klasy [concurrency:: join](../../parallel/concrt/reference/join-class.md) w celu zapobiegania zakleszczeniom w aplikacji. W aplikacji oprogramowania *zakleszczenie* występuje, gdy co najmniej dwa procesy przechowują zasób i wzajemnie czekają na inny proces zwolnienia innego zasobu.

Problem z rekomendowanych lokali ucztujących to konkretny przykład ogólnego zestawu problemów, które mogą wystąpić, gdy zestaw zasobów jest współużytkowany przez wiele współbieżnych procesów.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego instruktażu zapoznaj się z następującymi tematami:

- [Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)

- [Przewodnik: Tworzenie aplikacji opartej na agencie](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)

- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)

- [Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)

## <a name="sections"></a><a name="top"></a>Poszczególne

Ten Instruktaż zawiera następujące sekcje:

- [Problem z rekomendowanych lokali ucztujących](#problem)

- [Implementacja algorytmie](#deadlock)

- [Używanie sprzężenia w celu zapobiegania zakleszczeniom](#solution)

## <a name="the-dining-philosophers-problem"></a><a name="problem"></a>Problem z rekomendowanych lokali ucztujących

Problem z rekomendowanych lokali ucztujących ilustruje, jak zakleszczenie występuje w aplikacji. W tym problemie pięć ucztujących znajduje się w postaci okrągłej tabeli. Każdy Philosopher alternatywy między myśliją i jedzenia. Każdy Philosopher musi udostępnić Chopstick z sąsiadem po lewej stronie, a inne Chopstick z sąsiadem z prawej strony. Na poniższej ilustracji przedstawiono ten układ.

![Problem z rekomendowanych lokali ucztujących](../../parallel/concrt/media/dining_philosophersproblem.png "Problem z rekomendowanych lokali ucztujących")

Do Eat, Philosopher musi przechowywać dwie Chopsticks. Jeśli każdy Philosopher ma tylko jeden Chopstick i oczekuje na inny, a następnie Philosopher nie może być Eat i wszystkie zablokować dostęp.

[[Top](#top)]

## <a name="a-nave-implementation"></a><a name="deadlock"></a>Implementacja algorytmie

W poniższym przykładzie przedstawiono implementację algorytmie problemu ucztujących rekomendowanych lokali. `philosopher`Klasa, która pochodzi od [concurrency:: Agent](../../parallel/concrt/reference/agent-class.md), umożliwia każdemu Philosopher działania niezależnie. W przykładzie jest używany współdzielona tablica obiektów [concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) , aby zapewnić każdemu `philosopher` obiektowi wyłączny dostęp do pary Chopsticks.

Aby powiązać implementację z ilustracją, `philosopher` Klasa reprezentuje jeden Philosopher. **`int`** Zmienna reprezentuje każdy Chopstick. Obiekty są takie same `critical_section` jak posiadacze Chopsticks. `run`Metoda symuluje życie Philosopher. `think`Metoda symuluje czynność działania, a `eat` Metoda symuluje czynność jedzenia.

`philosopher`Obiekt blokuje oba `critical_section` obiekty, aby symulować usuwanie Chopsticks z posiadaczy przed wywołaniem `eat` metody. Po wywołaniu `eat` , `philosopher` obiekt zwraca Chopsticks do posiadaczy przez ustawienie `critical_section` obiektów z powrotem do stanu odblokowany.

`pickup_chopsticks`Metoda pokazuje, gdzie może wystąpić zakleszczenie. Jeśli każdy `philosopher` obiekt uzyska dostęp do jednego z blokad, żaden obiekt nie `philosopher` może kontynuować, ponieważ druga blokada jest kontrolowana przez inny `philosopher` obiekt.

### <a name="example"></a>Przykład

[!code-cpp[concrt-philosophers-deadlock#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_1.cpp)]

### <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie, `philosophers-deadlock.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **cl.exe/EHsc Philosophers-Deadlock. cpp**

[[Top](#top)]

## <a name="using-join-to-prevent-deadlock"></a><a name="solution"></a>Używanie sprzężenia w celu zapobiegania zakleszczeniom

W tej sekcji pokazano, jak używać buforów komunikatów i funkcji przekazywania komunikatów, aby wyeliminować prawdopodobieństwo zakleszczenia.

Aby powiązać ten przykład z wcześniejszym, `philosopher` Klasa zastępuje każdy obiekt za `critical_section` pomocą obiektu [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) i `join` obiektu. `join`Obiekt służy jako arbiter, który dostarcza Chopsticks do Philosopher.

Ten przykład używa `unbounded_buffer` klasy, ponieważ gdy obiekt docelowy otrzymuje komunikat z `unbounded_buffer` obiektu, wiadomość zostanie usunięta z kolejki komunikatów. Umożliwia to `unbounded_buffer` obiektowi, który przechowuje komunikat wskazujący, że Chopstick jest dostępny. `unbounded_buffer`Obiekt, który nie zawiera komunikatu, wskazuje, że Chopstick jest używany.

W tym przykładzie używa obiektu innego niż zachłanne, `join` ponieważ sprzężenie inne niż zachłanne zapewnia każdy `philosopher` dostęp do obiektu zarówno do Chopsticks, gdy oba `unbounded_buffer` obiekty zawierają komunikat. Zachłanne Join nie zapobiega zakleszczeniu, ponieważ sprzężenie zachłanne akceptuje komunikaty zaraz po ich udostępnieniu. Zakleszczenie może wystąpić, jeśli wszystkie `join` obiekty zachłanne odbierają jeden z komunikatów, ale czekają na to, że inne staną się dostępne.

Aby uzyskać więcej informacji na temat sprzężeń zachłanne i innych niż zachłanne, a różnice między różnymi typami buforów komunikatów, zobacz [asynchroniczne bloki komunikatów](../../parallel/concrt/asynchronous-message-blocks.md).

### <a name="to-prevent-deadlock-in-this-example"></a>W celu uniknięcia zakleszczenia w tym przykładzie

1. Usuń Poniższy kod z przykładu.

[!code-cpp[concrt-philosophers-deadlock#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_2.cpp)]

1. Zmień typ `_left` i `_right` składowe danych `philosopher` klasy na `unbounded_buffer` .

[!code-cpp[concrt-philosophers-join#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_3.cpp)]

1. Zmodyfikuj `philosopher` konstruktora, aby przyjmować `unbounded_buffer` obiekty jako parametry.

[!code-cpp[concrt-philosophers-join#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_4.cpp)]

1. Zmodyfikuj `pickup_chopsticks` metodę, aby użyć obiektu innego niż zachłanne `join` do odbierania komunikatów z buforów komunikatów dla obu Chopsticks.

[!code-cpp[concrt-philosophers-join#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_5.cpp)]

1. Zmodyfikuj `putdown_chopsticks` metodę, aby zwolnić dostęp do Chopsticks, wysyłając komunikat do buforów komunikatów dla obu Chopsticks.

[!code-cpp[concrt-philosophers-join#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_6.cpp)]

1. Zmodyfikuj `run` metodę, aby trzymać wyniki `pickup_chopsticks` metody i przekazać te wyniki do `putdown_chopsticks` metody.

[!code-cpp[concrt-philosophers-join#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_7.cpp)]

1. Zmodyfikuj deklarację `chopsticks` zmiennej w funkcji w taki `wmain` sposób, aby była tablicą `unbounded_buffer` obiektów, które zawierają jeden komunikat.

[!code-cpp[concrt-philosophers-join#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_8.cpp)]

### <a name="description"></a>Opis

Poniżej przedstawiono zakończono przykład, w którym są używane obiekty inne niż zachłanne, `join` Aby wyeliminować ryzyko zakleszczenia.

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

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie, `philosophers-join.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **cl.exe/EHsc Philosophers-Join. cpp**

[[Top](#top)]

## <a name="see-also"></a>Zobacz także

[Instruktaże środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)<br/>
[Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)
