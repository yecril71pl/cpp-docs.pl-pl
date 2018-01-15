---
title: "Wskazówki: Wdrażanie przyszłych operacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- implementing futures [Concurrency Runtime]
- futures, implementing [Concurrency Runtime]
ms.assetid: 82ea75cc-aaec-4452-b10d-8abce0a87e5b
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 119969860f031acbc2f1764a34a456d2e8a16437
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-implementing-futures"></a>Wskazówki: wdrażanie przyszłych operacji
W tym temacie przedstawiono sposób wykonania przyszłych operacji w aplikacji. Temat pokazuje, jak połączyć istniejące funkcje współbieżność środowiska wykonawczego na coś nieistniejącego więcej.  
  
> [!IMPORTANT]
>  W tym temacie przedstawiono koncepcję prognoz w celach demonstracyjnych. Firma Microsoft zaleca użycie [std::future](../../standard-library/future-class.md) lub [concurrency::task](../../parallel/concrt/reference/task-class.md) Jeżeli wymagane zadanie asynchroniczne, który oblicza wartość do późniejszego użycia.  
  
 A *zadań* jest obliczeń, który może być rozłożone na obliczenia dodatkowych, bardziej szczegółowo. A *przyszłych* jest zadanie asynchroniczne, który oblicza wartość do późniejszego użycia.  
  
 Aby zaimplementować prognoz, w tym temacie opisano `async_future` klasy. `async_future` Klasa korzysta z tych składników współbieżności środowiska wykonawczego: [concurrency::task_group](reference/task-group-class.md) klasy i [concurrency::single_assignment](../../parallel/concrt/reference/single-assignment-class.md) klasy. `async_future` Klasy używa `task_group` klasy do obliczenia wartości asynchronicznie i `single_assignment` klasę do przechowywania wyniku obliczenia. Konstruktor obiektu `async_future` klasy przyjmuje funkcja pracy, który oblicza wynik, i `get` metoda pobiera wynik.  
  
### <a name="to-implement-the-asyncfuture-class"></a>Aby implementować klasę async_future  
  
1.  Deklarowanie klasy szablonu o nazwie `async_future` który jest sparametryzowana typu obliczenia wynikowy. Dodaj `public` i `private` sekcji do tej klasy.  
  
 [!code-cpp[concrt-futures#2](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_1.cpp)]  
  
2.  W `private` sekcji `async_future` klasy, Zadeklaruj `task_group` i `single_assignment` element członkowski danych.  
  
 [!code-cpp[concrt-futures#3](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_2.cpp)]  
  

3.  W `public` sekcji `async_future` klasy, implementować konstruktora. Konstruktor jest szablon, który jest sparametryzowana w funkcji pracy, który oblicza wynik. Konstruktor asynchronicznie wykonuje funkcja pracy w `task_group` element członkowski danych i używa [concurrency::send](reference/concurrency-namespace-functions.md#send) funkcji, aby zapisać wynik, który ma `single_assignment` element członkowski danych.  
  
 [!code-cpp[concrt-futures#4](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_3.cpp)]  
  
4.  W `public` sekcji `async_future` klasy, implementować destruktor. Destruktor czeka na zakończenie zadania.  
  
 [!code-cpp[concrt-futures#5](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_4.cpp)]  
  

5.  W `public` sekcji `async_future` klasy, implementować `get` metody. Ta metoda używa [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkcji można pobrać wyniku funkcji pracy.  

  
 [!code-cpp[concrt-futures#6](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_5.cpp)]  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono pełną `async_future` klasy i przykład jego użycia. `wmain` Funkcja tworzy std::[wektor](../../standard-library/vector-class.md) obiekt, który zawiera 10 000 wartości losową liczbę całkowitą. Następnie używa `async_future` obiektów, aby znaleźć wartości najmniejsza i największa, które są zawarte w `vector` obiektu.  
  
### <a name="code"></a>Kod  
 [!code-cpp[concrt-futures#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_6.cpp)]  
  
### <a name="comments"></a>Komentarze  
 Ten przykład generuje następujące wyniki:  
  
```Output  
smallest: 0  
largest:  9999  
average:  4981  
```  
  
 W przykładzie użyto `async_future::get` metoda pobierania wyników obliczeń. `async_future::get` Metoda oczekuje na obliczenia na zakończenie czy obliczenia jest nadal aktywna.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  


 Aby rozszerzyć `async_future` klasy do obsługi wyjątków, które są generowane przez funkcję roboczego, zmodyfikuj `async_future::get` metodę do wywołania [concurrency::task_group::wait](reference/task-group-class.md#wait) metody. `task_group::wait` Metoda zgłasza wszelkie wyjątki, które zostały wygenerowane przez funkcję pracy.  


  
 W poniższym przykładzie przedstawiono zmodyfikowanej wersji `async_future` klasy. `wmain` Używa `try` - `catch` bloku, aby wydrukować wynik `async_future` obiektu lub drukować wartość wyjątku, który jest generowany przez funkcję pracy.  
  
 [!code-cpp[concrt-futures-with-eh#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_7.cpp)]  
  
 Ten przykład generuje następujące wyniki:  
  
```Output  
caught exception: error  
```  
  
 Aby uzyskać więcej informacji na temat modelu obsługi wyjątków w współbieżności środowiska wykonawczego, zobacz [obsługi wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `futures.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe futures.cpp/ehsc**  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność środowiska wykonawczego — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [task_group — klasa](reference/task-group-class.md)   
 [single_assignment, klasa](../../parallel/concrt/reference/single-assignment-class.md)
