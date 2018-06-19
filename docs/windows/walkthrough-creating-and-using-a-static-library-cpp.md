---
title: 'Wskazówki: Tworzenie i używanie biblioteki statycznej (C++) | Dokumentacja firmy Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d136dae553f623cbd607a69ab710fa9c6fe6c91b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891584"
---
# <a name="walkthrough-creating-and-using-a-static-library-c"></a>Wskazówki: tworzenie i używanie biblioteki statycznej (C++)
Ten przewodnik krok po kroku przedstawiono sposób tworzenia biblioteki statycznej (pliku lib) do użytku z aplikacjami C++. Używanie biblioteki statycznej jest to dobry sposób na ponowne użycie kodu. Zamiast ponownego wykonywania tej samej procedury w każdej aplikacji, która wymaga funkcji, zapisze je jeden raz w bibliotece statycznej i odwoływanie się z aplikacji. Kod powiązany z biblioteką statyczną staje się częścią aplikacji — nie trzeba zainstalować inny plik do kodu.  
  
 Ten przewodnik obejmuje następujące zadania:  
  
-   [Tworzenie projektu biblioteki statycznej](#BKMK_CreateLibProject)  
  
-   [Dodawanie klasy z biblioteką statyczną](#BKMK_AddClassToLib)  
  
-   [Tworzenie aplikacji konsoli C++, która odwołuje się do biblioteki statycznej](#BKMK_CreateAppToRefTheLib)  
  
-   [Korzystając z funkcji z biblioteki statycznej w aplikacji](#BKMK_UseLibInApp)  
  
-   [Aplikację](#BKMK_RunApp)  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Po zrozumieniu podstaw języka C++.  
  
##  <a name="BKMK_CreateLibProject"></a> Tworzenie projektu biblioteki statycznej  
  
#### <a name="to-create-a-static-library-project"></a>Aby utworzyć projekt biblioteki statycznej  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  W lewym okienku **nowy projekt** okna dialogowego rozwiń **zainstalowana**, **szablony**, **Visual C++**, a następnie wybierz  **Win32**.  
  
3.  W środkowym okienku wybierz **aplikacji konsoli Win32**.  
  
4.  Określ nazwę dla projektu — na przykład **MathFuncsLib**— w **nazwa** pole. Określ nazwę dla rozwiązania — na przykład **StaticLibrary**— w **Nazwa rozwiązania** pole. Wybierz **OK** przycisku.  
  
5.  Na **omówienie** strony **Kreator aplikacji Win32** oknie dialogowym wybierz **dalej** przycisku.  
  
6.  Na **ustawienia aplikacji** w obszarze **typu aplikacji**, wybierz pozycję **biblioteki statycznej.**  
  
7.  Na **ustawienia aplikacji** w obszarze **dodatkowe opcje**, wyczyść **Prekompilowanego nagłówka** pole wyboru.  
  
8.  Wybierz **Zakończ** przycisk, aby utworzyć projekt.  
  
##  <a name="BKMK_AddClassToLib"></a> Dodawanie klasy z biblioteką statyczną  
  
#### <a name="to-add-a-class-to-the-static-library"></a>Aby dodać klasę z biblioteką statyczną  
  
1.  Aby utworzyć plik nagłówka dla nowej klasy, otwórz menu skrótów dla **MathFuncsLib** projektu w **Eksploratora rozwiązań**, a następnie wybierz pozycję **Dodaj**, **nowy element** . W **Dodaj nowy element** okna dialogowego, w lewym okienku w obszarze **Visual C++**, wybierz pozycję **kod**. W środkowym okienku wybierz **plik nagłówków (.h)**. Określ nazwę pliku nagłówka — na przykład **MathFuncsLib.h**— a następnie wybierz pozycję **Dodaj** przycisku. Plik pusty nagłówek jest wyświetlany.  
  
2.  Dodaj klasę o nazwie **MyMathFuncs** celu typowych operacji matematycznych, takich jak dodawanie, odejmowanie mnożenia i dzielenia. Kod powinien wyglądać następująco:  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#100](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_1.h)]  
  
3.  Aby utworzyć plik źródłowy dla nowej klasy, otwórz menu skrótów **MathFuncsLib** projektu w **Eksploratora rozwiązań**, a następnie wybierz pozycję **Dodaj**, **nowy element** . W **Dodaj nowy element** okna dialogowego, w lewym okienku w obszarze **Visual C++**, wybierz pozycję **kod**. W środkowym okienku wybierz **plik C++ (.cpp)**. Określ nazwę pliku źródłowego — na przykład **MathFuncsLib.cpp**— a następnie wybierz pozycję **Dodaj** przycisku. Plik źródłowy puste, zostanie wyświetlony.  
  
4.  Używanie tego pliku źródłowego do implementowania **MyMathFuncs**. Kod powinien wyglądać następująco:  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#110](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_2.cpp)]  
  
5.  Kompilowanie biblioteki statycznej, wybierając **kompilacji**, **Kompiluj rozwiązanie** na pasku menu. Spowoduje to utworzenie bibliotekę statyczną, które mogą być używane przez inne programy.  
  
    > [!NOTE]
    >  Podczas kompilowania w wierszu polecenia programu Visual Studio, należy utworzyć program w dwóch krokach. Najpierw uruchom **/ehsc /c cl MathFuncsLib.cpp** skompilować kod i Utwórz plik obiektu o nazwie **MathFuncsLib.obj**. ( **Cl** polecenia wywołuje kompilator Cl.exe i **/c** opcja określa Kompiluj bez konsolidacji. Aby uzyskać więcej informacji, zobacz [/c (Kompiluj bez konsolidacji)](../build/reference/c-compile-without-linking.md).) Po drugie, uruchom **lib MathFuncsLib.obj** link kodu i tworzenia biblioteki statycznej **MathFuncsLib.lib**. ( **Lib** Library Manager Lib.exe wywołuje polecenie. Aby uzyskać więcej informacji, zobacz [odwołanie do biblioteki LIB](../build/reference/lib-reference.md).)  
  
##  <a name="BKMK_CreateAppToRefTheLib"></a> Tworzenie aplikacji konsoli C++, która odwołuje się do biblioteki statycznej  
  
#### <a name="to-create-a-c-console-app-that-references-the-static-library"></a>Aby utworzyć aplikację konsoli języka C++, która odwołuje się do biblioteki statycznej  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  W lewym okienku w obszarze **Visual C++**, wybierz pozycję **Win32**.  
  
3.  W środkowym okienku wybierz **aplikacji konsoli Win32**.  
  
4.  Określ nazwę dla projektu — na przykład **MyExecRefsLib**— w **nazwa** pole. W polu listy rozwijanej obok pozycji listy **rozwiązania**, wybierz pozycję **dodać do rozwiązania**. Spowoduje to dodanie nowego projektu do rozwiązania, które zawiera biblioteki statycznej. Wybierz **OK** przycisku.  
  
5.  Na **omówienie** strony **Kreator aplikacji Win32** oknie dialogowym wybierz **dalej** przycisku.  
  
6.  Na **ustawienia aplikacji** w obszarze **typu aplikacji**, wybierz pozycję **aplikacja Konsolowa**.  
  
7.  Na **ustawienia aplikacji** w obszarze **dodatkowe opcje**, wyczyść **Prekompilowanego nagłówka** pole wyboru.  
  
8.  Wybierz **Zakończ** przycisk, aby utworzyć projekt.  
  
##  <a name="BKMK_UseLibInApp"></a> Korzystając z funkcji z biblioteki statycznej w aplikacji  
  
#### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>Aby korzystać z funkcji z biblioteki statycznej w aplikacji  
  
1.  Po utworzeniu aplikacji konsoli programu pusty jest tworzona. Nazwa pliku źródłowego jest taka sama jak nazwa, które wcześniej wybrano. W tym przykładzie o nazwie **MyExecRefsLib.cpp**.  
  
2.  Przed użyciem procedury matematyczne w bibliotece statycznej, musi odwoływać się go. Aby to zrobić, otwórz menu skrótów **MyExecRefsLib** projektu w **Eksploratora rozwiązań**, a następnie wybierz pozycję **odwołania**. W **stron MyExecRefsLibProperty** okna dialogowego rozwiń **wspólne właściwości** węzła, wybierz opcję **Framework i odwołania**, a następnie wybierz **Dodaj Nowe odwołanie** przycisku. Aby uzyskać więcej informacji na temat **odwołania** okno dialogowe, zobacz [Dodawanie odwołań](../ide/adding-references-in-visual-cpp-projects.md).  
  
3.  **Dodaj odwołanie** okno dialogowe zawiera listę bibliotek, których można się odwołać. **Projekty** kartę Lista projektów w bieżącym rozwiązaniu i żadnych bibliotek, które zawierają. Na **projekty** wybierz opcję **MathFuncsLib** pole wyboru, a następnie wybierz pozycję **OK** przycisku.  
  
4.  Aby odwołać się do **MathFuncsLib.h** pliku nagłówka, należy zmodyfikować katalogi uwzględniona ścieżka. W **strony właściwości** okno dialogowe **MyExecRefsLib**, rozwiń węzeł **właściwości konfiguracji** węzła, rozwiń węzeł **C/C++** węzeł, i następnie wybierz **ogólne**. Obok pozycji **dodatkowe katalogi dołączenia**, podaj ścieżkę pliku **MathFuncsLib** katalogu lub wyszukaj go.  
  
     Aby przeglądać w poszukiwaniu ścieżki katalogu, otwarcie listy rozwijanej wartości właściwości, a następnie wybierz **Edytuj**. W **dodatkowe katalogi dołączenia** okno dialogowe, w polu tekstowym wybierz pusty wiersz, a następnie wybierz przycisk wielokropka (**...** ) na końcu linii. W **wybierz katalog** okno dialogowe, wybierz **MathFuncsLib** katalogu, a następnie wybierz **wybierz Folder** przycisk, aby zapisać wybrane opcje i zamknąć okno dialogowe. W **dodatkowe katalogi dołączenia** okna dialogowego wybierz **OK** przycisk, a następnie w **strony właściwości** okno dialogowe Wybierz **OK**przycisk, aby zapisać zmiany w projekcie.  
  
5.  Można teraz używać **MyMathFuncs** klasy w tej aplikacji. Aby to zrobić, Zamień zawartość **MyExecRefsLib.cpp** o tym kodzie:  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#120](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_3.cpp)]  
  
6.  Tworzenie pliku wykonywalnego, wybierając **kompilacji**, **Kompiluj rozwiązanie** na pasku menu.  
  
##  <a name="BKMK_RunApp"></a> Aplikację  
  
#### <a name="to-run-the-app"></a>Aby uruchomić aplikację  
  
1.  Upewnij się, że **MyExecRefsLib** został wybrany jako domyślny projekt, otwierając menu skrótów **MyExecRefsLib** w **Eksploratora rozwiązań**, a następnie wybierając  **Ustaw jako projekt startowy**.  
  
2.  Aby uruchomić projekt, na pasku menu, wybierz **debugowania**, **uruchomić bez debugowania**. Wynik powinien przypominać poniższe:  
  
    ```Output  
    a + b = 106.4  
    a - b = -91.6  
    a * b = 732.6  
    a / b = 0.0747475  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Tworzenie i używanie biblioteki dołączanej dynamicznie (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)   
 [Aplikacje klasyczne (Visual C++)](../windows/desktop-applications-visual-cpp.md)