---
title: 'Wskazówki: tworzenie i używanie biblioteki statycznej (C++)'
description: Służy C++ do tworzenia biblioteki statycznej (. lib) w programie Visual Studio.
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.author: corob
ms.openlocfilehash: c81ccd970383c8571a7d0d1e77d4b8fe44900bcf
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078180"
---
# <a name="walkthrough-creating-and-using-a-static-library-c"></a>Wskazówki: tworzenie i używanie biblioteki statycznej (C++)

W tym przewodniku krok po kroku pokazano, jak utworzyć bibliotekę statyczną (plik. lib) do użycia z C++ aplikacjami. Korzystanie z biblioteki statycznej to doskonały sposób na ponowne użycie kodu. Zamiast ponownie wdrażać te same procedury w każdej aplikacji, która wymaga funkcjonalności, należy napisać je jeden raz w bibliotece statycznej, a następnie odwołać się do niej z poziomu aplikacji. Kod połączony ze statyczną biblioteką jest częścią aplikacji — nie trzeba instalować kolejnego pliku w celu użycia kodu.

Ten przewodnik obejmuje następujące zadania:

- [Tworzenie projektu biblioteki statycznej](#CreateLibProject)

- [Dodawanie klasy do biblioteki statycznej](#AddClassToLib)

- [Tworzenie aplikacji C++ konsolowej, która odwołuje się do biblioteki statycznej](#CreateAppToRefTheLib)

- [Korzystanie z funkcji z biblioteki statycznej w aplikacji](#UseLibInApp)

- [Uruchamianie aplikacji](#RunApp)

## <a name="prerequisites"></a>Wymagania wstępne

Zrozumienie podstaw C++ języka.

##  <a name="creating-a-static-library-project"></a><a name="CreateLibProject"></a>Tworzenie projektu biblioteki statycznej

Instrukcje dotyczące sposobu tworzenia projektu różnią się w zależności od tego, czy używasz programu Visual Studio 2019 czy starszej wersji. Upewnij się, że masz poprawną wersję ustawioną w lewym górnym rogu tej strony.

::: moniker range="vs-2019"

### <a name="to-create-a-static-library-project-in-visual-studio-2019"></a>Aby utworzyć projekt biblioteki statycznej w programie Visual Studio 2019

1. Na pasku menu wybierz kolejno opcje **plik** > **Nowy** > **projekt** , aby otworzyć okno dialogowe **Utwórz nowy projekt** .

1. W górnej części okna dialogowego Ustaw **Język** na **C++** , ustaw **platformę** na **system Windows**i ustaw **Typ projektu** na **Biblioteka**.

1. Z listy filtrowane typy projektów wybierz pozycję **Biblioteka statyczna** , a następnie wybierz przycisk **dalej**. Na następnej stronie wprowadź *MathFuncsLib* w polu **Nazwa** , aby określić nazwę projektu, i w razie potrzeby określ lokalizację projektu.

1. Wybierz przycisk **Utwórz** , aby utworzyć projekt klienta.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-static-library-project-in-visual-studio-2017"></a>Aby utworzyć projekt biblioteki statycznej w programie Visual Studio 2017

1. Na pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

1. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **zainstalowane** > **C++Wizualizacja**, a następnie wybierz pozycję **Windows Desktop**. W środkowym okienku wybierz pozycję **Kreator pulpitu systemu Windows**.

1. Określ nazwę dla projektu — na przykład *MathFuncsLib*— w polu **Nazwa** . Określ nazwę dla rozwiązania — na przykład *StaticLibrary*— w polu **Nazwa rozwiązania** . Wybierz przycisk **OK** .

1. W obszarze **Typ aplikacji**wybierz pozycję **Biblioteka statyczna (. lib)** .

1. W obszarze **Opcje dodatkowe**Usuń zaznaczenie pola wyboru **prekompilowany nagłówek** .

1. Wybierz **przycisk OK** , aby utworzyć projekt.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-static-library-project-in-visual-studio-2015"></a>Aby utworzyć projekt biblioteki statycznej w programie Visual Studio 2015

1. Na pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

1. W oknie dialogowym **Nowy projekt** rozwiń węzeł **zainstalowane** > **Szablony** > **Wizualizacja C++** , a następnie wybierz opcję **Win32**. W środkowym okienku wybierz pozycję **aplikacja konsoli Win32**.

1. Określ nazwę dla projektu — na przykład *MathFuncsLib*— w polu **Nazwa** . Określ nazwę dla rozwiązania — na przykład *StaticLibrary*— w polu **Nazwa rozwiązania** . Wybierz przycisk **OK** .

1. Kliknij przycisk **Dalej**.

1. W obszarze **Typ aplikacji**wybierz pozycję **Biblioteka statyczna**. Następnie usuń zaznaczenie pola **prekompilowanego nagłówka** i wybierz pozycję **Zakończ**.

::: moniker-end

##  <a name="adding-a-class-to-the-static-library"></a><a name="AddClassToLib"></a>Dodawanie klasy do biblioteki statycznej

### <a name="to-add-a-class-to-the-static-library"></a>Aby dodać klasę do biblioteki statycznej

1. Aby utworzyć plik nagłówka dla nowej klasy, otwórz menu skrótów dla projektu **MathFuncsLib** w **Eksplorator rozwiązań**, a następnie wybierz **Dodaj** > **nowy element**. W oknie dialogowym **Dodaj nowy element** w lewym okienku w obszarze **C++Wizualizacja**wybierz pozycję **kod**. W środkowym okienku wybierz pozycję **plik nagłówka (. h)** . Określ nazwę pliku nagłówka — na przykład *MathFuncsLib. h*— a następnie wybierz przycisk **Dodaj** . Zostanie wyświetlony pusty plik nagłówkowy.

1. Dodaj klasę o nazwie `MyMathFuncs`, aby wykonywać typowe operacje matematyczne, takie jak dodawanie, odejmowanie, mnożenie i dzielenie. Kod powinien wyglądać następująco:

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#100](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_1.h)]

1. Aby utworzyć plik źródłowy dla nowej klasy, otwórz menu skrótów dla projektu **MathFuncsLib** w **Eksplorator rozwiązań**, a następnie wybierz **Dodaj** > **nowy element**. W oknie dialogowym **Dodaj nowy element** w lewym okienku w obszarze **C++Wizualizacja**wybierz pozycję **kod**. W środkowym okienku wybierz pozycję  **C++ plik (. cpp)** . Określ nazwę pliku źródłowego — na przykład *MathFuncsLib. cpp*, a następnie wybierz przycisk **Dodaj** . Zostanie wyświetlony pusty plik źródłowy.

1. Ten plik źródłowy służy do implementowania funkcji dla **MyMathFuncs**. Kod powinien wyglądać następująco:

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#110](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_2.cpp)]

1. Skompiluj bibliotekę statyczną, wybierając pozycję **kompiluj** > **Kompiluj rozwiązanie** na pasku menu. Kompilowanie tworzy bibliotekę statyczną, która może być używana przez inne programy.

   > [!NOTE]
   > Podczas kompilowania w wierszu polecenia programu Visual Studio należy skompilować program w dwóch krokach. Najpierw uruchom `cl /c /EHsc MathFuncsLib.cpp`, aby skompilować kod i utworzyć plik obiektu o nazwie `MathFuncsLib.obj`. (`cl` polecenie wywołuje kompilator, CL. exe, a opcja `/c` określa kompilację bez konsolidacji. Aby uzyskać więcej informacji, zobacz [/c (Kompiluj bez konsolidacji)](../build/reference/c-compile-without-linking.md). Następnie uruchom `lib MathFuncsLib.obj`, aby połączyć kod i utworzyć `MathFuncsLib.lib`biblioteki statycznej. (`lib` polecenie wywołuje Menedżera bibliotek, lib. exe. Aby uzyskać więcej informacji, zobacz [Dokumentacja biblioteki lib](../build/reference/lib-reference.md).

##  <a name="creating-a-c-console-app-that-references-the-static-library"></a><a name="CreateAppToRefTheLib"></a>Tworzenie aplikacji C++ konsolowej, która odwołuje się do biblioteki statycznej

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2019"></a>Aby utworzyć aplikację C++ konsolową, która odwołuje się do biblioteki statycznej w programie Visual Studio 2019

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy górny węzeł rozwiązania i wybierz polecenie **Dodaj** > **Nowy projekt** , aby otworzyć okno dialogowe **Dodawanie nowego projektu** .

1. W górnej części okna dialogowego Ustaw **Język** na **C++** , ustaw **platformę** na **system Windows**i ustaw **Typ projektu** na **Console**.

1. Z listy filtrowane typy projektów wybierz pozycję **Aplikacja konsolowa** , a następnie wybierz przycisk **dalej**. Na następnej stronie wprowadź *MyExecRefsLib* w polu **Nazwa** , aby określić nazwę projektu, i w razie potrzeby określ lokalizację projektu.

1. Wybierz przycisk **Utwórz** , aby utworzyć projekt klienta.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2017"></a>Aby utworzyć aplikację C++ konsolową, która odwołuje się do biblioteki statycznej w programie Visual Studio 2017

1. Na pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

1. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **zainstalowane** > **C++Wizualizacja**, a następnie wybierz pozycję **Windows Desktop**. W środkowym okienku wybierz pozycję **Kreator pulpitu systemu Windows**.

1. Określ nazwę dla projektu — na przykład *MyExecRefsLib*— w polu **Nazwa** . Z listy rozwijanej obok pozycji **rozwiązanie**wybierz pozycję **Dodaj do rozwiązania**. Polecenie dodaje nowy projekt do rozwiązania, które zawiera bibliotekę statyczną. Wybierz przycisk **OK** .

1. W obszarze **Typ aplikacji**wybierz pozycję **Aplikacja konsolowa (. exe)** .

1. W obszarze **Opcje dodatkowe**Usuń zaznaczenie pola wyboru **prekompilowany nagłówek** .

1. Wybierz **przycisk OK** , aby utworzyć projekt.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2015"></a>Aby utworzyć aplikację C++ konsolową, która odwołuje się do biblioteki statycznej w programie Visual Studio 2015

1. Na pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

1. W oknie dialogowym **Nowy projekt** rozwiń węzeł **zainstalowane** > **Szablony** > **Wizualizacja C++** , a następnie wybierz opcję **Win32**. W środkowym okienku wybierz pozycję **aplikacja konsoli Win32**.

1. Określ nazwę dla projektu — na przykład *MyExecRefsLib*— w polu **Nazwa** . Z listy rozwijanej obok pozycji **rozwiązanie**wybierz pozycję **Dodaj do rozwiązania**. Polecenie dodaje nowy projekt do rozwiązania, które zawiera bibliotekę statyczną. Wybierz przycisk **OK** .

1. Kliknij przycisk **Dalej**.

1. Upewnij się, że wybrano **aplikację konsolową** . Następnie zaznacz pole **pusty projekt** i wybierz pozycję **Zakończ**.

::: moniker-end

##  <a name="using-the-functionality-from-the-static-library-in-the-app"></a><a name="UseLibInApp"></a>Korzystanie z funkcji z biblioteki statycznej w aplikacji

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>Aby użyć funkcji z biblioteki statycznej w aplikacji

1. Po utworzeniu aplikacji konsolowej zostanie utworzony pusty program. Nazwa pliku źródłowego jest taka sama jak nazwa, którą wybrano wcześniej. W tym przykładzie nazywa się `MyExecRefsLib.cpp`.

1. Aby można było użyć procedur matematycznych w bibliotece statycznej, należy odwołać się do niej. Otwórz menu skrótów dla projektu **MyExecRefsLib** w **Eksplorator rozwiązań**, a następnie wybierz **Dodaj** **odwołanie** > .

1. Okno dialogowe **Dodaj odwołanie** zawiera listę bibliotek, do których można się odwołać. Karta **projekty** zawiera listę projektów w bieżącym rozwiązaniu i wszystkie biblioteki, do których się odwołują. Na karcie **projekty** zaznacz pole wyboru **MathFuncsLib** , a następnie wybierz przycisk **OK** .

1. Aby odwołać się do pliku nagłówkowego `MathFuncsLib.h`, należy zmodyfikować ścieżkę dołączone katalogów. W oknie dialogowym **strony właściwości** dla **MyExecRefsLib**rozwiń węzeł **Właściwości konfiguracji** , rozwiń węzeł **C++ C/** , a następnie wybierz pozycję **Ogólne**. Obok pozycji **Dodatkowe katalogi dołączania**określ ścieżkę do katalogu **MathFuncsLib** lub wyszukaj ją.

   Aby wyszukać ścieżkę katalogu, Otwórz listę rozwijaną wartość właściwości, a następnie wybierz pozycję **Edytuj**. W oknie dialogowym **Dodatkowe katalogi dołączane** w polu tekstowym Wybierz pusty wiersz, a następnie wybierz przycisk wielokropka ( **...** ) na końcu wiersza. W oknie dialogowym **Wybierz katalog** wybierz katalog **MathFuncsLib** , a następnie wybierz przycisk **Wybierz folder** , aby zapisać swój wybór i zamknąć okno dialogowe. W oknie dialogowym **Dodatkowe katalogi dołączane** wybierz przycisk **OK** , a następnie w oknie dialogowym **strony właściwości** wybierz przycisk **OK** , aby zapisać zmiany w projekcie.

1. Teraz możesz użyć klasy `MyMathFuncs` w tej aplikacji, dołączając nagłówek `#include "MathFuncsLib.h"` w kodzie. Zastąp zawartość `MyExecRefsLib.cpp` tym kodem:

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#120](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_3.cpp)]

1. Kompiluj plik wykonywalny, wybierając opcję **kompiluj** > **Kompiluj rozwiązanie** na pasku menu.

##  <a name="running-the-app"></a><a name="RunApp"></a>Uruchamianie aplikacji

### <a name="to-run-the-app"></a>Aby uruchomić aplikację

1. Upewnij się, że **MyExecRefsLib** jest wybrany jako domyślny projekt, otwierając menu skrótów dla **MyExecRefsLib** w **Eksplorator rozwiązań**, a następnie wybierając pozycję **Ustaw jako projekt startowy**.

1. Aby uruchomić projekt, na pasku menu wybierz polecenie **debuguj** > **Rozpocznij bez debugowania**. Dane wyjściowe powinny wyglądać następująco:

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>Zobacz też

[Przewodnik: tworzenie i używanie biblioteki dołączanej dynamicznie (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[Aplikacje klasyczne (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
