---
title: 'Wskazówki: Tworzenie projektu (C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- building projects [C++]
- projects [C++], building
- project building [C++]
ms.assetid: d459bc03-88ef-48d0-9f9a-82d17f0b6a4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c8d04dc3692076b867302af0e793eaac7ed25cb
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33332458"
---
# <a name="walkthrough-building-a-project-c"></a>Wskazówki: tworzenie projektu (C++)
W tym przewodniku celowo wprowadzać w swój kod, aby dowiedzieć się, jak wygląda błąd kompilacji i napraw błąd składni Visual C++. Podczas kompilowania projektu komunikat o błędzie wskazuje, co to jest problem i którym wystąpił.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
-   W tym przewodniku przyjęto założenie, że rozumiesz podstawowe informacje na temat języka C++.  
  
-   Założono również, że zostały wykonane wcześniej powiązane wskazówki, które są wymienione w [za pomocą środowiska IDE programu Visual Studio dla programowania w języku C++ pulpitu](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
### <a name="to-fix-compilation-errors"></a>Aby naprawić błędy kompilacji  
  
1.  W TestGames.cpp Usuń średnik w ostatnim wierszu, dzięki czemu jest podobny, to:  
  
     `return 0`  
  
2.  Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
3.  Komunikat w **listy błędów** okno oznacza, że wystąpił błąd podczas tworzenia projektu. Opis wygląda następująco:  
  
     `error C2143: syntax error : missing ';' before '}'`  
  
     Aby wyświetlić informacje pomocnicze o tym błędzie, zaznacz go w **listy błędów** okna, a następnie wybierz klawisz F1.  
  
4.  Dodaj średnik z powrotem do końca wiersza, który zawiera błąd składni:  
  
     `return 0;`  
  
5.  Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
     Komunikat w **dane wyjściowe** okna wskazuje pomyślnie skompilować projekt.  
  
    ```Output  
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------  
    1>  TestGames.cpp  
    1>  Game.vcxproj -> C:\Users\<username>\Documents\Visual Studio <version>\Projects\Game\Debug\Game.exe  
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========  
    ```  
  
## <a name="next-steps"></a>Następne kroki  
 **Poprzedni:** [wskazówki: Praca z projektami i rozwiązaniami (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) &#124; **dalej:**[wskazówki: Testowanie projektu (C++)](../ide/walkthrough-testing-a-project-cpp.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)