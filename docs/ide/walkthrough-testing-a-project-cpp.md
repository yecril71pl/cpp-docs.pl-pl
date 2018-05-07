---
title: 'Wskazówki: Testowanie projektu (C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- project testing [C++]
- testing projects
- projects [C++], testing
ms.assetid: 88cdd377-c5c8-4201-889d-32f5653ebead
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a9455fa9bf3c9f903f5018a1263978913aa35b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-testing-a-project-c"></a>Wskazówki: testowanie projektu (C++)
Jeśli program jest uruchomiony w trybie debugowania, można użyć punktów przerwania, aby wstrzymać program, aby sprawdzić stan zmiennych i obiektów.  
  
 W tym przewodniku Obejrzyj wartość zmiennej, jak program zostanie uruchomiony i ustalić, dlaczego wartość jest inna niż oczekiwana.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
-   W tym przewodniku przyjęto założenie, że rozumiesz podstawowe informacje na temat języka C++.  
  
-   Założono również, że zostały wykonane wcześniej powiązane wskazówki, które są wymienione w [za pomocą środowiska IDE programu Visual Studio dla programowania w języku C++ pulpitu](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
### <a name="to-run-a-program-in-debug-mode"></a>Aby uruchomić program w trybie debugowania  
  
1.  TestGames.cpp należy otworzyć do edycji.  
  
2.  Wybierz ten wiersz kodu:  
  
     `Cardgame.solitaire(1);`  
  
3.  Aby ustawić punkt przerwania w tym wierszu, na pasku menu wybierz **debugowania**, **Przełącz punkt przerwania**, lub wybierz klawisz F9. Czerwone koło pojawia się po lewej linii; oznacza to, że punkt przerwania jest ustawiony. Aby usunąć punkt przerwania, można wybrać polecenia menu lub klawisz F9 ponownie.  
  
     Jeśli używasz myszy, możesz również ustawić lub usunąć punkt przerwania, klikając na lewym marginesie.  
  
4.  Na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie**, lub wybierz klawisz F5.  
  
     Gdy program osiągnie wiersza, który ma punkt przerwania, wykonanie tymczasowego zatrzymania, ponieważ program jest w trybie przerwania. Żółta strzałka w lewo wiersz kodu oznacza, że jest następnego wiersza do wykonania.  
  
5.  Aby sprawdzić wartość `Cardgame::totalParticipants` zmiennej, przesuń wskaźnik myszy nad `Cardgame` , a następnie przenieś nad formantem rozszerzenia w lewej części okna etykietki narzędzia. Nazwa zmiennej `totalParticipants` i jego wartość 12 są wyświetlane.  
  
     Otwórz menu skrótów `Cardgame::totalParticipants` zmiennej, a następnie wybierz **Dodaj wyrażenie kontrolne** do wyświetlenia tej zmiennej w **1 czujki** okna. Można również wybrać zmienną i przeciągnij go na **1 czujki** okna.  
  
6.  Aby wkraczać do następnego wiersza kodu, na pasku menu wybierz **debugowania**, **Step Over**, lub wybierz klawisz F10.  
  
     Wartość `Cardgame::totalParticipants` w **1 czujki** okna jest teraz wyświetlany jako 13.  
  
7.  Otwórz menu skrótów `return 0;` instrukcji, a następnie wybierz **Uruchom do kursora**. Żółta strzałka w lewo punktów kodowych następną instrukcję do wykonania.  
  
8.  `Cardgame::totalParticipants` Gdy zakończenie Cardgame powinno ulec zmniejszeniu liczby. W tym momencie `Cardgame::totalParticipants` powinna być równa 0, ponieważ zostały usunięte wszystkie wystąpienia Cardgame, ale **1 czujki** okno oznacza to, że `Cardgame::totalparticipants` jest równe 18. Oznacza to, że jest to błąd w kodzie, które mogą wykrywać i rozwiązać, wykonując dalej wskazówki, [wskazówki: debugowanie projektu (C++)](../ide/walkthrough-debugging-a-project-cpp.md).  
  
9. Aby zatrzymać program, na pasku menu, wybierz **debugowania**, **Zatrzymaj debugowanie**, lub wybierz skrót klawiaturowy Shift + F5.  
  
## <a name="next-steps"></a>Następne kroki  
 **Poprzedni:** [wskazówki: Tworzenie projektu (C++)](../ide/walkthrough-building-a-project-cpp.md) &#124; **dalej:**[wskazówki: debugowanie projektu (C++)](../ide/walkthrough-debugging-a-project-cpp.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)