---
title: 'Porady: korzystanie z filtra bloku komunikatów'
ms.date: 11/04/2016
helpviewer_keywords:
- message-block filters, using [Concurrency Runtime]
- using message-block filters [Concurrency Runtime]
ms.assetid: db6b99fb-288d-4477-96dc-b9751772ebb2
ms.openlocfilehash: 512dda6503d5980dbdcc20a55ca0ee836d4d08e3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660138"
---
# <a name="how-to-use-a-message-block-filter"></a>Porady: korzystanie z filtra bloku komunikatów

W tym dokumencie przedstawiono sposób użycia funkcji filtru umożliwiające blokiem komunikatów asynchronicznych akceptowanie lub odrzucanie wiadomość na podstawie ładunku tego komunikatu.

Podczas tworzenia obiektu bloku komunikatu takich jak [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md), [concurrency::call](../../parallel/concrt/reference/call-class.md), lub [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md), możesz podać *funkcja filtrowania* określający, czy blok komunikatów akceptuje lub odrzuca komunikat. Funkcję filtru jest to wygodny sposób, aby zagwarantować, że blok komunikatów odbiera tylko niektóre wartości.

Funkcje filtra są ważne, ponieważ umożliwiają one nawiązanie połączenia bloki komunikatów do formularza *przepływu danych sieci*. W przypadku sieci przepływu danych bloki komunikatów sterowania przepływem danych przez przetwarzanie tylko tych wiadomości, które spełniają określone kryteria. To porównać do modelu przepływ sterowania, gdy przepływ danych jest regulowany przy użyciu struktury sterujące przykład instrukcje warunkowe, pętle i tak dalej.

Ten dokument zawiera prosty przykład sposobu użycia filtr komunikatu. Dodatkowe przykłady, używające filtry komunikatów i model przepływu danych do łączenia bloków komunikatów, zobacz [wskazówki: tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md) i [wskazówki: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md) .

## <a name="example"></a>Przykład

Należy wziąć pod uwagę następującą funkcję `count_primes`, która przedstawia podstawy używania Blok komunikatów, który nie filtruje wiadomości przychodzących. Blok komunikatów dołącza liczb pierwszych do [std::vector](../../standard-library/vector-class.md) obiektu. `count_primes` Funkcji wysyła kilka liczb do bloku komunikatów odbiera wartości danych wyjściowych z bloku komunikatów i drukuje tych dwóch liczb znajdujących się na pierwsze do konsoli.

[!code-cpp[concrt-primes-filter#1](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_1.cpp)]

`transformer` Obiektu przetwarza wszystkie wartości wejściowe; wymaga to jednak tylko te wartości, które są Północnej. Mimo że mogłyby być zapisywane aplikacji, tak aby nadawca wysyła tylko liczb pierwszych, nie zawsze znane wymagania odbiorcom wiadomości.

## <a name="example"></a>Przykład

Poniższa funkcja `count_primes_filter`, wykonuje to samo zadanie `count_primes` funkcji. Jednak `transformer` obiekt w tej wersji używa funkcji filtru, aby akceptować tylko tych wartości, które są prime. Funkcja, która wykonuje akcję odbiera tylko liczby pierwsze; w związku z tym, nie ma do wywołania `is_prime` funkcji.

Ponieważ `transformer` obiekt otrzymuje tylko liczby pierwsze `transformer` sam obiekt może zawierać liczb pierwszych. Innymi słowy `transformer` obiekt w tym przykładzie nie jest wymagane do dodawania liczb pierwszych, aby `vector` obiektu.

[!code-cpp[concrt-primes-filter#2](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_2.cpp)]

`transformer` Obiektu przetwarza teraz tylko tych wartości, które są Północnej. W poprzednim przykładzie `transformer` obiektów są przetwarzane wszystkie komunikaty. Dlatego taką samą liczbę wiadomości, które wysyła musi otrzymać bit poprzedniego przykładu. W tym przykładzie użyto wynik [concurrency::send](reference/concurrency-namespace-functions.md#send) funkcję, aby określić, ile komunikatów można otrzymywać `transformer` obiektu. `send` Funkcja zwraca **true** po buforu komunikatu zaakceptuje wiadomość i **false** po buforu komunikatu odrzuca komunikat. W związku z tym ile razy czy buforu komunikatu zaakceptuje wiadomość jest zgodna z liczbą, liczb pierwszych.

## <a name="example"></a>Przykład

Poniższy kod przedstawia kompletny przykład. Przykład wywołuje zarówno `count_primes` funkcji i `count_primes_filter` funkcji.

[!code-cpp[concrt-primes-filter#3](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_3.cpp)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `primes-filter.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc blokad filter.cpp**

## <a name="robust-programming"></a>Niezawodne programowanie

Funkcja filtru może być funkcji lambda, wskaźnika funkcji lub obiektu funkcji. Każdej funkcji filtru ma jedną z następujących form:

```Output
bool (T)
bool (T const &)
```

Aby wyeliminować niepotrzebnego kopiowania danych, użyj drugiego formularza, jeśli masz typ agregacji, który jest przekazywany przez wartość.

## <a name="see-also"></a>Zobacz też

[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Przewodnik: tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[Przewodnik: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[transformer, klasa](../../parallel/concrt/reference/transformer-class.md)
