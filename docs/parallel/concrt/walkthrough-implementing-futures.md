---
title: 'Przewodnik: Wdrażanie przyszłych operacji'
ms.date: 04/25/2019
helpviewer_keywords:
- implementing futures [Concurrency Runtime]
- futures, implementing [Concurrency Runtime]
ms.assetid: 82ea75cc-aaec-4452-b10d-8abce0a87e5b
ms.openlocfilehash: 00ad8bbe6f950ad531bad751686393dce66643bb
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857071"
---
# <a name="walkthrough-implementing-futures"></a>Przewodnik: Wdrażanie przyszłych operacji

W tym temacie przedstawiono sposób wykonania prognoz w aplikacji. Temat pokazuje, jak połączyć istniejącą funkcje w środowisku uruchomieniowym współbieżności w coś, ma większe.

> [!IMPORTANT]
>  W tym temacie przedstawiono koncepcję prognoz dla celów demonstracyjnych. Firma Microsoft zaleca użycie [std::future](../../standard-library/future-class.md) lub [concurrency::task](../../parallel/concrt/reference/task-class.md) jeżeli jest wymagane, zadanie asynchroniczne, które oblicza wartość do późniejszego użycia.

A *zadań* to obliczenie, które może być rozłożone na obliczenia dodatkowych, bardziej szczegółowo. A *przyszłych* to asynchroniczne zadanie, które oblicza wartość do późniejszego użycia.

Aby zaimplementować prognoz, w tym temacie opisano `async_future` klasy. `async_future` Klasa korzysta z tych składników środowiska uruchomieniowego współbieżności: [concurrency::task_group](reference/task-group-class.md) klasy i [concurrency::single_assignment](../../parallel/concrt/reference/single-assignment-class.md) klasy. `async_future` Klasy używa `task_group` klasy, aby obliczyć wartość asynchronicznego i `single_assignment` klasę do przechowywania wyników obliczeń. Konstruktor obiektu `async_future` klasa wykorzystuje funkcję pracy, który oblicza wynik, i `get` metoda pobiera wynik.

### <a name="to-implement-the-asyncfuture-class"></a>Aby implementować klasę async_future

1. Deklarowanie klasy szablonu o nazwie `async_future` , jest parametryzowane na typ wynikowy obliczeń. Dodaj `public` i `private` sekcji do tej klasy.

[!code-cpp[concrt-futures#2](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_1.cpp)]

1. W `private` części `async_future` klasy, Zadeklaruj `task_group` i `single_assignment` element członkowski danych.

[!code-cpp[concrt-futures#3](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_2.cpp)]

1. W `public` części `async_future` klasy, należy zaimplementować konstruktora. Konstruktor jest szablon, który jest sparametryzowane dla funkcji roboczych, które oblicza wynik. Konstruktor wykonuje asynchronicznie funkcja pracy w `task_group` element członkowski danych i używa [concurrency::send](reference/concurrency-namespace-functions.md#send) funkcję, aby zapisać wynik, który ma `single_assignment` element członkowski danych.

[!code-cpp[concrt-futures#4](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_3.cpp)]

1. W `public` części `async_future` klasy, implementować destruktor. Destruktor czeka na zakończenie zadania.

[!code-cpp[concrt-futures#5](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_4.cpp)]

1. W `public` części `async_future` klasy, implementować `get` metody. Ta metoda używa [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkcję, aby pobrać wynik funkcji pracy.

[!code-cpp[concrt-futures#6](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_5.cpp)]

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

W poniższym przykładzie pokazano pełne `async_future` klasy i przykłady ich użycia. `wmain` Funkcja tworzy std::[wektor](../../standard-library/vector-class.md) obiekt, który zawiera 10 000 losowych liczb całkowitych. Następnie używa `async_future` obiektu do znalezienia wartości najmniejszy i największy, które są zawarte w `vector` obiektu.

### <a name="code"></a>Kod

[!code-cpp[concrt-futures#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_6.cpp)]

### <a name="comments"></a>Komentarze

Ten przykład generuje następujące wyniki:

```Output
smallest: 0
largest:  9999
average:  4981
```

W przykładzie użyto `async_future::get` metody do pobierania wyników obliczeń. `async_future::get` Metoda czeka na obliczenie do zakończenia Jeśli obliczenie jest nadal aktywne.

## <a name="robust-programming"></a>Niezawodne programowanie

Aby rozszerzyć `async_future` klasy, aby obsłużyć wyjątki wyrzucane przez funkcję roboczego, zmodyfikuj `async_future::get` metodę do wywołania [CONCURRENCY::task_group:: wait](reference/task-group-class.md#wait) metody. `task_group::wait` Metoda zgłasza wyjątki, które zostały wygenerowane przez funkcję pracy.

W poniższym przykładzie pokazano zmodyfikowaną wersję `async_future` klasy. `wmain` Używa funkcji `try` - `catch` bloku, aby wydrukować wynik `async_future` obiektu lub drukowanie wartość wyjątek, który jest generowany przez funkcję pracy.

[!code-cpp[concrt-futures-with-eh#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_7.cpp)]

Ten przykład generuje następujące wyniki:

```Output
caught exception: error
```

Aby uzyskać więcej informacji na temat modelu obsługi wyjątków w środowisku uruchomieniowym współbieżności: zobacz [wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `futures.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc futures.cpp**

## <a name="see-also"></a>Zobacz także

[Środowisko uruchomieniowe współbieżności — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[task_group, klasa](reference/task-group-class.md)<br/>
[single_assignment, klasa](../../parallel/concrt/reference/single-assignment-class.md)
