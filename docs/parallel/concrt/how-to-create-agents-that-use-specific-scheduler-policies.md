---
title: 'Porady: tworzenie agentów korzystających ze specjalnych zasad harmonogramu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scheduler policies, agents [Concurrency Runtime]
- creating agents that use specific policies [Concurrency Runtime]
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9efa40d24ed4eaee5b9fd3995a4cf9ed696eb39a
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-create-agents-that-use-specific-scheduler-policies"></a>Porady: tworzenie agentów korzystających ze specjalnych zasad harmonogramu
Agent jest składnik aplikacji, które asynchronicznie współdziała z innymi składnikami rozwiązać większych zadań. Agent zwykle ma ustawione cyklu życia i zachowuje swój stan.  
  
 Każdy agent mogą mieć wymagania aplikacji. Na przykład agenta, który umożliwia interakcji z użytkownikiem (Pobieranie danych wejściowych lub wyświetlanie) może wymagać wyższy priorytet dostępu do zasobów obliczeniowych. Zasady harmonogramu umożliwiają sprawowanie kontroli nad strategii, używany w harmonogramie podczas zarządzania zadaniami. W tym temacie przedstawiono tworzenie agentów korzystających ze specjalnych zasad harmonogramu.  
  
 Na przykład podstawowa korzystający z zasad harmonogramu niestandardowego wraz z bloki komunikatów asynchronicznych, zobacz [porady: Określanie zasad harmonogramu określonych](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).  
  
 W tym temacie używa funkcji z asynchronicznego biblioteki agentów, takie jak agentów, bloki komunikatów i funkcje przekazywania komunikatów do wykonywania pracy. Aby uzyskać więcej informacji na temat biblioteki agentów asynchronicznych, zobacz [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano dwie klasy, które pochodzą z [concurrency::agent](../../parallel/concrt/reference/agent-class.md): `permutor` i `printer`. `permutor` Klasy oblicza permutacji wszystkich podanego ciągu wejściowego. `printer` Klasy drukuje wiadomości dotyczące postępu do konsoli. `permutor` Klasa wykonuje operację praktyce intensywnie, którego może używać wszystkich dostępnych zasobów obliczeniowych. Powinna być użyteczna, `printer` klasy wydrukuj każdego komunikatu o postępie w odpowiednim czasie.  
  
 Zapewnienie `printer` klasy odpowiedniego dostępu do zasobów obliczeniowych, w tym przykładzie użyto kroków opisanych w [porady: Zarządzanie przypadkiem Planisty](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) do utworzenia wystąpienia harmonogram ma zasady niestandardowe. Zasady niestandardowe określa priorytet wątku jako najwyższy priorytet.  
  
 Aby zilustrować korzyści wynikające ze stosowania harmonogramu, która ma zasady niestandardowe, w tym przykładzie wykonuje zadanie ogólną dwa razy. W przykładzie użyto najpierw harmonogramu domyślne można zaplanować obu zadań. Następnie w przykładzie użyto domyślnego harmonogramu można zaplanować `permutor` obiekt i harmonogramu, która ma zasady niestandardowe można zaplanować `printer` obiektu.  
  
 [!code-cpp[concrt-permute-strings#1](../../parallel/concrt/codesnippet/cpp/how-to-create-agents-that-use-specific-scheduler-policies_1.cpp)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
```Output  
With default scheduler:  
Computing all permutations of 'Grapefruit'...  
100% complete...  
 
With higher context priority:  
Computing all permutations of 'Grapefruit'...  
100% complete...  
```  
  
 Mimo że oba zestawy zadania tworzenia takiego samego wyniku, wersji, która używa niestandardowych zasad umożliwia `printer` obiektu uruchomienie priorytetem z podwyższonym poziomem uprawnień, tak aby bardziej responsively działa.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `permute-strings.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **permute — / ehsc cl.exe-strings.cpp**  
  
## <a name="see-also"></a>Zobacz też  
 [Zasady harmonogramu](../../parallel/concrt/scheduler-policies.md)   
 [Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)   
 

