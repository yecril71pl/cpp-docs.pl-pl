---
title: 'Instrukcje: Zapewnianie funkcji pracy wywoływania oraz klasy transformatora'
ms.date: 11/04/2016
helpviewer_keywords:
- call class, example
- using the transformer class [Concurrency Runtime]
- using the call class [Concurrency Runtime]
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
ms.openlocfilehash: c41c29dae277105f268171503e662e2a02e3857e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57277694"
---
# <a name="how-to-provide-work-functions-to-the-call-and-transformer-classes"></a>Instrukcje: Zapewnianie funkcji pracy wywoływania oraz klasy transformatora

W tym temacie przedstawiono kilka sposobów zapewnianie funkcji pracy do [concurrency::call](../../parallel/concrt/reference/call-class.md) i [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) klasy.

Pierwszy przykład przedstawia sposób przekazania wyrażenia lambda do `call` obiektu. Drugi przykład pokazuje, jak przekazać obiekt funkcji `call` obiektu. Trzeci przykład pokazuje jak powiązać metodę klasy `call` obiektu.

Do celów informacyjnych, co w tym temacie przykładzie `call` klasy. Aby uzyskać przykład, który używa `transformer` klasy, zobacz [jak: Używanie transformatora w potoku danych](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono typowe sposób używania `call` klasy. Ten przykład przekazuje funkcję lambda, która ma `call` konstruktora.

[!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
13 squared is 169.
```

## <a name="example"></a>Przykład

Poniższy przykład przypomina poprzedni, z tą różnicą, że używa `call` klasy wraz z obiekt funkcyjny (funktor).

[!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]

## <a name="example"></a>Przykład

Poniższy przykład przypomina poprzedni, z tą różnicą, że używa [std::bind1st](../../standard-library/functional-functions.md#bind1st) i [std::mem_fun](../../standard-library/functional-functions.md#mem_fun) funkcje, które można powiązać `call` obiekt do metody klasy.

Użyj tej techniki, jeśli zajdzie potrzeba powiązać `call` lub `transformer` obiektu do metody określonej klasy zamiast operatora wywołania funkcji `operator()`.

[!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]

Można także przypisać wynik `bind1st` funkcja [std::function](../../standard-library/function-class.md) obiektu lub użyj `auto` — słowo kluczowe, jak pokazano w poniższym przykładzie.

[!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `call.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc call.cpp**

## <a name="see-also"></a>Zobacz także

[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Instrukcje: używanie transformatora w potoku danych](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br/>
[call, klasa](../../parallel/concrt/reference/call-class.md)<br/>
[transformer, klasa](../../parallel/concrt/reference/transformer-class.md)
