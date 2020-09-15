---
title: 'Przewodnik: Kompilowanie programu w języku C w wierszu polecenia'
description: Przewodnik przedstawiający sposób tworzenia prostego programu Hello world stylu C.
ms.custom: conceptual
ms.date: 9/10/2020
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
ms.openlocfilehash: 57276f61ca8ff848db0313935bc1841de50f9874
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075611"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>Przewodnik: Kompilowanie programu w języku C w wierszu polecenia

Visual C++ zawiera kompilator języka C, za pomocą którego można utworzyć wszystko z podstawowych programów konsolowych do pełnych aplikacji klasycznych systemu Windows, aplikacji mobilnych i innych.

W tym instruktażu przedstawiono sposób tworzenia podstawowego, "Hello, World"-stylu C programu przy użyciu edytora tekstów, a następnie kompilowania go w wierszu polecenia. Jeśli wolisz korzystać z języka C++ w wierszu polecenia, zobacz [Przewodnik: kompilowanie natywnego programu C++ w wierszu polecenia](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md). Jeśli chcesz wypróbować program Visual Studio IDE zamiast korzystać z wiersza polecenia, zobacz [Przewodnik: Praca z projektami i rozwiązaniami (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) lub [Korzystanie z programu Visual Studio IDE do tworzenia aplikacji klasycznych w języku c++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, musisz mieć zainstalowany program Visual Studio i opcjonalne składniki Visual C++ albo narzędzia kompilacji dla programu Visual Studio.

Program Visual Studio to zaawansowane zintegrowane środowisko programistyczne, które obsługuje w pełni funkcjonalne Edytor, menedżerów zasobów, debugery i kompilatory dla wielu języków i platform. Aby uzyskać informacje na temat tych funkcji oraz sposobu pobierania i instalowania programu Visual Studio, w tym bezpłatnej wersji programu Visual Studio Community Edition, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio).

Narzędzia Build Tools for Visual Studio w wersji Visual Studio instalują tylko zestaw narzędzi wiersza polecenia, kompilatory, narzędzia i biblioteki potrzebne do tworzenia programów C i C++. Doskonale nadaje się do kompilowania laboratoriów lub ćwiczeń z zajęć i jest stosunkowo szybko instalowana. Aby zainstalować tylko zestaw narzędzi wiersza polecenia, Pobierz narzędzia kompilacji dla programu Visual Studio ze strony [pliki do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) i uruchom Instalatora. W Instalatorze programu Visual Studio wybierz obciążenie **narzędzia kompilacji C++** , a następnie wybierz **Zainstaluj**.

Aby można było skompilować program C lub C++ w wierszu polecenia, należy sprawdzić, czy są zainstalowane narzędzia i czy można uzyskać do nich dostęp z poziomu wiersza polecenia. Visual C++ ma złożone wymagania dotyczące środowiska wiersza polecenia, aby znaleźć narzędzia, nagłówki i biblioteki, których używa. **Nie można użyć Visual C++ w zwykłym oknie wiersza polecenia** bez pewnego przygotowania. Potrzebujesz okna *wiersza polecenia dla deweloperów* , czyli zwykłego okna wiersza polecenia, które ma wszystkie wymagane zmienne środowiskowe. Na szczęście program Visual C++ instaluje skróty umożliwiające uruchamianie poleceń deweloperskich, które mają skonfigurowane środowisko dla kompilacji wiersza polecenia. Niestety nazwy skrótów dla wiersza polecenia dla deweloperów i lokalizacji, gdzie się znajdują, są inne w prawie każdej wersji Visual C++ i różnych wersjach systemu Windows. Pierwsze zadanie instruktażu polega na znalezieniu odpowiedniego skrótu do użycia.

> [!NOTE]
> Skrót do wiersza polecenia dla deweloperów automatycznie ustawia prawidłowe ścieżki dla kompilatora i narzędzi oraz dla wszystkich wymaganych nagłówków i bibliotek. Niektóre z tych wartości są różne dla każdej konfiguracji kompilacji. Należy samodzielnie ustawić te wartości środowiskowe, jeśli nie używasz jednego z skrótów. Aby uzyskać więcej informacji, zobacz [Ustawianie zmiennych dotyczących ścieżki i środowiska dla kompilacji w wierszu polecenia](setting-the-path-and-environment-variables-for-command-line-builds.md). Ze względu na to, że środowisko kompilacji jest złożone, zdecydowanie zalecamy użycie skrótu wiersza polecenia dla deweloperów zamiast tworzenia własnych.

Te instrukcje różnią się w zależności od używanej wersji programu Visual Studio. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj kontrolki selektora **wersji** . Znajduje się w górnej części spisu treści na tej stronie.

::: moniker range="vs-2019"

## <a name="open-a-developer-command-prompt-in-visual-studio-2019"></a>Otwieranie wiersza polecenia dla deweloperów w programie Visual Studio 2019

Jeśli zainstalowano program Visual Studio 2019 w systemie Windows 10, otwórz menu Start, a następnie przewiń w dół i Otwórz folder **programu Visual studio 2019** (nie aplikację visual Studio 2019). Wybierz **wiersz polecenia dla deweloperów dla programu VS 2019** , aby otworzyć okno wiersza polecenia.

Jeśli używasz innej wersji systemu Windows, poszukaj w menu Start lub stronie startowej folderu Visual Studio Tools zawierającego skrót do wiersza polecenia dla deweloperów. Możesz również użyć funkcji wyszukiwania systemu Windows w celu wyszukania "wiersz polecenia dewelopera" i wybrać odpowiedni, który jest zgodny z zainstalowaną wersją programu Visual Studio. Użyj skrótu, aby otworzyć okno wiersza polecenia.

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-developer-command-prompt-in-visual-studio-2017"></a>Otwieranie wiersza polecenia dla deweloperów w programie Visual Studio 2017

Jeśli zainstalowano program Visual Studio 2017 w systemie Windows 10, otwórz menu Start, a następnie przewiń w dół i Otwórz folder **programu Visual studio 2017** (nie aplikację visual Studio 2017). Wybierz **wiersz polecenia dla deweloperów dla programu VS 2017** , aby otworzyć okno wiersza polecenia.

Jeśli używasz innej wersji systemu Windows, poszukaj w menu Start lub stronie startowej folderu Visual Studio Tools zawierającego skrót do wiersza polecenia dla deweloperów. Możesz również użyć funkcji wyszukiwania systemu Windows w celu wyszukania "wiersz polecenia dewelopera" i wybrać odpowiedni, który jest zgodny z zainstalowaną wersją programu Visual Studio. Użyj skrótu, aby otworzyć okno wiersza polecenia.

::: moniker-end

::: moniker range="vs-2015"

## <a name="open-a-developer-command-prompt-in-visual-studio-2015"></a>Otwieranie wiersza polecenia dla deweloperów w programie Visual Studio 2015

Jeśli zainstalowano narzędzia Microsoft Visual C++ build Tools 2015 w systemie Windows 10, otwórz menu **Start** , a następnie przewiń w dół i otwórz folder **Visual C++ build Tools** . Wybierz **Visual C++ 2015 wiersz polecenia narzędzi x86 Native Tools** , aby otworzyć okno wiersza polecenia.

Jeśli używasz innej wersji systemu Windows, poszukaj w menu Start lub stronie startowej folderu Visual Studio Tools zawierającego skrót do wiersza polecenia dla deweloperów. Możesz również użyć funkcji wyszukiwania systemu Windows w celu wyszukania "wiersz polecenia dewelopera" i wybrać odpowiedni, który jest zgodny z zainstalowaną wersją programu Visual Studio. Użyj skrótu, aby otworzyć okno wiersza polecenia.

::: moniker-end

Następnie sprawdź, czy Visual C++ wiersz polecenia dewelopera został poprawnie skonfigurowany. W oknie wiersza polecenia wprowadź `cl` i sprawdź, czy dane wyjściowe wyglądają następująco:

```Output
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

usage: cl [ option... ] filename... [ /link linkoption... ]
```

W zależności od wersji programu Visual C++ i zainstalowanych aktualizacji mogą wystąpić różnice w bieżącym katalogu lub numerze wersji. Jeśli powyższe dane wyjściowe są podobne do tego, co widzisz, możesz przystąpić do kompilowania programów C lub C++ w wierszu polecenia.

> [!NOTE]
> Jeśli wystąpi błąd, taki jak "CL", nie został rozpoznany jako polecenie wewnętrzne lub zewnętrzne, program interoperacyjny lub plik wsadowy, "Błąd C1034 lub błąd LNK1104 podczas uruchamiania **CL** polecenia, nie jest używany wiersz polecenia dewelopera lub wystąpił problem z instalacją Visual C++. Należy rozwiązać ten problem, zanim będzie można kontynuować.

Jeśli nie możesz znaleźć skrótu do wiersza polecenia dla deweloperów lub jeśli podczas wprowadzania zostanie wyświetlony komunikat o błędzie `cl` , instalacja Visual C++ może mieć problem. Jeśli używasz programu Visual Studio 2017 lub nowszego, spróbuj zainstalować ponownie **Programowanie aplikacji klasycznych przy użyciu obciążenia języka C++** w Instalatorze programu Visual Studio. Aby uzyskać szczegółowe informacje, zobacz [Install C++ Support in Visual Studio](vscpp-step-0-installation.md). Lub zainstaluj ponownie narzędzia kompilacji ze strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/) . Nie należy przechodzić do następnej sekcji do momentu tego działania. Aby uzyskać więcej informacji na temat instalowania programu Visual Studio i rozwiązywania związanych z nim problemów, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio).

> [!NOTE]
> W zależności od wersji systemu Windows na komputerze i konfiguracji zabezpieczeń systemu może być konieczne kliknięcie prawym przyciskiem myszy, aby otworzyć menu skrótów dla skrótu wiersza polecenia dla deweloperów, a następnie wybrać polecenie **Uruchom jako administrator** , aby pomyślnie skompilować i uruchomić program tworzony w ramach tego przewodnika.

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>Utwórz plik źródłowy w języku C i skompiluj go w wierszu polecenia

1. W oknie wiersza polecenia dla deweloperów wpisz polecenie, `cd c:\` Aby zmienić bieżący katalog roboczy na katalog główny dysku C:. Następnie wpisz polecenie, `md c:\simple` Aby utworzyć katalog, a następnie wprowadź `cd c:\simple` zmiany w tym katalogu. Ten katalog zawiera plik źródłowy i skompilowany program.

1. Wprowadź `notepad simple.c` w wierszu polecenia dla deweloperów. W oknie dialogowym alertu Notatnika wybierz pozycję **tak** , aby utworzyć nowy prosty plik c w katalogu roboczym.

1. W Notatniku wprowadź następujące wiersze kodu:

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. Na pasku menu Notatnika wybierz pozycję **plik**  >  **Zapisz** , aby zapisać prostą. c w katalogu roboczym.

1. Przełącz się z powrotem do okna wiersza polecenia dewelopera. Wprowadź `dir` w wierszu polecenia, aby wyświetlić zawartość katalogu c:\simple. Na liście katalogów powinien być widoczny plik źródłowy Simple. c, który wygląda następująco:

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

   Daty i inne szczegóły różnią się w zależności od komputera. Jeśli nie widzisz pliku kodu źródłowego, Simple. c, upewnij się, że został zmieniony w utworzonym katalogu c:\simple i w Notatniku upewnij się, że plik źródłowy został zapisany w tym katalogu. Upewnij się również, że kod źródłowy został zapisany z rozszerzeniem nazwy pliku c, a nie rozszerzeniem. txt.

1. Aby skompilować program, wpisz `cl simple.c` w wierszu polecenia dewelopera.

   W wierszach informacji wyjściowych wyświetlanych przez kompilator można zobaczyć nazwę programu wykonywalnego, simple.exe.

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
   > Jeśli wystąpi błąd, taki jak "CL", nie został rozpoznany jako polecenie wewnętrzne lub zewnętrzne, program interoperacyjny lub plik wsadowy, "Błąd C1034 lub błąd LNK1104, wiersz polecenia dewelopera nie jest poprawnie skonfigurowany. Aby uzyskać informacje na temat sposobu rozwiązania tego problemu, Wróć do sekcji **otwieranie wiersza polecenia dla deweloperów** .

   > [!NOTE]
   > Jeśli zostanie wyświetlony inny błąd kompilatora lub konsolidatora, Przejrzyj kod źródłowy, aby poprawić błędy, a następnie zapisz go i ponownie uruchom kompilator. Aby uzyskać informacje o określonych błędach, użyj pola wyszukiwania u góry tej strony, aby znaleźć numer błędu.

1. Aby uruchomić program, wpisz `simple` w wierszu polecenia.

   Program wyświetla ten tekst, a następnie kończy działanie:

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   Gratulacje, udało Ci się skompilować i uruchomić program C przy użyciu wiersza polecenia.

## <a name="next-steps"></a>Następne kroki

Ten przykład "Hello, World" jest bardzo prosty, ponieważ program C może uzyskać. Programy Real World mają pliki nagłówkowe i więcej plików źródłowych, linki w bibliotekach i wykonują użyteczne działania.

Kroki opisane w tym instruktażu umożliwiają utworzenie własnego kodu w języku C zamiast wpisywania przykładowego kodu. Możesz również utworzyć wiele przykładowych programów w języku C, które znajdziesz w innym miejscu. Aby skompilować program, który ma dodatkowe pliki kodu źródłowego, wprowadź je wszystkie w wierszu polecenia, na przykład:

`cl file1.c file2.c file3.c`

Kompilator wyprowadza program o nazwie file1.exe. Aby zmienić nazwę na program1.exe, Dodaj opcję konsolidatora [/out](reference/out-output-file-name.md) :

`cl file1.c file2.c file3.c /link /out:program1.exe`

Aby automatycznie przechwytywać błędy programowania, zalecamy skompilowanie przy użyciu opcji poziomu ostrzeżeń [/W3](reference/compiler-option-warning-level.md) lub [/W4](reference/compiler-option-warning-level.md) :

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

Kompilator, cl.exe, ma wiele dodatkowych opcji, które można zastosować do kompilowania, optymalizowania, debugowania i analizowania kodu. Aby uzyskać szybką listę, wpisz `cl /?` w wierszu polecenia dewelopera. Możesz również kompilować i łączyć oddzielnie i stosować Opcje konsolidatora w bardziej złożonych scenariuszach kompilacji. Aby uzyskać więcej informacji na temat opcji kompilatora i konsolidatora, zobacz  [Dokumentacja konstrukcyjna C/C++](reference/c-cpp-building-reference.md).

Aby skonfigurować i skompilować bardziej złożone projekty w wierszu polecenia, można użyć NMAKE i plików reguł programu make lub programów MSBuild i Project. Aby uzyskać więcej informacji na temat korzystania z tych narzędzi, zobacz [NMAKE Reference](reference/nmake-reference.md) and [MSBuild](msbuild-visual-cpp.md).

Języki C i C++ są podobne, ale nie są takie same. Kompilator Microsoft C/C++ (MSVC) korzysta z prostej reguły, aby określić, który język ma być używany podczas kompilowania kodu. Domyślnie kompilator MSVC traktuje wszystkie pliki kończące się na. c jako kod źródłowy C i wszystkie pliki kończące się na. cpp jako kod źródłowy języka C++. Aby wymusić, aby kompilator traktował wszystkie pliki jako C niezależne od rozszerzenia nazwy pliku, użyj opcji kompilatora [/TC](reference/tc-tp-tc-tp-specify-source-file-type.md) .

MSVC jest zgodna ze standardem ISO C99, ale nie jest ściśle zgodne. W większości przypadków przenośny kod C zostanie skompilowany i uruchomiony zgodnie z oczekiwaniami. Visual C++ zapewnia obsługę zmian w ISO C11/C17. Aby skompilować z obsługą C11/C17, Użyj flagi kompilatora `/std:c11` lub `/std:c17` . Niektóre funkcje biblioteki i nazwy funkcji POSIX są przestarzałe przez MSVC. Funkcje są obsługiwane, ale preferowane nazwy zostały zmienione. Aby uzyskać więcej informacji, zobacz [funkcje zabezpieczeń w artykule CRT](../c-runtime-library/security-features-in-the-crt.md) i [ostrzeżeniu kompilatora (poziom 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Zobacz także

[Przewodnik: tworzenie standardowego programu C++ (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[Dokumentacja języka C](../c-language/c-language-reference.md)<br/>
[Projekty i systemy kompilacji](projects-and-build-systems-cpp.md)<br/>
[Zgodność](../c-runtime-library/compatibility.md)
