---
title: 'Przewodnik: Tworzenie i używanie biblioteki statycznej (C++)'
description: Użyj języka C++, aby utworzyć bibliotekę statyczną (lib) w programie Visual Studio.
ms.custom: get-started-article
ms.date: 04/13/2020
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.openlocfilehash: 7148cc1de7c06ae57d61560311b342a1fc9dda1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335138"
---
# <a name="walkthrough-create-and-use-a-static-library"></a>Instruktaż: Tworzenie biblioteki statycznej i używanie ich

W tym przewodniku krok po kroku pokazano, jak utworzyć bibliotekę statyczną (plik lib) do użycia z aplikacjami W++. Korzystanie z biblioteki statycznej to świetny sposób na ponowne użycie kodu. Zamiast ponownie implementować te same procedury w każdej aplikacji, która wymaga funkcji, można napisać je jeden raz w bibliotece statycznej, a następnie odwołać się do niego z aplikacji. Kod połączony z biblioteką statyczną staje się częścią aplikacji — nie trzeba instalować innego pliku, aby użyć kodu.

Ten przewodnik obejmuje następujące zadania:

- [Tworzenie projektu biblioteki statycznej](#CreateLibProject)

- [Dodawanie klasy do biblioteki statycznej](#AddClassToLib)

- [Tworzenie aplikacji konsoli języka C++, która odwołuje się do biblioteki statycznej](#CreateAppToRefTheLib)

- [Korzystanie z funkcji z biblioteki statycznej w aplikacji](#UseLibInApp)

- [Uruchomienie aplikacji](#RunApp)

## <a name="prerequisites"></a>Wymagania wstępne

Zrozumienie podstaw języka C++.

## <a name="create-a-static-library-project"></a><a name="CreateLibProject"></a>Tworzenie projektu biblioteki statycznej

Instrukcje dotyczące tworzenia projektu różnią się w zależności od wersji programu Visual Studio. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj formantu selektor **wersji.** Znajduje się w górnej części spisu treści na tej stronie.

::: moniker range="vs-2019"

### <a name="to-create-a-static-library-project-in-visual-studio-2019"></a>Aby utworzyć projekt biblioteki statycznej w programie Visual Studio 2019

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu,** aby otworzyć okno dialogowe Tworzenie nowego **projektu.**

1. W górnej części okna dialogowego ustaw **język** na **C++,** ustaw **platformę** na **Windows**i ustaw **typ projektu** na **Biblioteka**.

1. Z filtru listy typów projektów wybierz Pozycję **Kreator pulpitu systemu Windows**, a następnie wybierz pozycję **Dalej**.

1. Na stronie **Konfigurowanie nowego projektu** wprowadź *MathLibrary* w polu **Nazwa projektu,** aby określić nazwę projektu. Wprowadź *StaticMath* w polu **Nazwa rozwiązania.** Wybierz przycisk **Utwórz,** aby otworzyć okno dialogowe **Projektu pulpitu systemu Windows.**

1. W oknie dialogowym **Projekt pulpitu systemu Windows** w obszarze Typ **aplikacji**wybierz pozycję **Biblioteka statyczna (lib)**.

1. W **obszarze Opcje dodatkowe**wyczyść pole wyboru Wstępnie **skompilowany nagłówek,** jeśli jest zaznaczony. Zaznacz pole **Puste okno projektu.**

1. Wybierz **przycisk OK,** aby utworzyć projekt.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-static-library-project-in-visual-studio-2017"></a>Aby utworzyć projekt biblioteki statycznej w programie Visual Studio 2017

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

1. W oknie dialogowym **Nowy projekt** wybierz pozycję **Zainstalowany** > **pulpit systemu Visual C++** > **dla systemu Windows**. W środkowym okienku wybierz pozycję **Kreator pulpitu systemu Windows**.

1. Określ nazwę projektu , na przykład *MathLibrary*, w polu **Nazwa.** Określ nazwę rozwiązania — na przykład *StaticMath*— w polu **Nazwa rozwiązania.** Wybierz przycisk **OK.**

1. W oknie dialogowym **Projekt pulpitu systemu Windows** w obszarze Typ **aplikacji**wybierz pozycję **Biblioteka statyczna (lib)**.

1. W **obszarze Opcje dodatkowe**wyczyść pole wyboru Wstępnie **skompilowany nagłówek,** jeśli jest zaznaczony. Zaznacz pole **Puste okno projektu.**

1. Wybierz **przycisk OK,** aby utworzyć projekt.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-static-library-project-in-visual-studio-2015"></a>Aby utworzyć projekt biblioteki statycznej w programie Visual Studio 2015

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

1. W oknie dialogowym **Nowy projekt** wybierz pozycję **Zainstalowane** > **szablony** > **Visual C++** > **Win32**. W środkowym okienku wybierz pozycję **Aplikacja konsoli Win32**.

1. Określ nazwę projektu , na przykład *MathLibrary*, w polu **Nazwa.** Określ nazwę rozwiązania — na przykład *StaticMath*— w polu **Nazwa rozwiązania.** Wybierz przycisk **OK.**

1. W **Kreatorze aplikacji Win32**wybierz pozycję **Dalej**.

1. Na stronie **Ustawienia aplikacji** w obszarze **Typ aplikacji**wybierz pozycję **Biblioteka statyczna**. W **obszarze Opcje dodatkowe**wyczyść pole wyboru Wstępnie **skompilowany nagłówek.** Wybierz **pozycję Zakończ,** aby utworzyć projekt.

::: moniker-end

## <a name="add-a-class-to-the-static-library"></a><a name="AddClassToLib"></a>Dodawanie klasy do biblioteki statycznej

### <a name="to-add-a-class-to-the-static-library"></a>Aby dodać klasę do biblioteki statycznej

1. Aby utworzyć plik nagłówka dla nowej klasy, kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów dla projektu **MathLibrary** w **Eksploratorze rozwiązań,** a następnie wybierz polecenie **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Kod języka Visual **C++** > **.** W środkowym okienku wybierz pozycję **Plik nagłówka (h)**. Określ nazwę pliku nagłówka, na przykład *MathLibrary.h,* a następnie wybierz przycisk **Dodaj.** Zostanie wyświetlony prawie pusty plik nagłówka.

1. Dodaj deklarację dla `Arithmetic` klasy o nazwie, aby wykonać typowe operacje matematyczne, takie jak dodawanie, odejmowanie, mnożenie i dzielenie. Kod powinien przypominać:

    ```cpp
    // MathLibrary.h
    #pragma once

    namespace MathLibrary
    {
        class Arithmetic
        {
        public:
            // Returns a + b
            static double Add(double a, double b);

            // Returns a - b
            static double Subtract(double a, double b);

            // Returns a * b
            static double Multiply(double a, double b);

            // Returns a / b
            static double Divide(double a, double b);
        };
    }
    ```

1. Aby utworzyć plik źródłowy dla nowej klasy, otwórz menu skrótów dla projektu **MathLibrary** w **Eksploratorze rozwiązań,** a następnie wybierz pozycję **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodawanie nowego elementu** w środkowym okienku wybierz pozycję Plik **C++ (cpp)**. Określ nazwę pliku źródłowego, na przykład *MathLibrary.cpp,* a następnie wybierz przycisk **Dodaj.** Zostanie wyświetlony pusty plik źródłowy.

1. Ten plik źródłowy służy do `Arithmetic`implementowania funkcji klasy . Kod powinien przypominać:

    ```cpp
    // MathLibrary.cpp
    // compile with: cl /c /EHsc MathLibrary.cpp
    // post-build command: lib MathLibrary.obj

    #include "MathLibrary.h"

    namespace MathLibrary
    {
        double Arithmetic::Add(double a, double b)
        {
            return a + b;
        }

        double Arithmetic::Subtract(double a, double b)
        {
            return a - b;
        }

        double Arithmetic::Multiply(double a, double b)
        {
            return a * b;
        }

        double Arithmetic::Divide(double a, double b)
        {
            return a / b;
        }
    }
    ```

1. Aby utworzyć bibliotekę statyczną, wybierz pozycję **Zbuduj** > **rozwiązanie kompilacji** na pasku menu. Kompilacja tworzy bibliotekę statyczną *MathLibrary.lib*, która może być używana przez inne programy.

   > [!NOTE]
   > Podczas tworzenia w wierszu polecenia programu Visual Studio, należy utworzyć program w dwóch krokach. Najpierw uruchom, `cl /c /EHsc MathLibrary.cpp` aby skompilować kod i utworzyć plik obiektu o nazwie *MathLibrary.obj*. (Polecenie `cl` wywołuje kompilator, Cl.exe, `/c` a opcja określa kompilację bez łączenia. Aby uzyskać więcej informacji, zobacz [/c (Compile Without Linking)](../build/reference/c-compile-without-linking.md).) Po drugie, uruchom, `lib MathLibrary.obj` aby połączyć kod i utworzyć bibliotekę statyczną *MathLibrary.lib*. (Polecenie `lib` wywołuje Menedżera biblioteki, Lib.exe. Aby uzyskać więcej informacji, zobacz [odwołanie do LIB](../build/reference/lib-reference.md).)

## <a name="create-a-c-console-app-that-references-the-static-library"></a><a name="CreateAppToRefTheLib"></a>Tworzenie aplikacji konsoli języka C++, która odwołuje się do biblioteki statycznej

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2019"></a>Aby utworzyć aplikację konsoli języka C++, która odwołuje się do biblioteki statycznej w programie Visual Studio 2019

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy górny **węzeł, Rozwiązanie "StaticMath",** aby otworzyć menu skrótów. Wybierz **pozycję Dodaj** > **nowy projekt,** aby otworzyć okno dialogowe Dodawanie nowego **projektu.**

1. W górnej części okna dialogowego ustaw filtr **typu projektu** na **Konsola**.

1. Z filtru listy typów projektów wybierz pozycję **Aplikacja konsoli,** a następnie wybierz pozycję **Dalej**. Na następnej stronie wprowadź *MathClient* w polu **Nazwa,** aby określić nazwę projektu.

1. Wybierz przycisk **Utwórz,** aby utworzyć projekt klienta.

1. Po utworzeniu aplikacji konsoli tworzony jest dla Ciebie pusty program. Nazwa pliku źródłowego jest taka sama jak nazwa wybrana wcześniej. W przykładzie nosi nazwę `MathClient.cpp`.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2017"></a>Aby utworzyć aplikację konsoli języka C++, która odwołuje się do biblioteki statycznej w programie Visual Studio 2017

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy górny **węzeł, Rozwiązanie "StaticMath",** aby otworzyć menu skrótów. Wybierz **pozycję Dodaj** > **nowy projekt,** aby otworzyć okno dialogowe Dodawanie nowego **projektu.**

1. W oknie dialogowym **Dodawanie nowego projektu** wybierz pozycję **Zainstalowany** > **program Visual C++** > Desktop dla systemu**Windows**. W środkowym okienku wybierz pozycję **Kreator pulpitu systemu Windows**.

1. Określ nazwę projektu — na przykład *MathClient*— w polu **Nazwa.** Wybierz przycisk **OK.**

1. W oknie dialogowym **Projekt pulpitu systemu Windows** w obszarze Typ **aplikacji**wybierz pozycję Aplikacja **konsoli (exe)**.

1. W **obszarze Opcje dodatkowe**wyczyść pole wyboru Wstępnie **skompilowany nagłówek,** jeśli jest zaznaczony.

1. Wybierz **przycisk OK,** aby utworzyć projekt.

1. Po utworzeniu aplikacji konsoli tworzony jest dla Ciebie pusty program. Nazwa pliku źródłowego jest taka sama jak nazwa wybrana wcześniej. W przykładzie nosi nazwę `MathClient.cpp`.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2015"></a>Aby utworzyć aplikację konsoli języka C++, która odwołuje się do biblioteki statycznej w programie Visual Studio 2015

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy górny **węzeł, Rozwiązanie "StaticMath",** aby otworzyć menu skrótów. Wybierz **pozycję Dodaj** > **nowy projekt,** aby otworzyć okno dialogowe Dodawanie nowego **projektu.**

1. W oknie dialogowym **Dodawanie nowego projektu** wybierz pozycję **Zainstalowana** > **aplikacja Visual C++** > **Win32**. W środkowym okienku wybierz pozycję **Aplikacja konsoli Win32**.

1. Określ nazwę projektu — na przykład *MathClient*— w polu **Nazwa.** Wybierz przycisk **OK.**

1. W oknie dialogowym **Kreator aplikacji usługi Win32** wybierz pozycję **Dalej**.

1. Na stronie **Ustawienia aplikacji** w obszarze **Typ aplikacji**upewnij się, że **wybrano aplikację konsoli.** W obszarze **Opcje dodatkowe**wyczyść pole wyboru **Wstępnie skompilowany nagłówek**, a następnie zaznacz pole wyboru Pusty **projekt.** Wybierz **pozycję Zakończ,** aby utworzyć projekt.

1. Aby dodać plik źródłowy do pustego projektu, kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów dla projektu **MathClient** w **Eksploratorze rozwiązań,** a następnie wybierz polecenie **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Kod języka Visual **C++** > **.** W środkowym okienku wybierz pozycję **Plik C++ (cpp)**. Określ nazwę pliku źródłowego, na przykład *MathClient.cpp,* a następnie wybierz przycisk **Dodaj.** Zostanie wyświetlony pusty plik źródłowy.

::: moniker-end

## <a name="use-the-functionality-from-the-static-library-in-the-app"></a><a name="UseLibInApp"></a>Korzystanie z funkcji z biblioteki statycznej w aplikacji

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>Aby korzystać z funkcji z biblioteki statycznej w aplikacji

1. Aby można było używać procedur matematycznych w bibliotece statycznej, należy się do niej odwołać. Otwórz menu skrótów dla projektu **MathClient** w **Eksploratorze rozwiązań,** a następnie wybierz polecenie **Dodaj** > **odwołanie**.

1. Okno dialogowe **Dodawanie odwołania** zawiera listę bibliotek, do których można się odwołać. Karta **Projekty** zawiera listę projektów w bieżącym rozwiązaniu i wszystkie biblioteki, do których się odwołują. Otwórz kartę **Projekty,** zaznacz pole wyboru **MathLibrary,** a następnie wybierz przycisk **OK.**

1. Aby odwołać się do pliku nagłówka, `MathLibrary.h` należy zmodyfikować ścieżkę dołączonych katalogów. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **MathClient,** aby otworzyć menu skrótów. Wybierz **polecenie Właściwości,** aby otworzyć okno dialogowe **Strony właściwości MathClient.**

1. W oknie dialogowym **Strony właściwości MathClient** ustaw okno **rozwijane Konfiguracja** na **Wszystkie konfiguracje**. Ustaw **platformę** rozwijaną dla **wszystkich platform**.

1. Wybierz stronę **właściwości Właściwości konfiguracyjne** > **C/C++** > **Ogólne.** We właściwości **Dodatkowe katalogi dołączania** określ ścieżkę katalogu **MathLibrary** lub wyszukaj go.

   Aby wyszukać ścieżkę katalogu:

   1. Otwórz listę rozwijaną Wartość właściwości **Dodatkowe dołącz katalogi,** a następnie wybierz pozycję **Edytuj**.

   1. W oknie dialogowym **Dodatkowe katalogi dołączania** kliknij dwukrotnie u góry pola tekstowego. Następnie wybierz przycisk wielokropka (**...**) na końcu linii.

   1. W oknie dialogowym **Wybieranie katalogu** przejdź w górę poziomu, a następnie wybierz katalog **MathLibrary.** Następnie wybierz przycisk **Wybierz folder,** aby zapisać zaznaczenie.

   1. W oknie dialogowym **Dodatkowe katalogi dołączania** wybierz przycisk **OK.**

   1. W oknie dialogowym **Strony właściwości** wybierz przycisk **OK,** aby zapisać zmiany w projekcie.

1. Teraz można użyć `Arithmetic` klasy w tej `#include "MathLibrary.h"` aplikacji, dołączając nagłówek w kodzie. Zastąp `MathClient.cpp` zawartość tego kodu:

    ```cpp
    // MathClient.cpp
    // compile with: cl /EHsc MathClient.cpp /link MathLibrary.lib

    #include <iostream>
    #include "MathLibrary.h"

    int main()
    {
        double a = 7.4;
        int b = 99;

        std::cout << "a + b = " <<
            MathLibrary::Arithmetic::Add(a, b) << std::endl;
        std::cout << "a - b = " <<
            MathLibrary::Arithmetic::Subtract(a, b) << std::endl;
        std::cout << "a * b = " <<
            MathLibrary::Arithmetic::Multiply(a, b) << std::endl;
        std::cout << "a / b = " <<
            MathLibrary::Arithmetic::Divide(a, b) << std::endl;

        return 0;
    }
    ```

1. Aby utworzyć plik wykonywalny, wybierz pozycję **Build** > **Build Solution** na pasku menu.

## <a name="run-the-app"></a><a name="RunApp"></a>Uruchamianie aplikacji

### <a name="to-run-the-app"></a>Aby uruchomić aplikację

1. Upewnij się, że **MathClient** jest wybrany jako projekt domyślny. Aby ją zaznaczyć, kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów dla **MathClient** w **Eksploratorze rozwiązań,** a następnie wybierz polecenie **Ustaw jako projekt StartUp**.

1. Aby uruchomić projekt, na pasku menu wybierz pozycję **Debugowanie** > **start bez debugowania**. Dane wyjściowe powinny przypominać:

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>Zobacz też

[Przewodnik: tworzenie i używanie biblioteki dołączanej dynamicznie (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[Aplikacje klasyczne (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
