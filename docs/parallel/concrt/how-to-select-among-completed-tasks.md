---
title: 'Instrukcje: Wybieranie spośród zadań wykonanych'
ms.date: 11/04/2016
helpviewer_keywords:
- selecting among completed tasks [Concurrency Runtime]
- completed tasks, selecting among [Concurrency Runtime]
ms.assetid: c8ccc160-043f-4599-847b-32ed270bb257
ms.openlocfilehash: 0d31f9bd16aaa70cc773e60e4f1193e66ec520f0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278031"
---
# <a name="how-to-select-among-completed-tasks"></a>Instrukcje: Wybieranie spośród zadań wykonanych

W tym przykładzie pokazano, jak używać [concurrency::choice](../../parallel/concrt/reference/choice-class.md) i [concurrency::join](../../parallel/concrt/reference/join-class.md) klasy zaznacz pierwsze zadanie do wykonania algorytmu wyszukiwania.

## <a name="example"></a>Przykład

Poniższy przykład wykonuje dwa algorytmy wyszukiwania i wybiera pierwszy algorytmu do ukończenia. Ten przykład definiuje `employee` typ, który zawiera identyfikator liczbowy i wynagrodzenia dla pracownika. `find_employee` Funkcja znajdzie pierwszy pracownika, który został podany identyfikator lub podany wynagrodzenia. `find_employee` Funkcji również obsługuje przypadek, w którym nie pracownik ma podany identyfikator lub wynagrodzenia. `wmain` Funkcja tworzy tablicę `employee` obiektów i wyszukuje kilka wartości identyfikatora i wynagrodzenia.

W przykładzie użyto `choice` obiektu, aby wybrać spośród następujących przypadkach:

1. Istnieje pracownika, który został podany identyfikator.

1. Istnieje pracownika, który został podany wynagrodzenia.

1. Nie istnieje żadne pracownika, który został podany identyfikator lub wynagrodzenia.

Pierwsze dwa przypadki, w przykładzie użyto [concurrency::single_assignment](../../parallel/concrt/reference/single-assignment-class.md) obiekt do przechowywania identyfikatora, a drugi `single_assignment` obiekt do przechowywania wynagrodzenia. W przykładzie użyto `join` obiektu w przypadku trzeciej. `join` Obiekt składa się z dwóch dodatkowych `single_assignment` obiektów: jeden dla przypadku, gdy istnieje nie pracownika, który został podany identyfikator i jeden dla przypadku, gdy istnieje nie pracownika, który został podany wynagrodzenia. `join` Obiektu wysyła komunikat, gdy każdy z jej członków odbiera komunikat. W tym przykładzie `join` obiektu wysyła komunikat informujący o tym, gdy nie pracownika, który został podany identyfikator lub istnieje wynagrodzenia.

W przykładzie użyto [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) obiektu do równoległego uruchamiania obu algorytmów wyszukiwania. Każde zadanie wyszukiwania zapisuje dane w jednym z `single_assignment` obiektów, aby wskazać, czy istnieje danego pracownika. W przykładzie użyto [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkcji w celu uzyskania indeksu pierwszego buforu, który zawiera komunikat i `switch` bloku, aby wydrukować wynik.

[!code-cpp[concrt-find-employee#1](../../parallel/concrt/codesnippet/cpp/how-to-select-among-completed-tasks_1.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
Employee with id 14758 has salary 27780.00.
Employee with salary 29150.00 has id 84345.
Employee with id 61935 has salary 29905.00.
No employee has id 899 or salary 31223.00.
```

W tym przykładzie użyto [concurrency::make_choice](reference/concurrency-namespace-functions.md#make_choice) funkcja pomocnika służąca do tworzenia `choice` obiektów i [concurrency::make_join](reference/concurrency-namespace-functions.md#make_join) funkcja pomocnika służąca do tworzenia `join` obiektów.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `find-employee.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Znajdź employee.cpp dla cl.exe/ehsc**

## <a name="see-also"></a>Zobacz także

[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)<br/>
[choice, klasa](../../parallel/concrt/reference/choice-class.md)<br/>
[join, klasa](../../parallel/concrt/reference/join-class.md)
