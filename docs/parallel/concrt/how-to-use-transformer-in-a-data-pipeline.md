---
title: 'Porady: używanie transformatora w potoku danych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- transformer class, example
- data pipelines, using transformer [Concurrency Runtime]
- using transformer in data pipelines [Concurrency Runtime]
ms.assetid: ca49cb3f-4dab-4b09-a9c9-d3a109ae4c29
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c39491543c4d3a16202dac3caee50122ba0c7cf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403126"
---
# <a name="how-to-use-transformer-in-a-data-pipeline"></a>Porady: używanie transformatora w potoku danych

Ten temat zawiera przykład podstawowy, który pokazuje, jak używać [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) klasy w potoku danych. Aby uzyskać bardziej szczegółowy przykład, który używa potoku danych do przetwarzania obrazu, zobacz [wskazówki: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

*Przetwarzanie potokowe danych* jest to typowy wzorzec w programowanie współbieżne. Potok danych składa się z szeregu etapach, gdzie każdy z etapów wykonuje pracę, a następnie przekazuje wynikiem tej pracy do kolejnego etapu. `transformer` Klasy potoków kluczowym czynnikiem danych, ponieważ odbierze wartości wejściowej, wykonuje pracę na tę wartość i następnie produkuje wynik dla innego składnika do użycia.

## <a name="example"></a>Przykład

W tym przykładzie używa następujących potoku danych do wykonania szeregu przekształcenia, biorąc pod uwagę początkowej wartości wejściowej:

1. Pierwszy etap oblicza wartość bezwzględną liczby danych wejściowych.

1. Drugi etap oblicza pierwiastek kwadratowy danych wejściowych.

1. Trzeci etap oblicza kwadratowy danych wejściowych.

1. Do przodu etapu neguje dane wejściowe.

1. Piątym etapie zapisuje wynik końcowy do buforu komunikatu.

Na koniec przykład drukuje wynik potoku do konsoli.

[!code-cpp[concrt-data-pipeline#1](../../parallel/concrt/codesnippet/cpp/how-to-use-transformer-in-a-data-pipeline_1.cpp)]

Ten przykład generuje następujące wyniki:

```Output
The result is -42.
```

Powszechne jest wprowadzanie dla etapu w potoku danych do wyprowadzenia wartości, którego typ różni się od jego wartości wejściowej. W tym przykładzie drugiego etapu przyjmuje wartość typu `int` jako dane wejściowe i generuje pierwiastek kwadratowy wartości ( `double`) jako dane wyjściowe.

> [!NOTE]
>  Potok danych przedstawiony w tym przykładzie jest do celów informacyjnych. Ponieważ każda operacja transformacji wykonuje małego wysiłku, obciążenie wymagane do wykonywania przekazywania komunikatów mogą przeważyć zalety przy użyciu potoku danych.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `data-pipeline.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc danych pipeline.cpp**

## <a name="see-also"></a>Zobacz też

[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Przewodnik: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)

