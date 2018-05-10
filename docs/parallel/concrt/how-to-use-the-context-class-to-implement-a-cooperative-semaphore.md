---
title: 'Porady: Korzystanie z klasy kontekstu do wdrażania Kooperatywnego semafora | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- cooperative semaphore implementing
- context class
ms.assetid: 22f4b9c0-ca22-4a68-90ba-39e99ea76696
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 481c5f092becee7f455294437bdc695a6e1e4057
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-use-the-context-class-to-implement-a-cooperative-semaphore"></a>Porady: korzystanie z klasy kontekstu do wdrażania a kooperatywnego semafora
W tym temacie przedstawiono sposób użycia klasy concurrency::Context do zaimplementowania klasy kooperatywnego semafora.  
  
 `Context` Klasa umożliwia blokowanie lub yield bieżącego kontekstu wykonywania. Blokowanie lub reaguje bieżącego kontekstu jest przydatne w przypadku bieżącego kontekstu nie może kontynuować, ponieważ zasób nie jest dostępny. A *semafora* przykładem jednego sytuacji, w którym bieżącego kontekstu wykonywania musi czekać, aż zasób stanie się dostępne. Semafor, takich jak obiekt sekcja krytyczna jest obiekt synchronizacji, który umożliwia kod w kontekście jednej wyłącznego dostępu do zasobu. W przeciwieństwie do obiektu sekcja krytyczna semafora umożliwia więcej niż jednego kontekstu jednocześnie dostęp do zasobu. Jeśli maksymalna liczba kontekstów utrzymuje blokadę semafora, każdy dodatkowy kontekst poczekaj, aż inny kontekst do zwolnienia blokady.  
  
### <a name="to-implement-the-semaphore-class"></a>Aby implementować klasę semafora  
  
1.  Deklarowanie klasy o nazwie `semaphore`. Dodaj `public` i `private` sekcji do tej klasy.  
  
 [!code-cpp[concrt-cooperative-semaphore#1](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_1.cpp)]  
  
2.  W `private` sekcji `semaphore` klasy, Zadeklaruj [std::atomic](../../standard-library/atomic-structure.md) zmiennej, która przechowuje Licznik semafora i [concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) obiekt przechowujący kontekstów który musi czekać, można uzyskać semafora.  
  
 [!code-cpp[concrt-cooperative-semaphore#2](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_2.cpp)]  
  
3.  W `public` sekcji `semaphore` klasy, implementować konstruktora. Pobiera konstruktora `long long` wartość, która określa maksymalną liczbę kontekstach, które można jednocześnie utrzymuje blokady.  
  
 [!code-cpp[concrt-cooperative-semaphore#3](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_3.cpp)]  

4.  W `public` sekcji `semaphore` klasy, implementować `acquire` metody. Zmniejsza to metoda semafora są liczone jako operacją niepodzielną. Jeśli Licznik semafora staje się ujemna, Dodaj bieżącego kontekstu w celu oczekiwania kolejki i wywołanie [concurrency::Context::Block](reference/context-class.md#block) metodę, aby zablokować bieżącego kontekstu.  
  
 [!code-cpp[concrt-cooperative-semaphore#4](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_4.cpp)]  
  
5.  W `public` sekcji `semaphore` klasy, implementować `release` metody. Ta metoda zwiększa Licznik semafora jako operacją niepodzielną. Jeśli Licznik semafora ma wartość ujemną, zanim operacja zwiększenia, istnieje co najmniej jeden kontekstu, która oczekuje na blokadę. W takim przypadku odblokować kontekstu, który znajduje się na początek kolejki oczekiwania.  
  
 [!code-cpp[concrt-cooperative-semaphore#5](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_5.cpp)]  
  
## <a name="example"></a>Przykład  
 `semaphore` Klasy w tym przykładzie zachowuje się wspólnie, ponieważ `Context::Block` i `Context::Yield` metody yield wykonywania, dzięki czemu środowiska uruchomieniowego można wykonywać inne zadania.  
  
 `acquire` Zmniejsza metody licznik, ale może nie zakończyć dodawanie kontekstu w kolejce oczekiwania przed innego wywołania kontekstowego `release` metody. Aby uwzględnić w tym celu `release` metoda używa pętli pokrętła, który wywołuje [concurrency::Context::Yield](reference/context-class.md#yield) metody oczekiwania na `acquire` metodę, aby zakończyć dodawanie kontekstu.  
  
 `release` Można wywołać metody `Context::Unblock` metody przed `acquire` wywołania metody `Context::Block` metody. Nie masz ochronę przed sytuacja wyścigu, ponieważ środowisko uruchomieniowe umożliwia tych metod można wywołać w dowolnej kolejności. Jeśli `release` wywołania metody `Context::Unblock` przed `acquire` wywołania metody `Context::Block` na tym samym kontekście pozostaje odblokowany tego kontekstu. Środowisko uruchomieniowe wymaga tylko, że każdego wywołania w celu `Context::Block` jest dopasowywany do odpowiedniego wywołania `Context::Unblock`.  
  
 W poniższym przykładzie przedstawiono pełną `semaphore` klasy. `wmain` Funkcja zawiera podstawowe sposoby użycia tej klasy. `wmain` Używa [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytm można utworzyć kilka zadań, które wymagają dostępu do semafora. Ponieważ trzech wątków można utrzymuje blokady w dowolnym momencie, niektóre zadania należy poczekać innego zadania zakończyć i zwalnia blokadę.  
  
 [!code-cpp[concrt-cooperative-semaphore#6](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_6.cpp)]  
  
 W tym przykładzie tworzy następujące przykładowe dane wyjściowe.  
  
```Output  
In loop iteration 5...  
In loop iteration 0...  
In loop iteration 6...  
In loop iteration 1...  
In loop iteration 2...  
In loop iteration 7...  
In loop iteration 3...  
In loop iteration 8...  
In loop iteration 9...  
In loop iteration 4...  
```  
  
 Aby uzyskać więcej informacji na temat `concurrent_queue` , zobacz [równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md). Aby uzyskać więcej informacji na temat `parallel_for` algorytmu, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `cooperative-semaphore.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc wspólnego semaphore.cpp**  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Można użyć *inicjowania jest nabywania zasobów* wzorca (RAII), aby ograniczyć dostęp do `semaphore` obiektu do danego zakresu. W obszarze wzorzec RAII to struktura danych został przydzielony na stosie. Tej struktury danych inicjuje lub uzyskuje zasobu, gdy jest tworzony i niszczy lub zwalnia tego zasobu, gdy zostanie zniszczony struktury danych. Wzorzec RAII gwarantuje, że destruktor jest wywoływana przed opuszcza otaczającego zakresu. W związku z tym zasobu jest poprawnie zarządzany, jest zwracany wyjątek, lub gdy funkcja zawiera wiele `return` instrukcje.  
  
 W poniższym przykładzie zdefiniowano klasę o nazwie `scoped_lock`, która jest zdefiniowana w `public` sekcji `semaphore` klasy. `scoped_lock` Podobny klasy [concurrency::critical_section::scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) i [concurrency::reader_writer_lock::scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) klasy. Konstruktor obiektu `semaphore::scoped_lock` klas uzyskuje dostęp do danego `semaphore` obiekt i destruktor zwalnia dostęp do tego obiektu.  
  
 [!code-cpp[concrt-cooperative-semaphore#7](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_7.cpp)]    
 Poniższy przykład modyfikuje treści funkcji pracy, który jest przekazywany do `parallel_for` algorytmu, tak że używa RAII zapewnienie wydaniu semafora przed funkcja zwraca wartość. Ta metoda zapewnia, że funkcja pracy jest bezpieczne wyjątku.  
  
 [!code-cpp[concrt-cooperative-semaphore#8](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_8.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Konteksty](../../parallel/concrt/contexts.md)   
 [Równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md)

