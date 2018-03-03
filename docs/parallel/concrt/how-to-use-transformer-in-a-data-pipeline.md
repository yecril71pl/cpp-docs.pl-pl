---
title: "Porady: używanie transformatora w potoku danych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- transformer class, example
- data pipelines, using transformer [Concurrency Runtime]
- using transformer in data pipelines [Concurrency Runtime]
ms.assetid: ca49cb3f-4dab-4b09-a9c9-d3a109ae4c29
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 76c8a50bd5a58d9fe6e4a68f05d9732e50fd04e8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-transformer-in-a-data-pipeline"></a>Porady: używanie transformatora w potoku danych
Ten temat zawiera podstawowe przykładzie, który przedstawia sposób użycia [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) klasy w potoku danych. Aby uzyskać bardziej szczegółowy przykład potoku danych używaną do przetwarzania obrazu, zobacz [wskazówki: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).  
  
 *Przetwarzanie potokowe danych* jest wspólnego wzorca w programowaniu współbieżnych. Potok danych składa się z szeregu etapach, gdzie na każdym z etapów wykonuje pracę, a następnie przekazuje jego wynik tej pracy do kolejnego etapu. `transformer` Klasy potoków kluczowym czynnikiem danych, ponieważ odbierze wartości wejściowej, przeprowadza pracę na tę wartość, a następnie powstaje innego składnika do użycia.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto następujących potoku danych można wykonać kilka przekształceń podane początkowej wartości wejściowej:  
  
1.  Pierwszym etapem oblicza wartość bezwzględna jej danych wejściowych.  
  
2.  Drugi etap oblicza pierwiastek kwadratowy jej danych wejściowych.  
  
3.  Trzeci etap oblicza kwadrat jej danych wejściowych.  
  
4.  Określonymi etap Negacja jej danych wejściowych.  
  
5.  Piątym etapie zapisuje wynik końcowy buforu komunikatu.  
  
 Na koniec przykładzie drukowanie wyników dla potoku do konsoli.  
  
 [!code-cpp[concrt-data-pipeline#1](../../parallel/concrt/codesnippet/cpp/how-to-use-transformer-in-a-data-pipeline_1.cpp)]  
  
 Ten przykład generuje następujące wyniki:  
  
```Output  
The result is -42.  
```  
  
 Jest typowe dla etapu w potoku danych zwracać wartość, której typ różni się od jego wartości wejściowej. W tym przykładzie drugiego etapu przyjmuje wartość typu `int` jako dane wejściowe i tworzy pierwiastek kwadratowy wartości ( `double`) jako dane wyjściowe.  
  
> [!NOTE]
>  Potoki danych w tym przykładzie jest ilustracyjną. Ponieważ każdej operacji przekształcania wykonuje małego wysiłku, obciążenie wymagane do przeprowadzenia przekazywania wiadomości mogą przeważają korzyści wynikające ze stosowania potoku danych.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `data-pipeline.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc danych pipeline.cpp**  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)   
 [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Przewodnik: tworzenie sieci przetwarzania obrazów](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)

