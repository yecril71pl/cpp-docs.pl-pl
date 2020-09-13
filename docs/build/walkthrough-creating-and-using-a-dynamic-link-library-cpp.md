---
title: 'Przewodnik: Tworzenie własnej biblioteki dołączanej dynamicznie (C++) i korzystanie z niej'
description: Użyj języka C++ do tworzenia biblioteki dołączanej dynamicznie (DLL) systemu Windows w programie Visual Studio.
ms.custom: conceptual
ms.date: 08/22/2019
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
ms.openlocfilehash: adca441a1b1b4e5e7b7efa44c4a292a8f1ddec35
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042202"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>Przewodnik: Tworzenie własnej biblioteki dołączanej dynamicznie (C++) i korzystanie z niej

W tym przewodniku krok po kroku przedstawiono sposób użycia środowiska IDE programu Visual Studio do utworzenia własnej biblioteki dołączanej dynamicznie (DLL), która jest zapisywana w języku Microsoft C++ (MSVC). Następnie pokazano, jak używać biblioteki DLL z innej aplikacji C++. Biblioteki DLL (nazywane również *bibliotekami udostępnionymi* w systemach operacyjnych opartych na systemie UNIX) są jednym z najbardziej przydatnych rodzajów składników systemu Windows. Można ich używać jako metody udostępniania kodu i zasobów oraz zmniejszania rozmiaru aplikacji. Biblioteki DLL mogą nawet ułatwić obsługę i zwiększanie możliwości aplikacji.

W tym instruktażu utworzysz bibliotekę DLL, która implementuje niektóre funkcje matematyczne. Następnie utworzysz aplikację konsolową, która używa funkcji z biblioteki DLL. Uzyskasz również wprowadzenie do niektórych technik programowania i Konwencji używanych w bibliotekach DLL systemu Windows.

Ten przewodnik obejmuje następujące zadania:

- Utwórz projekt DLL w programie Visual Studio.

- Dodaj eksportowane funkcje i zmienne do biblioteki DLL.

- Utwórz projekt aplikacji konsolowej w programie Visual Studio.

- Użyj funkcji i zmiennych zaimportowanych z biblioteki DLL w aplikacji konsolowej.

- Uruchom ukończoną aplikację.

Podobnie jak statycznie połączone biblioteki, biblioteka DLL _eksportuje_ zmienne, funkcje i zasoby według nazwy. Aplikacja kliencka _importuje_ nazwy do korzystania z tych zmiennych, funkcji i zasobów. W przeciwieństwie do biblioteki połączonej statycznie, system Windows łączy Importy w aplikacji z eksportami w bibliotece DLL w czasie ładowania lub w czasie wykonywania, zamiast łączyć je w czasie łączenia. System Windows wymaga dodatkowych informacji, które nie są częścią standardowego modelu kompilacji C++ do nawiązywania tych połączeń. Kompilator MSVC implementuje Niektóre rozszerzenia specyficzne dla firmy Microsoft w języku C++, aby zapewnić te dodatkowe informacje. Te rozszerzenia są wyjaśnione w miarę rzeczywistym.

Ten Instruktaż tworzy dwa rozwiązania Visual Studio; Ta, która kompiluje bibliotekę DLL, i która kompiluje aplikację kliencką. Biblioteka DLL używa konwencji wywoływania języka C. Może być wywoływana z aplikacji utworzonych w innych językach programowania, tak długo, jak platforma, konwencje wywoływania i konwencje łączenia są zgodne. Aplikacja kliencka używa _niejawnego łączenia_, gdzie system Windows łączy aplikację z biblioteką DLL w czasie ładowania. To łączenie umożliwia aplikacji wywoływanych przez biblioteki DLL funkcje, podobnie jak funkcje w bibliotece połączonej statycznie.

Ten Instruktaż nie obejmuje niektórych typowych sytuacji. Kod nie pokazuje użycia bibliotek DLL języka C++ według innych języków programowania. Nie pokazuje, jak [utworzyć bibliotekę DLL tylko do zasobów](creating-a-resource-only-dll.md)lub jak używać [jawnego łączenia](linking-an-executable-to-a-dll.md#linking-explicitly) do ładowania bibliotek DLL w czasie wykonywania, a nie w czasie ładowania. Zapewniona reszta, możesz użyć MSVC i programu Visual Studio, aby wykonać wszystkie te czynności.

Aby uzyskać linki do dodatkowych informacji o bibliotekach DLL, zobacz [tworzenie bibliotek DLL C/C++ w programie Visual Studio](dlls-in-visual-cpp.md). Aby uzyskać więcej informacji na temat niejawnego łączenia i jawnego łączenia, zobacz [Określanie, która Metoda łączenia ma być używana](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use). Aby uzyskać informacje na temat tworzenia bibliotek DLL języka C++ do użycia z językami programowania, które używają Konwencji połączeń języka C, zobacz [Eksportowanie funkcji języka c++ do użycia w plikach wykonywalnych języka c](exporting-cpp-functions-for-use-in-c-language-executables.md). Aby uzyskać informacje o sposobach tworzenia bibliotek DLL do użycia w językach .NET, zobacz [wywoływanie funkcji DLL z aplikacji Visual Basic](calling-dll-functions-from-visual-basic-applications.md).

## <a name="prerequisites"></a>Wymagania wstępne

- Komputer z systemem Microsoft Windows 7 lub nowszym. Zalecamy użycie systemu Windows 10 w celu uzyskania najlepszego środowiska programistycznego.

::: moniker range=">=vs-2017"

- Kopia programu Visual Studio. Aby uzyskać informacje na temat pobierania i instalowania programu Visual Studio, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio). Po uruchomieniu Instalatora upewnij się, że jest zaznaczone pole **Programowanie aplikacji klasycznych w języku C++** . Nie martw się, jeśli to obciążenie nie zostało zainstalowane podczas instalacji programu Visual Studio. Możesz ponownie uruchomić Instalatora i zainstalować go teraz.

   ![Programowanie aplikacji klasycznych w języku C++](media/desktop-development-with-cpp.png "Programowanie aplikacji klasycznych w języku C++")

::: moniker-end

::: moniker range="vs-2015"

- Kopia programu Visual Studio. Aby uzyskać informacje na temat pobierania i instalowania programu Visual Studio 2015, zobacz [Instalowanie programu Visual studio 2015](/visualstudio/install/install-visual-studio-2015?view=vs-2015&preserve-view=true). Zainstaluj kompilator i narzędzia języka C++ przy użyciu instalacji **niestandardowej** , ponieważ nie są one instalowane domyślnie.

::: moniker-end

- Zrozumienie podstaw korzystania ze środowiska IDE programu Visual Studio. Jeśli wcześniej używasz aplikacji klasycznych systemu Windows, prawdopodobnie Zadbaj o to. Aby zapoznać się z wprowadzeniem, zobacz [Przewodnik po funkcji środowiska IDE programu Visual Studio](/visualstudio/ide/visual-studio-ide).

- Zrozumienie wystarczającej podstawy języka C++ do wykonania. Nie martw się, nie wykonujemy żadnych zbyt skomplikowane.

::: moniker range="vs-2017"

> [!NOTE]
> W tym instruktażu przyjęto założenie, że używasz programu Visual Studio 2017 w wersji 15,9 lub nowszej. Niektóre starsze wersje programu Visual Studio 2017 mają wady w szablonach kodu lub używane są inne okna dialogowe interfejsu użytkownika. Aby uniknąć problemów, użyj Instalator programu Visual Studio do zaktualizowania programu Visual Studio 2017 do wersji 15,9 lub nowszej.

::: moniker-end

## <a name="create-the-dll-project"></a>Tworzenie projektu DLL

W tym zestawie zadań można utworzyć projekt dla biblioteki DLL, dodać kod i skompilować go. Aby rozpocząć, uruchom środowisko IDE programu Visual Studio i zaloguj się, jeśli zachodzi taka potrzeba. Instrukcje różnią się nieco w zależności od używanej wersji programu Visual Studio. Upewnij się, że w kontrolce w lewym górnym rogu tej strony została wybrana prawidłowa wersja.

::: moniker range=">=vs-2019"

### <a name="to-create-a-dll-project-in-visual-studio-2019"></a>Aby utworzyć projekt DLL w programie Visual Studio 2019

1. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt** , aby otworzyć okno dialogowe **Tworzenie nowego projektu** .

   ![Utwórz nowy projekt DLL](media/create-new-dll-project-2019.png "Tworzenie projektu MathLibrary")

1. W górnej części okna dialogowego Ustaw  **Język** na **C++**, ustaw **platformę** na **Windows**i ustaw **Typ projektu** na **Biblioteka**.

1. Z listy filtrowane typy projektów wybierz **bibliotekę dołączaną dynamicznie (dll)**, a następnie wybierz **dalej**.

1. Na stronie **Konfiguruj nowy projekt** wprowadź *MathLibrary* w polu **Nazwa projektu** , aby określić nazwę projektu. Pozostaw domyślne wartości **lokalizacji** i **nazwy rozwiązania** . Ustaw **rozwiązanie** , aby **utworzyć nowe rozwiązanie**. Usuń zaznaczenie pola wyboru **Umieść rozwiązanie i projekt w tym samym katalogu,** jeśli jest zaznaczone.

1. Wybierz przycisk **Utwórz** , aby utworzyć projekt.

Po utworzeniu rozwiązania można zobaczyć wygenerowany projekt i pliki źródłowe w oknie **Eksplorator rozwiązań** w programie Visual Studio.

![Wygenerowane rozwiązanie w programie Visual Studio](media/mathlibrary-solution-explorer-162.png "Wygenerowane rozwiązanie w programie Visual Studio")

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-dll-project-in-visual-studio-2017"></a>Aby utworzyć projekt DLL w programie Visual Studio 2017

1. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt** , aby otworzyć okno dialogowe **Nowy projekt** .

1. W lewym okienku okna dialogowego **Nowy projekt** wybierz pozycję **zainstalowane**  >  **Visual C++**  >  **pulpicie systemu Windows**. W środkowym okienku wybierz **bibliotekę dołączaną dynamicznie (dll)**. Wprowadź *MathLibrary* w polu **Nazwa** , aby określić nazwę projektu. Pozostaw domyślne wartości **lokalizacji** i **nazwy rozwiązania** . Ustaw **rozwiązanie** , aby **utworzyć nowe rozwiązanie**. Zaznacz opcję **Utwórz katalog dla rozwiązania** , jeśli nie jest zaznaczone.

   ![Nazwij projekt MathLibrary](media/mathlibrary-new-project-name-159.png "Nazwij projekt MathLibrary")

1. Wybierz przycisk **OK** , aby utworzyć projekt.

Po utworzeniu rozwiązania można zobaczyć wygenerowany projekt i pliki źródłowe w oknie **Eksplorator rozwiązań** w programie Visual Studio.

![Wygenerowane rozwiązanie w programie Visual Studio](media/mathlibrary-solution-explorer-159.png "Wygenerowane rozwiązanie w programie Visual Studio")

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-dll-project-in-visual-studio-2015-and-older-versions"></a>Aby utworzyć projekt DLL w programie Visual Studio 2015 i starszych wersjach

1. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

1. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **zainstalowane**  >  **Szablony**, wybierz pozycję **Visual C++**, a następnie w środkowym okienku wybierz pozycję **aplikacja konsoli Win32**. Wprowadź *MathLibrary* w polu tekstowym **Nazwa** , aby określić nazwę projektu. Pozostaw domyślne wartości **lokalizacji** i **nazwy rozwiązania** . Ustaw **rozwiązanie** , aby **utworzyć nowe rozwiązanie**. Zaznacz opcję **Utwórz katalog dla rozwiązania** , jeśli nie jest zaznaczone.

   ![Nazwij projekt MathLibrary](media/mathlibrary-project-name.png "Nazwij projekt MathLibrary")

1. Wybierz przycisk **OK** , aby odrzucić okno dialogowe **Nowy projekt** i uruchomić **Kreatora aplikacji Win32**.

   ![Omówienie Kreatora aplikacji Win32](media/mathlibrary-project-wizard-1.png "Omówienie Kreatora aplikacji Win32")

1. Wybierz przycisk **dalej** . Na stronie **Ustawienia aplikacji** w obszarze **Typ aplikacji**wybierz pozycję **Biblioteka DLL**.

   ![Kreator tworzenia biblioteki DLL w aplikacji Win32](media/mathlibrary-project-wizard-2.png "Kreator tworzenia biblioteki DLL w aplikacji Win32")

1. Wybierz przycisk **Zakończ** , aby utworzyć projekt.

Gdy Kreator ukończy rozwiązanie, w programie Visual Studio można zobaczyć wygenerowany projekt i pliki źródłowe w oknie **Eksplorator rozwiązań** .

![Wygenerowane rozwiązanie w programie Visual Studio](media/mathlibrary-solution-explorer-153.png "Wygenerowane rozwiązanie w programie Visual Studio")

::: moniker-end

Teraz ta biblioteka DLL nie działa znacznie. Następnie utworzysz plik nagłówka, aby zadeklarować funkcje eksportowane przez bibliotekę DLL, a następnie dodać definicje funkcji do biblioteki DLL, aby uczynić ją bardziej użyteczną.

### <a name="to-add-a-header-file-to-the-dll"></a>Aby dodać plik nagłówka do biblioteki DLL

1. Aby utworzyć plik nagłówkowy dla funkcji, na pasku menu wybierz **projekt**  >  **Dodaj nowy element**.

1. W oknie dialogowym **Dodaj nowy element** w okienku po lewej stronie wybierz pozycję **Visual C++**. W środkowym okienku wybierz pozycję **plik nagłówka (. h)**. Określ *MathLibrary. h* jako nazwę pliku nagłówkowego.

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

Zwróć uwagę na instrukcje preprocesora w górnej części pliku. Nowy szablon projektu dla projektu DLL dodaje ** _ProjectName_&#95;eksportu** do zdefiniowanych makr preprocesora. W tym przykładzie program Visual Studio definiuje **MATHLIBRARY&#95;eksportu** podczas kompilowania projektu DLL MATHLIBRARY.

Po zdefiniowaniu makra **MATHLIBRARY&#95;exports** makro **MATHLIBRARY&#95;API** ustawia `__declspec(dllexport)` modyfikator dla deklaracji funkcji. Ten modyfikator instruuje kompilator i konsolidator, aby wyeksportować funkcję lub zmienną z biblioteki DLL do użytku przez inne aplikacje. W przypadku niezdefiniowania **&#95;eksportów** , na przykład gdy plik nagłówkowy jest dołączany przez aplikację kliencką, **MATHLIBRARY&#95;API** stosuje `__declspec(dllimport)` modyfikator do deklaracji. Ten modyfikator optymalizuje Importowanie funkcji lub zmiennej w aplikacji. Aby uzyskać więcej informacji, zobacz [dllexport, dllimport](../cpp/dllexport-dllimport.md).

### <a name="to-add-an-implementation-to-the-dll"></a>Aby dodać implementację do biblioteki DLL

::: moniker range=">=vs-2019"

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **pliki źródłowe** , a następnie wybierz polecenie **Dodaj**  >  **nowy element**. Utwórz nowy plik CPP o nazwie *MathLibrary. cpp*w taki sam sposób, jak w poprzednim kroku dodano nowy plik nagłówkowy.

1. W oknie Edytor wybierz kartę **MathLibrary. cpp** , jeśli jest już otwarta. Jeśli tak nie jest, w **Eksplorator rozwiązań**kliknij dwukrotnie pozycję **MathLibrary. cpp** w folderze **pliki źródłowe** projektu **MathLibrary** , aby go otworzyć.

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

::: moniker-end

::: moniker range="<=vs-2017"

1. W oknie Edytor wybierz kartę **MathLibrary. cpp** , jeśli jest już otwarta. Jeśli tak nie jest, w **Eksplorator rozwiązań**kliknij dwukrotnie pozycję **MathLibrary. cpp** w folderze **pliki źródłowe** projektu **MathLibrary** , aby go otworzyć.

1. W edytorze Zastąp zawartość pliku MathLibrary. cpp następującym kodem:

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h" // use pch.h in Visual Studio 2019 and later
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

::: moniker-end

Aby sprawdzić, czy wszystko działa tak dalej, skompiluj bibliotekę dołączaną dynamicznie. Aby skompilować, wybierz opcję **Kompiluj**  >  **rozwiązanie** kompilacji na pasku menu. Biblioteka DLL i pokrewne dane wyjściowe kompilatora są umieszczane w folderze o nazwie *Debug* bezpośrednio pod folderem rozwiązania. Jeśli utworzysz kompilację wydania, dane wyjściowe są umieszczane w folderze o nazwie *Release*. Dane wyjściowe powinny wyglądać następująco:

::: moniker range=">=vs-2019"

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>pch.cpp
1>dllmain.cpp
1>MathLibrary.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

::: moniker-end

::: moniker range="vs-2017"

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>stdafx.cpp
1>dllmain.cpp
1>MathLibrary.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

::: moniker-end

::: moniker range="vs-2015"

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

::: moniker-end

Gratulacje, utworzono bibliotekę DLL przy użyciu programu Visual Studio! Następnie utworzysz aplikację kliencką, która używa funkcji wyeksportowanych przez DLL.

## <a name="create-a-client-app-that-uses-the-dll"></a>Tworzenie aplikacji klienckiej korzystającej z biblioteki DLL

Podczas tworzenia biblioteki DLL należy zastanowić się, w jaki sposób mogą jej używać aplikacje klienckie. Aby wywołać funkcje lub uzyskać dostęp do danych wyeksportowanych przez bibliotekę DLL, kod źródłowy klienta musi mieć deklaracje dostępne w czasie kompilacji. W czasie łączenia konsolidator wymaga informacji do rozpoznania wywołań funkcji lub dostępu do danych. Biblioteka DLL dostarcza te informacje w *bibliotece importu*, plik, który zawiera informacje o sposobach znajdowania funkcji i danych, a nie rzeczywistym kodzie. A w czasie wykonywania Biblioteka DLL musi być dostępna dla klienta w lokalizacji, w której system operacyjny może znaleźć.

Niezależnie od tego, czy jesteś własnym, czy też od innych firm, projekt aplikacji klienta potrzebuje kilku informacji do użycia biblioteki DLL. Musi znajdować się nagłówek, który deklaruje eksporty biblioteki DLL, biblioteki importu dla konsolidatora i samą bibliotekę DLL. Jednym z rozwiązań jest skopiowanie wszystkich tych plików do projektu klienta. W przypadku bibliotek DLL innych firm, które nie są prawdopodobnie zmieniane podczas opracowywania klienta, ta metoda może być najlepszym sposobem ich używania. Jednak w przypadku kompilowania biblioteki DLL lepiej jest unikać duplikacji. Jeśli utworzysz lokalną kopię plików DLL, które są opracowywane, można przypadkowo zmienić plik nagłówka w jednej kopii, ale nie w innym, lub użyć nieaktualnej biblioteki.

Aby uniknąć braku synchronizacji kodu, zalecamy ustawienie ścieżki include w projekcie klienta w celu uwzględnienia plików nagłówkowych DLL bezpośrednio z projektu DLL. Ponadto należy ustawić ścieżkę biblioteki w projekcie klienta, aby uwzględnić biblioteki importu bibliotek DLL z projektu DLL. A wreszcie Skopiuj skompilowaną bibliotekę DLL z projektu DLL do katalogu wyjściowego kompilacji klienta. Ten krok umożliwia aplikacji klienckiej użycie tego samego kodu DLL, który został skompilowany.

::: moniker range=">=vs-2019"

### <a name="to-create-a-client-app-in-visual-studio"></a>Aby utworzyć aplikację kliencką w programie Visual Studio

1. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt** , aby otworzyć okno dialogowe **Tworzenie nowego projektu** .

1. W górnej części okna dialogowego Ustaw  **Język** na **C++**, ustaw **platformę** na **Windows**i ustaw **Typ projektu** na **Console**.

1. Z listy filtrowane typy projektów wybierz pozycję **Aplikacja konsolowa** , a następnie wybierz przycisk **dalej**.

1. Na stronie **Konfiguruj nowy projekt** wprowadź *MathClient* w polu **Nazwa projektu** , aby określić nazwę projektu. Pozostaw domyślne wartości **lokalizacji** i **nazwy rozwiązania** . Ustaw **rozwiązanie** , aby **utworzyć nowe rozwiązanie**. Usuń zaznaczenie pola wyboru **Umieść rozwiązanie i projekt w tym samym katalogu,** jeśli jest zaznaczone.

   ![Nadaj nazwę projektowi klienta](media/mathclient-project-name-2019.png "Nadaj nazwę projektowi klienta")

1. Wybierz przycisk **Utwórz** , aby utworzyć projekt klienta.

Zostanie utworzony projekt minimalnej aplikacji konsolowej. Nazwa głównego pliku źródłowego jest taka sama jak nazwa projektu wprowadzona wcześniej. W tym przykładzie nosi nazwę **MathClient. cpp**. Można go skompilować, ale nie używa jeszcze biblioteki DLL.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-client-app-in-visual-studio-2017"></a>Aby utworzyć aplikację kliencką w programie Visual Studio 2017

1. Aby utworzyć aplikację C++, która używa utworzonej przez Ciebie biblioteki DLL, na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

1. W lewym okienku okna dialogowego **Nowy projekt** wybierz pozycję **pulpit systemu Windows** w obszarze **zainstalowane**  >  **Visual C++**. W środkowym okienku wybierz pozycję **Aplikacja konsolowa systemu Windows**. Określ nazwę projektu, *MathClient*, w polu **Nazwa** .  Pozostaw domyślne wartości **lokalizacji** i **nazwy rozwiązania** . Ustaw **rozwiązanie** , aby **utworzyć nowe rozwiązanie**. Zaznacz opcję **Utwórz katalog dla rozwiązania** , jeśli nie jest zaznaczone.

   ![Nadaj nazwę projektowi klienta](media/mathclient-new-project-name-159.png "Nadaj nazwę projektowi klienta")

1. Wybierz **przycisk OK** , aby utworzyć projekt aplikacji klienckiej.

Zostanie utworzony projekt minimalnej aplikacji konsolowej. Nazwa głównego pliku źródłowego jest taka sama jak nazwa projektu wprowadzona wcześniej. W tym przykładzie nosi nazwę **MathClient. cpp**. Można go skompilować, ale nie używa jeszcze biblioteki DLL.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-client-app-in-visual-studio-2015"></a>Aby utworzyć aplikację kliencką w programie Visual Studio 2015

1. Aby utworzyć aplikację C++, która używa utworzonej przez Ciebie biblioteki DLL, na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

1. W lewym okienku okna dialogowego **Nowy projekt** wybierz pozycję **Win32** w obszarze **zainstalowane**  >  **Szablony**  >  **Visual C++**. W środkowym okienku wybierz pozycję **aplikacja konsoli Win32**. Określ nazwę projektu, *MathClient*, w polu **Nazwa** . Pozostaw domyślne wartości **lokalizacji** i **nazwy rozwiązania** . Ustaw **rozwiązanie** , aby **utworzyć nowe rozwiązanie**. Zaznacz opcję **Utwórz katalog dla rozwiązania** , jeśli nie jest zaznaczone.

   ![Nadaj nazwę projektowi klienta](media/mathclient-project-name.png "Nadaj nazwę projektowi klienta")

1. Wybierz przycisk **OK** , aby odrzucić okno dialogowe **Nowy projekt** i uruchomić **Kreatora aplikacji Win32**. Na stronie **Omówienie** okna dialogowego **Kreator aplikacji Win32** wybierz przycisk **dalej** .

1. Na stronie **Ustawienia aplikacji** w obszarze **Typ aplikacji**wybierz pozycję **Aplikacja konsolowa** , jeśli nie została jeszcze wybrana.

1. Wybierz przycisk **Zakończ** , aby utworzyć projekt.

Po zakończeniu pracy kreatora zostanie utworzony projekt o minimalnej aplikacji konsolowej. Nazwa głównego pliku źródłowego jest taka sama jak nazwa projektu wprowadzona wcześniej. W tym przykładzie nosi nazwę **MathClient. cpp**. Można go skompilować, ale nie używa jeszcze biblioteki DLL.

::: moniker-end

Następnie, aby wywołać funkcje MathLibrary w kodzie źródłowym, projekt musi zawierać plik *MathLibrary. h* . Możesz skopiować ten plik nagłówka do projektu aplikacji klienckiej, a następnie dodać go do projektu jako istniejący element. Ta metoda może być dobrym wyborem dla bibliotek innych firm. Jeśli jednak pracujesz nad kodem biblioteki DLL i klienta w tym samym czasie, pliki nagłówkowe mogą nie być zsynchronizowane. Aby uniknąć tego problemu, należy ustawić ścieżkę do **katalogu dodatkowe katalogi dołączane** w projekcie w celu uwzględnienia ścieżki do oryginalnego nagłówka.

### <a name="to-add-the-dll-header-to-your-include-path"></a>Aby dodać nagłówek DLL do ścieżki dołączania

1. Kliknij prawym przyciskiem myszy węzeł **MathClient** w **Eksplorator rozwiązań** , aby otworzyć okno dialogowe **strony właściwości** .

1. W polu listy rozwijanej **Konfiguracja** wybierz opcję **wszystkie konfiguracje** , jeśli nie została jeszcze wybrana.

1. W lewym okienku wybierz pozycję **Właściwości konfiguracji**  >  **C/C++**  >  **Ogólne**.

1. W okienku właściwości wybierz kontrolkę listy rozwijanej obok pola **Dodatkowe katalogi dołączane** , a następnie wybierz pozycję **Edytuj**.

   ![Edytuj Właściwość dodatkowe katalogi dołączane](media/mathclient-additional-include-directories-property.png "Edytuj Właściwość dodatkowe katalogi dołączane")

1. Kliknij dwukrotnie w górnym okienku okna dialogowego **Dodatkowe katalogi dołączane** , aby włączyć kontrolkę edycji. Lub wybierz ikonę folderu, aby utworzyć nowy wpis.

1. W kontrolce Edycja określ ścieżkę do lokalizacji pliku nagłówkowego **MathLibrary. h** . Możesz wybrać kontrolkę wielokropka (**...**), aby przejść do odpowiedniego folderu.

   Możesz również wprowadzić ścieżkę względną z plików źródłowych klienta do folderu, który zawiera pliki nagłówkowe DLL. Jeśli wykonano instrukcje umieszczania projektu klienta w oddzielnym rozwiązaniu z biblioteki DLL, ścieżka względna powinna wyglądać następująco:

   `..\..\MathLibrary\MathLibrary`

   Jeśli biblioteka DLL i projekty klienta znajdują się w tym samym rozwiązaniu, ścieżka względna może wyglądać następująco:

   `..\MathLibrary`

   Gdy projekty DLL i klienta znajdują się w innych folderach, Dostosuj ścieżkę względną do dopasowania. Lub użyj kontrolki wielokropka, aby wyszukać folder.

   ![Dodaj lokalizację nagłówka do właściwości dodatkowe katalogi dołączane](media/mathclient-additional-include-directories.png "Dodaj lokalizację nagłówka do właściwości dodatkowe katalogi dołączane")

1. Po wprowadzeniu ścieżki do pliku nagłówkowego w oknie dialogowym **Dodatkowe katalogi dołączenia** wybierz przycisk **OK** . W oknie dialogowym **strony właściwości** wybierz przycisk **OK** , aby zapisać zmiany.

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

Ten kod może być skompilowany, ale nie połączony. Jeśli aplikacja kliencka zostanie utworzona teraz, lista błędów zawiera kilka błędów LNK2019. Dzieje się tak, ponieważ w projekcie brakuje pewnych informacji: nie określono, że projekt ma zależność od jeszcze *MathLibrary. lib* . I nie otrzymasz od Ciebie wskazówek, jak znaleźć plik *MathLibrary. lib* .

Aby rozwiązać ten problem, można skopiować plik biblioteki bezpośrednio do projektu aplikacji klienckiej. Konsolidator odnajdzie i użyje go automatycznie. Jeśli jednak biblioteka i aplikacja kliencka są opracowywane, co może prowadzić do zmian w jednej kopii, która nie jest wyświetlana w drugim. Aby uniknąć tego problemu, można ustawić właściwość **dodatkowe zależności** , aby poinformować system kompilacji, że projekt jest zależny od *MathLibrary. lib*. I można ustawić **dodatkową ścieżkę katalogów bibliotek** w projekcie, aby uwzględnić ścieżkę do oryginalnej biblioteki podczas łączenia.

### <a name="to-add-the-dll-import-library-to-your-project"></a>Aby dodać bibliotekę importowania biblioteki DLL do projektu

1. Kliknij prawym przyciskiem myszy węzeł **MathClient** w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości** , aby otworzyć okno dialogowe **strony właściwości** .

1. W polu listy rozwijanej **Konfiguracja** wybierz opcję **wszystkie konfiguracje** , jeśli nie została jeszcze wybrana. Gwarantuje to, że wszelkie zmiany właściwości mają zastosowanie zarówno do kompilacji debugowania, jak i wydania.

1. W lewym okienku wybierz kolejno pozycje **Właściwości konfiguracji**  >  **Linker**  >  **dane wejściowe**konsolidatora. W okienku właściwości wybierz kontrolkę listy rozwijanej obok pola Edytuj **dodatkowe zależności** , a następnie wybierz polecenie **Edytuj**.

   ![Edytuj Właściwość dodatkowe zależności](media/mathclient-additional-dependencies-property.png "Edytuj Właściwość dodatkowe zależności")

1. W oknie dialogowym **dodatkowe zależności** Dodaj *MathLibrary. lib* do listy w górnej kontrolce edycji.

   ![Dodawanie zależności biblioteki](media/mathclient-additional-dependencies.png "Dodawanie zależności biblioteki")

1. Wybierz **przycisk OK** , aby wrócić do okna dialogowego **strony właściwości** .

1. W lewym okienku wybierz kolejno pozycje **Właściwości konfiguracji**  >  **konsolidator**  >  **Ogólne**. W okienku właściwości wybierz kontrolkę listy rozwijanej obok pola edycji **Dodatkowe katalogi biblioteki** , a następnie wybierz polecenie **Edytuj**.

   ![Edytuj Właściwość dodatkowe katalogi biblioteki](media/mathclient-additional-library-directories-property.png "Edytuj Właściwość dodatkowe katalogi biblioteki")

1. Kliknij dwukrotnie w górnym okienku okna dialogowego **Dodatkowe katalogi biblioteki** , aby włączyć kontrolkę edycji. W kontrolce Edycja określ ścieżkę do lokalizacji pliku **MathLibrary. lib** . Domyślnie znajduje się on w folderze o nazwie *Debug* bezpośrednio w folderze rozwiązania biblioteki DLL. Jeśli utworzysz kompilację wydania, plik zostanie umieszczony w folderze o nazwie *Release*. Możesz użyć makra, `$(IntDir)` Aby konsolidator mógł znaleźć bibliotekę DLL, niezależnie od tego, jakiego rodzaju kompilacja została utworzona. Jeśli zawarto instrukcje umieszczania projektu klienta w oddzielnym rozwiązaniu od projektu DLL, ścieżka względna powinna wyglądać następująco:

   `..\..\MathLibrary\$(IntDir)`

   Jeśli biblioteka DLL i projekty klienta znajdują się w innych lokalizacjach, Dostosuj ścieżkę względną do dopasowania.

   ![Dodaj katalog biblioteki](media/mathclient-additional-library-directories.png "Dodaj katalog biblioteki")

1. Po wprowadzeniu ścieżki do pliku biblioteki w oknie dialogowym **Dodatkowe katalogi biblioteki** wybierz przycisk **OK** , aby wrócić do okna dialogowego **strony właściwości** . Wybierz **przycisk OK** , aby zapisać zmiany właściwości.

Twoja aplikacja kliencka może teraz kompilować i łączyć się, ale nadal nie ma wszystkiego, czego potrzebuje do uruchomienia. Gdy system operacyjny ładuje aplikację, szuka biblioteki DLL MathLibrary. Jeśli nie można odnaleźć biblioteki DLL w określonych katalogach systemowych, ścieżce środowiska lub lokalnego katalogu aplikacji, ładowanie nie powiedzie się. W zależności od systemu operacyjnego zobaczysz komunikat o błędzie podobny do tego:

![Błąd nie znaleziono biblioteki DLL MathLibrary](media/mathclient-system-error-mathlibrary-dll-not-found.png "Błąd nie znaleziono biblioteki DLL MathLibrary")

Jednym ze sposobów uniknięcia tego problemu jest skopiowanie biblioteki DLL do katalogu, który zawiera plik wykonywalny klienta w ramach procesu kompilacji. Do projektu można dodać **zdarzenie po kompilacji** , aby dodać polecenie, które kopiuje plik dll do katalogu wyjściowego kompilacji. Określone tutaj polecenie kopiuje bibliotekę DLL tylko wtedy, gdy jej nie ma lub została zmieniona. Używa makr do kopiowania do i z lokalizacji debugowania lub wersji w oparciu o konfigurację kompilacji.

### <a name="to-copy-the-dll-in-a-post-build-event"></a>Aby skopiować bibliotekę DLL w zdarzeniu po kompilacji

1. Kliknij prawym przyciskiem myszy węzeł **MathClient** w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości** , aby otworzyć okno dialogowe **strony właściwości** .

1. W polu listy rozwijanej **Konfiguracja** wybierz opcję **wszystkie konfiguracje** , jeśli nie została jeszcze wybrana.

1. W okienku po lewej stronie wybierz pozycję **Właściwości konfiguracji**  >  **kompilacja zdarzenia**  >  **po kompilacji**.

1. W okienku właściwości wybierz kontrolkę Edycja w polu **wiersz polecenia** . Jeśli zawarto instrukcje dotyczące umieszczania projektu klienta w oddzielnym rozwiązaniu z projektu DLL, wprowadź następujące polecenie:

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   Jeśli biblioteka DLL i projekty klienta znajdują się w innych katalogach, zmień ścieżkę względną do biblioteki DLL, aby była zgodna.

   ![Dodaj polecenie po kompilacji](media/mathclient-post-build-command-line.png "Dodaj polecenie po kompilacji")

1. Wybierz przycisk **OK** , aby zapisać zmiany właściwości projektu.

Teraz aplikacja kliencka ma wszystko, czego potrzebuje do skompilowania i uruchomienia. Skompiluj aplikację, wybierając pozycję **Kompiluj**  >  **kompilację** na pasku menu. Okno **danych wyjściowych** w programie Visual Studio powinno wyglądać podobnie do poniższego przykładu, w zależności od używanej wersji programu Visual Studio:

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Gratulacje, utworzono aplikację, która wywołuje funkcje w bibliotece DLL. Teraz uruchom aplikację, aby zobaczyć, co robi. Na pasku menu wybierz **Debuguj**  >  **Uruchom bez debugowania**. Program Visual Studio otwiera okno poleceń, które zostanie uruchomione w programie. Ostatnia część danych wyjściowych powinna wyglądać następująco:

![Uruchom aplikację kliencką bez debugowania](media/mathclient-run-without-debugging.png "Uruchom aplikację kliencką bez debugowania")

Naciśnij dowolny klawisz, aby odrzucić okno polecenia.

Po utworzeniu biblioteki DLL i aplikacji klienckiej można eksperymentować. Spróbuj ustawić punkty przerwania w kodzie aplikacji klienckiej, a następnie uruchom aplikację w debugerze. Zobacz, co się stanie, gdy przejdziesz do wywołania biblioteki. Dodaj inne funkcje do biblioteki lub napisz kolejną aplikację kliencką, która korzysta z biblioteki DLL.

Podczas wdrażania aplikacji należy również wdrożyć biblioteki DLL, z których korzysta. Najprostszym sposobem utworzenia bibliotek DLL, które można utworzyć, lub dołączenia ich od stron trzecich, jest umieszczenie ich w tym samym katalogu, w którym znajduje się aplikacja. Nazywa się to *wdrożeniem lokalnym aplikacji*. Aby uzyskać więcej informacji o wdrażaniu, zobacz [wdrażanie w Visual C++](../windows/deployment-in-visual-cpp.md).

## <a name="see-also"></a>Zobacz także

[Wywoływanie funkcji DLL z aplikacji Visual Basic](calling-dll-functions-from-visual-basic-applications.md)
