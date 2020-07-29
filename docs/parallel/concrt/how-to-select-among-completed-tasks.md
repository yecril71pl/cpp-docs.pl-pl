---
title: 'Porady: wybieranie spośród zadań wykonanych'
ms.date: 11/04/2016
helpviewer_keywords:
- selecting among completed tasks [Concurrency Runtime]
- completed tasks, selecting among [Concurrency Runtime]
ms.assetid: c8ccc160-043f-4599-847b-32ed270bb257
ms.openlocfilehash: fd9940dad0cd2f202bdc734a81a7eb37cd79420c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226727"
---
# <a name="how-to-select-among-completed-tasks"></a>Porady: wybieranie spośród zadań wykonanych

Ten przykład pokazuje, jak używać klas [concurrency:: Choice](../../parallel/concrt/reference/choice-class.md) i [concurrency:: join](../../parallel/concrt/reference/join-class.md) , aby wybrać pierwsze zadanie do ukończenia algorytmu wyszukiwania.

## <a name="example"></a>Przykład

Poniższy przykład wykonuje równolegle dwa algorytmy wyszukiwania i wybiera pierwszy algorytm do wykonania. Ten przykład definiuje `employee` Typ, który zawiera identyfikator liczbowy i wynagrodzenie dla pracownika. `find_employee`Funkcja znajduje pierwszego pracownika, który ma podany identyfikator lub wynagrodzenie. `find_employee`Funkcja obsługuje również przypadek, w którym żaden pracownik nie ma podanego identyfikatora lub wynagrodzenia. `wmain`Funkcja tworzy tablicę `employee` obiektów i wyszukuje kilka wartości identyfikatorów i wynagrodzeń.

W przykładzie zastosowano `choice` obiekt, aby wybrać spośród następujących przypadków:

1. Pracownik, który ma podany identyfikator istnieje.

1. Istnieje pracownik, który ma podane wynagrodzenie.

1. Nie istnieje pracownik, który ma podany identyfikator lub wynagrodzenie.

W przypadku pierwszych dwóch przypadków w przykładzie używany jest obiekt [concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) do przechowywania identyfikatora i innego `single_assignment` obiektu do przechowywania wynagrodzenia. W przykładzie zastosowano `join` obiekt dla trzeciego przypadku. `join`Obiekt składa się z dwóch dodatkowych `single_assignment` obiektów, jeden w przypadku, gdy nie istnieje pracownik, który ma podany identyfikator, i jeden dla przypadku, gdy nie istnieje pracownik, który ma podane wynagrodzenie. `join`Obiekt wysyła komunikat, gdy każdy z jego członków odbiera komunikat. W tym przykładzie `join` obiekt wysyła komunikat, gdy nie istnieje pracownik, który ma podany identyfikator lub wynagrodzenie.

W przykładzie używany jest obiekt [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) do uruchamiania jednocześnie obu algorytmów wyszukiwania. Każde zadanie wyszukiwania zapisuje w jednym z `single_assignment` obiektów, aby wskazać, czy dany pracownik istnieje. W przykładzie zastosowano funkcję [concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) , aby uzyskać indeks pierwszego buforu zawierającego komunikat i blok służący **`switch`** do drukowania wyniku.

[!code-cpp[concrt-find-employee#1](../../parallel/concrt/codesnippet/cpp/how-to-select-among-completed-tasks_1.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
Employee with id 14758 has salary 27780.00.
Employee with salary 29150.00 has id 84345.
Employee with id 61935 has salary 29905.00.
No employee has id 899 or salary 31223.00.
```

W tym przykładzie używana jest funkcja pomocnika [concurrency:: make_choice](reference/concurrency-namespace-functions.md#make_choice) do tworzenia `choice` obiektów i funkcji pomocnika [concurrency:: make_join](reference/concurrency-namespace-functions.md#make_join) do tworzenia `join` obiektów.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie, `find-employee.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **cl.exe/EHsc Find-Employee. cpp**

## <a name="see-also"></a>Zobacz także

[Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)<br/>
[Choice — Klasa](../../parallel/concrt/reference/choice-class.md)<br/>
[join — Klasa](../../parallel/concrt/reference/join-class.md)
