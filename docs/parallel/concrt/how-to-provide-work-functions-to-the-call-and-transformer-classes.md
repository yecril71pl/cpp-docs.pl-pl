---
title: 'Porady: zapewnianie funkcji pracy wywoływania oraz klasy transformatora | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- call class, example
- using the transformer class [Concurrency Runtime]
- using the call class [Concurrency Runtime]
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca7948a1258ac1b5193d379dd37f426360edc42e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687195"
---
# <a name="how-to-provide-work-functions-to-the-call-and-transformer-classes"></a>Porady: zapewnianie funkcji pracy dla wywoływania oraz klasy transformatora
W tym temacie przedstawiono kilka sposobów zapewnianie funkcji pracy do [concurrency::call](../../parallel/concrt/reference/call-class.md) i [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) klasy.  
  
 W pierwszym przykładzie przedstawiono sposób do przekazania wyrażenia lambda do `call` obiektu. Drugim przykładzie pokazano, jak przekazać obiekt funkcji do `call` obiektu. Trzeci przykładzie pokazano, jak można powiązać metodę klasy `call` obiektu.  
  
 Na ilustracji, co przykładzie, w tym temacie użyto `call` klasy. Na przykład, który używa `transformer` , zobacz [porady: używanie transformatora w potoku danych](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono typowy sposób używania `call` klasy. W tym przykładzie przekazuje funkcja lambda `call` konstruktora.  
  
 [!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
```Output  
13 squared is 169.  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przypomina poprzedni, z wyjątkiem tego, że używa `call` klasy wraz z obiektem funkcji (obiekt).  
  
 [!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]  
  
## <a name="example"></a>Przykład  

 Poniższy przykład przypomina poprzedni, z wyjątkiem tego, że używa [std::bind1st](../../standard-library/functional-functions.md#bind1st) i [std::mem_fun](../../standard-library/functional-functions.md#mem_fun) funkcje powiązać `call` obiektu do metody klasy.  

  
 Użyj tej metody, jeśli masz powiązać `call` lub `transformer` obiektu do metody określonej klasy zamiast operator wywołania funkcji, `operator()`.  
  
 [!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]  
  
 Można także przypisać wynik `bind1st` funkcja [std::function](../../standard-library/function-class.md) obiektu lub użyj `auto` — słowo kluczowe, jak pokazano w poniższym przykładzie.  
  
 [!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `call.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe call.cpp/ehsc**  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)   
 [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Porady: używanie transformatora w potoku danych](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)   
 [Call — klasa](../../parallel/concrt/reference/call-class.md)   
 [transformer, klasa](../../parallel/concrt/reference/transformer-class.md)
