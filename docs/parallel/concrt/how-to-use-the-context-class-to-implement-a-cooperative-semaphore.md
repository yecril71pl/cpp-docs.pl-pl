---
title: 'Porady: korzystanie z klasy kontekstu do wdrażania a kooperatywnego semafora'
ms.date: 11/04/2016
helpviewer_keywords:
- cooperative semaphore implementing
- context class
ms.assetid: 22f4b9c0-ca22-4a68-90ba-39e99ea76696
ms.openlocfilehash: 460a1de03f34cb8ef9753e761aaef37470cd6d0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467771"
---
# <a name="how-to-use-the-context-class-to-implement-a-cooperative-semaphore"></a>Porady: korzystanie z klasy kontekstu do wdrażania a kooperatywnego semafora

W tym temacie pokazano, jak korzystać z concurrency::Context klasy do zaimplementowania klasy kooperatywnego semafora.

`Context` Klasa pozwala zablokować, lub yield bieżącego kontekstu wykonywania. Blokowanie lub reaguje bieżącego kontekstu jest przydatne, gdy nie można kontynuować bieżącego kontekstu, ponieważ zasób jest niedostępny. A *semafora* jest przykładem jedna sytuacja, gdy bieżący kontekst wykonywania muszą czekać zasób stanie się dostępny. Semafor, takich jak obiekt sekcję krytyczną jest obiektem synchronizacji umożliwiającym kodu w jednym kontekście wyłącznego dostępu do zasobu. W przeciwieństwie do obiektu sekcję krytyczną semafor umożliwia więcej niż jednym kontekście jednocześnie dostęp do zasobu. Jeśli maksymalną liczbę kontekstów posiada blokadę semafor, każdy dodatkowy kontekst musi czekać na innego kontekstu, aby zwolnić blokadę.

### <a name="to-implement-the-semaphore-class"></a>Aby implementować klasę semafora

1. Deklarowanie klasy, który nosi nazwę `semaphore`. Dodaj `public` i `private` sekcji do tej klasy.

[!code-cpp[concrt-cooperative-semaphore#1](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_1.cpp)]

1. W `private` części `semaphore` klasy, Zadeklaruj [std::atomic](../../standard-library/atomic-structure.md) zmienna, która zawiera liczbę semafor i [concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) obiekt, który przechowuje kontekstów który należy poczekać do uzyskania semafora.

[!code-cpp[concrt-cooperative-semaphore#2](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_2.cpp)]

1. W `public` części `semaphore` klasy, należy zaimplementować konstruktora. Konstruktor przyjmuje liczbę `long long` wartość, która określa maksymalną liczbę kontekstów, które może jednocześnie zawierać blokady.

[!code-cpp[concrt-cooperative-semaphore#3](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_3.cpp)]

1. W `public` części `semaphore` klasy, implementować `acquire` metody. Zmniejsza to metoda semafora liczone jako operację niepodzielną. Jeśli liczba semafora staje się ujemna, Dodaj bieżącego kontekstu do końca okresu oczekiwania kolejki i wywołanie [concurrency::Context::Block](reference/context-class.md#block) metodę, aby zablokować bieżącego kontekstu.

[!code-cpp[concrt-cooperative-semaphore#4](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_4.cpp)]

1. W `public` części `semaphore` klasy, implementować `release` metody. Ta metoda zwiększa liczbę semafora jako operację niepodzielną. Liczba semafora jest ujemna przed wykonaniem operacji inkrementacji, czy istnieje co najmniej jeden kontekst, który jest oczekujący na blokadę. W tym przypadku odblokować kontekst, który znajduje się na wierzchu kolejki oczekiwania.

[!code-cpp[concrt-cooperative-semaphore#5](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_5.cpp)]

## <a name="example"></a>Przykład

`semaphore` Klasy, w tym przykładzie zachowuje się wspólne, ponieważ `Context::Block` i `Context::Yield` metody uzyskanie wykonywania, dzięki czemu środowisko uruchomieniowe można wykonywać inne zadania.

`acquire` Zmniejsza metoda licznika, ale nie może zakończyć dodawanie kontekstu do kolejki oczekiwania przed innym wywołania kontekstowego `release` metody. Do konta w tym celu `release` metoda używa pętli pokrętła, który wywołuje [concurrency::Context::Yield](reference/context-class.md#yield) metodę, aby czekać na `acquire` metodę, aby zakończyć dodawanie kontekstu.

`release` Można wywołać metody `Context::Unblock` metody przed `acquire` wywołania metody `Context::Block` metody. Nie trzeba chronić przed sytuacja wyścigu, ponieważ środowisko uruchomieniowe umożliwia dotyczącej tych metod, które ma zostać wywołana w dowolnej kolejności. Jeśli `release` wywołania metody `Context::Unblock` przed `acquire` wywołania metody `Context::Block` ten sam kontekst tego kontekstu nie zmieniają odblokowane. Środowisko uruchomieniowe wymaga jedynie, że każdy wywołanie `Context::Block` jest dopasowywany do odpowiedniego wywołania `Context::Unblock`.

W poniższym przykładzie pokazano pełne `semaphore` klasy. `wmain` Funkcji pokazuje podstawowe użycie tej klasy. `wmain` Używa funkcji [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytmu, aby utworzyć kilka zadań, które wymagają dostępu do semafora. Ponieważ trzech wątków może zawierać blokady w dowolnym momencie, niektóre zadania musi czekać na inne zadanie zakończyć i zwalnia blokadę.

[!code-cpp[concrt-cooperative-semaphore#6](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_6.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe.

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

Aby uzyskać więcej informacji na temat `concurrent_queue` klasy, zobacz [równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md). Aby uzyskać więcej informacji na temat `parallel_for` algorytmu, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `cooperative-semaphore.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc cooperative-semaphore.cpp**

## <a name="robust-programming"></a>Niezawodne programowanie

Możesz użyć *inicjowania jest pozyskiwanie zasobów* wzorca (RAII), aby ograniczyć dostęp do `semaphore` obiektu do danego zakresu. W obszarze wzór RAII to struktura danych jest przydzielany na stosie. Tej struktury danych inicjuje lub uzyskuje zasobu, gdy jest tworzony i niszczy lub zwalnia tego zasobu, kiedy niszczony jest struktury danych. Wzór RAII gwarantuje, że destruktor jest wywoływany przed zasięgu kończy działanie. W związku z tym, gdy wyjątek jest zgłaszany, lub gdy funkcja zawiera wiele zasobu jest poprawnie zarządzany `return` instrukcji.

W poniższym przykładzie zdefiniowano klasę, która nosi nazwę `scoped_lock`, który jest zdefiniowany w `public` części `semaphore` klasy. `scoped_lock` Klasa przypomina [concurrency::critical_section::scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) i [concurrency::reader_writer_lock::scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) klasy. Konstruktor obiektu `semaphore::scoped_lock` klasy uzyskuje dostęp do danego `semaphore` obiektu i destruktor zwalnia dostęp do tego obiektu.

[!code-cpp[concrt-cooperative-semaphore#7](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_7.cpp)]
Poniższy przykład modyfikuje treści funkcji pracy, który jest przekazywany do `parallel_for` algorytmu, tak że używa RAII, aby zapewnić jest zwolnienie semafora zanim funkcja zwróci. Ta technika gwarantuje, że funkcja pracy jest bezpieczna pod względem wyjątków.

[!code-cpp[concrt-cooperative-semaphore#8](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_8.cpp)]

## <a name="see-also"></a>Zobacz też

[Konteksty](../../parallel/concrt/contexts.md)<br/>
[Równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md)

