---
title: 'Przewodnik: Kompilowanie natywnego programu C++ w wierszu polecenia'
ms.custom: conceptual
ms.date: 09/24/2018
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
ms.openlocfilehash: d7b5bc88966f7edbb7179c36398b1dd95afb971f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814348"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>Przewodnik: Kompilowanie natywnego programu C++ w wierszu polecenia

Visual C++ dołącza kompilatora wiersza polecenia języka C++, który służy do tworzenia wszystkiego, od aplikacji konsolowych podstawowe dla aplikacji uniwersalnych platformy Windows, aplikacje komputerowe, sterowniki urządzeń i składniki .NET.

W tym instruktażu utworzysz podstawową "Hello, World"-stylu program w języku C++ przy użyciu tekstu w edytorze, a następnie skompilować go w wierszu polecenia. Jeśli chcesz wypróbować jej możliwości programu Visual Studio IDE, a nie przy użyciu wiersza polecenia, zobacz [instruktażu: Praca z projektami i rozwiązaniami (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) lub [używanie środowiska IDE programu Visual Studio do tworzenia aplikacji pulpitu C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

W tym przewodniku można użyć programu Visual C++, zamiast wpisywać ten, który jest wyświetlany, lub można użyć przykładowego kodu języka Visual C++ z innego artykułu pomocy.

## <a name="prerequisites"></a>Wymagania wstępne

Do przeprowadzenia tego instruktażu, należy zainstalować program Visual Studio i opcjonalną **programowanie aplikacji klasycznych w języku C++** obciążenia lub wiersza polecenia narzędzia Build Tools for Visual Studio.

Visual Studio to zaawansowane zintegrowane środowisko programistyczne (IDE) obsługującego edytora z w pełni funkcjonalne, menedżerów zasobów, debugery i kompilatorów dla wielu języków i platform. Aby uzyskać informacje na temat, aby pobrać i zainstalować program Visual Studio, w tym bezpłatnej wersji programu Visual Studio Community oraz zapewnia obsługę dla rozwoju języka C/C++, zobacz [Instalowanie obsługi języka C++ w programie Visual Studio](vscpp-step-0-installation.md).

Narzędzia Build Tools for Visual Studio instaluje tylko kompilatorów wiersza polecenia, narzędzi i bibliotek, których potrzebujesz do tworzenia programów C i C++. Jest doskonała do laboratoriów kompilacji lub klasą wykonuje i instaluje względnie szybko. Aby zainstalować tylko narzędzia wiersza polecenia, Pobierz [Build Tools for Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=875721).

Przed dokonaniem kompilacji program C lub C++ w wierszu polecenia, należy sprawdzić, czy narzędzia są zainstalowane i czy użytkownik może uzyskiwać do nich dostęp z poziomu wiersza polecenia. Visual C++ ma złożone wymagania dotyczące środowiska wiersza polecenia można znaleźć narzędzia, nagłówki i biblioteki, które są używane. **Nie można użyć Visual C++ w oknie wiersza polecenia zwykły** bez wykonania tej czynności kilka operacji przygotowania. Na szczęście Visual C++ instaluje skróty dla Ciebie uruchomić wiersz polecenia dla deweloperów, zawierającej środowisko dla kompilacji z wiersza polecenia. Niestety nazw skróty wiersza polecenia dla deweloperów i gdzie są przechowywane różnią się w prawie każdym wersji programu Visual C++ i w innych wersjach systemu Windows. Pierwsze zadanie przewodnik znajduje się właściwy do użycia.

> [!NOTE]
> Skrót do wiersza polecenia dla deweloperów automatycznie ustawia prawidłowe ścieżki dla kompilatora i narzędzi oraz wszelkie wymagane nagłówki i biblioteki. Jeśli używasz zwykły należy ustawić w tych wartości środowiskowe **polecenia** okna. Aby uzyskać więcej informacji, zobacz [Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji wiersza polecenia](setting-the-path-and-environment-variables-for-command-line-builds.md). Zaleca się, że używasz skrót do wiersza polecenia dla deweloperów, zamiast tworzyć własne.

### <a name="open-a-developer-command-prompt"></a>Otwórz wiersz polecenia dla deweloperów

1. Po zainstalowaniu programu Visual Studio 2017 w systemie Windows 10, otwórz Start menu i wybierz polecenie **wszystkie aplikacje**. Przewiń w dół i Otwórz **programu Visual Studio 2017** folder (a nie aplikacji programu Visual Studio 2017). Wybierz **wiersz polecenia programisty dla programu VS 2017** aby otworzyć okno wiersza polecenia.

   Jeśli zainstalowano program Microsoft Visual C++ Build Tools 2015 w systemie Windows 10, otwórz **Start** menu i wybrać **wszystkie aplikacje**. Przewiń w dół i Otwórz **Visual C++ Build Tools** folderu. Wybierz **natywnych wiersz polecenia narzędzi Visual C++ 2015 x86** aby otworzyć okno wiersza polecenia.

   Jeśli używasz innej wersji programu Visual Studio lub działają innej wersji systemu Windows, Szukaj w Start menu lub uruchomić stronę folderu Narzędzia programu Visual Studio, który zawiera skrót do wiersza polecenia dla deweloperów. Funkcja wyszukiwania Windows umożliwia również wyszukiwanie "wiersz polecenia dla deweloperów" i wybierz jedną, która jest zgodna z zainstalowaną wersją programu Visual Studio. Użyj skrótu, aby otworzyć okno wiersza polecenia.

1. Następnie sprawdź, czy wiersz polecenia dla deweloperów Visual C++ są prawidłowo skonfigurowane. W oknie wiersza polecenia wprowadź `cl` i sprawdź, czy dane wyjściowe wyglądają następująco:

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   Może to być różnice w bieżącym katalogu lub numerów wersji, w zależności od wersji programu Visual C++ i zainstalowane jakiekolwiek aktualizacje. Jeśli powyższe dane wyjściowe będą podobne do zostanie wyświetlony, możesz przystąpić do tworzenia programów C lub C++ w wierszu polecenia.

   > [!NOTE]
   > Jeśli wystąpi błąd, takie jak "" cl"nie jest rozpoznawana jako polecenie wewnętrzne lub zewnętrzne, program wykonywalny lub plik wsadowy" Błąd C1034 lub błąd LNK1104 po uruchomieniu **cl** polecenia, a następnie albo nie używasz wiersz polecenia dla deweloperów lub coś jest nie tak z instalacji programu Visual C++. Należy rozwiązać ten problem, zanim będzie można kontynuować.

   Jeśli nie możesz znaleźć Deweloper skrót do wiersza polecenia lub jeśli zostanie wyświetlony komunikat o błędzie po wprowadzeniu `cl`, a następnie instalację programu Visual C++ może wystąpić problem. Spróbuj ponownie zainstalować składnik Visual C++ w programie Visual Studio, lub ponownie zainstaluj program Microsoft Visual C++ Build Tools. Nie przejdź do następnej sekcji, dopóki ta funkcja działa. Aby uzyskać więcej informacji na temat instalowania i rozwiązywanie problemów z Visual C++, zobacz [Zainstaluj program Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > W zależności od wersji na komputerze oraz konfiguracji zabezpieczeń systemu Windows, może być konieczne, kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów dla skrót do wiersza polecenia dla deweloperów, a następnie wybierz **Uruchom jako administrator** do pomyślnie skompilować i uruchomić program, który utworzonych za pomocą tego przewodnika.

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Utwórz plik źródłowy języka Visual C++ i skompilować go w wierszu polecenia

1. W oknie wiersza polecenia dla deweloperów, wprowadź `md c:\hello` Utwórz katalog, a następnie wprowadź `cd c:\hello` zmiany do tego katalogu. Jest to katalog, gdzie plik źródłowy i skompilowany program są tworzone w.

1. Wprowadź `notepad hello.cpp` w oknie wiersza polecenia.

   Wybierz **tak** kiedy pojawi się monit o utworzenie pliku Notatnika. W tym kroku zostanie otwarte puste okno Notatnik, możesz wprowadzić swój kod w pliku o nazwie hello.cpp.

1. W programie Notatnik wprowadź następujące wiersze kodu:

   ```cpp
   #include <iostream>
   using namespace std;
   void main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   Ten kod jest prosty program, który będzie zapisać jeden wiersz tekstu na ekranie, a następnie zamknij. Aby zminimalizować błędy, skopiuj ten kod i wklej go do Notatnika.

1. Zapisz swoją pracę! W programie Notatnik w **pliku** menu, wybierz **Zapisz**.

   Gratulacje, utworzono plik źródłowy języka Visual C++, hello.cpp, który jest gotowy do skompilowania.

1. Przejdź z powrotem do okna wiersza polecenia dla deweloperów. Wprowadź `dir` w wierszu polecenia, aby wyświetlić listę zawartości katalogu c:\hello. Powinny zostać wyświetlone hello.cpp plików źródłowych na liście katalogu, który wygląda coś w rodzaju:

   ```Output
   c:\hello>dir
    Volume in drive C has no label.
    Volume Serial Number is CC62-6545

    Directory of c:\hello

   05/24/2016  05:36 PM    <DIR>          .
   05/24/2016  05:36 PM    <DIR>          ..
   05/24/2016  05:37 PM               115 hello.cpp
                  1 File(s)            115 bytes
                  2 Dir(s)  571,343,446,016 bytes free

   ```

   Daty i inne szczegóły różnią się na tym komputerze. Jeśli nie widzisz pliku kodu źródłowego, hello.cpp, upewnij się, że zmiany zostały wprowadzone do katalogu c:\hello, w którym został utworzony i w programie Notatnik, upewnij się, zapisać pliku źródłowego w tym katalogu. Upewnij się również zapisać kodu źródłowego z rozszerzeniem nazwy pliku .cpp, nie rozszerzenia .txt.

1. W wierszu polecenia dla deweloperów, wprowadź `cl /EHsc hello.cpp` skompilować program.

   Cl.exe — kompilator wygeneruje pliku .obj, który zawiera kod skompilowany, a następnie uruchamia konsolidator, aby utworzyć program wykonywalny o nazwie hello.exe. Nazwa ta pojawia się w wierszach danych wyjściowych wyświetlanych przez kompilator. Dane wyjściowe kompilatora powinien wyglądać mniej więcej tak:

   ```Output
   c:\hello>cl /EHsc hello.cpp
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   hello.cpp
   Microsoft (R) Incremental Linker Version 14.10.25017.0
   Copyright (C) Microsoft Corporation.  All rights reserved.

   /out:hello.exe
   hello.obj
   ```

   > [!NOTE]
   > Jeśli wystąpi błąd, takie jak "" cl"nie jest rozpoznawana jako polecenie wewnętrzne lub zewnętrzne, program wykonywalny lub plik wsadowy" Błąd C1034 lub błąd LNK1104, wiersza polecenia dla deweloperów nie jest skonfigurowany prawidłowo. Aby uzyskać informacje na temat rozwiązać ten problem, przejdź wstecz do **Otwórz wiersz polecenia dla deweloperów** sekcji.

   > [!NOTE]
   > Jeśli wystąpi inny kompilator lub konsolidator błędu lub ostrzeżenia, przejrzyj kod źródłowy, aby poprawić błędy, a następnie zapisz go i ponownie uruchomić kompilator. Aby uzyskać informacje o błędach Użyj pola wyszukiwania na tej stronie w witrynie MSDN do wyszukania numer błędu.

1. Aby uruchomić hello.exe program w wierszu polecenia, wprowadź `hello`.

   Ten program wyświetla ten tekst i kończy działanie:

   ```Output
   Hello, world, from Visual C++!
   ```

   Gratulacje, udało Ci skompilowane i uruchomić program w języku C++ za pomocą narzędzia wiersza polecenia.

## <a name="next-steps"></a>Następne kroki

W tym przykładzie "Hello, World" to około tak proste, jak pobrać program w języku C++. Programy rzeczywistych mają pliki nagłówkowe i więcej plików źródłowych, link w bibliotekach i wykonywania użytecznej pracy.

Kroki opisane w tym przewodniku służy do tworzenia własnego kodu C++, zamiast wpisywać pokazano przykładowy kod. Możesz także tworzyć wiele C++ przykładowych programów napisanych w których odnaleźć w innym miejscu. Można umieścić kod źródłowy i tworzenie aplikacji w dowolnym zapisywalny katalogu. Domyślnie środowiska IDE programu Visual Studio tworzy projekty w folderze dokumenty w podfolderze projektów folder programu Visual Studio o nazwie dla używanej wersji programu Visual Studio.

Skompilować program, który zawiera pliki kodu źródłowego dodatkowe, wprowadź je wszystkie w wierszu polecenia, takich jak:

`cl /EHsc file1.cpp file2.cpp file3.cpp`

`/EHsc` Opcji wiersza polecenia instruuje kompilator, aby włączyć obsługę wyjątku C++. Aby uzyskać więcej informacji, zobacz [/EH (Model obsługi wyjątku)](reference/eh-exception-handling-model.md).

Podczas podawania dodatkowych plików źródłowych, kompilator używa pierwszego pliku wejściowego, aby utworzyć nazwę programu. W tym przypadku dane wyjściowe programu o nazwie file1.exe. Aby zmienić nazwę program1.exe, Dodaj [/out](reference/out-output-file-name.md) — opcja konsolidatora:

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

I aby automatycznie wykryć więcej błędów programowania, zaleca się skompilować przy użyciu [/W3](reference/compiler-option-warning-level.md) lub [/W4](reference/compiler-option-warning-level.md) ostrzeżenie opcję poziomu:

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Kompilator cl.exe, ma wiele więcej opcji się do kompilacji, optymalizowanie, Debuguj i Analizuj swój kod. Lista szybkich, wprowadź `cl /?` w wierszu polecenia dla deweloperów. Można również skompilować i połączyć oddzielnie i zastosować opcje konsolidatora w bardziej złożonych scenariuszy kompilacji. Aby uzyskać więcej informacji dotyczących kompilatora i opcje konsolidatora i jego użycia, zobacz [odwołanie kompilacji C/C++](reference/c-cpp-building-reference.md).

NMAKE i pliki reguł programu make lub MSBuild i pliki projektu można użyć do konfigurowania i tworzyć bardziej złożone projekty w wierszu polecenia. Aby uzyskać więcej informacji na temat korzystania z tych narzędzi, zobacz [odwołanie NMAKE](reference/nmake-reference.md) i [MSBuild](msbuild-visual-cpp.md).

W językach C i C++ są podobne, ale nie sam. Kompilator MSVC używa prostej reguły, aby określić język, który będzie używany podczas kompiluje kod. Domyślnie kompilator MSVC traktuje wszystkie pliki, które kończą się na .c, jako kod źródłowy języka C i wszystkich plików, które kończą się na .cpp, jako kod źródłowy języka C++. Aby wymusić na kompilatorze traktowanie wszystkich plików, co kod C++ nie są zależne rozszerzenie nazwy pliku, użyj [TP](reference/tc-tp-tc-tp-specify-source-file-type.md) — opcja kompilatora.

Kompilator MSVC zawiera C Runtime Library (CRT) zgodne ze standardem ISO C99, ale nie jest ściśle zgodna. W większości przypadków kod przenośny skompilować i uruchomić zgodnie z oczekiwaniami. Visual C++ nie obsługuje pewnych zmian CRT w ISO C11. Niektóre funkcje biblioteki i nazwy funkcji POSIX są przestarzałe za pomocą kompilatora MSVC. Funkcje są obsługiwane, ale preferowane nazwy zostały zmienione. Aby uzyskać więcej informacji, zobacz [funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md) i [ostrzeżenie kompilatora (poziom 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty i systemów kompilacji](projects-and-build-systems-cpp.md)<br/>
[MSVC Compiler Options](reference/compiler-options.md)
