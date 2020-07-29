---
title: 'Wskazówki: debugowanie projektu (C++)'
ms.date: 04/25/2019
helpviewer_keywords:
- projects [C++], debugging
- project debugging [C++]
- debugging projects
ms.assetid: a5cade77-ba51-4b03-a7a0-6897e3cd6a59
ms.openlocfilehash: 61433213619c16caf67de905a6da93c7360db298
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219680"
---
# <a name="walkthrough-debugging-a-project-c"></a>Wskazówki: debugowanie projektu (C++)

W tym instruktażu zmodyfikujesz program, aby rozwiązać problem znaleziony podczas testowania projektu.

## <a name="prerequisites"></a>Wymagania wstępne

- W tym instruktażu założono, że rozumiesz podstawy języka C++.

- Przyjęto również założenie, że zostały wykonane wcześniejsze powiązane instruktaże, które są wymienione na liście [przy użyciu środowiska IDE programu Visual Studio na potrzeby programowania aplikacji klasycznych](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)w języku C++.

### <a name="to-fix-a-program-that-has-a-bug"></a>Aby naprawić program, który ma usterkę

1. Aby zobaczyć, co się dzieje `Cardgame` , gdy obiekt jest niszczony, Wyświetl destruktor dla `Cardgame` klasy.

   Na pasku menu wybierz polecenie **Wyświetl**  >  **Widok klasy**.

   W oknie **Widok klasy** rozwiń drzewo projektu **gry** i wybierz klasę **plik Cardgame** , aby wyświetlić elementy członkowskie i metody klasy.

   Otwórz menu skrótów dla destruktora **~ plik Cardgame (void)** , a następnie wybierz **Przejdź do definicji**.

1. Aby zmniejszyć `totalParticipants` czas plik Cardgame, Dodaj następujący kod między otwierającym i zamykającym nawiasem klamrowym `Cardgame::~Cardgame` destruktora.

   [!code-cpp[NVC_Walkthrough_Debugging_A_Project#110](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_1.cpp)]

1. Plik plik Cardgame. cpp powinien wyglądać podobnie do poniższego kodu:

   [!code-cpp[NVC_Walkthrough_Debugging_A_Project#111](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_2.cpp)]

1. Na pasku menu wybierz polecenie **Kompiluj**  >  **kompilację rozwiązania**.

1. Po zakończeniu kompilacji uruchom ją w trybie debugowania, wybierając **Debuguj**  >  **Rozpocznij debugowanie** na pasku menu lub wybierając klawisz **F5** . Program zatrzymuje się przy pierwszym punkcie przerwania.

1. Aby przejść przez program, na pasku menu wybierz **Debuguj**  >  **krok nad**lub wybierz klawisz **F10** .

   Należy zauważyć, że po wykonaniu każdego `Cardgame` konstruktora wartość `totalParticipants` rośnie. Gdy `PlayGames` Funkcja zwraca, ponieważ każde `Cardgame` wystąpienie wykracza poza zakres i jest usuwane (a destruktor jest wywoływany), `totalParticipants` zmniejsza. Tuż przed **`return`** wykonaniem instrukcji jest `totalParticipants` równa 0.

1. Kontynuuj przechodzenie przez program do momentu jego zakończenia lub pozwól na jego uruchomienie, wybierając polecenie **Debuguj**  >  **Run** na pasku menu lub wybierając klawisz **F5** .

## <a name="next-steps"></a>Następne kroki

**Poprzednie:** [Przewodnik: Testowanie projektu (C++)](../ide/walkthrough-testing-a-project-cpp.md)<br/>
**Dalej:** [Przewodnik: wdrażanie programu (C++)](../ide/walkthrough-deploying-your-program-cpp.md)

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty i systemy kompilacji](../build/projects-and-build-systems-cpp.md)<br/>
