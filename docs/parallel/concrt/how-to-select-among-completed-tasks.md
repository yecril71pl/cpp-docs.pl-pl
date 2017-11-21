---
title: "Porady: Wybieranie spośród zadań wykonanych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- selecting among completed tasks [Concurrency Runtime]
- completed tasks, selecting among [Concurrency Runtime]
ms.assetid: c8ccc160-043f-4599-847b-32ed270bb257
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a36e871c8cea0a1ed16362ab7d8683151fe17825
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-select-among-completed-tasks"></a>Porady: wybieranie spośród zadań wykonanych
Ten przykład przedstawia sposób użycia [concurrency::choice](../../parallel/concrt/reference/choice-class.md) i [concurrency::join](../../parallel/concrt/reference/join-class.md) klasy do wybrania pierwszego zadania do wykonania algorytmu wyszukiwania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie wykonuje dwa algorytmy wyszukiwania równolegle i wybiera pierwszy algorytm, aby zakończyć. W tym przykładzie definiuje `employee` typu, który zawiera identyfikator numeryczny i wynagrodzenie dla pracowników. `find_employee` Funkcja znajduje pierwszy pracownika, który ma podany identyfikator lub podana wynagrodzenia. `find_employee` Funkcja obsługi przez przypadek, lecz żaden pracownik nie ma podanego identyfikatora lub wynagrodzenia. `wmain` Funkcja tworzy tablicę `employee` obiektów i wyszukuje kilka wartości identyfikatora i wynagrodzenia.  
  
 W przykładzie użyto `choice` obiektu, aby wybrać spośród następujących przypadkach:  
  
1.  Istnieje pracownika, który ma podany identyfikator.  
  
2.  Istnieje pracownika, który ma podany wynagrodzenia.  
  
3.  Nie ma podanego identyfikatora lub wynagrodzenie pracownika nie istnieje.  
  
 Dla dwóch pierwszych przypadkach w przykładzie użyto [concurrency::single_assignment](../../parallel/concrt/reference/single-assignment-class.md) obiekt przechowujący identyfikator i drugą `single_assignment` obiektu do przechowywania wynagrodzenia. W przykładzie użyto `join` obiektu w przypadku trzecich. `join` Obiekt składa się z dwóch dodatkowych `single_assignment` obiektów: jeden dla przypadku, gdy istnieje nie pracownika, który ma podany identyfikator i jeden dla przypadku, gdy istnieje nie pracownika, który ma podany wynagrodzenia. `join` Obiekt wysyła komunikat wszystkich członków odebrania wiadomości. W tym przykładzie `join` obiekt wysyła wiadomość, gdy pracownik nie został podany identyfikator lub wynagrodzenie nie istnieje.  
  
 W przykładzie użyto [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) obiektu do uruchomienia obu algorytmów wyszukiwania równoległego. Każde zadanie wyszukiwania zapisuje dane w jednym z `single_assignment` obiektów, aby wskazać, czy istnieje danego pracownika. W przykładzie użyto [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkcji, aby uzyskać indeks pierwszego buforu, który zawiera komunikat i `switch` bloku, aby wydrukować wynik.  
  
 [!code-cpp[concrt-find-employee#1](../../parallel/concrt/codesnippet/cpp/how-to-select-among-completed-tasks_1.cpp)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
```Output  
Employee with id 14758 has salary 27780.00.  
Employee with salary 29150.00 has id 84345.  
Employee with id 61935 has salary 29905.00.  
No employee has id 899 or salary 31223.00.  
```  
  
 W tym przykładzie użyto [concurrency::make_choice](reference/concurrency-namespace-functions.md#make_choice) funkcja pomocnika służąca do tworzenia `choice` obiektów i [concurrency::make_join](reference/concurrency-namespace-functions.md#make_join) funkcja pomocnika służąca do tworzenia `join` obiektów.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `find-employee.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Znajdź/ehsc cl.exe-employee.cpp**  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md)   
 [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Funkcje przekazywania komunikatów](../../parallel/concrt/message-passing-functions.md)   
 [Klasa wyboru](../../parallel/concrt/reference/choice-class.md)   
 [JOIN — klasa](../../parallel/concrt/reference/join-class.md)
