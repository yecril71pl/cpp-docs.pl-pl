---
title: 'Instrukcje: Wysyłanie komunikatu w regularnych odstępach czasu'
ms.date: 11/04/2016
helpviewer_keywords:
- timer class, example
- sending messages at regular intervals [Concurrency Runtime]
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
ms.openlocfilehash: 0bf5f93e2a570761874232a88a23289e59e58d94
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257621"
---
# <a name="how-to-send-a-message-at-a-regular-interval"></a>Instrukcje: Wysyłanie komunikatu w regularnych odstępach czasu

W tym przykładzie pokazano, jak używać współbieżność::[timer, klasa](../../parallel/concrt/reference/timer-class.md) do wysyłania komunikatu w regularnych odstępach czasu.

## <a name="example"></a>Przykład

W poniższym przykładzie użyto `timer` obiektu raportować postęp długiej operacji. Ten przykład łącza `timer` obiekt [concurrency::call](../../parallel/concrt/reference/call-class.md) obiektu. `call` Obiektu wyświetla wskaźnik postępu do konsoli w regularnych odstępach czasu. [Concurrency::timer::start](reference/timer-class.md#start) metoda uruchamia czasomierz w kontekście oddzielne. `perform_lengthy_operation` Wywołaniach funkcji [concurrency::wait](reference/concurrency-namespace-functions.md#wait) funkcji w kontekście głównego, aby zasymulować czasochłonna operacja.

[!code-cpp[concrt-report-progress#1](../../parallel/concrt/codesnippet/cpp/how-to-send-a-message-at-a-regular-interval_1.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe:

```Output
Performing a lengthy operation..........done.
```

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `report-progress.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc raportu — progress.cpp**

## <a name="see-also"></a>Zobacz także

[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)
