---
title: 'Porady: zapewnianie funkcji pracy dla wywoływania oraz klasy transformatora'
ms.date: 11/04/2016
helpviewer_keywords:
- call class, example
- using the transformer class [Concurrency Runtime]
- using the call class [Concurrency Runtime]
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
ms.openlocfilehash: 4d2b7b3c88b51003a96526ef14d9940a8c26c3b3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142485"
---
# <a name="how-to-provide-work-functions-to-the-call-and-transformer-classes"></a>Porady: zapewnianie funkcji pracy dla wywoływania oraz klasy transformatora

W tym temacie przedstawiono kilka sposobów udostępniania funkcji roboczych do klas [concurrency:: Call](../../parallel/concrt/reference/call-class.md) i [concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) .

Pierwszy przykład pokazuje, jak przekazać wyrażenie lambda do obiektu `call`. Drugi przykład pokazuje, jak przekazać obiekt Function do obiektu `call`. Trzeci przykład pokazuje, jak powiązać metodę klasy z obiektem `call`.

W przypadku ilustracji każdy przykład w tym temacie używa klasy `call`. Aby zapoznać się z przykładem korzystającym z klasy `transformer`, zobacz [How to: use Transformer w potoku danych](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).

## <a name="example"></a>Przykład

Poniższy przykład przedstawia typowy sposób użycia klasy `call`. Ten przykład przekazuje funkcję lambda do konstruktora `call`.

[!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
13 squared is 169.
```

## <a name="example"></a>Przykład

Poniższy przykład przypomina poprzednią, z tą różnicą, że używa klasy `call` razem z obiektem funkcji (Funktor).

[!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]

## <a name="example"></a>Przykład

Poniższy przykład przypomina poprzednią, z tą różnicą, że używa funkcji [std:: bind1st —](../../standard-library/functional-functions.md#bind1st) i [std:: mem_fun](../../standard-library/functional-functions.md#mem_fun) , aby powiązać obiekt `call` z metodą klasy.

Użyj tej techniki, jeśli musisz powiązać obiekt `call` lub `transformer` z konkretną metodą klasy zamiast operatora wywołania funkcji, `operator()`.

[!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]

Można również przypisać wynik funkcji `bind1st` do obiektu [funkcji std:: Function](../../standard-library/function-class.md) lub użyć słowa kluczowego `auto`, jak pokazano w poniższym przykładzie.

[!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `call.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **CL. exe/EHsc. cpp**

## <a name="see-also"></a>Zobacz też

[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Instrukcje: używanie transformatora w potoku danych](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br/>
[call, klasa](../../parallel/concrt/reference/call-class.md)<br/>
[transformer, klasa](../../parallel/concrt/reference/transformer-class.md)
