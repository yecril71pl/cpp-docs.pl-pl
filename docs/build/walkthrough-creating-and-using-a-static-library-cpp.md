---
title: 'Przewodnik: Tworzenie i używanie biblioteki statycznej (C++)'
ms.custom: get-started-article
ms.date: 09/18/2018
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.author: corob
ms.openlocfilehash: 0d527681abb077a01b3d902c092a21de7a052867
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031511"
---
# <a name="walkthrough-creating-and-using-a-static-library-c"></a>Przewodnik: Tworzenie i używanie biblioteki statycznej (C++)

Ten przewodnik krok po kroku przedstawiono sposób tworzenia biblioteki statycznej (plik .lib) do użytku z aplikacjami C++. Używanie biblioteki statycznej to doskonały sposób na ponowne użycie kodu. Zamiast reimplementing tych samych procedur w każdej aplikacji, która wymaga funkcji, napisz je jeden raz w bibliotece statycznej, a następnie Odwołaj się do niego z aplikacji. Kod powiązany ze statyczneą biblioteką staje się częścią Twojej aplikacji — nie trzeba zainstalować innego pliku, aby użyć kodu.

W tym przewodniku opisano następujące zadania:

- [Tworzenie projektu biblioteki statycznej](#CreateLibProject)

- [Dodawanie klasy z biblioteką statyczną](#AddClassToLib)

- [Tworzenie aplikacji konsoli C++, który odwołuje się do biblioteki statycznej](#CreateAppToRefTheLib)

- [Korzystając z funkcji z biblioteki statycznej w aplikacji](#UseLibInApp)

- [Uruchamianie aplikacji](#RunApp)

## <a name="prerequisites"></a>Wymagania wstępne

Po zrozumieniu podstaw języka C++.

##  <a name="CreateLibProject"></a> Tworzenie projektu biblioteki statycznej

### <a name="to-create-a-static-library-project"></a>Aby utworzyć projekt biblioteki statycznej

1. Na pasku menu wybierz **pliku** > **New** > **projektu**.

1. W okienku po lewej stronie **nowy projekt** okna dialogowego rozwiń **zainstalowane** > **Visual C++**, a następnie wybierz pozycję **pulpitu Windows**. W środkowym okienku wybierz **kreatora pulpitu Windows**.

   > [!NOTE]
   > W przypadku wersji sprzed 2017, Visual Studio w **nowy projekt** okna dialogowego rozwiń **zainstalowane** > **szablony**  >  **Visual C++**, a następnie wybierz pozycję **Win32**. W środkowym okienku wybierz **Aplikacja konsoli Win32**.

1. Określ nazwę dla projektu — na przykład *MathFuncsLib*— w **nazwa** pole. Określ nazwę dla rozwiązania — na przykład *StaticLibrary*— w **Nazwa rozwiązania** pole. Wybierz **OK** przycisku.

    - For Visual Studio 2017,

        1. W obszarze **typ aplikacji**, wybierz opcję **biblioteka statyczna (.lib)**.

        1. W obszarze **dodatkowe opcje**, usuń zaznaczenie **prekompilowany nagłówek** pole wyboru.

        1. Wybierz **OK** do tworzenia projektu.

    - W przypadku wersji sprzed 2017, Visual Studio

        1. Kliknij przycisk **Dalej**.

        1. W obszarze **typ aplikacji**, wybierz opcję **biblioteki statycznej**. Następnie usuń zaznaczenie pola wyboru **prekompilowany nagłówek** pole, a następnie wybierz **Zakończ**.

##  <a name="AddClassToLib"></a> Dodawanie klasy z biblioteką statyczną

### <a name="to-add-a-class-to-the-static-library"></a>Aby dodać klasę do biblioteki statycznej

1. Aby utworzyć plik nagłówka dla nowej klasy, otwórz menu skrótów dla **MathFuncsLib** projektu w **Eksploratora rozwiązań**, a następnie wybierz **Dodaj**  >   **Nowy element**. W **Dodaj nowy element** okno dialogowe, w okienku po lewej stronie w obszarze **Visual C++**, wybierz opcję **kodu**. W środkowym okienku wybierz **plik nagłówka (.h)**. Określ nazwę dla pliku nagłówka — na przykład *MathFuncsLib.h*— a następnie wybierz **Dodaj** przycisku. Pusty nagłówek pliku jest wyświetlany.

1. Dodaj klasę o nazwie `MyMathFuncs` można wykonywać typowe operacje matematyczne, takie jak dodawanie, odejmowanie, mnożenie i dzielenie. Kod powinien przypominać:

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#100](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_1.h)]

1. Aby utworzyć plik źródłowy dla nowej klasy, otwórz menu skrótów dla **MathFuncsLib** projektu w **Eksploratora rozwiązań**, a następnie wybierz **Dodaj**  >   **Nowy element**. W **Dodaj nowy element** okno dialogowe, w okienku po lewej stronie w obszarze **Visual C++**, wybierz opcję **kodu**. W środkowym okienku wybierz **plik C++ (.cpp)**. Określ nazwę dla pliku źródłowego — na przykład *MathFuncsLib.cpp*— a następnie wybierz **Dodaj** przycisku. Pusty nagłówek pliku źródłowego jest wyświetlany.

1. Użyj tego pliku źródłowego do implementowania **MyMathFuncs**. Kod powinien przypominać:

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#110](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_2.cpp)]

1. Kompilowanie statycznej biblioteki łączy, wybierając **kompilacji** > **Kompiluj rozwiązanie** na pasku menu. Kompilowanie tworzy bibliotekę statyczną, które mogą być używane przez inne programy.

   > [!NOTE]
   > W przypadku tworzenia w wierszu polecenia programu Visual Studio, należy utworzyć program w dwóch krokach. Najpierw uruchom `cl /c /EHsc MathFuncsLib.cpp` skompilować kod i utworzyć plik obiektu o nazwie `MathFuncsLib.obj`. ( `cl` Polecenia wywołuje kompilator Cl.exe i `/c` opcja określa kompilacji bez konsolidacji. Aby uzyskać więcej informacji, zobacz [/c (Kompiluj bez konsolidacji)](../build/reference/c-compile-without-linking.md).) Po drugie, uruchom `lib MathFuncsLib.obj` połączyć kod i utworzyć statyczne biblioteki `MathFuncsLib.lib`. ( `lib` Olecenie wywołuje Library Manager, Lib.exe. Aby uzyskać więcej informacji, zobacz [odwołanie do biblioteki LIB](../build/reference/lib-reference.md).)

##  <a name="CreateAppToRefTheLib"></a> Tworzenie aplikacji konsoli C++, który odwołuje się do biblioteki statycznej

### <a name="to-create-a-c-console-app-that-references-the-static-library"></a>Aby utworzyć aplikację konsoli C++, który odwołuje się do biblioteki statycznej

1. Na pasku menu wybierz **pliku** > **New** > **projektu**.

1. W okienku po lewej stronie **nowy projekt** okna dialogowego rozwiń **zainstalowane** > **Visual C++**, a następnie wybierz pozycję **pulpitu Windows**. W środkowym okienku wybierz **kreatora pulpitu Windows**.

   > [!NOTE]
   > W przypadku wersji sprzed 2017, Visual Studio w **nowy projekt** okna dialogowego rozwiń **zainstalowane** > **szablony**  >  **Visual C++**, a następnie wybierz pozycję **Win32**. W środkowym okienku wybierz **Aplikacja konsoli Win32**.

1. Określ nazwę dla projektu — na przykład *MyExecRefsLib*— w **nazwa** pole. Z listy rozwijanej liście obok **rozwiązania**, wybierz opcję **Dodaj do rozwiązania**. Polecenie dodaje nowy projekt do rozwiązania, które zawiera bibliotekę statyczną. Wybierz **OK** przycisku.

    - For Visual Studio 2017,

        1. W obszarze **typ aplikacji**, wybierz opcję **Aplikacja konsoli (.exe)**.

        1. W obszarze **dodatkowe opcje**, usuń zaznaczenie **prekompilowany nagłówek** pole wyboru.

        1. Wybierz **OK** do tworzenia projektu.

    - W przypadku wersji sprzed 2017, Visual Studio

        1. Kliknij przycisk **Dalej**.

        1. Upewnij się, że **aplikacji konsolowej programu** jest zaznaczone. Następnie sprawdź **pusty projekt** pole, a następnie wybierz **Zakończ**.

##  <a name="UseLibInApp"></a> Korzystając z funkcji z biblioteki statycznej w aplikacji

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>Aby użyć funkcjonalności z biblioteki statycznej w aplikacji

1. Po utworzeniu aplikacji konsoli pusty program zostanie utworzony. Nazwa pliku źródłowego jest taka sama jak nazwa, która została wybrana wcześniej. W tym przykładzie jest on nazwany `MyExecRefsLib.cpp`.

1. Przed użyciem procedury matematyczne w bibliotece statycznej, należy to odwołać. Otwórz menu skrótów dla **MyExecRefsLib** projektu w **Eksploratora rozwiązań**, a następnie wybierz **Dodaj** > **odwołania**.

1. **Dodaj odwołanie** okno dialogowe wyświetla listę bibliotek, których można się odwołać. **Projektów** zawiera listę wszystkich projektów w bieżącym rozwiązaniu i wszystkie biblioteki, odwołują. Na **projektów** zaznacz **MathFuncsLib** pole wyboru, a następnie wybierz **OK** przycisku.

1. Odwołania do `MathFuncsLib.h` pliku nagłówkowym, musisz zmodyfikować zawartą ścieżkę katalogów. W **stron właściwości** okno dialogowe **MyExecRefsLib**, rozwiń węzeł **właściwości konfiguracji** węzła, rozwiń węzeł **C/C++** węzeł, i następnie wybierz pozycję **ogólne**. Obok pozycji **dodatkowe katalogi dołączenia**, określ ścieżkę **MathFuncsLib** katalogu lub wyszukaj go.

   Aby wyszukać ścieżkę katalogu, Otwórz listę rozwijaną listę wartości właściwości, a następnie wybierz **Edytuj**. W **dodatkowe katalogi dołączenia** okno dialogowe, w polu tekstowym zaznacz pusty wiersz, a następnie wybierz przycisk wielokropka (**...** ) na końcu wiersza. W **wybierz katalog** okno dialogowe, wybierz **MathFuncsLib** katalogu, a następnie wybierz **wybierz Folder** przycisk, aby zapisać swój wybór i zamknąć okno dialogowe. W **dodatkowe katalogi dołączenia** okna dialogowego wybierz **OK** przycisku, a następnie w polu **stron właściwości** okna dialogowego wybierz **OK**przycisk, aby zapisać zmiany w projekcie.

1. Teraz możesz używać `MyMathFuncs` klasy w tej aplikacji, umieszczając `#include "MathFuncsLib.h"` nagłówka w kodzie. Zastąp zawartość `MyExecRefsLib.cpp` przy użyciu tego kodu:

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#120](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_3.cpp)]

1. Tworzenie pliku wykonywalnego, wybierając **kompilacji** > **Kompiluj rozwiązanie** na pasku menu.

##  <a name="RunApp"></a> Uruchamianie aplikacji

### <a name="to-run-the-app"></a>Aby uruchomić aplikację

1. Upewnij się, że **MyExecRefsLib** jest wybrany jako domyślny projekt przez otwarcie menu skrótów dla **MyExecRefsLib** w **Solution Explorer**, a następnie wybierając  **Ustaw jako projekt startowy**.

1. Aby uruchomić projekt, na pasku menu, wybierz opcję **debugowania** > **Rozpocznij bez debugowania**. Dane wyjściowe powinny przypominać:

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>Zobacz także

[Przewodnik: Tworzenie i używanie biblioteki dołączanej dynamicznie (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[Aplikacje klasyczne (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
