---
title: 'Wskazówki: kompilowanie natywnego programu C++ na wiersz polecenia'
description: Użyj kompilatora języka Microsoft C++ z wiersza polecenia.
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

Program Visual Studio zawiera kompilator C i C++ w wierszu polecenia. Za jego pomocą można utworzyć wszystko z podstawowych aplikacji konsolowych, aby platforma uniwersalna systemu Windows aplikacje, aplikacje klasyczne, sterowniki urządzeń i składniki platformy .NET.

W tym instruktażu utworzysz podstawowy, "Hello, World" program w stylu języka C++ przy użyciu edytora tekstów, a następnie kompilujesz go w wierszu polecenia. Jeśli chcesz wypróbować program Visual Studio IDE zamiast korzystać z wiersza polecenia, zobacz [Przewodnik: Praca z projektami i rozwiązaniami (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) lub [Korzystanie z programu Visual Studio IDE do tworzenia aplikacji klasycznych w języku c++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

W tym instruktażu można użyć własnego programu C++ zamiast wpisywać ten, który jest wyświetlany. Możesz też użyć przykładu kodu C++ z innego artykułu pomocy.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, musisz mieć zainstalowane programy Visual Studio i opcjonalne **Programowanie aplikacji klasycznych w języku C++** lub narzędzia do kompilowania wiersza polecenia dla programu Visual Studio.

Program Visual Studio to *zintegrowane środowisko programistyczne* (IDE). Obsługuje ona w pełni funkcjonalne Edytor, menedżerów zasobów, debugery i kompilatory dla wielu języków i platform. Dostępne wersje obejmują bezpłatny program Visual Studio Community Edition, a wszystkie mogą obsługiwać programowanie C i C++. Aby uzyskać informacje na temat pobierania i instalowania programu Visual Studio, zobacz [Instalowanie obsługi języka C++ w programie Visual Studio](vscpp-step-0-installation.md).

Narzędzia kompilacji dla programu Visual Studio instalują tylko kompilatory wiersza polecenia, narzędzia i biblioteki potrzebne do tworzenia programów C i C++. Doskonale nadaje się do kompilowania laboratoriów lub ćwiczeń z zajęć i jest stosunkowo szybko instalowana. Aby zainstalować tylko narzędzia wiersza polecenia, należy poszukać narzędzia Build Tools for Visual Studio na stronie [pliki do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) .

Przed kompilacją programu C lub C++ w wierszu polecenia Sprawdź, czy są zainstalowane narzędzia i możesz uzyskać do nich dostęp z poziomu wiersza polecenia. Visual C++ ma złożone wymagania dotyczące środowiska wiersza polecenia, aby znaleźć narzędzia, nagłówki i biblioteki, których używa. **Nie można użyć Visual C++ w zwykłym oknie wiersza polecenia** bez wykonywania niektórych czynności przygotowawczych. Na szczęście Visual C++ instaluje skróty do uruchamiania wiersza polecenia dla deweloperów, który ma skonfigurowane środowisko dla kompilacji wiersza polecenia. Niestety nazwy skrótów dla wiersza polecenia dla deweloperów i lokalizacji, gdzie się znajdują, są inne w prawie każdej wersji Visual C++ i różnych wersjach systemu Windows. Pierwsze zadanie instruktażu wyszukuje prawo do użycia.

> [!NOTE]
> Skrót do wiersza polecenia dla deweloperów automatycznie ustawia prawidłowe ścieżki dla kompilatora i narzędzi oraz dla wszystkich wymaganych nagłówków i bibliotek. Należy samodzielnie ustawić te wartości środowiskowe, jeśli używasz zwykłego okna **wiersza polecenia** . Aby uzyskać więcej informacji, zobacz [Ustawianie zmiennych dotyczących ścieżki i środowiska dla kompilacji w wierszu polecenia](setting-the-path-and-environment-variables-for-command-line-builds.md). Zalecamy użycie skrótu wiersza polecenia dla deweloperów zamiast tworzenia własnych.

### <a name="open-a-developer-command-prompt"></a>Otwórz wiersz polecenia dewelopera

1. Jeśli zainstalowano program Visual Studio 2017 lub nowszy w systemie Windows 10, otwórz menu Start i wybierz pozycję **wszystkie aplikacje**. Przewiń w dół i Otwórz folder **programu Visual Studio** (nie aplikację Visual Studio). Wybierz **wiersz polecenia dla deweloperów dla programu vs** , aby otworzyć okno wiersza polecenia.

   Jeśli zainstalowano narzędzia Microsoft Visual C++ build Tools 2015 w systemie Windows 10, otwórz menu **Start** i wybierz pozycję **wszystkie aplikacje**. Przewiń w dół i Otwórz folder **Visual C++ build Tools** . Wybierz **Visual C++ 2015 wiersz polecenia narzędzi x86 Native Tools** , aby otworzyć okno wiersza polecenia.

   Możesz również użyć funkcji wyszukiwania systemu Windows w celu wyszukania "wiersz polecenia dewelopera" i wybrać odpowiedni, który jest zgodny z zainstalowaną wersją programu Visual Studio. Użyj skrótu, aby otworzyć okno wiersza polecenia.

1. Następnie sprawdź, czy Visual C++ wiersz polecenia dewelopera został poprawnie skonfigurowany. W oknie wiersza polecenia wprowadź `cl` i sprawdź, czy dane wyjściowe wyglądają następująco:

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   Mogą występować różnice w bieżącym katalogu lub numerze wersji. Te wartości zależą od wersji Visual C++ i zainstalowanych aktualizacji. Jeśli powyższe dane wyjściowe są podobne do tego, co widzisz, możesz przystąpić do kompilowania programów C lub C++ w wierszu polecenia.

   > [!NOTE]
   > Jeśli wystąpi błąd, taki jak "CL", nie został rozpoznany jako polecenie wewnętrzne lub zewnętrzne, program wykonywalny lub plik wsadowy, "Błąd C1034 lub błąd LNK1104 po uruchomieniu **`cl`** polecenia, wówczas nie jest używany wiersz polecenia dewelopera lub wystąpił problem z instalacją Visual C++. Należy rozwiązać ten problem, zanim będzie można kontynuować.

   Jeśli nie możesz znaleźć skrótu do wiersza polecenia dla deweloperów lub jeśli podczas wprowadzania `cl`zostanie wyświetlony komunikat o błędzie, instalacja Visual C++ może mieć problem. Spróbuj zainstalować ponownie składnik Visual C++ w programie Visual Studio lub zainstalować Microsoft Visual C++ narzędzia do kompilacji. Nie należy przechodzić do następnej sekcji, dopóki **`cl`** polecenie nie zostanie zadziała. Aby uzyskać więcej informacji na temat instalowania i rozwiązywania problemów Visual C++, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > W zależności od wersji systemu Windows na komputerze i konfiguracji zabezpieczeń systemu może być konieczne kliknięcie prawym przyciskiem myszy, aby otworzyć menu skrótów dla skrótu wiersza polecenia dla deweloperów, a następnie wybrać polecenie **Uruchom jako administrator** , aby pomyślnie skompilować i uruchomić program tworzony w ramach tego przewodnika.

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Utwórz plik źródłowy Visual C++ i skompiluj go w wierszu polecenia

1. W oknie wiersza polecenia dla deweloperów wpisz `md c:\hello` polecenie, aby utworzyć katalog, a następnie wprowadź `cd c:\hello` zmiany w tym katalogu. W tym katalogu znajduje się plik źródłowy i skompilowany program.

1. Wprowadź `notepad hello.cpp` w oknie wiersza polecenia.

   Wybierz opcję **tak** , gdy w Notatniku zostanie wyświetlony komunikat z prośbą o utworzenie pliku. Ten krok powoduje otwarcie pustego okna Notatnika, które jest gotowe do wprowadzenia kodu w pliku o nazwie Hello. cpp.

1. W Notatniku wprowadź następujące wiersze kodu:

   ```cpp
   #include <iostream>
   using namespace std;
   int main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   Ten kod jest prostym programem, który zapisze jeden wiersz tekstu na ekranie, a następnie zakończy działanie. Aby zminimalizować błędy, Skopiuj ten kod i wklej go do Notatnika.

1. Zapisz swoją służbę! W Notatnik, w menu **plik** , wybierz **Zapisz**.

   Gratulacje, utworzono plik źródłowy języka C++, Hello. cpp, który jest gotowy do skompilowania.

1. Przełącz się z powrotem do okna wiersza polecenia dewelopera. Wprowadź `dir` w wierszu polecenia, aby wyświetlić zawartość katalogu c:\hello. Plik źródłowy Hello. cpp powinien zostać wyświetlony na liście katalogów, która wygląda następująco:

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

   Daty i inne szczegóły różnią się w zależności od komputera. Jeśli nie widzisz pliku kodu źródłowego, *Hello. cpp*, upewnij się, że został zmieniony na utworzony katalog *c\\: Hello* . W Notatniku upewnij się, że plik źródłowy został zapisany w tym katalogu. Upewnij się również, że kod źródłowy został zapisany z rozszerzeniem *`.cpp`* nazwy pliku, a nie *`.txt`* rozszerzeniem.

1. W wierszu polecenia dla deweloperów wpisz `cl /EHsc hello.cpp` polecenie, aby skompilować program.

   Kompilator CL. exe generuje plik. obj, który zawiera skompilowany kod, a następnie uruchamia konsolidator, aby utworzyć program wykonywalny o nazwie Hello. exe. Ta nazwa jest wyświetlana w wierszach informacji wyjściowych wyświetlanych przez kompilator. Dane wyjściowe kompilatora powinny wyglądać następująco:

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
   > Jeśli wystąpi błąd, taki jak "CL", nie został rozpoznany jako polecenie wewnętrzne lub zewnętrzne, program interoperacyjny lub plik wsadowy, "Błąd C1034 lub błąd LNK1104, wiersz polecenia dewelopera nie jest poprawnie skonfigurowany. Aby uzyskać informacje na temat sposobu rozwiązania tego problemu, Wróć do sekcji **otwieranie wiersza polecenia dla deweloperów** .

   > [!NOTE]
   > Jeśli zostanie wyświetlony inny błąd kompilatora lub konsolidatora, Przejrzyj kod źródłowy, aby poprawić błędy, a następnie zapisz go i ponownie uruchom kompilator. Aby uzyskać informacje o określonych błędach, użyj pola wyszukiwania na tej stronie MSDN, aby wyszukać numer błędu.

1. Aby uruchomić program Hello. exe, w wierszu polecenia wpisz `hello`polecenie.

   Program wyświetla ten tekst i opuszcza:

   ```Output
   Hello, world, from Visual C++!
   ```

   Gratulacje, udało Ci się skompilować i uruchomić program C++ przy użyciu narzędzi wiersza polecenia.

## <a name="next-steps"></a>Następne kroki

Ten przykład "Hello, World" jest tak prosty, jak program w języku C++ może uzyskać. Programy Real World zazwyczaj mają pliki nagłówkowe, więcej plików źródłowych i łączą się z bibliotekami.

Kroki opisane w tym instruktażu umożliwiają utworzenie własnego kodu w języku C++ zamiast wpisywania przykładowego kodu. Te kroki umożliwiają również kompilowanie wielu przykładowych programów w języku C++, które znajdują się w innym miejscu. Możesz umieścić kod źródłowy i skompilować swoje aplikacje w dowolnym zapisywalnym katalogu. Domyślnie środowisko IDE programu Visual Studio tworzy projekty w folderze użytkownika w podfolderze *repozytoria\\źródłowego* . Starsze wersje mogą umieszczać projekty w *dokumentach\\programu Visual Studio \<w wersji \\>* Projects *.

Aby skompilować program, który ma dodatkowe pliki kodu źródłowego, wprowadź je wszystkie w wierszu polecenia, na przykład:

`cl /EHsc file1.cpp file2.cpp file3.cpp`

Opcja `/EHsc` wiersza polecenia instruuje kompilator, aby włączył standardowe zachowanie obsługi wyjątków C++. Bez niego, zgłoszone wyjątki mogą spowodować niezniszczenia obiektów i przecieków zasobów. Aby uzyskać więcej informacji, zobacz [/EH (model obsługi wyjątków)](reference/eh-exception-handling-model.md).

Po dostarczeniu dodatkowych plików źródłowych kompilator używa pierwszego pliku wejściowego do utworzenia nazwy programu. W takim przypadku wyprowadza program o nazwie plik1. exe. Aby zmienić nazwę na Program1. exe, Dodaj opcję konsolidatora [/out](reference/out-output-file-name.md) :

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Aby automatycznie przechwytywać błędy programowania, zalecamy skompilowanie przy użyciu opcji poziomu ostrzeżeń [/W3](reference/compiler-option-warning-level.md) lub [/W4](reference/compiler-option-warning-level.md) :

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

Kompilator, CL. exe, ma wiele dodatkowych opcji. Można je stosować do kompilowania, optymalizowania, debugowania i analizowania kodu. Aby uzyskać szybką listę, `cl /?` wpisz w wierszu polecenia dewelopera. Możesz również kompilować i łączyć oddzielnie i stosować Opcje konsolidatora w bardziej złożonych scenariuszach kompilacji. Aby uzyskać więcej informacji na temat opcji kompilatora i konsolidatora, zobacz [Dokumentacja konstrukcyjna C/C++](reference/c-cpp-building-reference.md).

Aby skonfigurować i skompilować bardziej złożone projekty w wierszu polecenia, można użyć NMAKE i plików reguł programu make, programów MSBuild i Project oraz CMake. Aby uzyskać więcej informacji na temat korzystania z tych narzędzi, zobacz [NMAKE Reference](reference/nmake-reference.md), [MSBuild](msbuild-visual-cpp.md)i [CMAKE projects w programie Visual Studio](cmake-projects-in-visual-studio.md).

Języki C i C++ są podobne, ale nie są takie same. Kompilator MSVC korzysta z prostej reguły, aby określić język, który ma być używany podczas kompilowania kodu. Domyślnie kompilator MSVC traktuje pliki, które kończą się *`.c`* jako kod źródłowy C, i pliki, które kończą się *`.cpp`* jako kod źródłowy języka C++. Aby wymusić traktowanie wszystkich plików jako języka C++ niezależnie od rozszerzenia nazwy pliku, należy użyć opcji [/TP](reference/tc-tp-tc-tp-specify-source-file-type.md) kompilatora.

Kompilator MSVC zawiera bibliotekę środowiska uruchomieniowego języka C (CRT), która jest zgodna ze standardem ISO C99, z drobnymi wyjątkami. Przenośny kod zwykle kompiluje i działa zgodnie z oczekiwaniami. Niektóre przestarzałe funkcje biblioteki i kilka nazw funkcji POSIX są przestarzałe przez kompilator MSVC. Funkcje są obsługiwane, ale preferowane nazwy zostały zmienione. Aby uzyskać więcej informacji, zobacz [funkcje zabezpieczeń w artykule CRT](../c-runtime-library/security-features-in-the-crt.md) i [ostrzeżeniu kompilatora (poziom 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty i systemy kompilacji](projects-and-build-systems-cpp.md)<br/>
[Opcje kompilatora MSVC](reference/compiler-options.md)
