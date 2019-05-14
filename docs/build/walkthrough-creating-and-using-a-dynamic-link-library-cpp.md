---
title: 'Przewodnik: Tworzenie i używanie własnych dynamicznej biblioteki łączy (C++)'
description: Użyj C++ do tworzenia biblioteki dołączanej (dynamicznie DLL) Windows w programie Visual Studio.
ms.custom: conceptual
ms.date: 04/22/2019
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
ms.openlocfilehash: 53cde029973c14bfc5aae521946ebeadbed738ca
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611987"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>Przewodnik: Tworzenie i używanie własnych dynamicznej biblioteki łączy (C++)

Ten przewodnik krok po kroku pokazano, jak użyć środowiska IDE programu Visual Studio do utworzenia własnego w języku C++ Biblioteka dołączana dynamicznie (DLL), a następnie użyć go z innej aplikacji C++. Biblioteki dll (znany także jako biblioteki udostępnione w systemach operacyjnych UNIX) są jednymi z najbardziej przydatnych rodzaje składników Windows. Można je jako sposób udostępniaj kod i zasoby, aby zmniejszyć rozmiar aplikacji i ułatwiają usługi i rozszerzaj swoje aplikacje. W tym przewodniku tworzy bibliotekę DLL, który implementuje pewne funkcje matematyczne, a następnie utwórz aplikację konsoli, która używa funkcji z biblioteki DLL. Po drodze zapoznaj się z wprowadzeniem do niektórych techniki programowania i Konwencji używanych w bibliotekach DLL Windows.

W tym przewodniku opisano następujące zadania:

- Utwórz projekt biblioteki DLL w programie Visual Studio.

- Dodaj wyeksportowanych funkcji i zmiennych do biblioteki DLL.

- Utwórz projekt aplikacji konsoli w programie Visual Studio.

- Korzystając z funkcji i zmiennych zaimportowany z biblioteki DLL w aplikacji konsoli.

- Uruchom ukończoną aplikację.

Statycznie połączone biblioteki DLL, takie jak _eksportuje_ zmienne, funkcje i zasoby według nazwy i aplikację _importuje_ te nazwy, aby użyć tych zmiennych, funkcji i zasobów. W odróżnieniu od statycznie połączoną bibliotekę Windows Importy w swojej aplikacji łączy się z eksportu w bibliotece DLL w czasie ładowania lub w czasie wykonywania, a nie połączenie ich w czasie połączenia. Windows wymaga dodatkowych informacji, które nie jest częścią standardowego modelu kompilacji C++, aby nawiązać połączenie. Kompilator MSVC implementuje niektóre rozszerzenia specyficzne dla firmy Microsoft do C++, aby zapewnić te dodatkowe informacje. Wyjaśnijmy tych rozszerzeń, kursu.

Ten poradnik tworzy dwa rozwiązań programu Visual Studio. taki, który tworzy bibliotekę DLL, a taki, który kompiluje aplikację kliencką. Biblioteki DLL używa konwencji wywoływania C, dzięki czemu można wywołać z aplikacji skompilowanych przy użyciu innych języków, tak długo, jak platformy i wywoływania i łączenie konwencje są zgodne. Ta aplikacja używa klienta _niejawna Konsolidacja_, gdzie Windows łączy aplikację z biblioteki DLL w czasie ładowania. To połączenie umożliwia aplikacji wywoływać funkcje dostarczone przez bibliotekę DLL, podobnie jak funkcje statycznie połączone biblioteki.

Ten przewodnik nie obejmuje niektóre typowe problemy. Korzystanie z bibliotek DLL języka C++ w innych językach programowania nie była widoczna. Go nie pokazuje jak utworzyć bibliotekę DLL tylko do zasobów. Również nie pokazuje użycie jawnego łączenia można załadować biblioteki dll w czasie wykonywania, a nie w czasie ładowania. Zachowaj spokój ducha i Visual C++ można użyć, aby korzystać z tych możliwości. Aby uzyskać linki do szczegółowych informacji o bibliotece dll, zobacz [Utwórz C /C++ bibliotek DLL w programie Visual Studio](dlls-in-visual-cpp.md). Aby uzyskać więcej informacji na temat łączenia niejawne i jawne tworzenie łączy, zobacz [określająca, które łączenie metody użyć](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use). Aby uzyskać informacji o tworzeniu bibliotek DLL języka C++ do użycia z usługą języki programowania, które używać konwencji powiązania języka C, zobacz [eksportowanie funkcji C++ do użycia w plikach wykonywalnych języka C](exporting-cpp-functions-for-use-in-c-language-executables.md). Aby uzyskać informacji na temat sposobu tworzenia bibliotek DLL dla języków .NET, zobacz [wywoływanie funkcji DLL z aplikacji Visual Basic](calling-dll-functions-from-visual-basic-applications.md).

## <a name="prerequisites"></a>Wymagania wstępne

- Komputer z systemem Microsoft Windows 7 lub nowszy. Zalecamy systemu Windows 10 dla najlepszego komfortu programowania.

- Kopię programu Visual Studio. Aby uzyskać informacje na temat sposobu pobierania i instalowania programu Visual Studio, zobacz [Zainstaluj program Visual Studio](/visualstudio/install/install-visual-studio). Po uruchomieniu Instalatora, upewnij się, że **programowanie aplikacji klasycznych w języku C++** zaznaczono obciążenia. Nie martw się, jeśli nie zainstalował tego obciążenia podczas instalowania programu Visual Studio. Można ponownie uruchom Instalatora i zainstaluj go teraz.

   ![Programowanie aplikacji klasycznych w języku C++](media/desktop-development-with-cpp.png "programowanie aplikacji klasycznych w języku C++")

- Zrozumienie podstaw przy użyciu programu Visual Studio IDE. Jeśli używano aplikacje komputerowe Windows przed prawdopodobnie można zachować. Aby zapoznać się z wprowadzeniem, zobacz [Przewodnik po funkcjach programu Visual Studio IDE](/visualstudio/ide/visual-studio-ide).

- Po zrozumieniu wystarczającą ilość podstawy języka C++ z nich skorzystać. Nie martw się — firma Microsoft nie robią niczego zbyt skomplikowana.

## <a name="create-the-dll-project"></a>Utwórz projekt biblioteki DLL

W tym zestawie zadania Tworzenie projektu dla biblioteki DLL, Dodaj kod i skompiluj go. Aby rozpocząć, uruchom środowiska IDE programu Visual Studio, a następnie zaloguj się, jeśli potrzebujesz. Instrukcje różnią się nieco w zależności od instalowanej wersji programu Visual Studio, którego używasz. Upewnij się, że masz odpowiednią wersję wybranego w kontrolce, w lewym górnym rogu tej strony.

::: moniker range="=vs-2019"

### <a name="to-create-a-dll-project-in-visual-studio-2019"></a>Aby utworzyć projekt DLL w programie Visual Studio 2019 r.

1. Na pasku menu wybierz **pliku** > **New** > **projektu** otworzyć **Utwórz nowy projekt** okno dialogowe.

   ![Utwórz nowy projekt DLL](media/create-new-dll-project-2019.png "Utwórz projekt MathLibrary")

1. W górnej części okna dialogowego, ustaw **języka** do **C++** ustaw **platformy** do **Windows**i ustaw **Typprojektu** do **biblioteki**. 

1. Wybierz z listy filtrowanej typów projektów, **Biblioteka dołączana dynamicznie (DLL)** wybierz **dalej**. Na następnej stronie podaj `MathLibrary` w **nazwa** polu Określ nazwę dla projektu i określ lokalizację projektu, w razie potrzeby.

1. Wybierz **Utwórz** przycisk, aby utworzyć projekt.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-dll-project-in-visual-studio-2017"></a>Aby utworzyć projekt DLL w programie Visual Studio 2017

1. Na pasku menu wybierz **pliku** > **New** > **projektu** otworzyć **nowy projekt** okno dialogowe.

1. W okienku po lewej stronie **nowy projekt** okna dialogowego rozwiń **zainstalowane** i **Visual C++** Jeśli to konieczne, a następnie wybierz **pulpitu Windows** . W środkowym okienku wybierz **kreatora pulpitu Windows**. Wprowadź `MathLibrary` w **nazwa** pole, aby określić nazwę dla projektu.

   ![Nazwij projekt MathLibrary](media/mathlibrary-new-project-name-153.png "nazwij projekt MathLibrary")

1. Wybierz **OK** przycisk, aby odrzucić **nowy projekt** okna dialogowego i uruchom **projektu pulpitu Windows** kreatora.

1. W **projektu pulpitu Windows** kreatora w obszarze **typ aplikacji**, wybierz opcję **Biblioteka dołączana dynamicznie (dll)**.

   ![Tworzenie biblioteki DLL w Kreatorze projektu pulpitu Windows](media/mathlibrary-desktop-project-wizard-dll.png "tworzy bibliotekę DLL w Kreatorze projektu pulpitu Windows")

1. Wybierz **OK** przycisk, aby utworzyć projekt.

> [!NOTE]
> Dodatkowe kroki są wymagane w celu rozwiązania problemu w programie Visual Studio 2017 w wersji 15.3. Wykonaj te instrukcje, aby zobaczyć, jeśli musisz wprowadzić tę zmianę.
>
>1. W **Eksploratora rozwiązań**, jeśli nie został jeszcze wybrany, wybierz opcję **MathLibrary** projekt **rozwiązania "MathLibrary"**.
>
>1. Na pasku menu wybierz **projektu** > **właściwości**.
>
>1. W okienku po lewej stronie **stron właściwości** okno dialogowe, wybierz opcję **preprocesora** w obszarze **właściwości konfiguracji** > **C/C++**. Sprawdź zawartość **definicje preprocesora** właściwości.<br/><br/>![Sprawdź właściwość definicje preprocesora](media/mathlibrary-153bug-preprocessor-definitions-check.png "Sprawdź właściwość definicje preprocesora")<br/><br/>Jeśli widzisz **MATHLIBRARY&#95;EKSPORTÓW** w **definicje preprocesora** listy, a następnie nie trzeba wprowadzić zmiany. Jeśli widzisz **MathLibrary&#95;EKSPORTÓW** zamiast niego, a następnie kontynuować wykonaj następujące kroki.
>
>1. W górnej części **stron właściwości** okno dialogowe, zmiana **konfiguracji** menu rozwijane **wszystkie konfiguracje**.
>
>1. W okienku właściwości, wybierz formant listy rozwijanej obok pola edycji dla **definicje preprocesora**, a następnie wybierz **Edytuj**.<br/><br/>![Edytuj właściwość definicje preprocesora](media/mathlibrary-153bug-preprocessor-definitions-property.png "Edytuj właściwość definicje preprocesora")
>
>1. W górnym okienku **definicje preprocesora** oknie dialogowym Dodaj nowy symbol `MATHLIBRARY_EXPORTS`.<br/><br/>![Dodaj MATHLIBRARY_EXPORTS symbol](media/mathlibrary-153bug-preprocessor-definitions-dialog.png "dodać MATHLIBRARY_EXPORTS symbol")
>
>1. Wybierz **OK** odrzucać **definicje preprocesora** okno dialogowe, a następnie wybierz **OK** Aby zapisać zmiany we właściwościach projektu.

::: moniker-end

::: moniker range="=vs-2015"

### <a name="to-create-a-dll-project-in-older-versions-of-visual-studio"></a>Aby utworzyć projekt DLL w starszych wersjach programu Visual Studio

1. Na pasku menu wybierz **pliku** > **New** > **projektu**.

1. W okienku po lewej stronie **nowy projekt** okna dialogowego rozwiń **zainstalowane** > **szablony**i wybierz **Visual C++**, i następnie w środkowym okienku wybierz **Aplikacja konsoli Win32**. Wprowadź `MathLibrary` w **nazwa** Edytuj pole, aby określić nazwę dla projektu.

   ![Nazwij projekt MathLibrary](media/mathlibrary-project-name.png "nazwij projekt MathLibrary")

1. Wybierz **OK** przycisk, aby odrzucić **nowy projekt** okna dialogowego i uruchom **Kreatora aplikacji Win32**.

   ![Omówienie Kreatora aplikacji Win32](media/mathlibrary-project-wizard-1.png "Omówienie Kreatora aplikacji Win32")

1. Wybierz **dalej** przycisku. Na **ustawienia aplikacji** w obszarze **typ aplikacji**, wybierz opcję **DLL**.

   ![Tworzenie biblioteki DLL w Kreatora aplikacji Win32](media/mathlibrary-project-wizard-2.png "Tworzenie biblioteki DLL w Kreatora aplikacji Win32")

1. Wybierz **Zakończ** przycisk, aby utworzyć projekt.

Po zakończeniu działania kreatora rozwiązania widać wygenerowanych plików projektu i źródła w **Eksploratora rozwiązań** okna w programie Visual Studio.

![Wygenerowany rozwiązania w programie Visual Studio](media/mathlibrary-solution-explorer-153.png "generowane rozwiązania w programie Visual Studio")

Po prawej stronie teraz tę bibliotekę DLL nie robi zbyt wielu. Następnie możesz utworzyć plik nagłówka do deklarowania funkcji DLL eksportuje, a następnie dodaj definicje funkcji do biblioteki DLL, aby zwiększyć jej użyteczność.

::: moniker-end

### <a name="to-add-a-header-file-to-the-dll"></a>Aby dodać plik nagłówkowy biblioteki dll

1. Aby utworzyć plik nagłówka dla funkcji, na pasku menu, wybierz opcję **projektu** > **Dodaj nowy element**.

1. W **Dodaj nowy element** w okienku po lewej stronie, wybierz w oknie dialogowym **Visual C++**. W środkowym okienku wybierz **plik nagłówka (.h)**. Określ `MathLibrary.h` jako nazwę pliku nagłówka.

   ![Dodaj nagłówek w oknie dialogowym Dodaj nowy element](media/mathlibrary-add-new-item-header-file.png "Dodaj nagłówek pliku w oknie dialogowym Dodaj nowy element")

1. Wybierz **Dodaj** przycisk, aby wygenerować pusty nagłówek pliku, który jest wyświetlany w nowym oknie edytora.

   ![Pusty plik MathLibrary.h w edytorze](media/edit-empty-mathlibrary-header.png "MathLibrary.h pusty plik w edytorze")

1. Zastąp zawartość pliku nagłówka przy użyciu tego kodu:

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

Tego pliku nagłówkowego deklaruje niektórych funkcji, aby wygenerować uogólnionego sekwencji Fibonacci danego dwie wartości początkowej. Wywołanie `fibonacci_init(1, 1)` generuje sekwencję znanych Fibonacci numer.

Zwróć uwagę, instrukcje preprocesora na początku pliku. Domyślnie dodaje szablon nowego projektu biblioteki DLL  **\<em > PROJECTNAME\</em >&#95;EKSPORTY** preprocesora makrach zdefiniowanych dla projektu biblioteki DLL. W tym przykładzie program Visual Studio definiuje **MATHLIBRARY&#95;EKSPORTÓW** podczas kompilowania projektu MathLibrary biblioteki DLL. 

::: moniker range="=vs-2017"

(Kreatora w programie Visual Studio 2017 w wersji 15.3 nie wymusza tę definicję symbolu na wielkie litery. Jeśli nazwa projektu "MathLibrary", a następnie symbol zdefiniowany jest MathLibrary&#95;EKSPORTY zamiast MATHLIBRARY&#95;eksportu. That's Dlaczego istnieją dodatkowe powyższe kroki, aby dodać ten symbol.)

::: moniker-end

Gdy **MATHLIBRARY&#95;EKSPORTÓW** — makro jest zdefiniowany, **MATHLIBRARY&#95;interfejsu API** zestawów — makro `__declspec(dllexport)` modyfikatora w deklaracji funkcji. Ten modyfikator informuje kompilator i konsolidator, aby wyeksportować funkcji lub zmiennej z biblioteki DLL, dzięki czemu mogą być używane przez inne aplikacje. Gdy **MATHLIBRARY&#95;EKSPORTY** jest niezdefiniowana, na przykład, gdy plik nagłówkowy jest uwzględniony przez aplikację kliencką **MATHLIBRARY&#95;interfejsu API** stosuje `__declspec(dllimport)` modyfikatora deklaracje. Ten modyfikator optymalizację importu funkcji lub zmienna w aplikacji. Aby uzyskać więcej informacji, zobacz [dllexport i dllimport](../cpp/dllexport-dllimport.md).

### <a name="to-add-an-implementation-to-the-dll"></a>Aby dodać implementację do biblioteki DLL

::: moniker range="vs-2019"

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **pliki źródłowe** węzeł i Dodaj nowy plik .cpp, o nazwie `MathLibrary.cpp` w taki sam sposób, jak dodać nowy plik nagłówkowy w poprzednim kroku.

::: moniker-end

1. W oknie edytora, wybierz kartę **MathLibrary.cpp** Jeśli jest już otwarty. W przeciwnym razie w **Eksploratora rozwiązań**, otwórz **MathLibrary.cpp** w **pliki źródłowe** folderu **MathLibrary** projektu.

1. W edytorze Zastąp zawartość pliku MathLibrary.cpp następującym kodem:

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h" // use pch.h in Visual Studio 2019
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

Aby sprawdzić, czy wszystko działa do tej pory, kompilowanie biblioteki dołączanej dynamicznie. Aby skompilować, wybierz opcję **kompilacji** > **Kompiluj rozwiązanie** na pasku menu. Dane wyjściowe powinny wyglądać mniej więcej tak:

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

Gratulacje, utworzono biblioteki DLL przy użyciu języka Visual C++! Następnie utworzysz aplikację kliencką, która używa funkcji eksportowanych przez DLL.

## <a name="create-a-client-app-that-uses-the-dll"></a>Utwórz aplikację kliencką, która używa biblioteki DLL

Podczas tworzenia biblioteki DLL należy myśleć o tym, jak używać biblioteki DLL. Aby skompilować kod, który wywołuje funkcji eksportowanych przez DLL, deklaracje muszą być zawarte w kodzie źródłowym klienta. W czasie, gdy te wywołania funkcji biblioteki DLL są rozwiązywane, konsolidator musi mieć *Importuj bibliotekę*, to plik biblioteki specjalne, która zawiera informacje o Windows o tym, jak można znaleźć funkcji, a nie rzeczywisty kod. I w czasie wykonywania, biblioteki DLL muszą być dostępne dla klienta w lokalizacji, która znajduje się system operacyjny.

Do korzystania z biblioteki dll, czy Twoje właścicielem lub biblioteki DLL innych firm, projekt aplikacji klienta należy znaleźć nagłówki, które deklarują biblioteki DLL eksportuje biblioteki importu dla konsolidatora i biblioteki DLL, sam. Jest jednym ze sposobów, aby skopiować te pliki do projektu client. Dla bibliotek DLL innych firm, które są raczej nie ulegnie zmianie, gdy klient jest w trakcie opracowywania ta metoda może być najlepszym sposobem, aby umożliwić ich używanie. W przypadku tworzenia również biblioteki DLL, zaleca się unikać dublowania. Jeśli wprowadzisz kopię plików DLL, które są w fazie projektowania, może przypadkowo zmienić pliku nagłówka w jednej kopii, ale nie drugiej, lub używana biblioteka nieaktualne. Aby uniknąć tego problemu, zalecane ustawienia ścieżki include w projekcie klienta, aby uwzględnić pliki nagłówkowe biblioteki DLL z projektu DLL. Ponadto można ustawić ścieżki biblioteki w projekcie klienta do uwzględnienia bibliotek importu biblioteki DLL z projektu DLL. A na koniec skopiuj skompilowane biblioteki DLL z projektu DLL do katalogu wyjściowego kompilacji. Ten krok umożliwia aplikację kliencką użyć tego samego kodu biblioteki DLL, które tworzysz.

::: moniker range="vs-2019"

### <a name="to-create-a-client-app-in-visual-studio-2019"></a>Aby utworzyć aplikację klienta w programie Visual Studio 2019 r.

1. Na pasku menu wybierz **pliku** > **New** > **projektu** otworzyć **Utwórz nowy projekt** okno dialogowe.

1. W górnej części okna dialogowego, ustaw **języka** do **C++** ustaw **platformy** do **Windows**i ustaw **Typprojektu** do **konsoli**. 

1. Wybierz z listy filtrowanej typów projektów, **aplikacja Konsolowa** wybierz **dalej**. Na następnej stronie podaj `MathClient` w **nazwa** polu Określ nazwę dla projektu i określ lokalizację projektu, w razie potrzeby.

   ![Nazwij projekt klienta](media/mathclient-project-name-2019.png "nazwij projekt klienta")

1. Wybierz **Utwórz** przycisk, aby utworzyć projekt klienta.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-client-app-in-visual-studio-2017"></a>Aby utworzyć aplikację klienta w programie Visual Studio 2017

1. Aby utworzyć C++ aplikację, która używa biblioteki DLL, który został utworzony, na pasku menu wybierz **pliku** > **New** > **projektu**.

1. W okienku po lewej stronie **nowy projekt** okno dialogowe, wybierz opcję **pulpitu Windows** w obszarze **zainstalowane** > **Visual C++**. W środkowym okienku wybierz **kreatora pulpitu Windows**. Określ nazwę dla projektu, `MathClient`w **nazwa** pole edycji.

   ![Nazwij projekt klienta](media/mathclient-new-project-name-153.png "nazwij projekt klienta")

1. Wybierz **OK** można uruchomić **projektu pulpitu Windows** kreatora. W kreatorze Wybierz **OK** Aby utworzyć projekt aplikacji klienta.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-client-app-in-older-versions-of-visual-studio-2017"></a>Aby utworzyć aplikację kliencką w starszych wersjach programu Visual Studio 2017

1. Aby utworzyć C++ aplikację, która używa biblioteki DLL, który został utworzony, na pasku menu wybierz **pliku** > **New** > **projektu**.

1. W okienku po lewej stronie **nowy projekt** okno dialogowe, wybierz opcję **Win32** w obszarze **zainstalowane** > **szablony**  >  **Visual C++**. W środkowym okienku wybierz **Aplikacja konsoli Win32**. Określ nazwę dla projektu, `MathClient`w **nazwa** pole edycji.

   ![Nazwij projekt klienta](media/mathclient-project-name.png "nazwij projekt klienta")

1. Wybierz **OK** przycisk, aby odrzucić **nowy projekt** okna dialogowego i uruchom **Kreatora aplikacji Win32**. Na **Przegląd** strony **Kreatora aplikacji Win32** okna dialogowego wybierz **dalej** przycisku.

1. Na **ustawienia aplikacji** w obszarze **typ aplikacji**, wybierz opcję **aplikacji konsolowej programu** Jeśli nie została jeszcze wybrana.

1. Wybierz **Zakończ** przycisk, aby utworzyć projekt.

::: moniker-end

Po zakończeniu pracy Kreatora projektu aplikacji konsolowej minimalny zostanie utworzony. Nazwa pliku głównego źródła jest taka sama jak nazwa projektu, wprowadzony wcześniej. W tym przykładzie jest on nazwany **MathClient.cpp**. Jego tworzenia, ale jeszcze nie używa biblioteki DLL.

Następnie można wywołać funkcji MathLibrary w kodzie źródłowym, projekt musi zawierać plik MathLibrary.h. Można skopiować ten plik nagłówka do projekt aplikacji klienta, a następnie dodać go do projektu jako istniejącego elementu. Ta metoda może być dobrym wyborem dla bibliotek innych firm. Jednak podczas pracy nad kodem dla biblioteki DLL w tym samym czasie jako klienta, który może prowadzić do zmiany w pliku nagłówkowym jeden, które nie są wyświetlane w innym. Aby uniknąć tego problemu, możesz zmienić **dodatkowe katalogi dołączenia** ścieżki w swoim projekcie zawiera ścieżkę do oryginalnego nagłówka.

### <a name="to-add-the-dll-header-to-your-include-path"></a>Aby dodać nagłówek DLL do swojej ścieżki dołączania

1. Kliknij prawym przyciskiem myszy **MathClient** w węźle **Eksploratora rozwiązań** otworzyć **stron właściwości** okna dialogowego.

1. W **konfiguracji** listy rozwijanej wybierz pozycję **wszystkie konfiguracje** Jeśli nie została jeszcze wybrana.

1. W okienku po lewej stronie wybierz **ogólne** w obszarze **właściwości konfiguracji** > **C/C++**.

1. W okienku właściwości wybierz kontrolkę listy rozwijanej obok **dodatkowe katalogi dołączenia** pole edycji, a następnie wybierz **Edytuj**.

   ![Edytuj właściwość dodatkowe katalogi dołączenia](media/mathclient-additional-include-directories-property.png "Edytuj właściwość dodatkowe katalogi dołączenia")

1. W górnym okienku kliknij dwukrotnie ikonę **dodatkowe katalogi dołączenia** okno dialogowe, aby włączyć formant edycji.

1. W formancie edycji, wpisz ścieżkę do lokalizacji **MathLibrary.h** pliku nagłówka. W takim przypadku można użyć ścieżki względnej z folderu, który zawiera pliki .cpp w projekcie klienta do folderu, który zawiera plik .h klasy w projekcie biblioteki DLL. Jeśli projekt klienta znajduje się w oddzielnym rozwiązaniu, w tym samym folderze, jako rozwiązanie do biblioteki DLL, ścieżka względna powinien wyglądać następująco:

   `..\..\MathLibrary\MathLibrary`

   Projekty biblioteki DLL i klienta znajdują się w tym samym rozwiązaniu, czy te rozwiązania są w różnych folderach, następnie należy dostosować ścieżki względnej odpowiednio.

   ![Dodaj nagłówek lokalizacji do właściwości dodatkowe katalogi dołączenia](media/mathclient-additional-include-directories.png "Dodaj lokalizację nagłówka do właściwości dodatkowe katalogi dołączenia")

1. Po wprowadzeniu ścieżkę do pliku nagłówka w **dodatkowe katalogi dołączenia** okna dialogowego wybierz **OK** przycisk, aby przejść z powrotem do **stron właściwości** okno dialogowe i następnie wybierz **OK** przycisk, aby zapisać zmiany.

Teraz możesz uwzględnić **MathLibrary.h** pliku i korzystanie z funkcji deklaruje w aplikacji klienckiej. Zastąp zawartość **MathClient.cpp** przy użyciu tego kodu:

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

Ten kod można skompilowany, ale nie jest to połączony, ponieważ konsolidator nie może odnaleźć biblioteki importowanej, wymagane do kompilowania aplikacji jeszcze. Konsolidator musi znaleźć pliku MathLibrary.lib połączyć pomyślnie. Dodaj plik MathLibrary.lib do kompilacji przez ustawienie **dodatkowe zależności** właściwości. Jeszcze raz można skopiować pliku biblioteki do projektu aplikacji klienta, ale jeśli zarówno aplikacja kliencka, jak i biblioteki są w fazie projektowania, który może prowadzić do zmian w jednej kopii, które nie są wyświetlane w innych. Aby uniknąć tego problemu, możesz zmienić **dodatkowe katalogi bibliotek** ścieżki w projekcie, aby zawrzeć ścieżkę w oryginalnej biblioteki, gdy tworzysz link.

### <a name="to-add-the-dll-import-library-to-your-project"></a>Aby dodać biblioteki importowanej biblioteki DLL do projektu

1. Kliknij prawym przyciskiem myszy **MathClient** w węźle **Eksploratora rozwiązań** otworzyć **stron właściwości** okna dialogowego.

1. W **konfiguracji** listy rozwijanej wybierz pozycję **wszystkie konfiguracje** Jeśli nie została jeszcze wybrana. To ustawienie zapewni, że ścieżka jest ustawiona dla obu debugowania i kompilacji wydania.

1. W okienku po lewej stronie wybierz **dane wejściowe** w obszarze **właściwości konfiguracji** > **konsolidatora**. W okienku właściwości wybierz kontrolkę listy rozwijanej obok **dodatkowe zależności** pole edycji, a następnie wybierz **Edytuj**.

   ![Edytuj właściwość dodatkowe zależności](media/mathclient-additional-dependencies-property.png "Edytuj właściwość dodatkowe zależności")

1. W **dodatkowe zależności** okno dialogowe, Dodaj `MathLibrary.lib` do listy w prawym górnym formant edycji.

   ![Dodaj zależność biblioteki](media/mathclient-additional-dependencies.png "Dodawanie zależności biblioteki")

1. Wybierz **OK** aby wrócić do **stron właściwości** okno dialogowe.

1. W okienku po lewej stronie wybierz **ogólne** w obszarze **właściwości konfiguracji** > **konsolidatora**. W okienku właściwości wybierz kontrolkę listy rozwijanej obok **dodatkowe katalogi bibliotek** pole edycji, a następnie wybierz **Edytuj**.

   ![Edytuj właściwość dodatkowe katalogi bibliotek](media/mathclient-additional-library-directories-property.png "Edytuj właściwość dodatkowe katalogi biblioteki")

1. W górnym okienku kliknij dwukrotnie ikonę **dodatkowe katalogi bibliotek** okno dialogowe, aby włączyć formant edycji. W formancie edycji, wpisz ścieżkę do lokalizacji **MathLibrary.lib** pliku. Wprowadź tę wartość, aby użyć makra, który działa w przypadku zarówno Debug i Release kompiluje:

   `..\..\MathLibrary\$(IntDir)`

   ![Dodaj katalog biblioteki](media/mathclient-additional-library-directories.png "Dodaj katalog biblioteki")

1. Po wprowadzeniu ścieżkę do pliku biblioteki w **dodatkowe katalogi bibliotek** okna dialogowego wybierz **OK** przycisk, aby przejść z powrotem do **stron właściwości** okno dialogowe.

Aplikację kliencką teraz kompilowanie i łączenie pomyślnie, ale nadal nie ma wszystko, czego potrzebuje do uruchomienia. Podczas ładowania aplikacji system operacyjny wyszukuje MathLibrary biblioteki DLL. Nie można odnaleźć biblioteki DLL w niektórych katalogów systemu, ścieżki środowiska lub katalogu aplikacji lokalnych, obciążenia nie powiedzie się. Jednym ze sposobów, aby uniknąć tego problemu jest Kopiuj bibliotekę DLL do katalogu, który zawiera plik wykonywalny klienta jako część procesu kompilacji. Aby skopiować bibliotekę DLL, można dodać **zdarzenia Postkompilacyjnego** do projektu, aby dodać polecenie które biblioteki DLL kopiuje do katalogu wyjściowego kompilacji. Określone tutaj polecenie kopiuje bibliotekę DLL tylko wtedy, gdy jest brak lub została zmieniona i używa makra można skopiować do i z prawidłowych Debuguj lub zwolnij lokalizacji dla danej konfiguracji.

### <a name="to-copy-the-dll-in-a-post-build-event"></a>Aby skopiować biblioteki DLL w zdarzeniu po kompilacji

1. Kliknij prawym przyciskiem myszy **MathClient** w węźle **Eksploratora rozwiązań** otworzyć **stron właściwości** okna dialogowego.

1. W polu listy rozwijanej konfiguracji wybierz **wszystkie konfiguracje** Jeśli nie została jeszcze wybrana.

1. W okienku po lewej stronie wybierz **zdarzenia Postkompilacyjnego** w obszarze **właściwości konfiguracji** > **zdarzenia kompilacji**.

1. W okienku właściwości, wybierz formant edycji w **wiersza polecenia** pola, a następnie wprowadź następujące polecenie:

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   ![Dodaj polecenie postkompilacyjnego](media/mathclient-post-build-command-line.png "Dodaj polecenie po kompilacji")

1. Wybierz **OK** przycisk, aby zapisać zmiany we właściwościach projektu.

Teraz aplikację kliencką ma wszystko, co jest potrzebne do kompilowania i uruchamiania. Kompiluj aplikację, wybierając **kompilacji** > **Kompiluj rozwiązanie** na pasku menu. **Dane wyjściowe** okna w programie Visual Studio powinny mieć mniej więcej tak:

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>pch.cpp
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.pdb (Partial PDB)
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Gratulacje, utworzono aplikację, która wywołuje funkcje w bibliotece DLL. Teraz można uruchomić aplikacji, aby zobaczyć, jak działa. Na pasku menu wybierz **debugowania** > **Rozpocznij bez debugowania**. Program Visual Studio otwiera okno polecenia do uruchomienia programu. Ostatnia część dane wyjściowe powinny wyglądać:

![Uruchom aplikację kliencką bez debugowania](media/mathclient-run-without-debugging.png "Uruchom aplikację kliencką bez debugowania")

Naciśnij dowolny klawisz, aby zamknąć okno polecenia.

Teraz, po utworzeniu biblioteki DLL i aplikacja kliencka, możesz eksperymentować. Spróbuj ustawić punkty przerwania w kodzie aplikacji klienckiej i uruchomić aplikację w debugerze. Zobacz, co się stanie, gdy wchodzisz do wywołania biblioteki. Dodawanie innych funkcji w bibliotece lub innej aplikacji klienta, który korzysta z biblioteki DLL do zapisu.

Podczas wdrażania aplikacji, należy wdrożyć używa biblioteki dll. Najprostszym sposobem udostępnienia biblioteki dll, tworzenia, lub możesz uwzględnić pochodzące od innych firm do aplikacji jest umieścić w tym samym katalogu co aplikacja, znany także jako *wdrożenia lokalnego dla aplikacji*. Aby uzyskać więcej informacji na temat wdrażania, zobacz [wdrożenia w programie Visual C++](../windows/deployment-in-visual-cpp.md).

## <a name="see-also"></a>Zobacz także

[Wywoływanie funkcji DLL z aplikacji języka Visual Basic](calling-dll-functions-from-visual-basic-applications.md)
