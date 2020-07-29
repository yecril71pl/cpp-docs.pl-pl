---
title: 'Porady: korzystanie z klasy kontekstu do wdrażania a kooperatywnego semafora'
ms.date: 11/04/2016
helpviewer_keywords:
- cooperative semaphore implementing
- context class
ms.assetid: 22f4b9c0-ca22-4a68-90ba-39e99ea76696
ms.openlocfilehash: 77cf33288761c75d056649ebe27f9d74c6fa62dc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230392"
---
# <a name="how-to-use-the-context-class-to-implement-a-cooperative-semaphore"></a>Porady: korzystanie z klasy kontekstu do wdrażania a kooperatywnego semafora

W tym temacie pokazano, jak używać klasy concurrency:: Context do implementowania wspólnej klasy semafora.

## <a name="remarks"></a>Uwagi

`Context`Klasa pozwala zablokować lub uzyskać bieżący kontekst wykonania. Blokowanie lub pozyskanie bieżącego kontekstu jest przydatne, gdy nie można wykonać bieżącego kontekstu, ponieważ zasób nie jest dostępny. *Semafor* to przykład jednej sytuacji, w której bieżący kontekst wykonywania musi oczekiwać na udostępnienie zasobu. Semafor, taki jak obiekt sekcji krytycznej, jest obiektem synchronizacji, który umożliwia kod w jednym kontekście, aby mieć wyłączny dostęp do zasobu. Jednak, w przeciwieństwie do obiektu sekcji krytycznej, semafor umożliwia jednocześnie dostęp do zasobu w więcej niż jednym kontekście. Jeśli maksymalna liczba kontekstów ma blokadę semafora, każdy dodatkowy kontekst musi czekać na inny kontekst, aby zwolnić blokadę.

### <a name="to-implement-the-semaphore-class"></a>Aby implementować klasę semafora

1. Zadeklaruj klasę o nazwie `semaphore` . Dodaj **`public`** **`private`** sekcje i do tej klasy.

[!code-cpp[concrt-cooperative-semaphore#1](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_1.cpp)]

1. W **`private`** sekcji `semaphore` klasy Zadeklaruj zmienną [std::](../../standard-library/atomic-structure.md) Variable, która przechowuje liczbę semaforów i obiekt [concurrency:: concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) , który przechowuje konteksty, które muszą oczekiwać na uzyskanie semafora.

[!code-cpp[concrt-cooperative-semaphore#2](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_2.cpp)]

1. W **`public`** sekcji `semaphore` klasy Zaimplementuj konstruktora. Konstruktor przyjmuje wartość określającą **`long long`** maksymalną liczbę kontekstów, które mogą jednocześnie blokować blokadę.

[!code-cpp[concrt-cooperative-semaphore#3](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_3.cpp)]

1. W **`public`** sekcji `semaphore` klasy Zaimplementuj `acquire` metodę. Ta metoda zmniejsza liczbę semaforów jako operację niepodzielną. Jeśli liczba semaforów przestała być ujemna, Dodaj bieżący kontekst do końca kolejki oczekiwania i Wywołaj metodę [concurrency:: Context:: Block](reference/context-class.md#block) , aby zablokować bieżący kontekst.

[!code-cpp[concrt-cooperative-semaphore#4](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_4.cpp)]

1. W **`public`** sekcji `semaphore` klasy Zaimplementuj `release` metodę. Ta metoda zwiększa liczbę semaforów jako operację niepodzielną. Jeśli liczba semaforów jest ujemna przed operacją przyrostu, istnieje co najmniej jeden kontekst, który oczekuje na blokadę. W takim przypadku należy odblokować kontekst, który znajduje się na początku kolejki oczekiwania.

[!code-cpp[concrt-cooperative-semaphore#5](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_5.cpp)]

## <a name="example"></a>Przykład

`semaphore`Klasa w tym przykładzie zachowuje się wspólnie, ponieważ `Context::Block` `Context::Yield` metody i umożliwiają wykonywanie innych zadań w środowisku uruchomieniowym.

`acquire`Metoda zmniejsza licznik, ale może nie zakończyć dodawania kontekstu do kolejki oczekiwania przed wywołaniem przez inny kontekst `release` metody. W tym celu `release` Metoda używa pętli pokrętła, która wywołuje metodę [concurrency:: Context:: Yield](reference/context-class.md#yield) , aby poczekać na `acquire` zakończenie dodawania kontekstu przez metodę.

`release`Metoda może wywołać `Context::Unblock` metodę przed wywołaniem metody `acquire` `Context::Block` . Nie ma potrzeby ochrony przed tym sytuacją wyścigu, ponieważ środowisko uruchomieniowe umożliwia wywoływanie tych metod w dowolnej kolejności. Jeśli `release` Metoda wywołuje `Context::Unblock` przed `acquire` wywołaniem metody `Context::Block` dla tego samego kontekstu, ten kontekst pozostaje odblokowany. Środowisko uruchomieniowe wymaga, aby każde wywołanie było `Context::Block` zgodne z odpowiednim wywołaniem do `Context::Unblock` .

Poniższy przykład pokazuje kompletną `semaphore` klasę. `wmain`Funkcja pokazuje podstawowe użycie tej klasy. `wmain`Funkcja używa algorytmu [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) do tworzenia kilku zadań, które wymagają dostępu do semafora. Ponieważ trzy wątki mogą utrzymywać blokadę w dowolnym momencie, niektóre zadania muszą oczekiwać na zakończenie innego zadania i zwolnić blokadę.

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

Aby uzyskać więcej informacji na temat `concurrent_queue` klasy, zobacz [Parallel Containers and Objects](../../parallel/concrt/parallel-containers-and-objects.md). Aby uzyskać więcej informacji na temat `parallel_for` algorytmu, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie, `cooperative-semaphore.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **cl.exe/EHsc Cooperative-Semaphore. cpp**

## <a name="robust-programming"></a>Niezawodne programowanie

Aby ograniczyć dostęp do obiektu do danego zakresu, można użyć wzorca *pozyskiwania zasobów* (RAII) `semaphore` . Pod wzorcem RAII, struktura danych jest przypisana na stosie. Ta struktura danych inicjuje lub uzyskuje zasób podczas jego tworzenia i niszczy lub zwalnia ten zasób, gdy struktura danych zostanie zniszczona. Wzorzec RAII gwarantuje, że destruktor jest wywoływany przed wyjściem z otaczającego zakresu. W związku z tym zasób jest prawidłowo zarządzany, gdy wyjątek jest zgłaszany lub funkcja zawiera wiele **`return`** instrukcji.

W poniższym przykładzie zdefiniowano klasę o nazwie `scoped_lock` , która jest zdefiniowana w **`public`** sekcji `semaphore` klasy. `scoped_lock`Klasa jest podobna do klasy [concurrency:: critical_section:: scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) i [concurrency:: reader_writer_lock:: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) . Konstruktor `semaphore::scoped_lock` klasy uzyskuje dostęp do danego `semaphore` obiektu, a destruktor zwalnia dostęp do tego obiektu.

[!code-cpp[concrt-cooperative-semaphore#7](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_7.cpp)]
Poniższy przykład modyfikuje treść funkcji pracy przekazanej do `parallel_for` algorytmu tak, aby korzystała z RAII, aby zapewnić, że semafor zostanie wyliczony przed zwróceniem funkcji. Ta technika gwarantuje, że funkcja pracy jest bezpieczna przed wyjątkami.

[!code-cpp[concrt-cooperative-semaphore#8](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_8.cpp)]

## <a name="see-also"></a>Zobacz także

[Konteksty](../../parallel/concrt/contexts.md)<br/>
[Równoległe kontenery i obiekty](../../parallel/concrt/parallel-containers-and-objects.md)
