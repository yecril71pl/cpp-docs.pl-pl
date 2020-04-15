---
title: 'Przewodnik: kompilowanie programu w języku C w wierszu polecenia'
ms.custom: conceptual
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
ms.openlocfilehash: d807fa75b32b515c2222fec9ea9d070266303e33
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335263"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>Przewodnik: kompilowanie programu w języku C w wierszu polecenia

Visual C++ zawiera kompilator C, którego można używać do tworzenia wszystkiego, od podstawowych programów konsoli po pełne aplikacje pulpitu systemu Windows, aplikacje mobilne i inne.

W tym instruktażu pokazano, jak utworzyć podstawowy program C w stylu "Hello, World" przy użyciu edytora tekstu, a następnie skompilować go w wierszu polecenia. Jeśli wolisz pracować w języku C++ w wierszu polecenia, zobacz [Przewodnik: Kompilowanie natywnego programu C++ w wierszu polecenia](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md). Jeśli chcesz wypróbować IDE programu Visual Studio zamiast używać wiersza polecenia, zobacz [Przewodnik: Praca z projektami i rozwiązaniami (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) lub Korzystanie z [środowiska IDE programu Visual Studio dla tworzenia pulpitu w języku C++.](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten instruktaż, musisz zainstalować program Visual Studio i opcjonalne składniki programu Visual C++ lub narzędzia kompilacji dla programu Visual Studio.

Visual Studio to zaawansowane zintegrowane środowisko programistyczne, które obsługuje w pełni funkcjonalny edytor, menedżerów zasobów, debugerów i kompilatorów dla wielu języków i platform. Aby uzyskać informacje na temat tych funkcji oraz sposobu pobierania i instalowania programu Visual Studio, w tym bezpłatnej wersji visual studio community, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio).

Narzędzia kompilacji dla programu Visual Studio w programie Visual Studio instaluje tylko zestaw narzędzi wiersza polecenia, kompilatory, narzędzia i biblioteki potrzebne do tworzenia programów W języku C i C++. Idealnie nadaje się do budowy laboratoriów lub ćwiczeń w klasie i instaluje się stosunkowo szybko. Aby zainstalować tylko zestaw narzędzi wiersza polecenia, pobierz narzędzia kompilacji dla programu Visual Studio ze strony [pobierania programu Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) i uruchom instalator. W instalatorze programu Visual Studio wybierz obciążenie **narzędzi kompilacji języka C++** i wybierz pozycję **Zainstaluj**.

Przed utworzeniem programu C lub C++ w wierszu polecenia należy sprawdzić, czy narzędzia są zainstalowane i czy można uzyskać do nich dostęp z wiersza polecenia. Visual C++ ma złożone wymagania dla środowiska wiersza polecenia, aby znaleźć narzędzia, nagłówki i biblioteki, których używa. **Nie można używać języka Visual C++ w oknie wiersza polecenia zwykły** bez przygotowania. Potrzebne jest okno *wiersza polecenia dewelopera,* które jest zwykłym oknem wiersza polecenia, które ma ustawione wszystkie wymagane zmienne środowiskowe. Na szczęście visual C++ instaluje skróty, aby uruchomić monity poleceń dewelopera, które mają środowisko skonfigurowane dla kompilacji wiersza polecenia. Niestety nazwy skrótów wiersza polecenia dewelopera i miejsca ich lokalizacji różnią się w prawie każdej wersji programu Visual C++ i w różnych wersjach systemu Windows. Pierwszym zadaniem instruktażowym jest znalezienie odpowiedniego skrótu do użycia.

> [!NOTE]
> Skrót wiersza polecenia dewelopera automatycznie ustawia poprawne ścieżki dla kompilatora i narzędzi oraz dla wszystkich wymaganych nagłówków i bibliotek. Niektóre z tych wartości są różne dla każdej konfiguracji kompilacji. Jeśli nie używasz jednego ze skrótów, należy ustawić te wartości środowiska samodzielnie. Aby uzyskać więcej informacji, zobacz [Ustawianie zmiennych ścieżki i środowiska dla kompilacji wiersza polecenia](setting-the-path-and-environment-variables-for-command-line-builds.md). Ponieważ środowisko kompilacji jest złożone, zdecydowanie zaleca się użycie skrótu wiersza polecenia dewelopera zamiast tworzenia własnych.

Te instrukcje różnią się w zależności od używanej wersji programu Visual Studio. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj formantu selektor **wersji.** Znajduje się w górnej części spisu treści na tej stronie.

::: moniker range="vs-2019"

## <a name="open-a-developer-command-prompt-in-visual-studio-2019"></a>Otwieranie wiersza polecenia dewelopera w programie Visual Studio 2019

Jeśli program Visual Studio 2019 został zainstalowany w systemie Windows 10, otwórz menu Start, a następnie przewiń w dół i otwórz folder **programu Visual Studio 2019** (a nie aplikację programu Visual Studio 2019). Wybierz **pozycję Developer Command Prompt for VS 2019** to open the command prompt window.Choose Developer Command Prompt for VS 2019 to open the command prompt window.

Jeśli używasz innej wersji systemu Windows, poszukaj w menu Start lub na stronie Start folderu narzędzi programu Visual Studio zawierającego skrót wiersza polecenia dewelopera. Można również użyć funkcji wyszukiwania systemu Windows, aby wyszukać "wiersz polecenia dewelopera" i wybrać taki, który pasuje do zainstalowanej wersji programu Visual Studio. Użyj skrótu, aby otworzyć okno wiersza polecenia.

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-developer-command-prompt-in-visual-studio-2017"></a>Otwieranie wiersza polecenia dewelopera w programie Visual Studio 2017

Jeśli program Visual Studio 2017 został zainstalowany w systemie Windows 10, otwórz menu Start, a następnie przewiń w dół i otwórz folder **programu Visual Studio 2017** (a nie aplikację programu Visual Studio 2017). Wybierz **pozycję Developer Command Prompt for VS 2017** to open the command prompt window .Choose Developer Command Prompt for VS 2017 to open the command prompt window.

Jeśli korzystasz z innej wersji systemu Windows, poszukaj w menu Start lub na stronie Start folderu narzędzi programu Visual Studio zawierającego skrót wiersza polecenia dewelopera. Można również użyć funkcji wyszukiwania systemu Windows, aby wyszukać "wiersz polecenia dewelopera" i wybrać taki, który pasuje do zainstalowanej wersji programu Visual Studio. Użyj skrótu, aby otworzyć okno wiersza polecenia.

::: moniker-end

::: moniker range="vs-2015"

## <a name="open-a-developer-command-prompt-in-visual-studio-2015"></a>Otwieranie wiersza polecenia dewelopera w programie Visual Studio 2015

Jeśli zainstalowano narzędzie Microsoft Visual C++ Build Tools 2015 w systemie Windows 10, otwórz menu **Start,** a następnie przewiń w dół i otwórz folder **Narzędzia kompilacji visual c++.** Wybierz pozycję **Visual C++ 2015 x86 Native Tools Command Prompt,** aby otworzyć okno wiersza polecenia.

Jeśli korzystasz z innej wersji systemu Windows, poszukaj w menu Start lub na stronie Start folderu narzędzi programu Visual Studio zawierającego skrót wiersza polecenia dewelopera. Można również użyć funkcji wyszukiwania systemu Windows, aby wyszukać "wiersz polecenia dewelopera" i wybrać taki, który pasuje do zainstalowanej wersji programu Visual Studio. Użyj skrótu, aby otworzyć okno wiersza polecenia.

::: moniker-end

Następnie sprawdź, czy wiersz polecenia dewelopera języka Visual C++ jest poprawnie skonfigurowany. W oknie wiersza `cl` polecenia wprowadź i sprawdź, czy dane wyjściowe wyglądają mniej więcej tak:

```Output
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

usage: cl [ option... ] filename... [ /link linkoption... ]
```

Mogą występować różnice w bieżących numerach katalogu lub wersji, w zależności od wersji programu Visual C++ i zainstalowanych aktualizacji. Jeśli powyższe dane wyjściowe są podobne do tego, co widzisz, możesz przystąpić do tworzenia programów C lub C++ w wierszu polecenia.

> [!NOTE]
> Jeśli pojawia się błąd, taki jak "cl' nie jest rozpoznawany jako polecenie wewnętrzne lub zewnętrzne, działający program lub plik wsadowy", błąd C1034 lub błąd LNK1104 po uruchomieniu polecenia **cl,** to albo nie używasz wiersza polecenia dewelopera, albo coś jest nie tak z instalacją visual C++. Musisz rozwiązać ten problem, zanim będzie można kontynuować.

Jeśli nie możesz znaleźć skrótu wiersza polecenia dewelopera lub po `cl`wprowadzeniu zostanie wyświetlony komunikat o błędzie , instalacja programu Visual C++ może mieć problem. Jeśli używasz programu Visual Studio 2017 lub nowszego, spróbuj ponownie zainstalować **programowanie pulpitu z** obciążeniem języka C++ w instalatorze programu Visual Studio. Aby uzyskać szczegółowe informacje, zobacz [Instalowanie pomocy technicznej języka C++ w programie Visual Studio](vscpp-step-0-installation.md). Lub zainstaluj ponownie narzędzia kompilacji ze strony [pobierania programu Visual Studio.](https://visualstudio.microsoft.com/downloads/) Nie idź do następnej sekcji, dopóki to się nie uchodzi. Aby uzyskać więcej informacji na temat instalowania programu Visual Studio i rozwiązywania problemów z programem Visual Studio, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio).

> [!NOTE]
> W zależności od wersji systemu Windows na komputerze i konfiguracji zabezpieczeń systemu może być trzeba kliknąć prawym przyciskiem myszy, aby otworzyć menu skrótów dla skrótu wiersza polecenia dewelopera, a następnie wybrać polecenie **Uruchom jako administrator,** aby pomyślnie skompilować i uruchomić program, który zostanie utworzony, wykonując ten przewodnik.

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>Tworzenie pliku źródłowego języka C i kompilowanie go w wierszu polecenia

1. W oknie wiersza polecenia `cd c:\` dewelopera wprowadź, aby zmienić bieżący katalog roboczy na katalog główny dysku C:. Następnie wprowadź, `md c:\simple` aby utworzyć katalog, `cd c:\simple` a następnie wprowadź, aby zmienić ten katalog. Ten katalog będzie przechowywać plik źródłowy i skompilowany program.

1. Wprowadź `notepad simple.c` w wierszu polecenia dewelopera. W oknie dialogowym alertu Notatnika, które się pojawia, wybierz pozycję **Tak,** aby utworzyć nowy plik simple.c w katalogu roboczym.

1. W Notatniku wprowadź następujące wiersze kodu:

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. Na pasku menu Notatnik wybierz pozycję**Zapisz** **plik,** > aby zapisać simple.c w katalogu roboczym.

1. Przełącz się z powrotem do okna wiersza polecenia dewelopera. Wprowadź `dir` w wierszu polecenia, aby wyświetlić listę zawartości katalogu c:\simple. Powinieneś zobaczyć plik źródłowy simple.c na liście katalogów, który wygląda mniej więcej tak:

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

   Daty i inne szczegóły będą się różnić na komputerze. Jeśli nie widzisz pliku kodu źródłowego simple.c, upewnij się, że został zmieniony na utworzony katalog c:\simple, a w Notatniku upewnij się, że plik źródłowy został zapisany w tym katalogu. Upewnij się również, że kod źródłowy został zapisany z rozszerzeniem nazwy pliku .c, a nie rozszerzeniem txt.

1. Aby skompilować `cl simple.c` program, wprowadź w wierszu polecenia dewelopera.

   Nazwę programu wykonywalnego simple.exe można zobaczyć w wierszach informacji wyjściowych wyświetlanych przez kompilator:

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
   > Jeśli pojawi się błąd, taki jak "'cl' nie jest rozpoznawany jako polecenie wewnętrzne lub zewnętrzne, działający program lub plik wsadowy", błąd C1034 lub błąd LNK1104, wiersz polecenia dewelopera nie jest poprawnie skonfigurowany. Aby uzyskać informacje na temat rozwiązywania tego problemu, wróć do sekcji **Otwieranie wiersza polecenia dewelopera.**

   > [!NOTE]
   > Jeśli zostanie wyświetlony błąd lub ostrzeżenie innego kompilatora lub konsolidatora, przejrzyj kod źródłowy, aby poprawić wszelkie błędy, a następnie zapisz go i uruchom kompilator ponownie. Aby uzyskać informacje o określonych błędach, użyj pola wyszukiwania u góry tej strony, aby wyszukać numer błędu.

1. Aby uruchomić program, `simple` wprowadź w wierszu polecenia.

   Program wyświetla ten tekst, a następnie kończy pracę:

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   Gratulacje, skompilowano i uruchomisz program C za pomocą wiersza polecenia.

## <a name="next-steps"></a>Następne kroki

Ten przykład "Hello, World" jest tak prosty, jak program C można uzyskać. Programy ze świata rzeczywistego mają pliki nagłówkowe i więcej plików źródłowych, łącza w bibliotekach i wykonują użyteczną pracę.

Można użyć kroków w tym instruktażu do tworzenia własnego kodu C zamiast wpisywania przykładowego kodu pokazano. Można również utworzyć wiele przykładowych programów kodu C, które można znaleźć w innym miejscu. Aby skompilować program, który ma dodatkowe pliki kodu źródłowego, wprowadź je wszystkie w wierszu polecenia, takie jak:

`cl file1.c file2.c file3.c`

Kompilator wyprowadza program o nazwie file1.exe. Aby zmienić nazwę na program1.exe, dodaj opcję [/out](reference/out-output-file-name.md) konsolidatora:

`cl file1.c file2.c file3.c /link /out:program1.exe`

Aby automatycznie wyłapać więcej błędów programowych, zalecamy skompilowanie przy użyciu opcji poziomu ostrzeżenia [/W3](reference/compiler-option-warning-level.md) lub [/W4:](reference/compiler-option-warning-level.md)

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

Kompilator cl.exe ma wiele innych opcji, które można zastosować do tworzenia, optymalizacji, debugowania i analizowania kodu. Aby uzyskać szybką `cl /?` listę, wprowadź w wierszu polecenia dewelopera. Można również skompilować i połączyć oddzielnie i zastosować opcje konsolidatora w bardziej złożonych scenariuszach kompilacji. Aby uzyskać więcej informacji na temat opcji kompilatora i konsolidatora oraz użycia, zobacz [Odwołanie do budynku C/C++.](reference/c-cpp-building-reference.md)

Za pomocą nmake i makefiles lub MSBuild i plików projektu do konfigurowania i tworzenia bardziej złożonych projektów w wierszu polecenia. Aby uzyskać więcej informacji na temat korzystania z tych narzędzi, zobacz [NMAKE Reference](reference/nmake-reference.md) i [MSBuild](msbuild-visual-cpp.md).

Języki C i C++ są podobne, ale nie takie same. Kompilator Microsoft C/C++ (MSVC) używa prostej reguły, aby określić, który język ma być używany podczas kompilowania kodu. Domyślnie kompilator MSVC traktuje wszystkie pliki, które kończą się w .c jako kod źródłowy C, a wszystkie pliki, które kończą się w .cpp jako kod źródłowy języka C++. Aby wymusić, aby kompilator traktował wszystkie pliki jako C nie zależne od rozszerzenia nazwy pliku, użyj opcji kompilatora [/Tc.](reference/tc-tp-tc-tp-specify-source-file-type.md)

MSVC jest zgodny ze standardem ISO C99, ale nie jest ściśle zgodny. W większości przypadków przenośny kod C skompiluje się i uruchomi zgodnie z oczekiwaniami. Visual C++ nie obsługuje większość zmian w ISO C11. Niektóre funkcje biblioteki i nazwy funkcji POSIX są przestarzałe przez MSVC. Funkcje są obsługiwane, ale preferowane nazwy uległy zmianie. Aby uzyskać więcej informacji, zobacz [Funkcje zabezpieczeń w crt](../c-runtime-library/security-features-in-the-crt.md) i [ostrzeżenie kompilatora (poziom 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Zobacz też

[Przewodnik: tworzenie standardowego programu C++ (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[C Referencje językowe](../c-language/c-language-reference.md)<br/>
[Projekty i systemy kompilacji](projects-and-build-systems-cpp.md)<br/>
[Zgodność](../c-runtime-library/compatibility.md)
