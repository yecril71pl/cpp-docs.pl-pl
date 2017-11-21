---
title: "Porady: wysyłanie komunikatu w regularnych odstępach czasu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- timer class, example
- sending messages at regular intervals [Concurrency Runtime]
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c5c10ba2a1fee400ef99799c7c83a3bdcacd084f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-send-a-message-at-a-regular-interval"></a>Porady: wysyłanie komunikatu w regularnych odstępach czasu
Ten przykład przedstawia sposób użycia concurrency::[klasa czasomierza](../../parallel/concrt/reference/timer-class.md) do wysyłania komunikatu w regularnych odstępach czasu.  
  
## <a name="example"></a>Przykład  

 W poniższym przykładzie użyto `timer` obiektu w celu raportowania postępu podczas długotrwałej operacji. Ten przykład łącza `timer` do obiektu [concurrency::call](../../parallel/concrt/reference/call-class.md) obiektu. `call` Obiektu drukuje wskaźnik postępu do konsoli w regularnych odstępach czasu. [Concurrency::timer::start](reference/timer-class.md#start) — metoda uruchamia czasomierz na oddzielnych kontekstu. `perform_lengthy_operation` Wywołania funkcji [concurrency::wait](reference/concurrency-namespace-functions.md#wait) funkcji w kontekście głównym, aby symulować czasochłonna operacja.  

  
 [!code-cpp[concrt-report-progress#1](../../parallel/concrt/codesnippet/cpp/how-to-send-a-message-at-a-regular-interval_1.cpp)]  
  
 W tym przykładzie tworzy następujące przykładowe dane wyjściowe:  
  
```Output  
Performing a lengthy operation..........done.  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `report-progress.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc raport progress.cpp**  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)   
 [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)
