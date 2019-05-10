---
title: 'Przewodnik: Debugowanie projektu (C++)'
ms.date: 04/25/2019
helpviewer_keywords:
- projects [C++], debugging
- project debugging [C++]
- debugging projects
ms.assetid: a5cade77-ba51-4b03-a7a0-6897e3cd6a59
ms.openlocfilehash: 55124bc2f240499cc163fca6d0004a79047060a4
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857251"
---
# <a name="walkthrough-debugging-a-project-c"></a>Przewodnik: Debugowanie projektu (C++)

W tym przewodniku możesz zmodyfikować program, aby rozwiązać ten problem, który znaleziony podczas testowania projektu.

## <a name="prerequisites"></a>Wymagania wstępne

- W tym przewodniku przyjęto założenie, że rozumiesz podstawy języka C++.

- Przyjęto również założenie, że zostały wykonane wcześniej pokrewne instruktaże, które są wymienione w [przy użyciu programu Visual Studio IDE dla programowanie aplikacji klasycznych w języku C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

### <a name="to-fix-a-program-that-has-a-bug"></a>Aby naprawić program, który zawiera usterkę

1. Aby zobaczyć, co występuje, gdy `Cardgame` obiekt jest niszczony, wyświetlanie destruktor dla `Cardgame` klasy.

   Na pasku menu wybierz **widoku** > **Widok klas**.

   W **Widok klas** okna, rozwiń węzeł **gry** drzewa projektu i wybierz pozycję **wartość Cardgame** klasy, aby wyświetlić elementy członkowskie klasy i metody.

   Otwórz menu skrótów dla **~Cardgame(void)** destruktora, a następnie wybierz **przejdź do definicji**.

1. Aby zmniejszyć `totalParticipants` po zakończeniu wartość Cardgame, Dodaj następujący kod między otwierające i zamykające nawiasy klamrowe z `Cardgame::~Cardgame` destruktora.

   [!code-cpp[NVC_Walkthrough_Debugging_A_Project#110](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_1.cpp)]

1. Plik Cardgame.cpp powinien wyglądać podobnie poniższy kod, po zmianach przypominać:

   [!code-cpp[NVC_Walkthrough_Debugging_A_Project#111](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_2.cpp)]

1. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.

1. Po zakończeniu kompilacji, uruchom go w trybie debugowania, wybierając **debugowania** > **Rozpocznij debugowanie** na pasku menu lub wybierając **F5** klucza. Program wstrzymuje w pierwszym punkcie przerwania.

1. Aby przejść przez program, na pasku menu wybierz **debugowania** > **Step Over**, lub wybierz **F10** klucza.

   Należy zauważyć, że po każdym poleceniu `Cardgame` Konstruktor wykonuje wartość `totalParticipants` zwiększa się. Gdy `PlayGames` funkcja zwróci wartość, ponieważ do każdego `Cardgame` wystąpienie wykracza poza zakres i zostanie usunięta i destruktor jest wywoływany, `totalParticipants` zmniejsza. Tuż przed `return` instrukcja jest wykonywana, `totalParticipants` jest równa 0.

1. Kontynuuj przechodzenie krok po kroku za pośrednictwem programu aż do jej zakończenia lub pozwolić mu działać, wybierając **debugowania** > **Uruchom** na pasku menu lub wybierając **F5** klucza.

## <a name="next-steps"></a>Następne kroki

**Poprzednie:** [Przewodnik: Testowanie projektu (C++)](../ide/walkthrough-testing-a-project-cpp.md)<br/>
**Dalej:** [Przewodnik: Wdrażanie programu (C++)](../ide/walkthrough-deploying-your-program-cpp.md)<br/>

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty i systemy kompilacji](../build/projects-and-build-systems-cpp.md)<br/>
