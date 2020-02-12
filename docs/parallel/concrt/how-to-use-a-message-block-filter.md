---
title: 'Porady: korzystanie z filtra bloku komunikatów'
ms.date: 11/04/2016
helpviewer_keywords:
- message-block filters, using [Concurrency Runtime]
- using message-block filters [Concurrency Runtime]
ms.assetid: db6b99fb-288d-4477-96dc-b9751772ebb2
ms.openlocfilehash: 074d3989ce48b0b6d69206e3f83c374a2ec65c93
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142818"
---
# <a name="how-to-use-a-message-block-filter"></a>Porady: korzystanie z filtra bloku komunikatów

W tym dokumencie przedstawiono sposób użycia funkcji filtru w celu włączenia asynchronicznego bloku komunikatów do akceptowania lub odrzucania komunikatu na podstawie ładunku tego komunikatu.

Podczas tworzenia obiektu bloku komunikatów, takiego jak [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md), [concurrency:: Call](../../parallel/concrt/reference/call-class.md)lub [concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md), można dostarczyć *funkcję filtru* , która określa, czy blok komunikatów akceptuje lub odrzuca komunikat. Funkcja filtru jest użytecznym sposobem zagwarantowania, że blok komunikatów odbiera tylko niektóre wartości.

Funkcja filters jest ważna, ponieważ umożliwia łączenie bloków komunikatów z *sieciami przepływu danych*. W sieci przepływu danych bloki komunikatów sterują przepływem danych przez przetwarzanie tylko tych komunikatów, które spełniają określone kryteria. Porównaj to z modelem przepływu sterowania, gdzie przepływ danych jest regulowany przy użyciu struktur kontroli, takich jak instrukcje warunkowe, pętle i tak dalej.

Ten dokument zawiera podstawowy przykład użycia filtru komunikatów. Aby uzyskać dodatkowe przykłady, które używają filtrów komunikatów i modelu przepływu danych do łączenia bloków komunikatów, zobacz [Przewodnik: tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md) i [Przewodnik: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

## <a name="example"></a>Przykład

Rozważmy następującą funkcję `count_primes`, która ilustruje podstawowe użycie bloku komunikatów, który nie filtruje komunikatów przychodzących. Blok komunikatów dołącza podstawowe numery do obiektu [wektora std:: Vector](../../standard-library/vector-class.md) . Funkcja `count_primes` wysyła kilka liczb do bloku komunikatów, odbiera wartości wyjściowe z bloku komunikatów i drukuje te liczby, które są dostępne w konsoli programu.

[!code-cpp[concrt-primes-filter#1](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_1.cpp)]

Obiekt `transformer` przetwarza wszystkie wartości wejściowe; jednak wymaga to tylko tych wartości, które są podstawowe. Mimo że aplikacja może zostać zapisywana w taki sposób, aby nadawca wiadomości wysyłał tylko numery podstawowe, wymagania odbiorcy wiadomości nie zawsze są znane.

## <a name="example"></a>Przykład

Następująca funkcja `count_primes_filter`, wykonuje to samo zadanie co funkcja `count_primes`. Jednak obiekt `transformer` w tej wersji używa funkcji filtru, aby akceptować tylko te wartości, które są podstawowe. Funkcja wykonująca akcję tylko otrzymuje numery podstawowe; w związku z tym nie musi wywoływać funkcji `is_prime`.

Ponieważ obiekt `transformer` otrzymuje tylko cyfry podstawowe, obiekt `transformer` może zawierać liczby pierwszych. Innymi słowy, obiekt `transformer` w tym przykładzie nie jest wymagany do dodawania numerów pierwszych do obiektu `vector`.

[!code-cpp[concrt-primes-filter#2](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_2.cpp)]

Obiekt `transformer` teraz przetwarza tylko te wartości, które są podstawowe. W poprzednim przykładzie `transformer` obiekt przetwarza wszystkie komunikaty. W związku z tym poprzedni przykład musi otrzymać taką samą liczbę wysyłanych komunikatów. W tym przykładzie jest używany wynik funkcji [concurrency:: Send](reference/concurrency-namespace-functions.md#send) , aby określić, ile komunikatów ma być odbieranych z obiektu `transformer`. Funkcja `send` zwraca **wartość true** , jeśli bufor komunikatów akceptuje komunikat i ma **wartość false** , gdy bufor komunikatów odrzuci komunikat. W związku z tym, ile razy bufor komunikatów akceptuje komunikat jest zgodny z liczbą pierwszych wartości.

## <a name="example"></a>Przykład

Poniższy kod przedstawia kompletny przykład. Przykład wywołuje zarówno funkcję `count_primes`, jak i funkcję `count_primes_filter`.

[!code-cpp[concrt-primes-filter#3](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_3.cpp)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `primes-filter.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **CL. exe/EHsc primes-Filter. cpp**

## <a name="robust-programming"></a>Skuteczne programowanie

Funkcja filtru może być funkcją lambda, wskaźnikiem funkcji lub obiektem funkcji. Każda funkcja filtru przyjmuje jedną z następujących form:

```Output
bool (T)
bool (T const &)
```

Aby wyeliminować niepotrzebne kopiowanie danych, należy użyć drugiego formularza w przypadku typu agregacji, który jest przesyłany przez wartość.

## <a name="see-also"></a>Zobacz też

[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Przewodnik: tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[Przewodnik: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[transformer, klasa](../../parallel/concrt/reference/transformer-class.md)
