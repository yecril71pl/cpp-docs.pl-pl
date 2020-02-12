---
title: 'Wskazówki: wdrażanie przyszłych operacji'
ms.date: 04/25/2019
helpviewer_keywords:
- implementing futures [Concurrency Runtime]
- futures, implementing [Concurrency Runtime]
ms.assetid: 82ea75cc-aaec-4452-b10d-8abce0a87e5b
ms.openlocfilehash: 2b9d889dac195bb60651cbb76110d54b6231a5fd
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141977"
---
# <a name="walkthrough-implementing-futures"></a>Wskazówki: wdrażanie przyszłych operacji

W tym temacie pokazano, jak zaimplementować przyszłość w aplikacji. W tym temacie pokazano, jak połączyć istniejące funkcje w środowisko uruchomieniowe współbieżności na coś, co robi więcej.

> [!IMPORTANT]
> W tym temacie przedstawiono koncepcję przyszłych zastosowań w celach demonstracyjnych. Zalecamy używanie [std:: Future](../../standard-library/future-class.md) lub [concurrency:: Task](../../parallel/concrt/reference/task-class.md) , gdy wymagane jest zadanie asynchroniczne, które oblicza wartość do późniejszego użycia.

*Zadanie* to obliczenie, które może być rozłożone na dodatkowe, bardziej szczegółowe obliczenia. *Przyszłość* to asynchroniczne zadanie, które oblicza wartość do późniejszego użycia.

Aby zaimplementować przyszłość, ten temat definiuje klasę `async_future`. Klasa `async_future` używa tych składników środowisko uruchomieniowe współbieżności: Klasa [concurrency:: task_group](reference/task-group-class.md) oraz Klasa [concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) . Klasa `async_future` używa klasy `task_group` do obliczania wartości asynchronicznej i klasy `single_assignment` do przechowywania wyniku obliczeń. Konstruktor klasy `async_future` pobiera funkcję roboczą, która oblicza wynik, a metoda `get` pobiera wynik.

### <a name="to-implement-the-async_future-class"></a>Aby implementować klasę async_future

1. Zadeklaruj klasę szablonu o nazwie `async_future`, która jest sparametryzowane dla typu wyniku obliczeń. Dodaj `public` i `private` sekcje do tej klasy.

[!code-cpp[concrt-futures#2](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_1.cpp)]

1. W sekcji `private` klasy `async_future` Zadeklaruj `task_group` i `single_assignment` element członkowski danych.

[!code-cpp[concrt-futures#3](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_2.cpp)]

1. W sekcji `public` klasy `async_future` Zaimplementuj konstruktora. Konstruktor jest szablon, który jest sparametryzowane dla funkcji pracy, która oblicza wynik. Konstruktor asynchronicznie wykonuje funkcję Work w elemencie członkowskim danych `task_group` i używa funkcji [concurrency:: Send](reference/concurrency-namespace-functions.md#send) , aby zapisać wynik do `single_assignment` elementu członkowskiego danych.

[!code-cpp[concrt-futures#4](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_3.cpp)]

1. W sekcji `public` klasy `async_future` Zaimplementuj destruktor. Destruktor czeka na zakończenie zadania.

[!code-cpp[concrt-futures#5](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_4.cpp)]

1. W sekcji `public` klasy `async_future` Zaimplementuj metodę `get`. Ta metoda używa funkcji [concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) , aby pobrać wynik funkcji służbowej.

[!code-cpp[concrt-futures#6](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_5.cpp)]

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

W poniższym przykładzie przedstawiono kompletną klasę `async_future` i przykład użycia. Funkcja `wmain` tworzy obiekt[wektorów](../../standard-library/vector-class.md) std:: Vector, który zawiera 10 000 losowe wartości całkowite. Następnie używa `async_future` obiektów, aby znaleźć najmniejsze i największe wartości, które są zawarte w obiekcie `vector`.

### <a name="code"></a>Kod

[!code-cpp[concrt-futures#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_6.cpp)]

### <a name="comments"></a>Komentarze

Ten przykład generuje następujące wyniki:

```Output
smallest: 0
largest:  9999
average:  4981
```

W przykładzie zastosowano metodę `async_future::get` w celu pobrania wyników obliczeń. Metoda `async_future::get` czeka na zakończenie obliczeń, jeśli obliczenie jest nadal aktywne.

## <a name="robust-programming"></a>Skuteczne programowanie

Aby zwiększyć klasę `async_future`, aby obsługiwała wyjątki, które są zgłaszane przez funkcję służbową, należy zmodyfikować metodę `async_future::get`, aby wywołać metodę [concurrency:: task_group:: wait](reference/task-group-class.md#wait) . Metoda `task_group::wait` zgłasza wszystkie wyjątki, które zostały wygenerowane przez funkcję służbową.

W poniższym przykładzie przedstawiono zmodyfikowaną wersję klasy `async_future`. Funkcja `wmain` używa bloku `try`-`catch` do drukowania wyniku obiektu `async_future` lub do wydrukowania wartości wyjątku, który jest generowany przez funkcję służbową.

[!code-cpp[concrt-futures-with-eh#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_7.cpp)]

Ten przykład generuje następujące wyniki:

```Output
caught exception: error
```

Aby uzyskać więcej informacji na temat modelu obsługi wyjątków w środowisko uruchomieniowe współbieżności, zobacz [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `futures.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**CL. exe/EHsc przyszłość. cpp**

## <a name="see-also"></a>Zobacz też

[Środowisko uruchomieniowe współbieżności — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[task_group, klasa](reference/task-group-class.md)<br/>
[single_assignment, klasa](../../parallel/concrt/reference/single-assignment-class.md)
