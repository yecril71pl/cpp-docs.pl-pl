---
title: 'Przewodnik: Tworzenie i używanie biblioteki statycznej (C++)'
description: Użyj języka C++ do utworzenia biblioteki statycznej (. lib) w programie Visual Studio.
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
# <a name="walkthrough-create-and-use-a-static-library"></a>Przewodnik: Tworzenie i używanie biblioteki statycznej

W tym przewodniku krok po kroku pokazano, jak utworzyć bibliotekę statyczną (plik. lib) do użycia z aplikacjami języka C++. Korzystanie z biblioteki statycznej to doskonały sposób na ponowne użycie kodu. Zamiast ponownie wdrażać te same procedury w każdej aplikacji, która wymaga funkcjonalności, należy napisać je jeden raz w bibliotece statycznej, a następnie odwołać się do niej z poziomu aplikacji. Kod połączony ze statyczną biblioteką jest częścią aplikacji — nie trzeba instalować kolejnego pliku w celu użycia kodu.

Ten przewodnik obejmuje następujące zadania:

- [Utwórz projekt biblioteki statycznej](#CreateLibProject)

- [Dodawanie klasy do biblioteki statycznej](#AddClassToLib)

- [Tworzenie aplikacji konsolowej w języku C++, która odwołuje się do biblioteki statycznej](#CreateAppToRefTheLib)

- [Korzystanie z funkcji z biblioteki statycznej w aplikacji](#UseLibInApp)

- [Uruchomienie aplikacji](#RunApp)

## <a name="prerequisites"></a>Wymagania wstępne

Zrozumienie podstaw języka C++.

## <a name="create-a-static-library-project"></a><a name="CreateLibProject"></a>Utwórz projekt biblioteki statycznej

Instrukcje dotyczące sposobu tworzenia projektu różnią się w zależności od używanej wersji programu Visual Studio. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj kontrolki selektora **wersji** . Znajduje się w górnej części spisu treści na tej stronie.

::: moniker range="vs-2019"

### <a name="to-create-a-static-library-project-in-visual-studio-2019"></a>Aby utworzyć projekt biblioteki statycznej w programie Visual Studio 2019

1. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt** , aby otworzyć okno dialogowe **Tworzenie nowego projektu** .

1. W górnej części okna dialogowego Ustaw **Język** na **C++**, ustaw **platformę** na **Windows**i ustaw **Typ projektu** na **Biblioteka**.

1. Z listy filtrowane typy projektów wybierz pozycję **Kreator pulpitu systemu Windows**, a następnie kliknij przycisk **dalej**.

1. Na stronie **Konfiguruj nowy projekt** wprowadź *MathLibrary* w polu **Nazwa projektu** , aby określić nazwę projektu. Wprowadź *StaticMath* w polu **Nazwa rozwiązania** . Wybierz przycisk **Utwórz** , aby otworzyć okno dialogowe **projekt pulpitu systemu Windows** .

1. W oknie dialogowym **projekt pulpitu systemu Windows** w obszarze **Typ aplikacji**wybierz pozycję **Biblioteka statyczna (. lib)**.

1. W obszarze **Opcje dodatkowe**Usuń zaznaczenie pola wyboru **prekompilowany nagłówek** , jeśli jest zaznaczone. Zaznacz pole **pusty projekt** .

1. Wybierz **przycisk OK** , aby utworzyć projekt.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-static-library-project-in-visual-studio-2017"></a>Aby utworzyć projekt biblioteki statycznej w programie Visual Studio 2017

1. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

1. W oknie dialogowym **Nowy projekt** wybierz pozycję **zainstalowane** > **Visual C++** > **pulpicie systemu Windows**. W środkowym okienku wybierz pozycję **Kreator pulpitu systemu Windows**.

1. Określ nazwę dla projektu — na przykład *MathLibrary*— w polu **Nazwa** . Określ nazwę dla rozwiązania — na przykład *StaticMath*— w polu **Nazwa rozwiązania** . Wybierz przycisk **OK** .

1. W oknie dialogowym **projekt pulpitu systemu Windows** w obszarze **Typ aplikacji**wybierz pozycję **Biblioteka statyczna (. lib)**.

1. W obszarze **Opcje dodatkowe**Usuń zaznaczenie pola wyboru **prekompilowany nagłówek** , jeśli jest zaznaczone. Zaznacz pole **pusty projekt** .

1. Wybierz **przycisk OK** , aby utworzyć projekt.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-static-library-project-in-visual-studio-2015"></a>Aby utworzyć projekt biblioteki statycznej w programie Visual Studio 2015

1. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

1. W oknie **dialogowym Nowy projekt** wybierz pozycję **zainstalowane** > **Szablony** > **Visual C++** > **Win32**. W środkowym okienku wybierz pozycję **aplikacja konsoli Win32**.

1. Określ nazwę dla projektu — na przykład *MathLibrary*— w polu **Nazwa** . Określ nazwę dla rozwiązania — na przykład *StaticMath*— w polu **Nazwa rozwiązania** . Wybierz przycisk **OK** .

1. W **Kreatorze aplikacji Win32**wybierz **dalej**.

1. Na stronie **Ustawienia aplikacji** w obszarze **Typ aplikacji**wybierz pozycję **Biblioteka statyczna**. W obszarze **Opcje dodatkowe**Usuń zaznaczenie pola wyboru **prekompilowanego nagłówka** . Wybierz pozycję **Zakończ** , aby utworzyć projekt.

::: moniker-end

## <a name="add-a-class-to-the-static-library"></a><a name="AddClassToLib"></a>Dodawanie klasy do biblioteki statycznej

### <a name="to-add-a-class-to-the-static-library"></a>Aby dodać klasę do biblioteki statycznej

1. Aby utworzyć plik nagłówka dla nowej klasy, kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów dla projektu **MathLibrary** w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję kod **Visual C++** > **Code**. W środkowym okienku wybierz pozycję **plik nagłówka (. h)**. Określ nazwę pliku nagłówka — na przykład *MathLibrary. h*— a następnie wybierz przycisk **Dodaj** . Zostanie wyświetlony niemal pusty plik nagłówkowy.

1. Dodaj deklarację dla klasy o nazwie `Arithmetic` do wykonaj Typowe operacje matematyczne, takie jak dodawanie, odejmowanie, mnożenie i dzielenie. Kod powinien wyglądać następująco:

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

1. Aby utworzyć plik źródłowy dla nowej klasy, otwórz menu skrótów dla projektu **MathLibrary** w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodaj nowy element** w środkowym okienku wybierz opcję **plik C++ (. cpp)**. Określ nazwę pliku źródłowego — na przykład *MathLibrary. cpp*, a następnie wybierz przycisk **Dodaj** . Zostanie wyświetlony pusty plik źródłowy.

1. Ten plik źródłowy służy do implementowania funkcji dla klasy `Arithmetic`. Kod powinien wyglądać następująco:

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

1. Aby skompilować bibliotekę statyczną, wybierz pozycję **Kompiluj** > **kompilację rozwiązania** na pasku menu. Kompilacja tworzy statyczną bibliotekę, *MathLibrary. lib*, która może być używana przez inne programy.

   > [!NOTE]
   > Podczas kompilowania w wierszu polecenia programu Visual Studio należy skompilować program w dwóch krokach. Najpierw uruchom `cl /c /EHsc MathLibrary.cpp` polecenie, aby skompilować kod i utworzyć plik obiektu o nazwie *MathLibrary. obj*. ( `cl` Polecenie wywołuje kompilator, CL. exe i `/c` opcja określa kompilację bez konsolidacji. Aby uzyskać więcej informacji, zobacz [/c (Kompiluj bez konsolidacji)](../build/reference/c-compile-without-linking.md). Następnie uruchom `lib MathLibrary.obj` polecenie, aby połączyć kod i utworzyć bibliotekę statyczną *MathLibrary. lib*. ( `lib` Polecenie wywołuje Menedżera bibliotek, lib. exe. Aby uzyskać więcej informacji, zobacz [Dokumentacja biblioteki lib](../build/reference/lib-reference.md).

## <a name="create-a-c-console-app-that-references-the-static-library"></a><a name="CreateAppToRefTheLib"></a>Tworzenie aplikacji konsolowej w języku C++, która odwołuje się do biblioteki statycznej

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2019"></a>Aby utworzyć aplikację konsolową w języku C++, która odwołuje się do biblioteki statycznej w programie Visual Studio 2019

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy górny węzeł, **rozwiązanie "StaticMath"**, aby otworzyć menu skrótów. Wybierz pozycję **Dodaj** > **Nowy projekt** , aby otworzyć okno dialogowe **Dodawanie nowego projektu** .

1. W górnej części okna dialogowego Ustaw filtr **Typ projektu** na **Console**.

1. Z listy filtrowane typy projektów wybierz pozycję **Aplikacja konsolowa** , a następnie wybierz przycisk **dalej**. Na następnej stronie wprowadź *MathClient* w polu **Nazwa** , aby określić nazwę projektu.

1. Wybierz przycisk **Utwórz** , aby utworzyć projekt klienta.

1. Po utworzeniu aplikacji konsolowej zostanie utworzony pusty program. Nazwa pliku źródłowego jest taka sama jak nazwa, którą wybrano wcześniej. W tym przykładzie nazywamy `MathClient.cpp`.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2017"></a>Aby utworzyć aplikację konsolową w języku C++, która odwołuje się do biblioteki statycznej w programie Visual Studio 2017

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy górny węzeł, **rozwiązanie "StaticMath"**, aby otworzyć menu skrótów. Wybierz pozycję **Dodaj** > **Nowy projekt** , aby otworzyć okno dialogowe **Dodawanie nowego projektu** .

1. W oknie dialogowym **Dodaj nowy projekt** wybierz pozycję **zainstalowane** > **Visual C++** > **pulpicie systemu Windows**. W środkowym okienku wybierz pozycję **Kreator pulpitu systemu Windows**.

1. Określ nazwę dla projektu — na przykład *MathClient*— w polu **Nazwa** . Wybierz przycisk **OK** .

1. W oknie dialogowym **projekt pulpitu systemu Windows** w obszarze **Typ aplikacji**wybierz pozycję **Aplikacja konsolowa (exe)**.

1. W obszarze **Opcje dodatkowe**Usuń zaznaczenie pola wyboru **prekompilowany nagłówek** , jeśli jest zaznaczone.

1. Wybierz **przycisk OK** , aby utworzyć projekt.

1. Po utworzeniu aplikacji konsolowej zostanie utworzony pusty program. Nazwa pliku źródłowego jest taka sama jak nazwa, którą wybrano wcześniej. W tym przykładzie nazywamy `MathClient.cpp`.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2015"></a>Aby utworzyć aplikację konsolową w języku C++, która odwołuje się do biblioteki statycznej w programie Visual Studio 2015

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy górny węzeł, **rozwiązanie "StaticMath"**, aby otworzyć menu skrótów. Wybierz pozycję **Dodaj** > **Nowy projekt** , aby otworzyć okno dialogowe **Dodawanie nowego projektu** .

1. W oknie dialogowym **Dodaj nowy projekt** wybierz pozycję **zainstalowane** > **Visual C++** > **Win32**. W środkowym okienku wybierz pozycję **aplikacja konsoli Win32**.

1. Określ nazwę dla projektu — na przykład *MathClient*— w polu **Nazwa** . Wybierz przycisk **OK** .

1. W oknie dialogowym **Kreator aplikacji Win32** wybierz pozycję **dalej**.

1. Na stronie **Ustawienia aplikacji** w obszarze **Typ aplikacji**upewnij się, że jest wybrana **Aplikacja konsolowa** . W obszarze **Opcje dodatkowe**wyczyść opcję **prekompilowany nagłówek**, a następnie zaznacz pole wyboru **pusty projekt** . Wybierz pozycję **Zakończ** , aby utworzyć projekt.

1. Aby dodać plik źródłowy do pustego projektu, kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów dla projektu **MathClient** w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję kod **Visual C++** > **Code**. W środkowym okienku wybierz opcję **plik C++ (. cpp)**. Określ nazwę pliku źródłowego — na przykład *MathClient. cpp*, a następnie wybierz przycisk **Dodaj** . Zostanie wyświetlony pusty plik źródłowy.

::: moniker-end

## <a name="use-the-functionality-from-the-static-library-in-the-app"></a><a name="UseLibInApp"></a>Korzystanie z funkcji z biblioteki statycznej w aplikacji

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>Aby użyć funkcji z biblioteki statycznej w aplikacji

1. Aby można było użyć procedur matematycznych w bibliotece statycznej, należy odwołać się do niej. Otwórz menu skrótów dla projektu **MathClient** w **Eksplorator rozwiązań**, a następnie wybierz **Dodaj** > **odwołanie**.

1. Okno dialogowe **Dodaj odwołanie** zawiera listę bibliotek, do których można się odwołać. Karta **projekty** zawiera listę projektów w bieżącym rozwiązaniu i wszystkie biblioteki, do których się odwołują. Otwórz kartę **projekty** , zaznacz pole wyboru **MathLibrary** , a następnie wybierz przycisk **OK** .

1. Aby odwołać `MathLibrary.h` się do pliku nagłówkowego, należy zmodyfikować ścieżkę uwzględnionych katalogów. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **MathClient** , aby otworzyć menu skrótów. Wybierz **Właściwości** , aby otworzyć okno dialogowe **strony właściwości MathClient** .

1. W oknie dialogowym **strony właściwości MathClient** Ustaw listę rozwijaną **konfiguracji** na **wszystkie konfiguracje**. Ustaw listę rozwijaną **platformy** na **wszystkie platformy**.

1. Wybierz stronę właściwości**Ogólne**  > **C/C++** >  **Właściwości konfiguracji**. We właściwości **Dodatkowe katalogi dołączane** określ ścieżkę do katalogu **MathLibrary** lub wyszukaj ją.

   Aby wyszukać ścieżkę katalogu:

   1. Otwórz listę rozwijaną **Dodatkowe katalogi dołączanych katalogów** , a następnie wybierz pozycję **Edytuj**.

   1. W oknie dialogowym **Dodatkowe katalogi dołączane** kliknij dwukrotnie w górnej części pola tekstowego. Następnie wybierz przycisk wielokropka (**...**) na końcu wiersza.

   1. W oknie dialogowym **Wybierz katalog** przejdź do góry, a następnie wybierz katalog **MathLibrary** . Następnie wybierz przycisk **Wybierz folder** , aby zapisać swój wybór.

   1. W oknie dialogowym **Dodatkowe katalogi dołączane** wybierz przycisk **OK** .

   1. W oknie dialogowym **strony właściwości** wybierz przycisk **OK** , aby zapisać zmiany w projekcie.

1. Teraz możesz użyć `Arithmetic` klasy w tej aplikacji, dołączając `#include "MathLibrary.h"` nagłówek w kodzie. Zastąp zawartość `MathClient.cpp` z tym kodem:

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

1. Aby skompilować plik wykonywalny, wybierz opcję **Kompiluj** > **kompilację rozwiązania** na pasku menu.

## <a name="run-the-app"></a><a name="RunApp"></a>Uruchamianie aplikacji

### <a name="to-run-the-app"></a>Aby uruchomić aplikację

1. Upewnij się, że **MathClient** jest wybrany jako projekt domyślny. Aby go zaznaczyć, kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów dla **MathClient** w **Eksplorator rozwiązań**, a następnie wybierz pozycję **Ustaw jako projekt startowy**.

1. Aby uruchomić projekt, na pasku menu wybierz **Debuguj** > **Uruchom bez debugowania**. Dane wyjściowe powinny wyglądać następująco:

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>Zobacz też

[Przewodnik: tworzenie i używanie biblioteki dołączanej dynamicznie (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[Aplikacje klasyczne (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
