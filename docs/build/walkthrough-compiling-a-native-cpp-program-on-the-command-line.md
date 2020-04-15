---
title: 'Wskazówki: kompilowanie natywnego programu C++ na wiersz polecenia'
description: Użyj kompilatora Języka Microsoft C++ z wiersza polecenia.
ms.custom: conceptual
ms.date: 04/02/2020
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
ms.openlocfilehash: c24fdfdaef612059d5c2fbaaa58f10d83f5fe3a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335228"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>Wskazówki: kompilowanie natywnego programu C++ na wiersz polecenia

Visual Studio zawiera wiersz polecenia C i C++ kompilator. Można go używać do tworzenia wszystkiego, od podstawowych aplikacji konsoli do aplikacji uniwersalnej platformy systemu Windows, aplikacji klasycznych, sterowników urządzeń i składników .NET.

W tym instruktażu utworzysz podstawowy program w stylu C++ w stylu "Hello, World", używając edytora tekstu, a następnie skompiluj go w wierszu polecenia. Jeśli chcesz wypróbować IDE programu Visual Studio zamiast używać wiersza polecenia, zobacz [Przewodnik: Praca z projektami i rozwiązaniami (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) lub Korzystanie z [środowiska IDE programu Visual Studio dla tworzenia pulpitu w języku C++.](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)

W tym instruktażu można użyć własnego programu C++ zamiast wpisywać ten, który jest wyświetlany. Lub można użyć przykładu kodu języka C++ z innego artykułu pomocy.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten instruktaż, musisz zainstalować program Visual Studio i **opcjonalny program rozwoju pulpitu z** obciążeniem języka C++ lub narzędzia kompilacji wiersza polecenia dla programu Visual Studio.

Visual Studio to *zintegrowane środowisko programistyczne* (IDE). Obsługuje w pełni funkcjonalny edytor, menedżerów zasobów, debugerów i kompilatorów dla wielu języków i platform. Dostępne wersje obejmują bezpłatną wersję społeczności programu Visual Studio, a wszystkie mogą obsługiwać rozwój języka C i C++. Aby uzyskać informacje dotyczące pobierania i instalowania programu Visual Studio, zobacz [Instalowanie pomocy technicznej języka C++ w programie Visual Studio](vscpp-step-0-installation.md).

Narzędzia kompilacji dla programu Visual Studio instaluje tylko kompilatory wiersza polecenia, narzędzia i biblioteki potrzebne do tworzenia programów C i C++. Idealnie nadaje się do budowy laboratoriów lub ćwiczeń w klasie i instaluje się stosunkowo szybko. Aby zainstalować tylko narzędzia wiersza polecenia, poszukaj narzędzia kompilacji dla programu Visual Studio na stronie [Pliki do pobrania programu Visual Studio.](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)

Przed utworzeniem programu C lub C++ w wierszu polecenia sprawdź, czy narzędzia są zainstalowane, i można uzyskać do nich dostęp z wiersza polecenia. Visual C++ ma złożone wymagania dla środowiska wiersza polecenia, aby znaleźć narzędzia, nagłówki i biblioteki, których używa. **Nie można użyć języka Visual C++ w oknie wiersza polecenia zwykły** bez wykonywania niektórych przygotowania. Na szczęście visual C++ instaluje skróty, aby uruchomić wiersz polecenia dewelopera, który ma środowisko skonfigurowane dla kompilacji wiersza polecenia. Niestety nazwy skrótów wiersza polecenia dewelopera i miejsca ich lokalizacji różnią się w prawie każdej wersji programu Visual C++ i w różnych wersjach systemu Windows. Pierwszym zadaniem instruktażowego jest znalezienie odpowiedniego do użycia.

> [!NOTE]
> Skrót wiersza polecenia dewelopera automatycznie ustawia poprawne ścieżki dla kompilatora i narzędzi oraz dla wszystkich wymaganych nagłówków i bibliotek. Aby użyć zwykłego okna **wiersza polecenia,** należy ustawić te wartości środowiska samodzielnie. Aby uzyskać więcej informacji, zobacz [Ustawianie zmiennych ścieżki i środowiska dla kompilacji wiersza polecenia](setting-the-path-and-environment-variables-for-command-line-builds.md). Zaleca się użycie skrótu wiersza polecenia dewelopera zamiast tworzenia własnych.

### <a name="open-a-developer-command-prompt"></a>Otwieranie wiersza polecenia dewelopera

1. Jeśli program Visual Studio 2017 lub nowszy został zainstalowany w systemie Windows 10, otwórz menu Start i wybierz pozycję **Wszystkie aplikacje**. Przewiń w dół i otwórz folder **programu Visual Studio** (nie aplikację Visual Studio). Wybierz pozycję **Developer Command Prompt for VS to** open the command window .Choose Developer Command Prompt for VS to open the command prompt window.

   Jeśli zainstalowano narzędzie Microsoft Visual C++ Build Tools 2015 w systemie Windows 10, otwórz menu **Start** i wybierz pozycję **Wszystkie aplikacje**. Przewiń w dół i otwórz folder **Narzędzia kompilacji języka Visual C++.** Wybierz pozycję **Visual C++ 2015 x86 Native Tools Command Prompt,** aby otworzyć okno wiersza polecenia.

   Można również użyć funkcji wyszukiwania systemu Windows, aby wyszukać "wiersz polecenia dewelopera" i wybrać taki, który pasuje do zainstalowanej wersji programu Visual Studio. Użyj skrótu, aby otworzyć okno wiersza polecenia.

1. Następnie sprawdź, czy wiersz polecenia dewelopera języka Visual C++ jest poprawnie skonfigurowany. W oknie wiersza `cl` polecenia wprowadź i sprawdź, czy dane wyjściowe wyglądają mniej więcej tak:

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   Mogą występować różnice w bieżących numerach katalogu lub wersji. Te wartości zależą od wersji programu Visual C++ i wszystkich zainstalowanych aktualizacji. Jeśli powyższe dane wyjściowe są podobne do tego, co widzisz, możesz przystąpić do tworzenia programów C lub C++ w wierszu polecenia.

   > [!NOTE]
   > Jeśli pojawia się błąd, taki jak "'cl' nie jest rozpoznawany jako polecenie wewnętrzne lub zewnętrzne, działający program lub plik wsadowy", błąd C1034 lub błąd LNK1104 po uruchomieniu **`cl`** polecenia, to albo nie używasz wiersza polecenia dewelopera, albo coś jest nie tak z instalacją visual C++. Musisz rozwiązać ten problem, zanim będzie można kontynuować.

   Jeśli nie możesz znaleźć skrótu wiersza polecenia dewelopera lub po `cl`wprowadzeniu zostanie wyświetlony komunikat o błędzie , instalacja programu Visual C++ może mieć problem. Spróbuj ponownie zainstalować składnik Visual C++ w programie Visual Studio lub ponownie zainstaluj narzędzia kompilacji programu Microsoft Visual C++. Nie przejdź do następnej sekcji, **`cl`** dopóki polecenie nie zadziała. Aby uzyskać więcej informacji na temat instalowania i rozwiązywania problemów z programem Visual C++, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > W zależności od wersji systemu Windows na komputerze i konfiguracji zabezpieczeń systemu może być trzeba kliknąć prawym przyciskiem myszy, aby otworzyć menu skrótów dla skrótu wiersza polecenia dewelopera, a następnie wybrać polecenie **Uruchom jako administrator,** aby pomyślnie skompilować i uruchomić program, który zostanie utworzony, wykonując ten przewodnik.

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Tworzenie pliku źródłowego języka Visual C++ i kompilowanie go w wierszu polecenia

1. W oknie wiersza polecenia `md c:\hello` dewelopera wprowadź, aby `cd c:\hello` utworzyć katalog, a następnie wprowadź, aby zmienić do tego katalogu. Ten katalog jest, gdzie plik źródłowy i skompilowany program są tworzone w.

1. Wprowadź `notepad hello.cpp` w oknie wiersza polecenia.

   Wybierz **pozycję Tak,** gdy Notatnik wyświetli monit o utworzenie pliku. Ten krok otwiera puste okno Notatnika, gotowe do wprowadzenia kodu w pliku o nazwie hello.cpp.

1. W Notatniku wprowadź następujące wiersze kodu:

   ```cpp
   #include <iostream>
   using namespace std;
   int main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   Ten kod jest prosty program, który napisze jeden wiersz tekstu na ekranie, a następnie zakończy. Aby zminimalizować błędy, skopiuj ten kod i wklej go do Notatnika.

1. Zapisz swoją pracę! W Notatniku w menu **Plik** wybierz polecenie **Zapisz**.

   Gratulacje, utworzono plik źródłowy języka C++, hello.cpp, który jest gotowy do kompilacji.

1. Przełącz się z powrotem do okna wiersza polecenia dewelopera. Wprowadź `dir` w wierszu polecenia, aby wyświetlić listę zawartości katalogu c:\hello. Powinieneś zobaczyć plik źródłowy hello.cpp w liście katalogów, który wygląda mniej więcej tak:

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

   Daty i inne szczegóły będą się różnić na komputerze. Jeśli nie widzisz pliku kodu źródłowego, *hello.cpp*, upewnij się, że został zmieniony na utworzony katalog *c:\\hello.* W Notatniku upewnij się, że plik źródłowy został zapisany w tym katalogu. Upewnij się również, że kod *`.cpp`* źródłowy został zapisany *`.txt`* z rozszerzeniem nazwy pliku, a nie z rozszerzeniem.

1. W wierszu polecenia `cl /EHsc hello.cpp` dewelopera wprowadź, aby skompilować program.

   Kompilator cl.exe generuje plik obj zawierający skompilowany kod, a następnie uruchamia konsolidator w celu utworzenia programu wykonywalnego o nazwie hello.exe. Ta nazwa pojawia się w wierszach informacji wyjściowych wyświetlanych przez kompilator. Dane wyjściowe kompilatora powinny wyglądać mniej więcej tak:

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
   > Jeśli pojawi się błąd, taki jak "'cl' nie jest rozpoznawany jako polecenie wewnętrzne lub zewnętrzne, działający program lub plik wsadowy", błąd C1034 lub błąd LNK1104, wiersz polecenia dewelopera nie jest poprawnie skonfigurowany. Aby uzyskać informacje na temat rozwiązywania tego problemu, wróć do sekcji **Otwieranie wiersza polecenia dewelopera.**

   > [!NOTE]
   > Jeśli zostanie wyświetlony błąd lub ostrzeżenie innego kompilatora lub konsolidatora, przejrzyj kod źródłowy, aby poprawić wszelkie błędy, a następnie zapisz go i uruchom kompilator ponownie. Aby uzyskać informacje o określonych błędach, użyj pola wyszukiwania na tej stronie MSDN, aby wyszukać numer błędu.

1. Aby uruchomić program hello.exe, w wierszu polecenia wprowadź . `hello`

   Program wyświetla ten tekst i kończy pracę:

   ```Output
   Hello, world, from Visual C++!
   ```

   Gratulacje, skompilowano i uruchomisz program C++ przy użyciu narzędzi wiersza polecenia.

## <a name="next-steps"></a>Następne kroki

Ten przykład "Hello, World" jest tak prosty, jak program C++. Programy ze świata rzeczywistego zwykle mają pliki nagłówkowe, więcej plików źródłowych i łącza do bibliotek.

Można użyć kroków w tym instruktażu do tworzenia własnego kodu C++ zamiast wpisywania przykładowego kodu pokazano. Te kroki umożliwiają również tworzenie wielu przykładowych programów kodu języka C++, które można znaleźć w innym miejscu. Możesz umieścić kod źródłowy i tworzyć aplikacje w dowolnym katalogu zapisywalnym. Domyślnie visual studio IDE tworzy projekty w folderze użytkownika, w *\\źródłowym repozytorium* podfolderu. Starsze wersje mogą umieszczać projekty w *folderze Documents\\Visual Studio \<>\\ *Projects*.

Aby skompilować program, który ma dodatkowe pliki kodu źródłowego, wprowadź je wszystkie w wierszu polecenia, takie jak:

`cl /EHsc file1.cpp file2.cpp file3.cpp`

Opcja `/EHsc` wiersza polecenia instruuje kompilator, aby włączyć standardowe zachowanie obsługi wyjątków C++. Bez niego wyjątki zarzucić może spowodować niezniezuconych obiektów i wycieków zasobów. Aby uzyskać więcej informacji, zobacz [/EH (Model obsługi wyjątków)](reference/eh-exception-handling-model.md).

Po podaniu dodatkowych plików źródłowych kompilator używa pierwszego pliku wejściowego do utworzenia nazwy programu. W takim przypadku wyprowadza program o nazwie file1.exe. Aby zmienić nazwę na program1.exe, dodaj opcję [/out](reference/out-output-file-name.md) konsolidatora:

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Aby automatycznie wyłapać więcej błędów programowych, zalecamy skompilowanie przy użyciu opcji poziomu ostrzeżenia [/W3](reference/compiler-option-warning-level.md) lub [/W4:](reference/compiler-option-warning-level.md)

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Kompilator cl.exe ma o wiele więcej opcji. Można je zastosować do tworzenia, optymalizacji, debugowania i analizowania kodu. Aby uzyskać szybką `cl /?` listę, wprowadź w wierszu polecenia dewelopera. Można również skompilować i połączyć oddzielnie i zastosować opcje konsolidatora w bardziej złożonych scenariuszach kompilacji. Aby uzyskać więcej informacji na temat opcji kompilatora i konsolidatora oraz użycia, zobacz [Odwołanie do budynku C/C++.](reference/c-cpp-building-reference.md)

Za pomocą NMAKE i makefiles, MSBuild i plików projektu lub CMake można skonfigurować i tworzyć bardziej złożone projekty w wierszu polecenia. Aby uzyskać więcej informacji na temat korzystania z tych narzędzi, zobacz [NMAKE Reference](reference/nmake-reference.md), [MSBuild](msbuild-visual-cpp.md)i [CMake projektów w programie Visual Studio](cmake-projects-in-visual-studio.md).

Języki C i C++ są podobne, ale nie takie same. Kompilator MSVC używa prostej reguły, aby określić, który język ma być używany podczas kompilowania kodu. Domyślnie kompilator MSVC traktuje pliki, *`.c`* które kończą się jako kod *`.cpp`* źródłowy języka C, i pliki, które kończą się jako kod źródłowy języka C++. Aby wymusić, aby kompilator traktował wszystkie pliki jako C++ niezależnie od rozszerzenia nazwy pliku, użyj opcji kompilatora [/TP.](reference/tc-tp-tc-tp-specify-source-file-type.md)

Kompilator MSVC zawiera bibliotekę środowiska wykonawczego C (CRT), która jest zgodna ze standardem ISO C99, z niewielkimi wyjątkami. Przenośny kod zazwyczaj kompiluje i działa zgodnie z oczekiwaniami. Niektóre przestarzałe funkcje biblioteki i kilka nazw funkcji POSIX są przestarzałe przez kompilator MSVC. Funkcje są obsługiwane, ale preferowane nazwy uległy zmianie. Aby uzyskać więcej informacji, zobacz [Funkcje zabezpieczeń w crt](../c-runtime-library/security-features-in-the-crt.md) i [ostrzeżenie kompilatora (poziom 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Zobacz też

[Odwołanie do języka języka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty i systemy kompilacji](projects-and-build-systems-cpp.md)<br/>
[Opcje kompilatora MSVC](reference/compiler-options.md)
