---
title: 'Wskazówki: Testowanie projektu (C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 09/14/2018
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
ms.openlocfilehash: 56614dc0829834e77cfdf10d8d88ed44492237e3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070143"
---
# <a name="walkthrough-testing-a-project-c"></a>Wskazówki: testowanie projektu (C++)

Jeśli program jest uruchomiony w trybie debugowania, można użyć punktów przerwania, aby zatrzymać program i przeanalizować stan zmiennych i obiektów.

W tym przewodniku oglądać wartości zmiennej po uruchomieniu programu i wywnioskować, dlatego wartość nie jest, czego oczekiwać.

## <a name="prerequisites"></a>Wymagania wstępne

- W tym przewodniku przyjęto założenie, że rozumiesz podstawy języka C++.

- Przyjęto również założenie, że zostały wykonane wcześniej pokrewne instruktaże, które są wymienione w [przy użyciu programu Visual Studio IDE dla programowanie aplikacji klasycznych w języku C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

### <a name="to-run-a-program-in-debug-mode"></a>Aby uruchomić program w trybie debugowania

1. Games.cpp należy otworzyć do edycji.

1. Wybierz ten wiersz kodu:

   `Cardgame.solitaire(1);`

1. Aby ustawić punkt przerwania w danym wierszu, na pasku menu wybierz **debugowania** > **Przełącz punkt przerwania**, lub wybierz **F9** klucza. Czerwony okrąg pojawia się na lewo od linii; oznacza to, że punkt przerwania jest ustawiony. Aby usunąć punkt przerwania, możesz wybrać polecenie menu lub **F9** klucza ponownie.

   Jeśli używasz myszy, możesz również ustawić lub usunąć punkt przerwania, klikając w lewy margines.

1. Na pasku menu wybierz **debugowania** > **Rozpocznij debugowanie**, lub wybierz **F5** klucza.

   Kiedy program osiąga linię, która posiada punkt przerwania, wykonanie czasowo się zatrzymuje, ponieważ Twój program jest w trybie przerwania. Żółta strzałka w lewo od linii kodu wskazuje następny wiersz ma być wykonywane.

1. Aby sprawdzić wartość `Cardgame::totalParticipants` zmiennej, przesuń wskaźnik nad `Cardgame` i przenieś ją nad kontrolką rozciągania po lewej stronie okna etykiety narzędzi. Nazwa zmiennej `totalParticipants` i jego wartość **12** są wyświetlane.

   Otwórz menu skrótów dla `Cardgame::totalParticipants` zmiennej, a następnie wybierz **Dodaj czujkę** Aby wyświetlić tę zmienna w **Czujka 1** okna. Możesz również wyróżnić zmienną i przeciągnij ją do **Czujka 1** okna.

1. Aby przejść do następnego wiersza kodu, na pasku menu wybierz **debugowania** > **Step Over**, lub wybierz **F10** klucza.

   Wartość `Cardgame::totalParticipants` w **Czujka 1** okna jest teraz wyświetlany jako **13**.

1. Otwórz menu skrótów dla `return 0;` instrukcji, a następnie wybierz **Uruchom do kursora**. Żółta strzałka po lewej stronie kodu wskazuje na następną instrukcję do wykonania.

1. `Cardgame::totalParticipants` Kiedy Zmniejsz liczbę `Cardgame` kończy. W tym momencie `Cardgame::totalParticipants` powinna być równa 0, ponieważ wszystkie `Cardgame` wystąpienia zostały usunięte, ale **Czujka 1** okno wskazuje, że `Cardgame::totalparticipants` jest równa **18**. Różnica wskazuje, że jest to błąd w kodzie, w którym można wykryć i naprawić poprzez wypełnienie poniższych wskazówek, [wskazówki: debugowanie projektu (C++)](../ide/walkthrough-debugging-a-project-cpp.md).

1. Aby zatrzymać program, na pasku menu, wybierz opcję **debugowania** > **Zatrzymaj debugowanie**, lub wybierz **Shift**+**F5**skróty klawiaturowe.

## <a name="next-steps"></a>Następne kroki

**Poprzedni:** [wskazówki: Tworzenie projektu (C++)](../ide/walkthrough-building-a-project-cpp.md)<br/>
**Następnie:** [wskazówki: debugowanie projektu (C++)](../ide/walkthrough-debugging-a-project-cpp.md)<br/>

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)<br/>
