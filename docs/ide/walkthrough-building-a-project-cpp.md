---
title: 'Przewodnik: Tworzenie projektu (C++)'
ms.date: 04/25/2019
helpviewer_keywords:
- building projects [C++]
- projects [C++], building
- project building [C++]
ms.assetid: d459bc03-88ef-48d0-9f9a-82d17f0b6a4d
ms.openlocfilehash: ea477e7b2f5435e049b242e68d151cc1f2d20624
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65708135"
---
# <a name="walkthrough-building-a-project-c"></a>Przewodnik: Tworzenie projektu (C++)

W tym instruktażu celowo wprowadzono C++ błąd składni w kodzie, aby dowiedzieć się, jak wygląda błąd kompilacji i jak go naprawić. Podczas kompilowania projektu, komunikat o błędzie wskazuje, co to jest problem i gdzie się pojawił.

## <a name="prerequisites"></a>Wymagania wstępne

- W tym przewodniku przyjęto założenie, że rozumiesz podstawy języka C++.

- Przyjęto również założenie, że zostały wykonane wcześniej pokrewne instruktaże, które są wymienione w [przy użyciu programu Visual Studio IDE dla programowanie aplikacji klasycznych w języku C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

### <a name="to-fix-compilation-errors"></a>Aby naprawić błędy kompilacji

1. W Game.cpp Usuń średnik w ostatnim wierszu, tak aby wyglądała jak instrukcji:

   `return 0`

1. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.

1. Wiadomości w **lista błędów** okno wskazuje, że wystąpił błąd podczas tworzenia projektu. Opis wygląda komunikat o błędzie:

   `error C2143: syntax error: missing ';' before '}'`

   Aby wyświetlić Pomoc dotyczącą tego błędu, wyróżnij go w **lista błędów** okna, a następnie wybierz **F1** klucza.

1. Dodać średnik z powrotem do końca wiersza, który zawiera błąd składni:

   `return 0;`

1. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.

   Wiadomości w **dane wyjściowe** okno wskazuje, że projekt został pomyślnie skompilowany.

    ```Output
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------
    1>Game.cpp
    1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
    ```

## <a name="next-steps"></a>Następne kroki

**Poprzednie:** [Przewodnik: Praca z projektami i rozwiązaniami (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)<br/>
**Dalej:** [Przewodnik: Testowanie projektu (C++)](../ide/walkthrough-testing-a-project-cpp.md)<br/>

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty i systemy kompilacji](../build/projects-and-build-systems-cpp.md)<br/>
