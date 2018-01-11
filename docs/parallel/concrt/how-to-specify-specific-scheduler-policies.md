---
title: "Porady: Określanie specjalnych zasad harmonogramu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- specifying scheduler policies [Concurrency Runtime]
- scheduler policies, specifying [Concurrency Runtime]
ms.assetid: 9c5149f9-ac34-4ff3-9e79-0bad103e4e6b
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: af30b38a89eb7e4b50c7d31be2d3ba6572843b1e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-specify-specific-scheduler-policies"></a>Porady: określanie specjalnych zasad harmonogramu
Zasady harmonogramu umożliwiają sprawowanie kontroli nad strategii, używany w harmonogramie podczas zarządzania zadaniami. W tym temacie pokazano, jak używać zasad harmonogramu umożliwia podwyższenie priorytetu wątku zadania drukuje wskaźnik postępu do konsoli.  
  
 Na przykład korzystający z zasad harmonogramu niestandardowego wraz z agentów asynchronicznych zobacz [porady: tworzenie agentów tej zasady użycia określonego harmonogramu](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje dwie czynności równoległe. Pierwszym zadaniem oblicza n<sup>th</sup> Fibonacci numer. Drugie zadanie drukuje wskaźnik postępu do konsoli.  
  
 Pierwszym zadaniem używa dekompozycji cykliczne do wyliczenia numer Fibonacci. Oznacza to rekursywnie każdego zadania tworzy podzadania do obliczenia ogólnej wynik. Zadanie, które używa dekompozycji cykliczne może korzystać ze wszystkich dostępnych zasobów, a tym samym blokować go, inne zadania. W tym przykładzie zadanie, które wyświetla wskaźnik postępu może nie odbierać szybki dostęp do zasobów obliczeniowych.  
  
 Aby zapewnić zadanie, które wyświetla postęp komunikat odpowiedniego dostępu do zasobów obliczeniowych, w tym przykładzie użyto kroków opisanych w [porady: Zarządzanie wystąpieniem harmonogramu](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) do utworzenia wystąpienia harmonogram ma zasady niestandardowe. Zasady niestandardowe określa priorytet wątku jako najwyższy priorytet.  
  
 W tym przykładzie użyto [concurrency::call](../../parallel/concrt/reference/call-class.md) i [concurrency::timer](../../parallel/concrt/reference/timer-class.md) klasy do drukowania wskaźnik postępu. Te klasy mają wersji ich konstruktorów przyjmujących odwołanie do [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) obiekt, który planuje je. W przykładzie użyto domyślnego harmonogramu, można zaplanować zadanie, które oblicza liczbę Fibonacci i wystąpieniem harmonogramu, można zaplanować zadanie, które wyświetla wskaźnik postępu.  
  
 Aby zilustrować korzyści wynikające ze stosowania harmonogramu, która ma zasady niestandardowe, w tym przykładzie wykonuje zadanie ogólną dwa razy. W przykładzie użyto najpierw harmonogramu domyślne można zaplanować obu zadań. W przykładzie użyto następnie harmonogramu domyślne można zaplanować pierwszego zadania i harmonogramu, która ma zasad niestandardowych do zaplanowania zadania drugiego.  
  
 [!code-cpp[concrt-scheduler-policy#1](../../parallel/concrt/codesnippet/cpp/how-to-specify-specific-scheduler-policies_1.cpp)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
```Output  
Default scheduler:  
...........................................................................done  
Scheduler that has a custom policy:  
...........................................................................done  
```  
  
 Mimo że oba zestawy zadania tworzenia takiego samego wyniku, wersji, która używa niestandardowych zasad włącza zadanie, które wyświetla wskaźnik postępu uruchomienie priorytetem z podwyższonym poziomem uprawnień, tak aby bardziej responsively działa.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `scheduler-policy.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc harmonogramu policy.cpp**  
  
## <a name="see-also"></a>Zobacz też  
 [Zasady harmonogramu](../../parallel/concrt/scheduler-policies.md)   
 [Porady: Zarządzanie przypadkiem Planisty](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)   
 [Instrukcje: tworzenie agentów korzystających ze specjalnych zasad harmonogramu](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)

