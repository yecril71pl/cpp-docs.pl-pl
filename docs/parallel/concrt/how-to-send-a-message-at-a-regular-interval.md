---
title: 'Porady: wysyłanie komunikatu w regularnych odstępach czasu'
ms.date: 11/04/2016
helpviewer_keywords:
- timer class, example
- sending messages at regular intervals [Concurrency Runtime]
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
ms.openlocfilehash: c51a5cab6fcae5eb45b9d9b54c0dad8e8ec393b2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142462"
---
# <a name="how-to-send-a-message-at-a-regular-interval"></a>Porady: wysyłanie komunikatu w regularnych odstępach czasu

Ten przykład pokazuje, jak używać klasy concurrency::[Timer](../../parallel/concrt/reference/timer-class.md) do wysyłania komunikatu w regularnych odstępach czasu.

## <a name="example"></a>Przykład

Poniższy przykład używa obiektu `timer` do raportowania postępu podczas długotrwałej operacji. Ten przykład łączy obiekt `timer` do obiektu [concurrency:: Call](../../parallel/concrt/reference/call-class.md) . Obiekt `call` drukuje wskaźnik postępu do konsoli w regularnych odstępach czasu. Metoda [concurrency:: Timer:: Start](reference/timer-class.md#start) uruchamia czasomierz w oddzielnym kontekście. Funkcja `perform_lengthy_operation` wywołuje funkcję [concurrency:: wait](reference/concurrency-namespace-functions.md#wait) w głównym kontekście w celu symulowania czasochłonnej operacji.

[!code-cpp[concrt-report-progress#1](../../parallel/concrt/codesnippet/cpp/how-to-send-a-message-at-a-regular-interval_1.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe:

```Output
Performing a lengthy operation..........done.
```

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `report-progress.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **CL. exe/EHsc Report-Progress. cpp**

## <a name="see-also"></a>Zobacz też

[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)
