---
title: 'Przewodnik: Tworzenie własnej biblioteki dołączanej dynamicznie (C++) i korzystanie z niej'
description: Służy C++ do tworzenia biblioteki dołączanej dynamicznie (dll) systemu Windows w programie Visual Studio.
ms.custom: conceptual
ms.date: 08/19/2019
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
ms.openlocfilehash: 9dffec9d7d974ceb3bf1ca4546a303fab47ee0be
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630681"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>Przewodnik: Tworzenie własnej biblioteki dołączanej dynamicznie (C++) i korzystanie z niej

W tym przewodniku krok po kroku przedstawiono sposób użycia środowiska IDE programu Visual Studio do utworzenia własnej biblioteki dołączanej dynamicznie (DLL), C++która jest zapisywana w programie, C++ a następnie użycie jej z innej aplikacji. Biblioteki DLL (nazywane również bibliotekami udostępnionymi w systemach operacyjnych opartych na systemie UNIX) są jednym z najbardziej przydatnych rodzajów składników systemu Windows. Można ich używać jako metody udostępniania kodu i zasobów, zmniejszania rozmiaru aplikacji oraz ułatwiania obsługi i zwiększania liczby aplikacji. W tym instruktażu utworzysz bibliotekę DLL, która implementuje niektóre funkcje matematyczne, a następnie utworzysz aplikację konsolową, która używa funkcji z biblioteki DLL. W ten sposób wprowadzamy wprowadzenie do niektórych technik programowania i Konwencji używanych w bibliotekach DLL systemu Windows.

Ten przewodnik obejmuje następujące zadania:

- Utwórz projekt DLL w programie Visual Studio.

- Dodaj eksportowane funkcje i zmienne do biblioteki DLL.

- Utwórz projekt aplikacji konsolowej w programie Visual Studio.

- Użyj funkcji i zmiennych zaimportowanych z biblioteki DLL w aplikacji konsolowej.

- Uruchom ukończoną aplikację.

Podobnie jak statycznie połączone biblioteki, biblioteka DLL _eksportuje_ zmienne, funkcje i zasoby według nazwy, a Twoja aplikacja _importuje_ te nazwy do korzystania z tych zmiennych, funkcji i zasobów. W przeciwieństwie do biblioteki połączonej statycznie, system Windows łączy Importy w aplikacji z eksportami w bibliotece DLL w czasie ładowania lub w czasie wykonywania, zamiast łączyć je w czasie łączenia. System Windows wymaga dodatkowych informacji, które nie są częścią standardowego C++ modelu kompilacji do nawiązywania tych połączeń. Kompilator MSVC implementuje Niektóre rozszerzenia specyficzne dla firmy Microsoft w C++ celu zapewnienia tych dodatkowych informacji. Te rozszerzenia są wyjaśnione w miarę rzeczywistym.

Ten Instruktaż tworzy dwa rozwiązania Visual Studio; Ta, która kompiluje bibliotekę DLL, i która kompiluje aplikację kliencką. Biblioteka DLL używa konwencji wywoływania języka C, aby można ją było wywołać z aplikacji skompilowanych przy użyciu innych języków, o ile jest zgodne z platformą i konwencjami łączenia i połączeń. Aplikacja kliencka używa _niejawnego łączenia_, gdzie system Windows łączy aplikację z biblioteką DLL w czasie ładowania. To łączenie umożliwia aplikacji wywoływanych przez biblioteki DLL funkcje, podobnie jak funkcje w bibliotece połączonej statycznie.

Ten Instruktaż nie obejmuje niektórych typowych sytuacji. Nie pokazuje on użycia C++ bibliotek DLL przez inne języki programowania. Nie pokazuje, jak utworzyć bibliotekę DLL tylko do zasobów. Nie pokazuje również użycia jawnego łączenia do ładowania bibliotek DLL w czasie wykonywania, a nie w czasie ładowania. Zapewniona reszta, możesz użyć programu Visual Studio, aby wykonać wszystkie te czynności. Aby uzyskać linki do dodatkowych informacji o bibliotekach DLL, zobacz [Tworzenie C/C++ dll w programie Visual Studio](dlls-in-visual-cpp.md). Aby uzyskać więcej informacji na temat niejawnego łączenia i jawnego łączenia, zobacz [Określanie, która Metoda łączenia ma być używana](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use). Aby uzyskać informacje na C++ temat tworzenia bibliotek DLL do użycia z językami programowania, które używają Konwencji połączeń języka c, zobacz [Eksportowanie C++ funkcji do użycia w plikach wykonywalnych języka c](exporting-cpp-functions-for-use-in-c-language-executables.md). Aby uzyskać informacje o sposobach tworzenia bibliotek DLL do użycia w językach .NET, zobacz [wywoływanie funkcji DLL z aplikacji Visual Basic](calling-dll-functions-from-visual-basic-applications.md).

## <a name="prerequisites"></a>Wymagania wstępne

- Komputer z systemem Microsoft Windows 7 lub nowszym. Zalecamy użycie systemu Windows 10 w celu uzyskania najlepszego środowiska programistycznego.

- Kopia programu Visual Studio. Aby uzyskać informacje na temat pobierania i instalowania programu Visual Studio, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio). Po uruchomieniu Instalatora upewnij się, że jest zaznaczone pole **programowanie opracowywania C++ aplikacji klasycznych** . Nie martw się, jeśli to obciążenie nie zostało zainstalowane podczas instalacji programu Visual Studio. Możesz ponownie uruchomić Instalatora i zainstalować go teraz.

   ![Programowanie aplikacji C++ klasycznych](media/desktop-development-with-cpp.png "Programowanie aplikacji C++ klasycznych")

- Zrozumienie podstaw korzystania ze środowiska IDE programu Visual Studio. Jeśli wcześniej używasz aplikacji klasycznych systemu Windows, prawdopodobnie Zadbaj o to. Aby zapoznać się z wprowadzeniem, zobacz [Przewodnik po funkcji środowiska IDE programu Visual Studio](/visualstudio/ide/visual-studio-ide).

- Zrozumienie wystarczającej podstawy C++ języka do wykonania. Nie martw się, nie wykonujemy żadnych zbyt skomplikowane.

## <a name="create-the-dll-project"></a>Tworzenie projektu DLL

W tym zestawie zadań można utworzyć projekt dla biblioteki DLL, dodać kod i skompilować go. Aby rozpocząć, uruchom środowisko IDE programu Visual Studio i zaloguj się, jeśli zachodzi taka potrzeba. Instrukcje różnią się nieco w zależności od używanej wersji programu Visual Studio. Upewnij się, że w kontrolce w lewym górnym rogu tej strony została wybrana prawidłowa wersja.

::: moniker range="=vs-2019"

### <a name="to-create-a-dll-project-in-visual-studio-2019"></a>Aby utworzyć projekt DLL w programie Visual Studio 2019

1. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt** , aby otworzyć okno dialogowe **Tworzenie nowego projektu** .

   ![Utwórz nowy projekt DLL](media/create-new-dll-project-2019.png "Tworzenie projektu MathLibrary")

1. W górnej części okna dialogowego Ustaw **Język** na **C++** , ustaw platformę na **system Windows**i ustaw **Typ projektu** na **Biblioteka**. 

1. Z listy filtrowane typy projektów wybierz **bibliotekę dołączaną dynamicznie (dll)** , a następnie wybierz **dalej**. Na następnej stronie wprowadź `MathLibrary` wartość w polu **Nazwa** , aby określić nazwę projektu, i w razie potrzeby określ lokalizację projektu.

1. Wybierz przycisk **Utwórz** , aby utworzyć projekt.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-dll-project-in-visual-studio-2017"></a>Aby utworzyć projekt DLL w programie Visual Studio 2017

1. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt** , aby otworzyć okno dialogowe **Nowy projekt** .

1. W lewym okienku okna dialogowego **Nowy projekt** rozwiń opcję **zainstalowane** i  **C++ wizualizacje** w razie potrzeby, a następnie wybierz pozycję **Windows Desktop**. W środkowym okienku wybierz pozycję **Kreator pulpitu systemu Windows**. Wprowadź `MathLibrary` wartość w polu **Nazwa** , aby określić nazwę projektu.

   ![Nazwij projekt MathLibrary](media/mathlibrary-new-project-name-153.png "Nazwij projekt MathLibrary")

1. Wybierz przycisk **OK** , aby odrzucić okno dialogowe **Nowy projekt** i uruchomić kreatora **projektu pulpitu systemu Windows** .

1. W kreatorze **projektów klasycznych systemu Windows** w obszarze **Typ aplikacji**wybierz pozycję **biblioteka dołączana dynamicznie (. dll)** .

   ![Tworzenie biblioteki DLL w Kreatorze projektów klasycznych systemu Windows](media/mathlibrary-desktop-project-wizard-dll.png "Tworzenie biblioteki DLL w Kreatorze projektów klasycznych systemu Windows")

1. Wybierz przycisk **OK** , aby utworzyć projekt.

> [!NOTE]
> Aby rozwiązać problem w programie Visual Studio 2017 w wersji 15,3, wymagane są dodatkowe czynności. Postępuj zgodnie z tymi instrukcjami, aby zobaczyć, czy trzeba wprowadzić tę zmianę.
>
>1. W **Eksplorator rozwiązań**, jeśli nie została jeszcze wybrana, wybierz projekt **MathLibrary** w obszarze **rozwiązanie "MathLibrary"** .
>
>1. Na pasku menu wybierz **Właściwości** **projektu** > .
>
>1. W lewym okienku okna dialogowego **strony właściwości** wybierz opcję preprocesora w obszarze **Właściwości** > konfiguracji**CC++/** . Sprawdź zawartość właściwości **Definicje preprocesora** .<br/><br/>![Sprawdź Właściwość Definicje preprocesora](media/mathlibrary-153bug-preprocessor-definitions-check.png "Sprawdź Właściwość Definicje preprocesora")<br/><br/>Jeśli widzisz **eksporty&#95;MATHLIBRARY** na liście **Definicje preprocesora** , nie musisz zmieniać żadnych elementów. Jeśli zamiast tego zobaczysz **eksporty MathLibrary&#95;** , Kontynuuj, wykonując następujące kroki.
>
>1. W górnej części okna dialogowego **strony właściwości** Zmień listę rozwijaną **konfiguracji** na **wszystkie konfiguracje**.
>
>1. W okienku właściwości wybierz kontrolkę listy rozwijanej obok pola edycji dla **definicji preprocesora**, a następnie wybierz polecenie **Edytuj**.<br/><br/>![Edytuj Właściwość Definicje preprocesora](media/mathlibrary-153bug-preprocessor-definitions-property.png "Edytuj Właściwość Definicje preprocesora")
>
>1. W górnym okienku okna dialogowego **Definicje preprocesora** Dodaj nowy symbol, `MATHLIBRARY_EXPORTS`.<br/><br/>![Dodaj symbol MATHLIBRARY_EXPORTS](media/mathlibrary-153bug-preprocessor-definitions-dialog.png "Dodaj symbol MATHLIBRARY_EXPORTS")
>
>1. Wybierz **przycisk OK** , aby zamknąć okno dialogowe **Definicje preprocesora** , a następnie wybierz przycisk **OK** , aby zapisać zmiany właściwości projektu.

::: moniker-end

::: moniker range="=vs-2015"

### <a name="to-create-a-dll-project-in-older-versions-of-visual-studio"></a>Aby utworzyć projekt DLL we wcześniejszych wersjach programu Visual Studio

1. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

1. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **zainstalowane** > **Szablony**, wybierz pozycję **C++Wizualizacja**, a następnie w środkowym okienku wybierz pozycję **aplikacja konsoli Win32**. Wprowadź `MathLibrary` wartość w polu **Nazwa** , aby określić nazwę projektu.

   ![Nazwij projekt MathLibrary](media/mathlibrary-project-name.png "Nazwij projekt MathLibrary")

1. Wybierz przycisk **OK** , aby odrzucić okno dialogowe **Nowy projekt** i uruchomić **Kreatora aplikacji Win32**.

   ![Omówienie Kreatora aplikacji Win32](media/mathlibrary-project-wizard-1.png "Omówienie Kreatora aplikacji Win32")

1. Wybierz **dalej** przycisku. Na stronie **Ustawienia aplikacji** w obszarze **Typ aplikacji**wybierz pozycję **Biblioteka DLL**.

   ![Kreator tworzenia biblioteki DLL w aplikacji Win32](media/mathlibrary-project-wizard-2.png "Kreator tworzenia biblioteki DLL w aplikacji Win32")

1. Wybierz przycisk **Zakończ** , aby utworzyć projekt.

Gdy Kreator ukończy rozwiązanie, w programie Visual Studio można zobaczyć wygenerowany projekt i pliki źródłowe w oknie **Eksplorator rozwiązań** .

![Wygenerowane rozwiązanie w programie Visual Studio](media/mathlibrary-solution-explorer-153.png "Wygenerowane rozwiązanie w programie Visual Studio")

Teraz ta biblioteka DLL nie działa znacznie. Następnie utworzysz plik nagłówka, aby zadeklarować funkcje eksportowane przez bibliotekę DLL, a następnie dodać definicje funkcji do biblioteki DLL, aby uczynić ją bardziej użyteczną.

::: moniker-end

### <a name="to-add-a-header-file-to-the-dll"></a>Aby dodać plik nagłówka do biblioteki DLL

1. Aby utworzyć plik nagłówkowy dla funkcji, na pasku menu wybierz **projekt** > **Dodaj nowy element**.

1. W oknie dialogowym **Dodaj nowy element** w okienku po lewej stronie wybierz pozycję **Wizualizacja C++** . W środkowym okienku wybierz pozycję **plik nagłówka (. h)** . Określ `MathLibrary.h` jako nazwę pliku nagłówkowego.

   ![Dodaj nagłówek w oknie dialogowym Dodaj nowy element](media/mathlibrary-add-new-item-header-file.png "Dodaj plik nagłówka w oknie dialogowym Dodaj nowy element")

1. Wybierz przycisk **Dodaj** , aby wygenerować pusty plik nagłówka, który zostanie wyświetlony w nowym oknie edytora.

   ![Pusty plik MathLibrary. h w edytorze](media/edit-empty-mathlibrary-header.png "Pusty plik MathLibrary. h w edytorze")

1. Zastąp zawartość pliku nagłówkowego tym kodem:

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

Ten plik nagłówkowy deklaruje pewne funkcje, aby utworzyć uogólnioną sekwencję Fibonacci, uwzględniając dwie wartości początkowe. Wywołanie w celu `fibonacci_init(1, 1)` wygenerowania znanej sekwencji Fibonacci Number.

Zwróć uwagę na instrukcje preprocesora w górnej części pliku. Domyślnie nowy szablon projektu dla biblioteki DLL dodaje  **\<em > ProjectName\</em >&#95;eksportu** do zdefiniowanego makra preprocesora dla projektu DLL. W tym przykładzie program Visual Studio definiuje **eksporty MATHLIBRARY&#95;** podczas kompilowania projektu DLL MATHLIBRARY. 

::: moniker range="=vs-2017"

(Kreator w programie Visual Studio 2017 w wersji 15,3 nie wymusić tej definicji symbolu wielką literą. Jeśli nazwa projektu to "MathLibrary", wówczas zdefiniowany symbol jest MathLibrary&#95;eksportu zamiast MathLibrary&#95;eksportu. Dlatego należy wykonać dodatkowe czynności powyżej, aby dodać ten symbol.)

::: moniker-end

Po zdefiniowaniu makra **MATHLIBRARY&#95;exports** makro **interfejsu API&#95;MATHLIBRARY** ustawia `__declspec(dllexport)` modyfikator dla deklaracji funkcji. Ten modyfikator nakazuje kompilatorowi i konsolidatorowi wyeksportowanie funkcji lub zmiennej z biblioteki DLL, aby mogła ona być używana przez inne aplikacje. Gdy **eksporty MATHLIBRARY&#95;** są niezdefiniowane, na przykład gdy plik nagłówkowy jest dołączany przez aplikację kliencką, interfejs `__declspec(dllimport)` **API MATHLIBRARY&#95;** stosuje modyfikator do deklaracji. Ten modyfikator optymalizuje Importowanie funkcji lub zmiennej w aplikacji. Aby uzyskać więcej informacji, zobacz [dllexport, dllimport](../cpp/dllexport-dllimport.md).

### <a name="to-add-an-implementation-to-the-dll"></a>Aby dodać implementację do biblioteki DLL

::: moniker range="vs-2019"

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **pliki źródłowe** i Dodaj nowy plik CPP o nazwie `MathLibrary.cpp` w taki sam sposób, jak w poprzednim kroku dodano nowy plik nagłówkowy.

::: moniker-end

1. W oknie Edytor wybierz kartę **MathLibrary. cpp** , jeśli jest już otwarta. Jeśli tak nie jest, w **Eksplorator rozwiązań**Otwórz **MathLibrary. cpp** w folderze **pliki źródłowe** projektu **MathLibrary** .

1. W edytorze Zastąp zawartość pliku MathLibrary. cpp następującym kodem:

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "pch.h" // use stdafx.h in Visual Studio 2017 and earlier
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

Aby sprawdzić, czy wszystko działa tak dalej, skompiluj bibliotekę dołączaną dynamicznie. Aby skompilować, wybierz opcję **Kompiluj** > **rozwiązanie** kompilacji na pasku menu. Dane wyjściowe powinny wyglądać podobnie do tego. Należy zauważyć, że plik wykonywalny DLL i pokrewne dane wyjściowe kompilatora są umieszczane w folderze o nazwie *Debug* bezpośrednio pod folderem rozwiązania. Jeśli utworzysz kompilację wydania, dane wyjściowe zostaną umieszczone w folderze o nazwie *Release*:

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>MathLibrary.cpp
1>dllmain.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.pdb (Partial PDB)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Gratulacje, utworzono bibliotekę DLL przy użyciu programu Visual Studio! Następnie utworzysz aplikację kliencką, która używa funkcji wyeksportowanych przez DLL.

## <a name="create-a-client-app-that-uses-the-dll"></a>Tworzenie aplikacji klienckiej korzystającej z biblioteki DLL

Podczas tworzenia biblioteki DLL należy zastanowić się, jak można użyć biblioteki DLL. Aby skompilować kod, który wywołuje funkcje eksportowane przez bibliotekę DLL, deklaracje muszą być zawarte w kodzie źródłowym klienta. W czasie połączenia, gdy są rozwiązywane te wywołania funkcji DLL, konsolidator musi mieć *bibliotekę importu*, specjalny plik biblioteki zawierający informacje dla systemu Windows, w jaki sposób można znaleźć funkcje, a nie rzeczywisty kod. A w czasie wykonywania Biblioteka DLL musi być dostępna dla klienta w lokalizacji, w której system operacyjny może znaleźć.

Aby skorzystać z biblioteki DLL, niezależnie od tego, czy posiadana lub zewnętrzna Biblioteka DLL, projekt aplikacji klienckiej musi znaleźć nagłówki, które deklarują eksporty biblioteki DLL, biblioteki importu dla konsolidatora i samą bibliotekę DLL. Jednym ze sposobów jest skopiowanie wszystkich tych plików do projektu klienta. W przypadku bibliotek DLL innych firm, które nie są prawdopodobnie zmieniane podczas opracowywania klienta, ta metoda może być najlepszym sposobem ich używania. Jednak w przypadku kompilowania biblioteki DLL lepiej jest unikać duplikacji. Jeśli wykonujesz kopię plików DLL, które są opracowywane, możesz przypadkowo zmienić plik nagłówka w jednej kopii, ale nie w innym, lub użyć nieaktualnej biblioteki. Aby uniknąć tego problemu, zalecamy ustawienie ścieżki include w projekcie klienta w celu uwzględnienia plików nagłówkowych DLL z projektu DLL. Ponadto należy ustawić ścieżkę biblioteki w projekcie klienta, aby uwzględnić biblioteki importu bibliotek DLL z projektu DLL. A wreszcie Skopiuj skompilowaną bibliotekę DLL z projektu DLL do katalogu wyjściowego kompilacji. Ten krok umożliwia aplikacji klienckiej użycie tego samego kodu DLL, który został skompilowany.

::: moniker range="vs-2019"

### <a name="to-create-a-client-app-in-visual-studio-2019"></a>Aby utworzyć aplikację kliencką w programie Visual Studio 2019

1. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt** , aby otworzyć okno dialogowe **Tworzenie nowego projektu** .

1. W górnej części okna dialogowego Ustaw **Język** na **C++** , ustaw platformę na **system Windows**i ustaw **Typ projektu** na **Console**. 

1. Z listy filtrowane typy projektów wybierz pozycję **Aplikacja konsolowa** , a następnie wybierz przycisk **dalej**. Na następnej stronie wprowadź `MathClient` wartość w polu **Nazwa** , aby określić nazwę projektu, i w razie potrzeby określ lokalizację projektu.

   ![Nadaj nazwę projektowi klienta](media/mathclient-project-name-2019.png "Nadaj nazwę projektowi klienta")

1. Wybierz przycisk **Utwórz** , aby utworzyć projekt klienta.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-client-app-in-visual-studio-2017"></a>Aby utworzyć aplikację kliencką w programie Visual Studio 2017

1. C++ Aby utworzyć aplikację, która używa utworzonej biblioteki DLL, na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

1. W lewym okienku okna dialogowego **Nowy projekt** wybierz pozycję **pulpit systemu Windows** w obszarze **zainstalowane** > **C++wizualizacje**. W środkowym okienku wybierz pozycję **Kreator pulpitu systemu Windows**. Określ nazwę projektu, `MathClient`w polu **Nazwa** .

   ![Nadaj nazwę projektowi klienta](media/mathclient-new-project-name-153.png "Nadaj nazwę projektowi klienta")

1. Wybierz **przycisk OK** , aby uruchomić kreatora **projektu pulpitu systemu Windows** . W kreatorze wybierz **przycisk OK** , aby utworzyć projekt aplikacji klienckiej.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-client-app-in-older-versions-of-visual-studio-2017"></a>Aby utworzyć aplikację kliencką w starszych wersjach programu Visual Studio 2017

1. C++ Aby utworzyć aplikację, która używa utworzonej biblioteki DLL, na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

1. W lewym okienku okna dialogowego **Nowy projekt** wybierz pozycję **Win32** w obszarze **zainstalowane** > **Szablony** > **Visual C++** . W środkowym okienku wybierz pozycję **aplikacja konsoli Win32**. Określ nazwę projektu, `MathClient`w polu **Nazwa** .

   ![Nadaj nazwę projektowi klienta](media/mathclient-project-name.png "Nadaj nazwę projektowi klienta")

1. Wybierz przycisk **OK** , aby odrzucić okno dialogowe **Nowy projekt** i uruchomić **Kreatora aplikacji Win32**. Na stronie **Omówienie** okna dialogowego **Kreator aplikacji Win32** wybierz przycisk **dalej** .

1. Na stronie **Ustawienia aplikacji** w obszarze **Typ aplikacji**wybierz pozycję **Aplikacja konsolowa** , jeśli nie została jeszcze wybrana.

1. Wybierz przycisk **Zakończ** , aby utworzyć projekt.

::: moniker-end

Po zakończeniu pracy kreatora zostanie utworzony projekt o minimalnej aplikacji konsolowej. Nazwa głównego pliku źródłowego jest taka sama jak nazwa projektu wprowadzona wcześniej. W tym przykładzie nosi nazwę **MathClient. cpp**. Można go skompilować, ale nie używa jeszcze biblioteki DLL.

Następnie, aby wywołać funkcje MathLibrary w kodzie źródłowym, projekt musi zawierać plik MathLibrary. h. Możesz skopiować ten plik nagłówka do projektu aplikacji klienckiej, a następnie dodać go do projektu jako istniejący element. Ta metoda może być dobrym wyborem dla bibliotek innych firm. Jeśli jednak pracujesz nad kodem biblioteki DLL w tym samym czasie co Twój klient, co może prowadzić do zmian w jednym pliku nagłówkowym, który nie jest wyświetlany w drugim. Aby uniknąć tego problemu, można zmienić ścieżkę dołączania **dodatkowych katalogów** w projekcie w celu uwzględnienia ścieżki do oryginalnego nagłówka.

### <a name="to-add-the-dll-header-to-your-include-path"></a>Aby dodać nagłówek DLL do ścieżki dołączania

1. Kliknij prawym przyciskiem myszy węzeł **MathClient** w **Eksplorator rozwiązań** , aby otworzyć okno dialogowe **strony właściwości** .

1. W polu listy rozwijanej **Konfiguracja** wybierz opcję **wszystkie konfiguracje** , jeśli nie została jeszcze wybrana.

1. W okienku po lewej stronie wybierz pozycję **Ogólne** w obszarze **Właściwości** > konfiguracji**C/C++** .

1. W okienku właściwości wybierz kontrolkę listy rozwijanej obok pola **Dodatkowe katalogi** dołączane, a następnie wybierz pozycję **Edytuj**.

   ![Edytuj Właściwość dodatkowe katalogi dołączane](media/mathclient-additional-include-directories-property.png "Edytuj Właściwość dodatkowe katalogi dołączane")

1. Kliknij dwukrotnie w górnym okienku okna dialogowego **Dodatkowe katalogi** dołączane, aby włączyć kontrolkę edycji.

1. W kontrolce Edycja określ ścieżkę do lokalizacji pliku nagłówkowego **MathLibrary. h** . Kliknij strzałkę w dół, a następnie wybierz polecenie  **\<Edytuj >** . Możesz kliknąć ikonę folderu, a następnie przycisk wielokropka ( **...** ), aby przejść do odpowiedniego folderu.
 
   Możesz również w tym przypadku wpisać ścieżkę względną w folderze zawierającym pliki. cpp w projekcie klienta do folderu, który zawiera plik. h w projekcie DLL. Jeśli projekt klienta znajduje się w osobnym rozwiązaniu w tym samym folderze co rozwiązanie biblioteki DLL, ścieżka względna powinna wyglądać następująco:

   `..\MathLibrary\MathLibrary`

   Jeśli biblioteka DLL i projekty klienta znajdują się w tym samym rozwiązaniu lub rozwiązania znajdują się w różnych folderach, należy odpowiednio dostosować ścieżkę względną lub inaczej przeglądać w poszukiwaniu folderu, używając opisanej wcześniej metody.

   ![Dodaj lokalizację nagłówka do właściwości dodatkowe katalogi dołączane](media/mathclient-additional-include-directories.png "Dodaj lokalizację nagłówka do właściwości dodatkowe katalogi dołączane")

1. Po wprowadzeniu ścieżki do pliku nagłówkowego w oknie dialogowym **Dodatkowe katalogi** dołączane wybierz przycisk **OK** , aby powrócić do okna dialogowego **strony właściwości** , a następnie wybierz przycisk **OK** , aby zapisać zmiany.

Teraz możesz dołączyć plik **MathLibrary. h** i użyć funkcji zadeklarowanych w aplikacji klienckiej. Zastąp zawartość **MathClient. cpp** przy użyciu tego kodu:

```cpp
// MathClient.cpp : Client app for MathLibrary DLL.
// #include "pch.h" Uncomment for Visual Studio 2017 and earlier
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

Ten kod może być skompilowany, ale nie połączony, ponieważ konsolidator nie może znaleźć biblioteki importowanej wymaganej do skompilowania aplikacji. Konsolidator musi znaleźć plik MathLibrary. lib, aby połączyć się pomyślnie. Dodaj plik MathLibrary. lib do kompilacji, ustawiając właściwość **dodatkowe zależności** . Ponownie można skopiować plik biblioteki do projektu aplikacji klienckiej, ale jeśli biblioteka i aplikacja kliencka są w fazie opracowywania, co może prowadzić do zmian w jednej kopii, która nie jest wyświetlana w drugim. Aby uniknąć tego problemu, można zmienić ścieżkę **katalogów dodatkowych bibliotek** w projekcie w celu uwzględnienia ścieżki do oryginalnej biblioteki podczas łączenia.

### <a name="to-add-the-dll-import-library-to-your-project"></a>Aby dodać bibliotekę importowania biblioteki DLL do projektu

1. Kliknij prawym przyciskiem myszy węzeł **MathClient** w **Eksplorator rozwiązań** , aby otworzyć okno dialogowe **strony właściwości** .

1. W polu listy rozwijanej **Konfiguracja** wybierz opcję **wszystkie konfiguracje** , jeśli nie została jeszcze wybrana. To ustawienie zapewnia, że ścieżka jest ustawiona zarówno dla kompilacji debugowania, jak i wydania.

1. W lewym okienku wybierz pozycję **dane wejściowe** w obszarze **Właściwości** > konfiguracji**konsolidator**. W okienku właściwości wybierz kontrolkę listy rozwijanej obok pola Edytuj **dodatkowe zależności** , a następnie wybierz polecenie **Edytuj**.

   ![Edytuj Właściwość dodatkowe zależności](media/mathclient-additional-dependencies-property.png "Edytuj Właściwość dodatkowe zależności")

1. W oknie dialogowym **dodatkowe zależności** Dodaj `MathLibrary.lib` do listy w górnej kontrolce edycji.

   ![Dodawanie zależności biblioteki](media/mathclient-additional-dependencies.png "Dodawanie zależności biblioteki")

1. Wybierz **przycisk OK** , aby wrócić do okna dialogowego **strony właściwości** .

1. W lewym okienku wybierz pozycję **Ogólne** w obszarze **Właściwości** > konfiguracji**konsolidator**. W okienku właściwości wybierz kontrolkę listy rozwijanej obok pola edycji **Dodatkowe katalogi biblioteki** , a następnie wybierz polecenie **Edytuj**.

   ![Edytuj Właściwość dodatkowe katalogi biblioteki](media/mathclient-additional-library-directories-property.png "Edytuj Właściwość dodatkowe katalogi biblioteki")

1. Kliknij dwukrotnie w górnym okienku okna dialogowego **Dodatkowe katalogi biblioteki** , aby włączyć kontrolkę edycji. W kontrolce Edycja określ ścieżkę do lokalizacji pliku **MathLibrary. lib** . Znajduje się w folderze o nazwie `Debug` bezpośrednio w folderze rozwiązania. Jeśli utworzysz kompilację wydania, dane wyjściowe zostaną umieszczone w folderze o nazwie `Release`. Możesz użyć poniższego makra, aby konsolidator mógł znaleźć bibliotekę DLL niezależnie od tego, jakiego rodzaju kompilacja została utworzona:

   **Visual Studio 2019:**

   `..\MathLibrary\$(IntDir)`

   **Program Visual Studio 2017 i jego wcześniejsze wersje:**

   `..\..\MathLibrary\$(IntDir)`

   ![Dodaj katalog biblioteki](media/mathclient-additional-library-directories.png "Dodaj katalog biblioteki")

1. Po wprowadzeniu ścieżki do pliku biblioteki w oknie dialogowym **Dodatkowe katalogi biblioteki** wybierz przycisk **OK** , aby wrócić do okna dialogowego **strony właściwości** .

Twoja aplikacja kliencka może teraz kompilować i łączyć się, ale nadal nie ma wszystkiego, czego potrzebuje do uruchomienia. Gdy system operacyjny ładuje aplikację, szuka biblioteki DLL MathLibrary. Jeśli nie można odnaleźć biblioteki DLL w określonych katalogach systemowych, ścieżce środowiska lub lokalnego katalogu aplikacji, ładowanie nie powiedzie się. Jednym ze sposobów uniknięcia tego problemu jest skopiowanie biblioteki DLL do katalogu, który zawiera plik wykonywalny klienta w ramach procesu kompilacji. Aby skopiować bibliotekę DLL, można dodać do projektu **zdarzenie po kompilacji** , aby dodać polecenie, które kopiuje bibliotekę DLL do katalogu wyjściowego kompilacji. Określone tutaj polecenie kopiuje bibliotekę DLL tylko wtedy, gdy nie ma lub została zmieniona, i używa makr do kopiowania do i z prawidłowych lokalizacji debugowania lub wersji dla danej konfiguracji.

### <a name="to-copy-the-dll-in-a-post-build-event"></a>Aby skopiować bibliotekę DLL w zdarzeniu po kompilacji

1. Kliknij prawym przyciskiem myszy węzeł **MathClient** w **Eksplorator rozwiązań** , aby otworzyć okno dialogowe **strony właściwości** .

1. W polu listy rozwijanej konfiguracja wybierz opcję **wszystkie konfiguracje** , jeśli nie została jeszcze wybrana.

1. W lewym okienku wybierz **zdarzenie po kompilacji** w obszarze **Właściwości** > konfiguracji**zdarzenia kompilacji**.

1. W okienku właściwości wybierz kontrolkę Edycja w polu **wiersz polecenia** , a następnie wprowadź następujące polecenie:

   **Visual Studio 2019:**

   `xcopy /y /d "..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

    **Program Visual Studio 2017 i jego wcześniejsze wersje:**

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   ![Dodaj polecenie po kompilacji](media/mathclient-post-build-command-line.png "Dodaj polecenie po kompilacji")

1. Wybierz przycisk **OK** , aby zapisać zmiany właściwości projektu.

Teraz aplikacja kliencka ma wszystko, czego potrzebuje do skompilowania i uruchomienia. Skompiluj aplikację, wybierając pozycję **Kompiluj** > **kompilację** na pasku menu. Okno **danych wyjściowych** w programie Visual Studio powinno wyglądać podobnie do poniższego przykładu, w zależności od używanej wersji programu Visual Studio:

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>pch.cpp
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.pdb (Partial PDB)
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Gratulacje, utworzono aplikację, która wywołuje funkcje w bibliotece DLL. Teraz uruchom aplikację, aby zobaczyć, co robi. Na pasku menu wybierz **Debuguj** > **Uruchom bez debugowania**. Program Visual Studio otwiera okno poleceń, które zostanie uruchomione w programie. Ostatnia część danych wyjściowych powinna wyglądać następująco:

![Uruchom aplikację kliencką bez debugowania](media/mathclient-run-without-debugging.png "Uruchom aplikację kliencką bez debugowania")

Naciśnij dowolny klawisz, aby odrzucić okno polecenia.

Po utworzeniu biblioteki DLL i aplikacji klienckiej można eksperymentować. Spróbuj ustawić punkty przerwania w kodzie aplikacji klienckiej, a następnie uruchom aplikację w debugerze. Zobacz, co się stanie, gdy przejdziesz do wywołania biblioteki. Dodaj inne funkcje do biblioteki lub napisz kolejną aplikację kliencką, która korzysta z biblioteki DLL.

Podczas wdrażania aplikacji należy również wdrożyć biblioteki DLL, z których korzysta. Najprostszym sposobem, aby pliki dll, które tworzysz lub które zostały dołączone od stron trzecich dostępnych dla aplikacji, są umieszczane w tym samym katalogu, w którym znajduje się aplikacja, nazywana również wdrożeniem na *poziomie aplikacji*. Aby uzyskać więcej informacji o wdrażaniu, zobacz [wdrażanie C++w programie Visual ](../windows/deployment-in-visual-cpp.md).

## <a name="see-also"></a>Zobacz także

[Wywoływanie funkcji DLL z aplikacji języka Visual Basic](calling-dll-functions-from-visual-basic-applications.md)
