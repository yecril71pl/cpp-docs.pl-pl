---
title: "Wskazówki: Debugowanie projektu (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- projects [C++], debugging
- project debugging [C++]
- debugging projects
ms.assetid: a5cade77-ba51-4b03-a7a0-6897e3cd6a59
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ec7a363d3aa4601e33e44d15fbb3d667c3a87db4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-debugging-a-project-c"></a>Wskazówki: debugowanie projektu (C++)
W tym przewodniku możesz zmodyfikować program, aby rozwiązać ten problem, który wykryte podczas testowania projektu.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
-   W tym przewodniku przyjęto założenie, że rozumiesz podstawowe informacje na temat języka C++.  
  
-   Założono również, że zostały wykonane wcześniej powiązane wskazówki, które są wymienione w [za pomocą środowiska IDE programu Visual Studio dla programowania w języku C++ pulpitu](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
### <a name="to-fix-a-program-that-has-a-bug"></a>Aby naprawić program, który ma usterki  
  
1.  Aby wyświetlić zdarzenia występujące podczas `Cardgame` obiekt zostanie zniszczony, wyświetlanie destruktor dla elementu `Cardgame` klasy.  
  
     Na pasku menu wybierz **widoku**, **widoku klasy**.  
  
     W **widoku klasy** okna, rozwiń węzeł **gry** drzewa projektu i wybierz **Cardgame** klasę, aby wyświetlić elementy członkowskie klasy i metody.  
  
     Otwórz menu skrótów **~Cardgame(void)** destruktora, a następnie wybierz **przejdź do definicji**.  
  
2.  Aby zmniejszyć `totalParticipants` gdy zakończenie Cardgame, Dodaj następujący kod pomiędzy otwierającym, a klamrowe nawiasy zamykające z `Cardgame::~Cardgame` destruktora.  
  
     [!code-cpp[NVC_Walkthrough_Debugging_A_Project#110](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_1.cpp)]  
  
3.  Plik Cardgame.cpp powinien wyglądać następująco po zmianie jej:  
  
     [!code-cpp[NVC_Walkthrough_Debugging_A_Project#111](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_2.cpp)]  
  
4.  Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
5.  Po zakończeniu kompilacji, uruchom go w trybie debugowania, wybierając **debugowania**, **Rozpocznij debugowanie** paska menu lub wybierając klawisz F5. Wstrzymuje program w pierwszej punktu przerwania.  
  
6.  Do wykonania kroków opisanych programu, na pasku menu wybierz **debugowania**, **Step Over**, lub wybierz klawisz F10.  
  
     Zwróć uwagę, że po wykonaniu każdego konstruktora Cardgame, wartość `totalParticipants` zwiększa. Gdy `PlayGames` funkcja zwraca, każde wystąpienie Cardgame wykracza poza zakres i zostanie usunięta (i nosi nazwę destruktor), `totalParticipants` zmniejsza. Tuż przed `return` instrukcja jest wykonywana, `totalParticipants` jest równe 0.  
  
7.  Kontynuować krokowe wykonywanie programu aż do jej zakończenia lub pozwolić na jego uruchomienia, wybierając **debugowania**, **Uruchom** paska menu lub wybierając klawisz F5.  
  
## <a name="next-steps"></a>Następne kroki  
 **Poprzedni:** [wskazówki: Testowanie projektu (C++)](../ide/walkthrough-testing-a-project-cpp.md) &#124; **Dalej:**[wskazówki: Wdrażanie Twojego programu (C++)](../ide/walkthrough-deploying-your-program-cpp.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)