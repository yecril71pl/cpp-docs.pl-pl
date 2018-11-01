---
title: 'Przewodnik: Kompilowanie programu C w wierszu polecenia'
ms.custom: conceptual
ms.date: 09/24/2018
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
ms.openlocfilehash: 756e0fa820806142f05ba45a52735692298f80d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656875"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>Przewodnik: Kompilowanie programu C w wierszu polecenia

Visual C++ obejmuje kompilator C, który służy do tworzenia wszystkiego, od programów podstawowa Konsola pełnej aplikacji komputerowych Windows, aplikacje mobilne i więcej.

W tym instruktażu przedstawiono sposób tworzenia podstawowego, "Hello, World"-stylu programu C przy użyciu typu text editor i skompilować go w wierszu polecenia. Jeśli wolisz przebiega w języku C++ w wierszu polecenia, zobacz [wskazówki: kompilowanie natywnego programu C++ w wierszu polecenia](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md). Jeśli chcesz wypróbować jej możliwości programu Visual Studio IDE, a nie przy użyciu wiersza polecenia, zobacz [wskazówki: Praca z projektami i rozwiązaniami (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) lub [przy użyciu programu Visual Studio IDE dla programowanie aplikacji klasycznych w języku C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="prerequisites"></a>Wymagania wstępne

Do przeprowadzenia tego instruktażu, należy zainstalowano program Visual Studio i opcjonalne składniki Visual C++ lub narzędzia Build Tools dla programu Visual Studio.

Program Visual Studio jest zintegrowanego środowiska projektowego obsługującego edytora z w pełni funkcjonalne, menedżerów zasobów, debugery i kompilatorów dla wielu języków i platform. Aby uzyskać informacje na temat tych funkcji i jak pobrać i zainstalować program Visual Studio, w tym bezpłatnej wersji programu Visual Studio Community, zobacz [Zainstaluj program Visual Studio](/visualstudio/install/install-visual-studio).

Narzędzia Build Tools dla programu Visual Studio w wersji programu Visual Studio instaluje tylko narzędzi wiersza polecenia, kompilatory, narzędzia i biblioteki wymagane do tworzenia programów C i C++. Jest doskonała do laboratoriów kompilacji lub klasą wykonuje i instaluje względnie szybko. Aby zainstalować tylko narzędzia wiersza polecenia, Pobierz [Build Tools for Visual Studio](https://go.microsoft.com/fwlink/p/?linkid=875721) i uruchom Instalatora.

Przed dokonaniem kompilacji program C lub C++ w wierszu polecenia, należy sprawdzić, czy narzędzia są zainstalowane i czy użytkownik może uzyskiwać do nich dostęp z poziomu wiersza polecenia. Visual C++ ma złożone wymagania dotyczące środowiska wiersza polecenia można znaleźć narzędzia, nagłówki i biblioteki, które są używane. **Nie można użyć Visual C++ w oknie wiersza polecenia zwykły** bez pewnych przygotowań. Potrzebujesz *wiersz polecenia dla deweloperów* okno jest oknem regularne wiersza polecenia, które zawiera wszystkie zmienne środowiskowe wymagane Ustaw. Na szczęście Visual C++ instaluje skróty dla Ciebie uruchomić wiersz polecenia dla deweloperów, które środowisko dla kompilacji z wiersza polecenia. Niestety nazw skróty wiersza polecenia dla deweloperów i gdzie są przechowywane różnią się w prawie każdym wersji programu Visual C++ i w innych wersjach systemu Windows. Jest pierwsze zadanie wskazówki można znaleźć odpowiednie skrótu do użycia.

> [!NOTE]
> Skrót do wiersza polecenia dla deweloperów automatycznie ustawia prawidłowe ścieżki dla kompilatora i narzędzi oraz wszelkie wymagane nagłówki i biblioteki. Niektóre z tych wartości różnią się dla każdej konfiguracji kompilacji. Należy ustawić te wartości środowiskowe samodzielnie, jeśli nie używasz skrótów klawiaturowych. Aby uzyskać więcej informacji, zobacz [Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji wiersza polecenia](../build/setting-the-path-and-environment-variables-for-command-line-builds.md). Ponieważ środowisko kompilacji jest złożone, zdecydowanie zalecamy używasz skrót do wiersza polecenia dla deweloperów, zamiast tworzyć własne.

## <a name="open-a-developer-command-prompt"></a>Otwórz wiersz polecenia dla deweloperów

1. Po zainstalowaniu programu Visual Studio 2017 w systemie Windows 10, otwórz Start menu, a następnie przewiń w dół i Otwórz **programu Visual Studio 2017** folder (a nie aplikacji programu Visual Studio 2017). Wybierz **wiersz polecenia programisty dla programu VS 2017** aby otworzyć okno wiersza polecenia.

   Jeśli zainstalowano program Microsoft Visual C++ Build Tools 2015 w systemie Windows 10, otwórz **Start** menu, a następnie przewiń w dół i Otwórz **Visual C++ Build Tools** folderu. Wybierz **natywnych wiersz polecenia narzędzi Visual C++ 2015 x86** aby otworzyć okno wiersza polecenia.

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

   Jeśli nie możesz znaleźć Deweloper skrót do wiersza polecenia lub jeśli zostanie wyświetlony komunikat o błędzie po wprowadzeniu `cl`, a następnie instalację programu Visual C++ może wystąpić problem. Jeśli używasz programu Visual Studio 2017, spróbuj zainstalować ponownie **programowanie aplikacji klasycznych w języku C++** obciążenie w Instalatorze programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Instalowanie obsługi języka C++ w programie Visual Studio](../build/vscpp-step-0-installation.md). Czy ponownie zainstalować [Build Tools for Visual Studio](https://go.microsoft.com/fwlink/p/?linkid=875721). Nie przejdź do następnej sekcji, dopóki ta funkcja działa. Aby uzyskać więcej informacji na temat instalowania i rozwiązywanie problemów z programu Visual Studio, zobacz [Zainstaluj program Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > W zależności od wersji na komputerze oraz konfiguracji zabezpieczeń systemu Windows, może być konieczne, kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów dla skrót do wiersza polecenia dla deweloperów, a następnie wybierz **Uruchom jako Administrator** do pomyślnie skompilować i uruchomić program, który utworzonych za pomocą tego przewodnika.

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>Utwórz plik źródłowy C i skompilować go w wierszu polecenia

1. W oknie wiersza polecenia dla deweloperów, wprowadź `cd c:\` Aby zmienić bieżący katalog roboczy w folderze głównym dysku C:. Następnie wprowadź `md c:\simple` Utwórz katalog, a następnie wprowadź `cd c:\simple` zmiany do tego katalogu. Ten katalog będzie przechowywać pliku źródłowego i skompilowanego programu.

1. Wprowadź `notepad simple.c` w wierszu polecenia dla deweloperów. W programie Notatnik alertu wyświetlonego oknie dialogowym wybierz **tak** do utworzenia nowego pliku simple.c w katalogu roboczym.

1. W programie Notatnik wprowadź następujące wiersze kodu:

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. Na pasku menu Notatnika wybierz **pliku** > **Zapisz** można zapisać simple.c w katalogu roboczym.

1. Przejdź z powrotem do okna wiersza polecenia dla deweloperów. Wprowadź `dir` w wierszu polecenia, aby wyświetlić listę zawartości katalogu c:\simple. Powinny zostać wyświetlone simple.c plików źródłowych na liście katalogu, który wygląda coś w rodzaju:

    ```Output
    C:\simple>dir
     Volume in drive C has no label.
     Volume Serial Number is CC62-6545

     Directory of C:\simple

    10/02/2017  03:46 PM    <DIR>          .
    10/02/2017  03:46 PM    <DIR>          ..
    10/02/2017  03:36 PM               143 simple.c
                   1 File(s)            143 bytes
                   2 Dir(s)  514,900,566,016 bytes free

    ```

   Daty i inne szczegóły różnią się na tym komputerze. Jeśli nie widzisz pliku kodu źródłowego, simple.c, upewnij się, że zmiany zostały wprowadzone do katalogu c:\simple, w którym został utworzony i w programie Notatnik, upewnij się, zapisać pliku źródłowego w tym katalogu. Upewnij się również zapisać kodu źródłowego z rozszerzeniem nazwy pliku .c, nie rozszerzenia .txt.

1. Aby skompilować program, należy wprowadzić `cl simple.c` w wierszu polecenia dla deweloperów.

   Można wyświetlić nazwę programu wykonywalnego simple.exe w wierszach danych wyjściowych wyświetlanych przez kompilator:

    ```Output
    c:\simple>cl simple.c
    Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
    Copyright (C) Microsoft Corporation.  All rights reserved.

    simple.c
    Microsoft (R) Incremental Linker Version 14.10.25017.0
    Copyright (C) Microsoft Corporation.  All rights reserved.

    /out:simple.exe
    simple.obj
    ```

   > [!NOTE]
   > Jeśli wystąpi błąd, takie jak "" cl"nie jest rozpoznawana jako polecenie wewnętrzne lub zewnętrzne, program wykonywalny lub plik wsadowy" Błąd C1034 lub błąd LNK1104, wiersza polecenia dla deweloperów nie jest skonfigurowany prawidłowo. Aby uzyskać informacje na temat rozwiązać ten problem, przejdź wstecz do **Otwórz wiersz polecenia dla deweloperów** sekcji.

   > [!NOTE]
   > Jeśli wystąpi inny kompilator lub konsolidator błędu lub ostrzeżenia, przejrzyj kod źródłowy, aby poprawić błędy, a następnie zapisz go i ponownie uruchomić kompilator. Aby uzyskać informacje o błędach Użyj pola wyszukiwania w górnej części tej strony do wyszukania numer błędu.

1. Aby uruchomić program, należy wprowadzić `simple` w wierszu polecenia.

   Program wyświetla tekst, a następnie kończy działanie:

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   Gratulacje, udało skompilowane i uruchomić C program przy użyciu wiersza polecenia.

## <a name="next-steps"></a>Następne kroki

W tym przykładzie "Hello, World" to około tak proste, jak pobrać C program. Programy rzeczywistych mają pliki nagłówkowe i więcej plików źródłowych, link w bibliotekach i wykonywania użytecznej pracy.

Kroki opisane w tym przewodniku służy do tworzenia własnego kodu języka C, zamiast wpisywać pokazano przykładowy kod. Możesz także tworzyć wiele C przykładowych programów napisanych w których odnaleźć w innym miejscu. Skompilować program, który zawiera pliki kodu źródłowego dodatkowe, wprowadź je wszystkie w wierszu polecenia, takich jak:

`cl file1.c file2.c file3.c`

Kompilator generuje program o nazwie file1.exe. Aby zmienić nazwę program1.exe, Dodaj [/out](../build/reference/out-output-file-name.md) — opcja konsolidatora:

`cl file1.c file2.c file3.c /link /out:program1.exe`

I aby automatycznie wykryć więcej błędów programowania, zaleca się skompilować przy użyciu [/W3](../build/reference/compiler-option-warning-level.md) lub [/W4](../build/reference/compiler-option-warning-level.md) ostrzeżenie opcję poziomu:

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

Kompilator cl.exe, ma wiele więcej opcji się do kompilacji, optymalizowanie, Debuguj i Analizuj swój kod. Lista szybkich, wprowadź `cl /?` w wierszu polecenia dla deweloperów. Można również skompilować i połączyć oddzielnie i zastosować opcje konsolidatora w bardziej złożonych scenariuszy kompilacji. Aby uzyskać więcej informacji dotyczących kompilatora i opcje konsolidatora i jego użycia, zobacz [odwołanie kompilacji C/C++](../build/reference/c-cpp-building-reference.md).

NMAKE i pliki reguł programu make lub MSBuild i pliki projektu można użyć do konfigurowania i tworzyć bardziej złożone projekty w wierszu polecenia. Aby uzyskać więcej informacji na temat korzystania z tych narzędzi, zobacz [odwołanie NMAKE](../build/nmake-reference.md) i [MSBuild](../build/msbuild-visual-cpp.md).

W językach C i C++ są podobne, ale nie sam. Kompilator języka Visual C++ używa prostej reguły, aby określić język, który będzie używany podczas kompiluje kod. Domyślnie kompilator języka Visual C++ traktuje wszystkie pliki, które kończą się na .c, jako kod źródłowy języka C i wszystkich plików, które kończą się na .cpp, jako kod źródłowy języka C++. Aby wymusić na kompilatorze traktowanie wszystkich plików jako C nie zależne od rozszerzenia nazwy pliku, należy użyć [TP](../build/reference/tc-tp-tc-tp-specify-source-file-type.md) — opcja kompilatora.

Kompilator Visual C++, C jest zgodne ze standardem ISO C99, ale nie jest ściśle zgodna. W większości przypadków przenośny kod C skompilować i uruchomić zgodnie z oczekiwaniami. Visual C++ nie obsługuje większość zmian w ISO C11. Niektóre funkcje biblioteki i nazwy funkcji POSIX są przestarzałe przez kompilator Visual C++. Funkcje są obsługiwane, ale preferowane nazwy zostały zmienione. Aby uzyskać więcej informacji, zobacz [funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md) i [ostrzeżenie kompilatora (poziom 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Zobacz także

[Przewodnik: tworzenie standardowego programu C++ (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[Dokumentacja języka C](../c-language/c-language-reference.md)<br/>
[Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)<br/>
[Zgodność](../c-runtime-library/compatibility.md)
