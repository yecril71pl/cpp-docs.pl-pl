---
title: 'Wskazówki: Tworzenie i używanie własnych dynamicznej biblioteki łącza (C++) | Dokumentacja firmy Microsoft'
ms.custom: conceptual
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19c9c013d591f4c6de14ecd4a2c582d8f0f3e4d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392591"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>Wskazówki: Tworzenie i używanie własnych dynamicznej biblioteki łącza (C++)

Ten przewodnik krok po kroku pokazano, jak używać środowiska IDE programu Visual Studio do tworzenia własnych biblioteki dołączanej (dynamicznie DLL) w języku C++, a następnie użyć go z innej aplikacji C++. Biblioteki DLL są jednym z najbardziej przydatne rodzaje składniki systemu Windows. Można je jako sposobu udostępniania kodu i zasobów, zmniejszyć rozmiar aplikacji oraz ułatwiają usługi i rozszerzenie aplikacji. W tym przewodniku Utwórz bibliotekę DLL, który implementuje niektóre funkcje matematyczne, a następnie utwórz aplikację konsoli, która korzysta z funkcji z biblioteki DLL. Na bieżąco możesz uzyskać wprowadzenie do programowania technik i konwencje stosowane w biblioteki DLL systemu Windows.

Ten przewodnik obejmuje następujące zadania:

- Tworzenie projektu biblioteki DLL w programie Visual Studio.

- Dodaj eksportowane funkcje i zmienne, do pliku DLL.

- Utwórz projekt aplikacji konsoli w programie Visual Studio.

- Korzystając z funkcji i zmienne zaimportowany z biblioteki DLL w aplikacji konsoli.

- Uruchom ukończonej aplikacji.

Statycznie połączone biblioteki DLL, takich jak _eksportuje_ zmienne, funkcje i zasoby wg nazwy oraz aplikacji _importuje_ te nazwy mają być używane te zmienne, funkcje i zasoby. W odróżnieniu od biblioteki statycznie połączonej z systemem Windows Importy w aplikacji łączy się z eksportu w bibliotece DLL w czasie ładowania lub w czasie wykonywania, zamiast łącząc je w momencie łącza. System Windows wymaga informacji dodatkowych, których nie należały do standardowego modelu C++ w kompilacji, aby nawiązać połączenie. Kompilator Visual C++ implementuje niektóre specyficzne dla firmy Microsoft rozszerzenia języka c++, aby podać te informacje dodatkowe. Te rozszerzenia możemy wyjaśniono, jak rozszerzana.

W tym przewodniku tworzy dwa rozwiązań programu Visual Studio. jedną, która tworzy bibliotekę DLL i jedną, która tworzy aplikację klienta. Biblioteki DLL używa konwencji wywoływania C, więc może ona zostać wywołana z aplikacji skompilowanych za pomocą innych języków tak długo, jak platformy i wywoływanie i łączenie konwencje zgodne. Używa aplikacji klient _Konsolidacja niejawna_, gdzie łącza aplikacji systemu Windows w trakcie ładowania biblioteki dll. Umożliwia to aplikacji wywoływać funkcje dostarczony biblioteki DLL, podobnie jak funkcje statycznie połączone biblioteki.

Ten przewodnik nie obejmuje niektóre typowe problemy. Korzystanie z biblioteki DLL języka C++ w innych językach programowania nie była widoczna. Nie wyświetla Tworzenie biblioteki DLL tylko z zasobami. Również nie pokazuje użycie Konsolidacja jawna można załadować biblioteki dll w czasie wykonywania, a nie w czasie ładowania. Możesz mieć pewność, można użyć programu Visual C++ do wykonywania wszystkich tych czynności. Łącza do dodatkowych informacji dotyczących bibliotek DLL, zobacz [biblioteki dll w programie Visual C++](../build/dlls-in-visual-cpp.md). Aby uzyskać więcej informacji na temat Konsolidacja niejawna i Konsolidacja jawna zobacz [określania którego łączenie metody użyć](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use). Aby uzyskać informacje dotyczące tworzenia biblioteki DLL języka C++ do użycia z języków używające konwencjami połączenie języka C programowania, zobacz [eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md). Aby uzyskać informacje o sposobie tworzenia biblioteki DLL dla języków .NET, zobacz [wywoływanie funkcji DLL z aplikacji Visual Basic](../build/calling-dll-functions-from-visual-basic-applications.md).

W tym przewodniku zastosowano 2017 usługi Visual Studio, ale kod i większość instrukcji mają zastosowanie do wcześniejszych wersji. Procedurę tworzenia nowych projektów zmienione w programie Visual Studio 2017 wersji 15 ustęp 3. Ten przewodnik zawiera opis sposobu tworzenia projektów dla zarówno nowszych i starszych wersji. Wyszukaj z procedury odpowiedniej wersji programu Visual Studio.

## <a name="prerequisites"></a>Wymagania wstępne

- Komputer z systemem Microsoft Windows 7 lub nowszy. Zalecamy systemu Windows 10 dla najlepsze środowisko programistyczne.

- Kopia programu Visual Studio 2017 r. Aby uzyskać informacje o tym, jak pobrać i zainstalować program Visual Studio, zobacz [zainstalować program Visual Studio 2017](/visualstudio/install/install-visual-studio). Po uruchomieniu Instalatora, upewnij się, że **tworzenia klasycznych aplikacji w języku C++** obciążenie jest zaznaczony. Nie martw się, należy zainstalować ten obciążenia podczas instalowania programu Visual Studio. Można ponownie uruchomić Instalatora i go teraz zainstalować.

   ![Tworzenie pulpitu za pomocą języka C++](media/desktop-development-with-cpp.png "tworzenia klasycznych aplikacji w języku C++")

- Zrozumienie podstaw przy użyciu programu Visual Studio IDE. Jeśli używano aplikacji klasycznych systemu Windows przed, prawdopodobnie można zachować. Aby obejrzeć wprowadzenie, zobacz [samouczek funkcji programu Visual Studio IDE](/visualstudio/ide/visual-studio-ide).

- Opis wystarczającej podstawy języka C++ w odbiorze. Nie martw się, firma Microsoft nie wykonywać żadnych czynności, zbyt złożony.

## <a name="create-the-dll-project"></a>Tworzenie projektu biblioteki DLL

W tym zestawie zadania utworzenia projektu dla biblioteki DLL, Dodaj kod i skompiluj go. Aby rozpocząć, uruchom środowiska IDE programu Visual Studio, a następnie zaloguj się, jeśli potrzebujesz. Instrukcje dotyczące programu Visual Studio 2017 wersji 15 ustęp 3 znajdować na pierwszym. Instrukcje dotyczące starszych wersji nastąpić później, więc przejść od razu Jeśli potrzebujesz.

### <a name="to-create-a-dll-project-in-visual-studio-2017-version-153-or-later"></a>Aby utworzyć projekt biblioteki DLL w Visual Studio 2017 wersji 15.3 lub nowszej

1. Na pasku menu wybierz **pliku**, **nowy**, **projektu** otworzyć **nowy projekt** okno dialogowe.

1. W lewym okienku **nowy projekt** okna dialogowego rozwiń **zainstalowana** i **Visual C++** Jeśli wymagane, a następnie wybierz pozycję **Windows Desktop**. W środkowym okienku wybierz **kreatora pulpitu systemu Windows**. Wprowadź `MathLibrary` w **nazwa** pole, aby określić nazwę dla projektu.

   ![Nazwij projekt MathLibrary](media/mathlibrary-new-project-name-153.png "nazwij projekt MathLibrary")

1. Wybierz **OK** przycisk, aby odrzucić **nowy projekt** okna dialogowego i rozpocząć **projekt pulpitu systemu Windows** kreatora.

1. W **projekt pulpitu systemu Windows** kreatora w obszarze **typu aplikacji**, wybierz pozycję **Biblioteka dołączana dynamicznie (dll)**.

   ![Utwórz bibliotekę DLL w Kreatorze projektu pulpitu systemu Windows](media/mathlibrary-desktop-project-wizard-dll.png "Utwórz bibliotekę DLL w Kreatorze projektu pulpitu systemu Windows")

1. Wybierz **OK** przycisk, aby utworzyć projekt.

> [!NOTE]
> Wymagane są dodatkowe kroki w celu rozwiązania problemu w programie Visual Studio 2017 wersji 15 ustęp 3. Wykonaj te instrukcje, aby zobaczyć, jeśli należy wprowadzić tę zmianę.
>
>1. W **Eksploratora rozwiązań**, jeśli nie został jeszcze wybrany, wybierz pozycję **MathLibrary** projektu w obszarze **rozwiązania "MathLibrary"**.
>
>1. Na pasku menu wybierz **projektu**, **właściwości**.
>
>1. W lewym okienku **strony właściwości** okno dialogowe, wybierz opcję **preprocesora** w obszarze **właściwości konfiguracji**, **C/C++**. Sprawdź zawartość **definicje preprocesora** właściwości.<br/><br/>![Sprawdź właściwość definicje preprocesora](media/mathlibrary-153bug-preprocessor-definitions-check.png "Sprawdź właściwość definicje preprocesora")<br/><br/>Jeśli widzisz **MATHLIBRARY&#95;EKSPORTÓW** w **definicje preprocesora** listy, a następnie jest konieczne wprowadzanie zmian. Jeśli widzisz **MathLibrary&#95;EKSPORTÓW** , następnie przejdź do wykonaj następujące kroki.
>
>1. W górnej części **strony właściwości** okna dialogowego, zmień **konfiguracji** listy rozwijanej **wszystkie konfiguracje**.
>
>1. W okienku właściwości wybierz kontrolka listy rozwijanej obok pola edycji **definicje preprocesora**, a następnie wybierz pozycję **Edytuj**.<br/><br/>![Zmień wartość właściwości definicje preprocesora](media/mathlibrary-153bug-preprocessor-definitions-property.png "Edytuj właściwość definicje preprocesora")
>
>1. W górnym okienku **definicje preprocesora** okna dialogowego, Dodaj nowy symbol `MATHLIBRARY_EXPORTS`.<br/><br/>![Dodaj MATHLIBRARY_EXPORTS symbol](media/mathlibrary-153bug-preprocessor-definitions-dialog.png "dodania symbolu MATHLIBRARY_EXPORTS")
>
>1. Wybierz **OK** aby odrzucić **definicje preprocesora** okna dialogowego, a następnie wybierz pozycję **OK** Aby zapisać zmiany we właściwościach projektu.

### <a name="to-create-a-dll-project-in-older-versions-of-visual-studio"></a>Aby utworzyć projekt biblioteki DLL w starszych wersjach programu Visual Studio

1. Na pasku menu wybierz **pliku**, **nowy**, **projektu**.

1. W lewym okienku **nowy projekt** okna dialogowego rozwiń **zainstalowana**, **szablony**i wybierz **Visual C++**, a następnie w Centrum w okienku, wybierz opcję **aplikacji konsoli Win32**. Wprowadź `MathLibrary` w **nazwa** edytować pole, aby określić nazwę dla projektu.

   ![Nazwij projekt MathLibrary](media/mathlibrary-project-name.png "nazwij projekt MathLibrary")

1. Wybierz **OK** przycisk, aby odrzucić **nowy projekt** okna dialogowego i rozpocząć **Kreator aplikacji Win32**.

   ![Omówienie Kreator aplikacji Win32](media/mathlibrary-project-wizard-1.png "omówienie Kreator aplikacji Win32")

1. Wybierz **dalej** przycisku. Na **ustawienia aplikacji** w obszarze **typu aplikacji**, wybierz pozycję **DLL**.

   ![Utwórz bibliotekę DLL w Kreator aplikacji Win32](media/mathlibrary-project-wizard-2.png "Tworzenie biblioteki DLL w Kreator aplikacji Win32")

1. Wybierz **Zakończ** przycisk, aby utworzyć projekt.

Po zakończeniu działania kreatora rozwiązania widać plików projektu i źródło wygenerowanych w **Eksploratora rozwiązań** okna w programie Visual Studio.

![Wygenerowany rozwiązania w programie Visual Studio](media/mathlibrary-solution-explorer-153.png "wygenerowany rozwiązania w programie Visual Studio")

Prawo teraz tej biblioteki DLL nie bardzo. Następnie utwórz plik nagłówka do zadeklarowania funkcji biblioteki DLL eksportuje, a następnie dodaj definicje funkcji plik dll, aby był bardziej użyteczne.

### <a name="to-add-a-header-file-to-the-dll"></a>Aby dodać plik nagłówka biblioteki dll

1. Aby utworzyć plik nagłówka dla funkcji, na pasku menu, wybierz **projektu**, **Dodaj nowy element**.

1. W **Dodaj nowy element** okno dialogowe, w okienku po lewej stronie wybierz **Visual C++**. W środkowym okienku wybierz **plik nagłówków (.h)**. Określ `MathLibrary.h` jako nazwę pliku nagłówka.

   ![Dodaj nagłówek w oknie dialogowym Dodawanie nowego elementu](media/mathlibrary-add-new-item-header-file.png "Dodaj nagłówek pliku w oknie dialogowym Dodawanie nowego elementu")

1. Wybierz **Dodaj** przycisk, aby wygenerować plik pusty nagłówek, który jest wyświetlany w nowym oknie edytora.

   ![Pusty plik MathLibrary.h w edytorze](media/edit-empty-mathlibrary-header.png "MathLibrary.h pusty plik w edytorze")

1. Zastąp zawartość pliku nagłówka ten kod:

   ```cpp
   // MathLibrary.h - Contains declarations of math functions
   #pragma once

   #ifdef MATHLIBRARY_EXPORTS
   #define MATHLIBRARY_API __declspec(dllexport)
   #else
   #define MATHLIBRARY_API __declspec(dllimport)
   #endif

   // The Fibonacci recurrence relation describes a sequence F
   // where F(n) is { n = 0, a
   //               { n = 1, b
   //               { n > 1, F(n-2) + F(n-1)
   // for some initial integral values a and b.
   // If the sequence is initialized F(0) = 1, F(1) = 1,
   // then this relation produces the well-known Fibonacci
   // sequence: 1, 1, 2, 3, 5, 8, 13, 21, 34, ...

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   extern "C" MATHLIBRARY_API void fibonacci_init(
       const unsigned long long a, const unsigned long long b);

   // Produce the next value in the sequence.
   // Returns true on success and updates current value and index;
   // false on overflow, leaves current value and index unchanged.
   extern "C" MATHLIBRARY_API bool fibonacci_next();

   // Get the current value in the sequence.
   extern "C" MATHLIBRARY_API unsigned long long fibonacci_current();

   // Get the position of the current value in the sequence.
   extern "C" MATHLIBRARY_API unsigned fibonacci_index();
   ```

Ten plik nagłówka deklaruje niektóre funkcje do tworzenia uogólniony sekwencji Fibonacci danego dwóch wartości początkowej. Wywołanie `fibonacci_init(1, 1)` generuje znanych Fibonacci numer sekwencji.

Zwróć uwagę, preprocesora instrukcje w górnej części pliku. Domyślnie dodaje nowy projekt szablonu dla biblioteki DLL ***PROJECTNAME *&#95;EKSPORTÓW** do zdefiniowanego makra preprocesora dla projektu biblioteki DLL. W tym przykładzie definiuje Visual Studio **MATHLIBRARY&#95;EKSPORTÓW** po utworzeniu projektu MathLibrary biblioteki DLL. (Kreatora w programie Visual Studio 2017 wersji 15 ustęp 3 nie wymusza definicji symbolu, aby wielkimi literami. Jeśli nazwy projektu "MathLibrary", symbol zdefiniowany jest MathLibrary&#95;EKSPORTÓW zamiast MATHLIBRARY&#95;eksportu. That's Dlaczego istnieją dodatkowe kroki opisane powyżej, aby dodać ten symbol.)

Podczas **MATHLIBRARY&#95;EKSPORTÓW** makro jest zdefiniowany, **MATHLIBRARY&#95;interfejsu API** zestawy makro `__declspec(dllexport)` modyfikatora w deklaracji funkcji. Modyfikator informuje kompilator i konsolidator, aby wyeksportować funkcji lub zmienna z biblioteki DLL, dzięki czemu mogą być używane przez inne aplikacje. Gdy **MATHLIBRARY&#95;EKSPORTUJE** jest niezdefiniowana, na przykład, gdy plik nagłówka jest dołączony przez aplikację klienta **MATHLIBRARY&#95;interfejsu API** stosuje `__declspec(dllimport)` modyfikator do deklaracje. Modyfikator optymalizuje importu funkcji lub zmienna w aplikacji. Aby uzyskać więcej informacji, zobacz [dllexport i dllimport](../cpp/dllexport-dllimport.md).

### <a name="to-add-an-implementation-to-the-dll"></a>Aby dodać implementację biblioteki dll

1. W oknie edytora, wybierz kartę **MathLibrary.cpp** Jeśli jest już otwarty. W przeciwnym razie w **Eksploratora rozwiązań**, otwórz **MathLibrary.cpp** w **pliki źródłowe** folderu **MathLibrary** projektu.

1. W edytorze Zastąp zawartość pliku MathLibrary.cpp następujący kod:

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h"
   #include <utility>
   #include <limits.h>
   #include "MathLibrary.h"

   // DLL internal state variables:
   static unsigned long long previous_;  // Previous value, if any
   static unsigned long long current_;   // Current sequence value
   static unsigned index_;               // Current seq. position

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   void fibonacci_init(
       const unsigned long long a,
       const unsigned long long b)
   {
       index_ = 0;
       current_ = a;
       previous_ = b; // see special case when initialized
   }

   // Produce the next value in the sequence.
   // Returns true on success, false on overflow.
   bool fibonacci_next()
   {
       // check to see if we'd overflow result or position
       if ((ULLONG_MAX - previous_ < current_) ||
           (UINT_MAX == index_))
       {
           return false;
       }

       // Special case when index == 0, just return b value
       if (index_ > 0)
       {
           // otherwise, calculate next sequence value
           previous_ += current_;
       }
       std::swap(current_, previous_);
       ++index_;
       return true;
   }

   // Get the current value in the sequence.
   unsigned long long fibonacci_current()
   {
       return current_;
   }

   // Get the current index position in the sequence.
   unsigned fibonacci_index()
   {
       return index_;
   }
   ```

Aby sprawdzić, czy wszystko działa tak daleko, kompilować biblioteki dołączanej dynamicznie. Aby skompilować, wybierz **kompilacji**, **Kompiluj rozwiązanie** na pasku menu. Dane wyjściowe powinny wyglądać następująco:

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>stdafx.cpp
1>MathLibrary.cpp
1>dllmain.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.pdb (Partial PDB)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Gratulacje, po utworzeniu biblioteki DLL przy użyciu programu Visual C++! Następnie utworzysz aplikację klienta, która korzysta z funkcji wyeksportowane przez bibliotekę DLL.

## <a name="create-a-client-app-that-uses-the-dll"></a>Tworzenie aplikacji klienta, który używa biblioteki DLL

Podczas tworzenia biblioteki DLL muszą myśleć o używaniu biblioteki DLL. Aby skompilować kod, który wywołuje funkcje wyeksportowane przez bibliotekę DLL, deklaracji musi być uwzględniona w kodzie źródłowym klienta. W czasie łącza, gdy te wywołania funkcji biblioteki DLL są rozwiązane, musi mieć konsolidator *Importowanie biblioteki*, specjalny rodzaj plik biblioteki, który zawiera informacje umożliwiające Znajdź funkcje, a nie rzeczywiste kodu dla systemu Windows. I w czasie wykonywania, biblioteki DLL muszą być dostępne dla klienta, w lokalizacji, która znajduje się system operacyjny.

Aby korzystać z biblioteki DLL, czy z właścicielem lub DLL innych firm, projekt aplikacji klienta musi być w stanie odnaleźć eksportuje nagłówki, które deklaruje biblioteki DLL, biblioteki importu dla konsolidatora i biblioteki DLL, sama. Jednym ze sposobów jest skopiować te pliki do projektu client. Biblioteki DLL innych firm, które prawdopodobnie nie można zmienić, gdy klient jest rozwijany może to być najlepszym sposobem korzystania z nich. Podczas tworzenia także biblioteki DLL, zaleca się uniknąć jego duplikowania. Jeśli kopię plików DLL, które są opracowywane, może przypadkowo zmiany w jednej kopii, ale nie dla drugiego pliku nagłówka, lub użycia nieaktualny biblioteki. Aby uniknąć tego problemu, firma Microsoft zaleca się, że ścieżka include jest ustawiony w projekcie klienta, aby uwzględnić pliki nagłówków biblioteki DLL z projektu DLL. Ponadto należy ustawić ścieżkę biblioteki w projekt klienta w celu uwzględnienia bibliotek DLL importu z projektu DLL. A na koniec skopiować zbudowanych biblioteki DLL z projektu DLL do katalogu danych wyjściowych kompilacji. To zapewnia, że Twoja aplikacja kliencka używa tego samego kodu DLL tworzonego.

### <a name="to-create-a-client-app-in-visual-studio-2017-version-153-or-later"></a>Aby utworzyć aplikację klienta w Visual Studio 2017 wersji 15.3 lub nowszej

1. Aby utworzyć aplikację języka C++, która korzysta z biblioteki DLL, nowo utworzony, na pasku menu wybierz polecenie **pliku**, **nowy**, **projektu**.

1. W lewym okienku **nowy projekt** okno dialogowe, wybierz opcję **Windows Desktop** w obszarze **zainstalowana**, **Visual C++**. W środkowym okienku wybierz **kreatora pulpitu systemu Windows**. Określ nazwę dla projektu, `MathClient`w **nazwa** polu edycji.

   ![Nazwij projekt klienta](media/mathclient-new-project-name-153.png "Nazwa projektu klienta")

1. Wybierz **OK** uruchomić **projekt pulpitu systemu Windows** kreatora. W kreatorze Wybierz **OK** do utworzenia projektu aplikacji klienta.

### <a name="to-create-a-client-app-in-older-versions-of-visual-studio-2017"></a>Aby utworzyć aplikację klienta w starszych wersjach programu Visual Studio 2017 r.

1. Aby utworzyć aplikację języka C++, która korzysta z biblioteki DLL, nowo utworzony, na pasku menu wybierz polecenie **pliku**, **nowy**, **projektu**.

1. W lewym okienku **nowy projekt** okno dialogowe, wybierz opcję **Win32** w obszarze **zainstalowana**, **szablony**, **językaVisualC++**. W środkowym okienku wybierz **aplikacji konsoli Win32**. Określ nazwę dla projektu, `MathClient`w **nazwa** polu edycji.

   ![Nazwij projekt klienta](media/mathclient-project-name.png "Nazwa projektu klienta")

1. Wybierz **OK** przycisk, aby odrzucić **nowy projekt** okna dialogowego i rozpocząć **Kreator aplikacji Win32**. Na **omówienie** strony **Kreator aplikacji Win32** oknie dialogowym wybierz **dalej** przycisku.

1. Na **ustawienia aplikacji** w obszarze **typu aplikacji**, wybierz pozycję **aplikacja Konsolowa** Jeśli nie została jeszcze wybrana.

1. Wybierz **Zakończ** przycisk, aby utworzyć projekt.

Po zakończeniu pracy kreatora Projekt aplikacji konsoli minimalnego jest tworzona. Nazwa pliku głównego źródła jest taka sama jak nazwa projektu, wprowadzony wcześniej. W tym przykładzie o nazwie **MathClient.cpp**. Można go utworzyć, ale jeszcze nie używa biblioteki DLL.

Następnie wywołaniem funkcji MathLibrary w kodzie źródłowym projektu musi zawierać plik MathLibrary.h. Można skopiować ten plik nagłówka do projektu aplikacji klienta, a następnie dodaj go do projektu jako istniejący element. Może to być dobry wybór w przypadku bibliotek innych firm. Jednak jeśli pracujesz nad kod dla biblioteki DLL w tym samym czasie jako klienta, który może prowadzić do zmian w jeden nagłówek pliku, które nie są uwzględniane w innym. Aby uniknąć tego problemu, można zmienić **dodatkowe katalogi dołączenia** ścieżki w swoim projekcie zawiera ścieżkę do oryginalnego nagłówka.

### <a name="to-add-the-dll-header-to-your-include-path"></a>Aby dodać nagłówka biblioteki DLL do Twojej zawierają ścieżki

1. Otwórz **strony właściwości** okno dialogowe **MathClient** projektu.

1. W **konfiguracji** listy rozwijanej wybierz pozycję **wszystkie konfiguracje** Jeśli nie została jeszcze wybrana.

1. W okienku po lewej stronie wybierz **ogólne** w obszarze **właściwości konfiguracji**, **C/C++**.

1. W okienku właściwości wybierz kontrolka listy rozwijanej **dodatkowe katalogi dołączenia** pole edycji, a następnie wybierz pozycję **Edytuj**.

   ![Zmień wartość właściwości dodatkowe katalogi dołączenia](media/mathclient-additional-include-directories-property.png "Edytuj właściwość dodatkowe katalogi dołączenia")

1. Kliknij dwukrotnie w górnym okienku **dodatkowe katalogi dołączenia** okno dialogowe umożliwiające kontrolki edycji.

1. W formancie edycyjnym, określ ścieżkę do lokalizacji **MathLibrary.h** pliku nagłówka. W takim przypadku można użyć ścieżki względnej:

   `..\..\MathLibrary\MathLibrary`

   ![Dodaj nagłówek lokalizacji dla właściwości dodatkowe katalogi dołączenia](media/mathclient-additional-include-directories.png "Dodaj lokalizację nagłówka do właściwości dodatkowe katalogi dołączenia")

1. Po wprowadzeniu ścieżka do pliku nagłówka w **dodatkowe katalogi dołączenia** oknie dialogowym wybierz **OK** przycisk, aby powrócić do **strony właściwości** okno dialogowe i następnie wybierz pozycję **OK** przycisk, aby zapisać zmiany.

Obecnie można uwzględnić **MathLibrary.h** plików oraz korzystanie z funkcji deklaruje w aplikacji klienta. Zastąp zawartość **MathClient.cpp** przy użyciu tego kodu:

```cpp
// MathClient.cpp : Client app for MathLibrary DLL.
#include "stdafx.h"
#include <iostream>
#include "MathLibrary.h"

int main()
{
    // Initialize a Fibonacci relation sequence.
    fibonacci_init(1, 1);
    // Write out the sequence values until overflow.
    do {
        std::cout << fibonacci_index() << ": "
            << fibonacci_current() << std::endl;
    } while (fibonacci_next());
    // Report count of values written before overflow.
    std::cout << fibonacci_index() + 1 <<
        " Fibonacci sequence values fit in an " <<
        "unsigned 64-bit integer." << std::endl;
}
```

Ten kod można skompilować, ale nie jest to połączony, ponieważ konsolidator nie można znaleźć biblioteki importu wymagane do tworzenia aplikacji jeszcze. Konsolidator musi umożliwiać można znaleźć pliku MathLibrary.lib, aby połączyć się pomyślnie. Plik MathLibrary.lib należy dodać do kompilacji, ustawiając **dodatkowe zależności** właściwości. Ponownie można skopiować pliku biblioteki do projektu aplikacji klienta, ale jeśli opracowywane są zarówno biblioteki i aplikacji klienckiej, która może prowadzić do zmiany w jednej kopii, które nie są uwzględniane w innym. Aby uniknąć tego problemu, można zmienić **dodatkowe katalogi bibliotek** ścieżki w swoim projekcie zawiera ścieżkę do oryginalna Biblioteka podczas łączenia.

### <a name="to-add-the-dll-import-library-to-your-project"></a>Aby dodać do projektu biblioteki importowanej biblioteki DLL

1. Otwórz **strony właściwości** okno dialogowe **MathClient** projektu.

1. W **konfiguracji** listy rozwijanej wybierz pozycję **wszystkie konfiguracje** Jeśli nie została jeszcze wybrana.

1. W okienku po lewej stronie wybierz **dane wejściowe** w obszarze **właściwości konfiguracji**, **konsolidatora**. W okienku właściwości wybierz kontrolka listy rozwijanej **dodatkowe zależności** pole edycji, a następnie wybierz pozycję **Edytuj**.

   ![Edytuj właściwość dodatkowe zależności](media/mathclient-additional-dependencies-property.png "Edytuj właściwość dodatkowe zależności")

1. W **dodatkowe zależności** okna dialogowego, Dodaj `MathLibrary.lib` do listy w górnym formantu edycyjnego.

   ![Dodaj zależności biblioteki](media/mathclient-additional-dependencies.png "Dodaj zależności biblioteki")

1. Wybierz **OK** aby powrócić do **strony właściwości** okno dialogowe.

1. W okienku po lewej stronie wybierz **ogólne** w obszarze **właściwości konfiguracji**, **konsolidatora**. W okienku właściwości wybierz kontrolka listy rozwijanej **dodatkowe katalogi bibliotek** pole edycji, a następnie wybierz pozycję **Edytuj**.

   ![Zmień wartość właściwości dodatkowe katalogi bibliotek](media/mathclient-additional-library-directories-property.png "Edytuj właściwość dodatkowe katalogi bibliotek")

1. Kliknij dwukrotnie w górnym okienku **dodatkowe katalogi bibliotek** okno dialogowe umożliwiające kontrolki edycji. W formancie edycyjnym, określ ścieżkę do lokalizacji **MathLibrary.lib** pliku. Wprowadź tę wartość, aby użyć makra, który działa w przypadku zarówno Debug i Release kompiluje:

   `..\..\MathLibrary\$(IntDir)`

   ![Dodaj katalog biblioteki](media/mathclient-additional-library-directories.png "Dodaj katalog biblioteki")

1. Po wprowadzeniu ścieżka do pliku biblioteki w **dodatkowe katalogi bibliotek** oknie dialogowym wybierz **OK** przycisk, aby powrócić do **strony właściwości** okno dialogowe.

Aplikację klienta można teraz skompilować i połączyć pomyślnie, ale nadal nie ma on wszystko, co jest potrzebne do uruchomienia. Jeśli system operacyjny ładuje aplikację, szuka MathLibrary DLL. Nie można odnaleźć biblioteki DLL w niektórych katalogów systemu, ścieżka środowiska lub katalogu aplikacji lokalnych, obciążenia nie powiedzie się. Jednym ze sposobów uniknięcia tego problemu jest Kopiuj bibliotekę DLL do katalogu zawierającego plik wykonywalny z klienta jako część procesu kompilacji. Aby skopiować plik DLL, można dodać **zdarzenia Postkompilacyjnego** do projektu, aby dodać polecenie które biblioteki DLL kopiuje do katalogu danych wyjściowych kompilacji. Polecenie określone tutaj kopiuje plik DLL tylko, jeśli nie istnieje lub została zmieniona, a używa makra kopiowania do i z lokalizacji debugowania lub wersji detalicznej poprawne dla danej konfiguracji.

### <a name="to-copy-the-dll-in-a-post-build-event"></a>Aby skopiować biblioteki DLL w zdarzenie mające miejsce po kompilacji

1. Otwórz **strony właściwości** okno dialogowe **MathClient** projektu, jeśli nie jest już otwarty.

1. W polu listy rozwijanej konfiguracji wybierz **wszystkie konfiguracje** Jeśli nie została jeszcze wybrana.

1. W okienku po lewej stronie wybierz **zdarzenia Postkompilacyjnego** w obszarze **właściwości konfiguracji**, **zdarzeń kompilacji**.

1. W okienku właściwości, wybierz w formancie edycyjnym **wiersza polecenia** pola, a następnie wprowadź następujące polecenie:

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   ![Dodaj polecenie postkompilacyjnego](media/mathclient-post-build-command-line.png "Dodaj polecenie mające miejsce po kompilacji")

1. Wybierz **OK** przycisk, aby zapisać zmiany we właściwościach projektu.

Twoja aplikacja kliencka ma teraz wszystko, czego należy go skompilować i uruchomić. Tworzenie aplikacji, wybierając **kompilacji**, **Kompiluj rozwiązanie** na pasku menu. **Dane wyjściowe** okna w programie Visual Studio powinna zawierać mniej więcej tak:

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>stdafx.cpp
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.pdb (Partial PDB)
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Gratulacje, po utworzeniu aplikacji, która wywołuje funkcje w bibliotece DLL. Teraz można uruchomić aplikacji, aby zobaczyć, jakie operacje. Na pasku menu wybierz **debugowania**, **uruchomić bez debugowania**. Visual Studio zostanie otwarte okno polecenia do uruchomienia programu. Ostatnia część dane wyjściowe powinny wyglądać następująco:

![Uruchomienie aplikacji klienckiej bez debugowania](media/mathclient-run-without-debugging.png "uruchomienie aplikacji klienckiej bez debugowania")

Naciśnij dowolny klawisz, aby zamknąć okno wiersza poleceń.

Teraz, po utworzeniu biblioteki DLL i aplikacji klienckiej, możesz eksperymentować. Spróbuj ustawić punkty przerwania w kodzie aplikacji klienckiej i uruchamianie aplikacji w debugerze. Zobacz, co się stanie po kroku do wywołania biblioteki. Dodawanie innych funkcji do biblioteki lub innej aplikacji klienta, który korzysta z biblioteki DLL do zapisu.

Podczas wdrażania aplikacji, należy wdrożyć używa bibliotek DLL. Najprostszym sposobem, aby udostępnić bibliotek DLL, podczas tworzenia lub wprowadzeniem innych firm do aplikacji jest nazywane również umieścić je w tym samym katalogu co aplikacja, *wdrożenia lokalnej dla aplikacji*. Aby uzyskać więcej informacji na temat wdrażania, zobacz [wdrożenia w programie Visual C++](..\ide\deployment-in-visual-cpp.md).

## <a name="see-also"></a>Zobacz też

[Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)  
[Wdrażanie natywnych aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)  
[Przewodnik: wdrażanie Twojego programu (C++)](../ide/walkthrough-deploying-your-program-cpp.md)  
[Wywoływanie funkcji DLL z aplikacji języka Visual Basic](../build/calling-dll-functions-from-visual-basic-applications.md)