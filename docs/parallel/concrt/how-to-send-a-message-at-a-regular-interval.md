---
title: 'Porady: wysyłanie komunikatu w regularnych odstępach czasu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- timer class, example
- sending messages at regular intervals [Concurrency Runtime]
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3c476d9cf633ce9b676dc8f658c94bd0b240461
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384302"
---
# <a name="how-to-send-a-message-at-a-regular-interval"></a>Porady: wysyłanie komunikatu w regularnych odstępach czasu

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

## <a name="see-also"></a>Zobacz też

[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)
