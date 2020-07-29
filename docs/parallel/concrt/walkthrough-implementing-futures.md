---
title: 'Wskazówki: wdrażanie przyszłych operacji'
ms.date: 04/25/2019
helpviewer_keywords:
- implementing futures [Concurrency Runtime]
- futures, implementing [Concurrency Runtime]
ms.assetid: 82ea75cc-aaec-4452-b10d-8abce0a87e5b
ms.openlocfilehash: 9bf46b7f2a761aaf0c07e1017524c8ddf533aca6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230301"
---
# <a name="walkthrough-implementing-futures"></a>Wskazówki: wdrażanie przyszłych operacji

W tym temacie pokazano, jak zaimplementować przyszłość w aplikacji. W tym temacie pokazano, jak połączyć istniejące funkcje w środowisko uruchomieniowe współbieżności na coś, co robi więcej.

> [!IMPORTANT]
> W tym temacie przedstawiono koncepcję przyszłych zastosowań w celach demonstracyjnych. Zalecamy używanie [std:: Future](../../standard-library/future-class.md) lub [concurrency:: Task](../../parallel/concrt/reference/task-class.md) , gdy wymagane jest zadanie asynchroniczne, które oblicza wartość do późniejszego użycia.

*Zadanie* to obliczenie, które może być rozłożone na dodatkowe, bardziej szczegółowe obliczenia. *Przyszłość* to asynchroniczne zadanie, które oblicza wartość do późniejszego użycia.

Aby zaimplementować przyszłość, ten temat definiuje `async_future` klasę. `async_future`Klasa używa tych składników Środowisko uruchomieniowe współbieżności: Klasa [concurrency:: task_group](reference/task-group-class.md) i [concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) klasy. `async_future`Klasa używa `task_group` klasy do obliczania wartości asynchronicznej i `single_assignment` klasy do przechowywania wyniku obliczenia. Konstruktor `async_future` klasy pobiera funkcję roboczą, która oblicza wynik, a `get` Metoda pobiera wynik.

### <a name="to-implement-the-async_future-class"></a>Aby implementować klasę async_future

1. Zadeklaruj klasę szablonu o nazwie `async_future` , która jest sparametryzowana dla typu obliczanego wyniku. Dodaj **`public`** **`private`** sekcje i do tej klasy.

[!code-cpp[concrt-futures#2](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_1.cpp)]

1. W **`private`** sekcji `async_future` klasy Zadeklaruj `task_group` `single_assignment` element członkowski danych i.

[!code-cpp[concrt-futures#3](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_2.cpp)]

1. W **`public`** sekcji `async_future` klasy Zaimplementuj konstruktora. Konstruktor jest szablon, który jest sparametryzowane dla funkcji pracy, która oblicza wynik. Konstruktor asynchronicznie wykonuje funkcję Work w `task_group` składowej danych i używa funkcji [concurrency:: Send](reference/concurrency-namespace-functions.md#send) , aby zapisać wynik do `single_assignment` elementu członkowskiego danych.

[!code-cpp[concrt-futures#4](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_3.cpp)]

1. W **`public`** sekcji `async_future` klasy Zaimplementuj destruktor. Destruktor czeka na zakończenie zadania.

[!code-cpp[concrt-futures#5](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_4.cpp)]

1. W **`public`** sekcji `async_future` klasy Zaimplementuj `get` metodę. Ta metoda używa funkcji [concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) , aby pobrać wynik funkcji służbowej.

[!code-cpp[concrt-futures#6](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_5.cpp)]

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład pokazuje kompletną `async_future` klasę i przykład użycia. `wmain`Funkcja tworzy obiekt wektor::[Vector](../../standard-library/vector-class.md) , który zawiera 10 000 losowe wartości całkowite. Następnie używa `async_future` obiektów, aby znaleźć najmniejsze i największe wartości, które są zawarte w `vector` obiekcie.

### <a name="code"></a>Kod

[!code-cpp[concrt-futures#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_6.cpp)]

### <a name="comments"></a>Komentarze

Ten przykład generuje następujące wyniki:

```Output
smallest: 0
largest:  9999
average:  4981
```

W przykładzie zastosowano `async_future::get` metodę w celu pobrania wyników obliczeń. `async_future::get`Metoda czeka na zakończenie obliczeń, jeśli obliczenie jest nadal aktywne.

## <a name="robust-programming"></a>Niezawodne programowanie

Aby zwiększyć klasę obsługującą `async_future` wyjątki, które są zgłaszane przez funkcję służbową, zmodyfikuj `async_future::get` metodę w celu wywołania metody [concurrency:: task_group:: wait](reference/task-group-class.md#wait) . `task_group::wait`Metoda zgłasza wszystkie wyjątki, które zostały wygenerowane przez funkcję służbową.

W poniższym przykładzie przedstawiono zmodyfikowaną wersję `async_future` klasy. `wmain`Funkcja używa **`try`** - **`catch`** bloku do drukowania wyniku `async_future` obiektu lub do drukowania wartości wyjątku, który jest generowany przez funkcję służbową.

[!code-cpp[concrt-futures-with-eh#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_7.cpp)]

Ten przykład generuje następujące wyniki:

```Output
caught exception: error
```

Aby uzyskać więcej informacji na temat modelu obsługi wyjątków w środowisko uruchomieniowe współbieżności, zobacz [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie, `futures.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**cl.exe przyszłość/EHsc. cpp**

## <a name="see-also"></a>Zobacz także

[Instruktaże środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Klasa task_group](reference/task-group-class.md)<br/>
[Klasa single_assignment](../../parallel/concrt/reference/single-assignment-class.md)
