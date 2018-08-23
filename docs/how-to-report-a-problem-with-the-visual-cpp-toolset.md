---
title: Jak zgłosić problem za pomocą narzędzi Visual C++ | Dokumentacja firmy Microsoft
ms.date: 06/21/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 359c9d3f72ffa87abf49c6e3ca90743ad0fc80a3
ms.sourcegitcommit: 9be4b66efa45dc132cef06eb3b258c2252ea23a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2018
ms.locfileid: "42465532"
---
# <a name="how-to-report-a-problem-with-the-visual-c-toolset-or-documentation"></a>Jak zgłosić problem za pomocą zestawu narzędzi Visual C++ lub dokumentacji

Jeśli wystąpią problemy z kompilatorem języka Microsoft Visual C++, konsolidator, lub innych narzędzi i bibliotek, chcemy dowiedzieć się o nich. Jeśli problem będzie się w naszej dokumentacji, chcemy się dowiedzieć, zbyt.

## <a name="how-to-report-a-c-toolset-issue"></a>Jak zgłosić problem zestawu narzędzi języka C++

Jest najlepszym sposobem, aby dać nam znać o problemie, aby wysłać nam raport, który zawiera opis problemów napotkanych wcześniej, szczegółowe informacje o jak kompilujesz program, a *odtwarzania*, pełną przypadek testowy, możemy użyć do odtworzenia Wystąpił problem na własnych maszynach. Te informacje umożliwiają szybko sprawdzić, czy problem istnieje w naszym kodzie i nie jest lokalny do środowiska, aby określić, czy ma wpływ na innych wersji kompilatora i diagnozować ich przyczyny.

W poniższych sekcjach przeczytasz o co sprawia, że dobry raport, jak wygenerować odtwarzania dla rodzaju problem, który Ci się znaleźć i jak wysyłanie raportu, aby zespół pracujący nad produktem. Raporty są ważne dla nas i dla innych deweloperów takich jak Ty. Dziękujemy za pomoc w ulepszeniu programu Visual C++!

## <a name="how-to-prepare-your-report"></a>Jak przygotować raport

Tworzenie raportu o wysokiej jakości jest ważne, ponieważ jest bardzo trudne do odtworzenia problemu, który wystąpił na własnych maszynach bez pełne informacje. Lepsze raportu, tym bardziej efektywnie jesteśmy stanie Utwórz i zdiagnozować problem.

Jako minimum powinien zawierać raportu

- Pełne informacji o wersji zestawu narzędzi, z którego korzystasz.

- Cl.exe pełny wiersz polecenia używany do tworzenia kodu.

- Szczegółowy opis napotkany problem.

- Odtwórz: źródła pełną, uproszczona, niezależna przykładowy kod, który pokazuje problem.

Czytaj dalej, aby dowiedzieć się więcej o określonych informacji i gdzie można znaleźć, a także sposób tworzenia dobrych odtwarzania.

### <a name="the-toolset-version"></a>Wersja zestawu narzędzi

Potrzebujemy informacji pełnej wersji i architektury docelowej z zestawem narzędzi, który powoduje, że ten problem, aby firma Microsoft testować swoje odtwarzania względem tego samego zestawu narzędzi na naszych komputerach. Jeśli firma Microsoft może odtworzyć problem, te informacje również daje nam punkt wyjścia do badania, które wersje zestawu narzędzi załączniku ten sam problem.

#### <a name="to-report-the-full-version-of-the-compiler-youre-using"></a>Aby zgłosić pełną wersję kompilatora, którego używasz

1. Otwórz **wiersz polecenia dla deweloperów** odpowiadającej architektury konfiguracji i wersji programu Visual Studio umożliwia kompilowanie projektu. Na przykład, jeśli tworzysz za pomocą programu Visual Studio 2017 na x64 x64 wybierz elementy docelowe, **x64 natywnych narzędzi wiersza polecenia dla programu VS 2017**. Aby uzyskać więcej informacji, zobacz [skróty wiersza polecenia dla deweloperów](build/building-on-the-command-line.md#developer-command-prompt-shortcuts).

1. W oknie konsoli wiersza polecenia dla deweloperów, wprowadź polecenie **cl /Bv**.

Dane wyjściowe powinny wyglądać następująco:

```Output
C:\Users\username\Source>cl /Bv
Microsoft (R) C/C++ Optimizing Compiler Version 19.14.26428.1 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

Compiler Passes:
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\cl.exe:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c1.dll:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c1xx.dll:      Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\c2.dll:        Version 19.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\link.exe:      Version 14.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\mspdb140.dll:  Version 14.14.26428.1
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\VC\Tools\MSVC\14.14.26428\bin\HostX86\x86\1033\clui.dll: Version 19.14.26428.1

cl : Command line error D8003 : missing source filename
```

Skopiuj i Wklej wszystkie dane wyjściowe do raportu.

### <a name="the-command-line"></a>W wierszu polecenia

Potrzebujemy dokładny wiersz polecenia (cl.exe i wszystkie jej argumenty) używane do kompilowania swojego kodu, dzięki czemu możemy ją tworzyć je w taki sam sposób na naszych komputerach. Jest to ważne, ponieważ został napotkany problem może istnieć tylko podczas kompilowania przy użyciu określonego argumentu lub kombinacja argumentów.

Najlepszym miejscem, aby znaleźć te informacje są w dzienniku kompilacji natychmiast, po których występuje problem. Daje to gwarancję, że wiersz polecenia zawiera dokładnie te same argumenty, które mogą być przyczyną problemu.

#### <a name="to-report-the-contents-of-the-command-line"></a>Aby zgłosić zawartość wiersza polecenia

1. Znajdź **CL.command.1.tlog** pliku i otwórz go. Domyślnie ten plik znajduje się w folderze Moje dokumenty w \\programu Visual Studio *wersji*\\projektów\\*SolutionName* \\ *ProjectName*\\*konfiguracji*\\*ProjectName*.tlog\\CL.command.1.tlog, lub w folderze użytkownika w obszarze \\Źródła\\repozytoriów\\*SolutionName*\\*ProjectName*\\*konfiguracji* \\ *ProjectName*.tlog\\CL.command.1.tlog. Jeśli używasz innego systemu kompilacji, lub jeśli zmienisz domyślną lokalizację dla projektu może być w innej lokalizacji.

   W tym pliku można znaleźć nazwy plików kodu źródłowego, a następnie argumenty wiersza polecenia używane do kompilowania ich, każdy w osobnych wierszach.

1. Znajdź wiersz, który zawiera nazwę pliku źródła kodu, w którym występuje problem; wiersz poniżej zawiera odpowiednie argumenty wiersza polecenia cl.exe.

Skopiuj i Wklej całego wiersza polecenia do raportu.

### <a name="a-description-of-the-problem"></a>Opis problemu

Potrzebujemy, aby uzyskać szczegółowy opis problemu, które wystąpiły, aby mogli zweryfikować, że widzimy ten sam efekt na naszych komputerach; jego również czasami przydatne dla nas wiedzieć, co próbujesz osiągnąć oczekiwany efekt.

Podaj **dokładnie komunikaty o błędach** podane przez zestaw narzędzi lub zachowanie dokładnego czasu wykonywania, zostanie wyświetlony. Potrzebujemy tych informacji, aby zweryfikować, że firma Microsoft została poprawnie odtworzyć problem. Zawsze podawaj **wszystkich** kompilatora, dane wyjściowe, nie tylko ostatni komunikat o błędzie. Potrzebujemy wyświetlić wszystkie elementy, które doprowadziły do problemu, który możesz zgłaszać. Jeśli ten problem można duplikować, za pomocą kompilatora wiersza polecenia, te dane wyjściowe kompilatora jest preferowana; IDE oraz innych systemów kompilacji może filtrować komunikaty o błędach, zobacz lub przechwytywać tylko pierwszego wiersza komunikatu o błędzie.

Jeśli problem będzie się, że kompilator akceptuje nieprawidłowy kod i nie generuje diagnostyki, należy pamiętać, to w raporcie.

Aby zgłosić problem zachowanie środowiska uruchomieniowego, należy dołączyć **dokładna kopia** program drukuje i powinna się pojawić. Najlepiej, jeśli to jest osadzony w danych wyjściowych instrukcji, na przykład `printf("This should be 5: %d\n", actual_result);`. Jeśli program ulegnie awarii, zawiesza się mówią, że także.

Dodaj inne szczegóły, które mogą pomóc nam zdiagnozować problem, który wystąpił, takich jak żadnych obejść zostały znalezione. Należy unikać powtarzania informacjach znajdujących się gdzie indziej w raporcie.

### <a name="the-repro"></a>Odtwórz

Odtwórz jest przykładów kodu źródłowego kompletny, niezależny odtwarzalnie demonstruje problem już wystąpił (stąd nazwa). Potrzebujemy odtwarzania, dzięki czemu możemy odtworzyć błąd, na naszych komputerach. Kod powinny być wystarczające, aby utworzyć prosty plik wykonywalny, który kompiluje i uruchamia lub który może skompilować i uruchomić, a dla problemu, który Ci się znaleźć. Odtwórz nie jest fragment kodu; powinna mieć pełne funkcje i klasy i zawierają wszystkie niezbędne # dyrektyw, nawet w przypadku standardowych nagłówków include.

#### <a name="what-makes-a-good-repro"></a>Co sprawia, że dobry odtwarzania

Jest dobrą odtwarzania:

- **Minimalny.** Reprodukcje powinien być możliwie najmniejsze, ale nadal pokazują napotkany problem. Reprodukcje nie muszą być złożone ani realistyczne; Wystarczy wyświetlić kod, który jest zgodny do warstwy standardowa lub implementacji kompilatora udokumentowanego lub w przypadku braku diagnostyczne, kod, który nie jest zgodna. Proste, aby punkt reprodukcje, zawierające wystarczający tylko kod, aby zademonstrować problem są najlepsze. Jeśli wyeliminować lub uprościć kod i pozostają zgodność i można także pozostawić ten problem, bez zmian, należy to zrobić. Nie trzeba obejmują przeciwdziałania przykłady kodu, który działa.

- **Self-Contained.** Reprodukcje należy unikać niepotrzebne zależności. Jeśli można odtworzyć problem bez bibliotek innych firm, należy to zrobić. Czy można odtworzyć problem bez konieczności wprowadzania kodu biblioteki, oprócz instrukcji proste dane wyjściowe (na przykład `puts("this shouldn't compile");`, `std::cout << value;`, i `printf("%d\n", value);` zgadzasz), należy to zrobić. To idealne rozwiązanie, jeśli na przykład, można zmniejszone do pliku z kodem jednego źródła, bez odwołania do żadnych nagłówków użytkownika. Zmniejszenie ilości kodu, który mamy można rozważyć jako możliwe Współautor problem jest teraz znacznie USA.

- **W najnowszej wersji kompilatora.** Reprodukcje należy używać najnowszej aktualizacji do najnowszej wersji zestawu narzędzi lub najnowszej wersji wstępnej następnej aktualizacji lub kolejnej głównej wersji, jeśli to możliwe. Bardzo często Naprawiono problemów, które mogą wystąpić w starszych wersjach zestawu narzędzi w nowszych wersjach. Poprawki są backported do starszych wersji tylko w wyjątkowych okolicznościach.

- **Sprawdza, czy inne kompilatory** w razie potrzeby. Reprodukcje obejmujące przenośnego kodu C++ należy sprawdzić zachowanie względem innych kompilatorów, jeśli jest to możliwe. Standardowe określa poprawność program i żadnego kompilatora jest doskonałym rozwiązaniem, ale jeśli MSVC nie Clang i kompilatora GCC zaakceptować kodzie bez diagnostyki, prawdopodobnie patrzysz na usterkę w naszym kompilatora. (Inne możliwości obejmują różnice w systemach Unix i Windows zachowanie lub różnych poziomach implementacji standardów C++ i tak dalej). Z drugiej strony Jeśli wszystkie kompilatory odrzucić kodu, następnie jest prawdopodobne, że Twój kod jest nieprawidłowy. Oglądanie komunikatów o błędach różnych może pomóc zdiagnozować problem samodzielnie.

   Możesz znaleźć listy kompilatory online, aby przetestować kod w [Kompilatory języka C++ w trybie Online](https://isocpp.org/blog/2013/01/online-c-compilers) w witrynie sieci Web ISO C++ lub to nadzorowana [listy kompilatory C++ Online](https://arnemertz.github.io/online-compilers/) w witrynie GitHub. Niektóre szczególne przykłady [Wandbox](https://wandbox.org/), [Explorer kompilatora](https://godbolt.org/), i [Coliru](http://coliru.stacked-crooked.com/).

   > [!NOTE]
   > Kompilatora online witryn sieci Web nie są powiązane z firmą Microsoft. Wiele witryn internetowych z kompilatora online są uruchamiane jako projektów osobistych, a niektóre z tych witrynach mogą być niedostępne po to odczytu, ale wyszukiwania powinien znajdować się inne osoby, których można użyć.

Problemy z kompilatora, konsolidatora i w bibliotekach, często pojawiają się w szczególności sposobów. Typ problemu, który wystąpi określi, jakiego rodzaju odtwarzania należy uwzględnić w raporcie. Bez odpowiedniego odtwarzania mamy nie ma niczego do zbadania. Poniżej przedstawiono niektóre rodzaje problemów, które może zostać wyświetlony i instrukcje dotyczące generowania rodzaje reprodukcje ma być użyte do zgłaszania każdego rodzaju problemów.

#### <a name="frontend-parser-crash"></a>Awaria serwera sieci Web (analizator składni)

Występują awarie frontonu fazie analizy kompilatora. Zwykle, kompilator będzie emitować [krytyczny C1001 błąd](error-messages/compiler-errors-1/fatal-error-c1001.md) i odwoływać się do źródła kodu pliku i numer wiersza w którym wystąpił błąd; często otrzymywane msc1.cpp pliku, ale można zignorować te dane.

Dla tego rodzaju awaria podaj [wstępnie przetworzony odtwarzania](#preprocessed-repros).

Poniżej przedstawiono przykładowe dane wyjściowe kompilatora dla tego rodzaju awarii:

```Output
SandBoxHost.cpp
d:\o\dev\search\foundation\common\tools\sandbox\managed\managed.h(929):
        fatal error C1001: An internal error has occurred in the compiler.
(compiler file 'msc1.cpp', line 1369)
To work around this problem, try simplifying or changing the program near the
        locations listed above.
Please choose the Technical Support command on the Visual C++
Help menu, or open the Technical Support help file for more information
d:\o\dev\search\foundation\common\tools\sandbox\managed\managed.h(929):
        note: This diagnostic occurred in the compiler generated function
        'void Microsoft::Ceres::Common::Tools::Sandbox::SandBoxedProcess::Dispose(bool)'
Internal Compiler Error in d:\o\dev\otools\bin\x64\cl.exe.  You will be prompted
        to send an error report to Microsoft later.
INTERNAL COMPILER ERROR in 'd:\o\dev\otools\bin\x64\cl.exe'
    Please choose the Technical Support command on the Visual C++
    Help menu, or open the Technical Support help file for more information
```

#### <a name="backend-code-generation-crash"></a>Awaria wewnętrznej bazy danych (Generowanie kodu)

Kod fazy generowania kompilatora odbywały się awarii wewnętrznej bazy danych. Zwykle, kompilator będzie emitować [krytyczny C1001 błąd](error-messages/compiler-errors-1/fatal-error-c1001.md)i nie może odwoływać się do pliku kodu źródłowego i skojarzone z tym problemem numer wiersza; często otrzymywane kompilatora pliku\\utc\\src\\p2\\main.c, ale można zignorować te dane.

Dla tego rodzaju awaria podaj [odtwarzania łącze](#link-repros) używasz generowanie kodu czasie konsolidowania (LTCG), włączenie przez **/GL** argument wiersza polecenia, aby cl.exe. Jeśli nie, podaj [wstępnie przetworzony odtwarzania](#preprocessed-repros) zamiast tego.

Oto przykładowe dane wyjściowe kompilatora dla wewnętrznej bazy danych o awariach, w której nie zastosowano LTCG. Jeśli dane wyjściowe kompilatora wygląda następująco należy podać [wstępnie przetworzony odtwarzania](#preprocessed-repros).

```Output
repro.cpp
\\officefile\public\tadg\vc14\comperror\repro.cpp(13) : fatal error C1001:
        An internal error has occurred in the compiler.
(compiler file 'f:\dd\vctools\compiler\utc\src\p2\main.c', line 230)
To work around this problem, try simplifying or changing the program near the
        locations listed above.
Please choose the Technical Support command on the Visual C++
Help menu, or open the Technical Support help file for more information
INTERNAL COMPILER ERROR in
        'C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\BIN\cl.exe'
    Please choose the Technical Support command on the Visual C++
    Help menu, or open the Technical Support help file for more information
```

Jeśli wiersz, rozpoczyna się od **wewnętrzny błąd KOMPILATORA** wspomniany link.exe zamiast cl.exe LTCG został włączony i należy podać [odtwarzania łącze](#link-repros). Jeśli jej nie jasne, czy LTCG został włączony z komunikatu o błędzie kompilatora, może być konieczne Sprawdź argumenty wiersza polecenia, które zostały skopiowane z kompilacji Zaloguj się w poprzednim kroku dla **/GL** argument wiersza polecenia.

#### <a name="linker-crash"></a>Awaria konsolidatora

Występują awarie konsolidatora w fazie tworzenia łącza po uruchomieniu kompilator. Zazwyczaj zostanie wyemitowany przez konsolidator [błąd narzędzi konsolidatora LNK1000](error-messages/tool-errors/linker-tools-error-lnk1000.md).

> [!NOTE]
> Dane wyjściowe wspomniany C1001 lub obejmuje generowanie kodu w czasie konsolidacji, zapoznaj się [(Generowanie kodu) w wewnętrznej bazie danych o awariach](#backend-code-generation-crash) zamiast tego uzyskać więcej informacji.

Dla tego rodzaju awaria podaj [odtwarzania łącze](#link-repros).

Oto przykładowe dane wyjściowe kompilatora dla tego rodzaju awaria.

```Output
z:\foo.obj : error LNK1000: Internal error during IMAGE::Pass2

  Version 14.00.22816.0

  ExceptionCode            = C0000005
  ExceptionFlags           = 00000000
  ExceptionAddress         = 00007FF73C9ED0E6 (00007FF73C9E0000)
        "z:\tools\bin\x64\link.exe"
  NumberParameters         = 00000002
  ExceptionInformation[ 0] = 0000000000000000
  ExceptionInformation[ 1] = FFFFFFFFFFFFFFFF

CONTEXT:

  Rax    = 0000000000000400  R8     = 0000000000000000
  Rbx    = 000000655DF82580  R9     = 00007FF840D2E490
  Rcx    = 005C006B006F006F  R10    = 000000655F97E690
  Rdx    = 000000655F97E270  R11    = 0000000000000400
  Rsp    = 000000655F97E248  R12    = 0000000000000000
  Rbp    = 000000655F97EFB0  E13    = 0000000000000000
  Rsi    = 000000655DF82580  R14    = 000000655F97F390
  Rdi    = 0000000000000000  R15    = 0000000000000000
  Rip    = 00007FF73C9ED0E6  EFlags = 0000000000010206
  SegCs  = 0000000000000033  SegDs  = 000000000000002B
  SegSs  = 000000000000002B  SegEs  = 000000000000002B
  SegFs  = 0000000000000053  SegGs  = 000000000000002B
  Dr0    = 0000000000000000  Dr3    = 0000000000000000
  Dr1    = 0000000000000000  Dr6    = 0000000000000000
  Dr2    = 0000000000000000  Dr7    = 0000000000000000
```

Jeśli łączenie przyrostowe jest włączone, a awaria wystąpił dopiero po pomyślnej łącze początkowej, (oznacza to, dopiero po pierwszej pełnej konsolidacji jest oparta kolejnych łączeń przyrostowych) podaj także kopię obiektu (.obj), a pliki biblioteki (lib) odnoszą się do plików źródłowych, które zostały zmodyfikowane po początkowej łącze zostało ukończone.

#### <a name="bad-code-generation"></a>Wygenerowanie złego kodu

Wygenerowanie złego kodu jest rzadkie, ale występuje, gdy kompilator generuje przez pomyłkę niepoprawny kod, który spowoduje, że aplikacja ulega awarii na środowiska uruchomieniowego zamiast wykrywania tego problemu w czasie kompilacji. Jeśli uważasz, że ten problem występuje wyniki w wygenerowanie złego kodu, raport będzie traktowany takie same [(Generowanie kodu) w wewnętrznej bazie danych o awariach](#backend-code-generation-crash).

Dla tego rodzaju awaria podaj [odtwarzania łącze](#link-repros) używasz generowanie kodu czasie konsolidowania (LTCG), włączenie przez **/GL** argument wiersza polecenia, aby cl.exe. Podaj [wstępnie przetworzony odtwarzania](#preprocessed-repros) w przeciwnym razie.

## <a name="how-to-generate-a-repro"></a>Sposób generowania odtwarzania

Aby pomóc nam śledzenie źródło problemu, [dobre odtwarzania](#what-makes-a-good-repro) jest istotne. Przed wykonaniem dowolnej czynności opisane poniżej dla określonych typów reprodukcje spróbuj zagęszczanie kod, który pokazuje, jak najszerzej problem. Spróbuj wyeliminować lub zminimalizować zależności, wymagane nagłówki i biblioteki i ograniczyć opcje kompilatora i definicje preprocesora używane, jeśli jest to możliwe.

Poniżej przedstawiono instrukcje dotyczące generowania różne rodzaje reprodukcje, które będą używane do różnych rodzajów problemów w raporcie.

### <a name="preprocessed-repros"></a>Wstępnie przetworzony reprodukcje

A *wstępnie przetworzony odtwarzania* jest plikiem jednego źródła, który demonstruje problem, wygenerowany z danych wyjściowych preprocesora C przy użyciu **/P** — opcja kompilatora na oryginalnego pliku źródłowego odtwarzania. Ta inlines uwzględniony w nagłówkach, można usunąć zależności na dodatkowe źródła i pliki nagłówkowe i rozwiązuje również makra, #ifdefs i innych poleceń preprocesora, zależnych środowisku lokalnym.

> [!NOTE]
> Wstępnie przetworzony reprodukcje nie są tak przydatne w przypadku problemów, które może być skutkiem błędów w naszej implementacji standardowej biblioteki, ponieważ firma Microsoft często chcą zastąpić naszej implementacji najnowsze, w toku, aby zobaczyć, czy już rozwiązaliśmy problem. W tym przypadku nie Przetwarzaj wstępnie odtwarzania, a jeśli nie można zmniejszyć problem z plikiem pojedyncze źródło pakietu kodu w pliku zip lub podobnych, lub rozważ zastosowanie odtworzenia projektu środowiska IDE. Aby uzyskać więcej informacji, zobacz [innych reprodukcje](#other-repros).

#### <a name="to-preprocess-a-source-code-file"></a>Można wstępnie przetworzyć plik kodu źródłowego

1. Przechwytywanie argumenty wiersza polecenia używane do konstruowania swoje odtwarzania, zgodnie z opisem w [zgłosić zawartość wiersza polecenia](#to-report-the-contents-of-the-command-line).

1. Otwórz **wiersz polecenia dla deweloperów** odpowiadającej architektury konfiguracji i wersji programu Visual Studio umożliwia kompilowanie projektu.

1. Przejdź do katalogu, zawierająca projekt Twojego odtwarzania.

1. W oknie konsoli wiersza polecenia dla deweloperów, wprowadź polecenie **cl /P** *argumenty* *filename.cpp*, gdzie *argumenty* jest Lista argumentów przechwycone powyżej, a *filename.cpp* to nazwa pliku źródłowego odtwarzania. To polecenie replikuje wiersza polecenia używane do odtworzenia, ale zatrzymuje kompilację po przebiegu preprocesora i generuje kod źródłowy wstępnie przetworzony do *filename*. mam.

Jeśli są przetwarzania wstępnego C + +/ CX pliku z kodem źródłowym, lub są za pomocą funkcji moduły języka C++, niektóre dodatkowe kroki są wymagane. Aby uzyskać więcej informacji zobacz sekcje poniżej.

Po wygenerowaniu wstępnie przetworzonego pliku, to dobry pomysł, aby upewnić się, że problem reprodukcje nadal przy użyciu wstępnie przetworzonego pliku.

#### <a name="to-confirm-that-the-error-still-repros-with-the-preprocessed-file"></a>Aby upewnić się, że błąd jest nadal reprodukcje przy użyciu wstępnie przetworzony plik

1. W oknie konsoli wiersza polecenia dla deweloperów, wprowadź polecenie **cl** *argumenty* **/TP** *filename*.i mówić cl.exe, aby skompilować wstępnie przetworzonego pliku jako pliku źródłowego języka C++, gdzie *argumenty* znajduje się lista argumentów przechwycone powyżej, ale także z dowolnymi **/D** i **/I** argumenty usunięte (ponieważ już zostały umieszczone w pliku wstępnie przetworzony); i gdzie *filename*.i jest nazwę wstępnie przetworzonego pliku.

1. Upewnij się, że problem jest przedstawiony.

Na koniec dołączyć wstępnie przetworzony odtwarzania *filename*.i do raportu.

### <a name="preprocessed-ccx-winrtuwp-code-repros"></a>Wstępnie przetworzony C + +/ CX WinRT/UWP kodu reprodukcje

Jeśli używasz języka C + +/ CX, aby utworzyć plik wykonywalny, istnieją pewne dodatkowe kroki wymagane do tworzenia i sprawdzania poprawności wstępnie przetworzony odtwarzania.

#### <a name="to-preprocess-ccx-source-code"></a>Można wstępnie przetworzyć C + +/ CX kodu źródłowego

1. Utwórz plik wstępnie przetworzone źródło, zgodnie z opisem w [można wstępnie przetworzyć plik kodu źródłowego](#to-preprocess-a-source-code-file).

1. Wyszukaj wygenerowany _filename_pliku .i **#using** dyrektywy.

1. Sporządź listę wszystkich plików, do którego istnieje odwołanie. Opuść wszelkie Windows\*pliki .winmd, pliki platform.winmd i mscorlib.dll.

Aby przygotować się do zweryfikowania, że wstępnie przetworzony plik nadal odtwarza ten problem,

1. Utwórz nowy katalog dla wstępnie przetworzony plik i skopiuj go do nowego katalogu.

1. Skopiuj pliki .winmd z Twojej **#using** listy do nowego katalogu.

1. Utwórz plik vccorlib.h pusty w nowym katalogu.

1. Edytuj wstępnie przetworzony plik, aby usunąć dowolny **#using** dyrektywy dla biblioteki mscorlib.dll.

1. Edytuj plik wstępnie przetworzony, aby zmienić żadnych ścieżek bezwzględnych tylko bez nazwy plików dla plików skopiowanych winmd.

Upewnij się, że wstępnie przetworzony plik nadal odtwarza ten problem, jak powyżej.

### <a name="preprocessed-c-modules-repros"></a>Wstępnie przetworzony reprodukcje moduły języka C++

Jeśli używasz funkcji modułów kompilatora C++ istnieją wykonanie innych czynności wymagane do tworzenia i sprawdzania poprawności wstępnie przetworzony odtwarzania.

#### <a name="to-preprocess-a-source-code-file-that-uses-a-module"></a>Można wstępnie przetworzyć pliku kodu źródłowego, który używa modułu

1. Przechwytywanie argumenty wiersza polecenia używane do konstruowania swoje odtwarzania, zgodnie z opisem w [zgłosić zawartość wiersza polecenia](#to-report-the-contents-of-the-command-line).

1. Otwórz **wiersz polecenia dla deweloperów** odpowiadającej architektury konfiguracji i wersji programu Visual Studio umożliwia kompilowanie projektu.

1. Przejdź do katalogu, zawierająca projekt Twojego odtwarzania.

1. W oknie konsoli wiersza polecenia dla deweloperów, wprowadź polecenie **cl /P** *argumenty* *filename.cpp*, gdzie *argumenty* jest Lista argumentów przechwycone powyżej, i *filename.cpp* to nazwa pliku źródłowego, który korzysta z modułu.

1. Przejdź do katalogu, zawierającego projekt odtwarzania z wbudowanej interfejsu modułu (dane wyjściowe .ifc).

1. Przechwyć argumenty wiersza polecenia używane do tworzenia interfejsu modułu.

1. W oknie konsoli wiersza polecenia dla deweloperów, wprowadź polecenie **cl /P** *argumenty* *modulename.ixx*, gdzie *argumenty* jest Lista argumentów przechwycone powyżej, a *modulename.ixx* to nazwa pliku który jest tworzony interfejs modułu.

Po wygenerowaniu wstępnie przetworzonych plików, to dobry pomysł, aby upewnić się, że problem reprodukcje nadal przy użyciu wstępnie przetworzonego pliku.

#### <a name="to-confirm-that-the-error-still-repros-with-the-preprocessed-file"></a>Aby upewnić się, że błąd jest nadal reprodukcje przy użyciu wstępnie przetworzony plik

1. W oknie konsoli dewelopera zmiany do katalogu zawierającego projekt odtwarzania.

1. Wprowadź polecenie **cl** *argumenty* **/TP** *filename*.i opisanych powyżej, aby skompilować wstępnie przetworzony plik tak, jakby była pliku źródłowego języka C++.

1. Upewnij się, że problem nadal jest przedstawiony przez wstępnie przetworzony plik.

Na koniec dołączania plików wstępnie przetworzony odtwarzania (*filename*.i i *modulename*.i) wraz z danych wyjściowych .ifc do raportu.

### <a name="link-repros"></a>Reprodukcje łącza

A *link odtwarzania* jest generowanych przez konsolidator zawartość katalogu określonego przez **łącze\_odtwarzania** zmiennej środowiskowej. Zawiera ona artefaktów kompilacji, które wspólnie pokazują problem występujący w czasie łącze, na przykład awarię wewnętrznej bazy danych obejmujące generowanie kodu czasie konsolidowania (LTCG) lub awarii konsolidatora. Te artefakty kompilacji mogą wymaganiom konsolidatora danych wejściowych, dzięki czemu można odtworzyć problem. Odtwórz łącza można utworzyć łatwo za pomocą tej zmiennej środowiskowej umożliwiające odtwarzania wbudowane możliwości generowania konsolidator.

#### <a name="to-generate-a-link-repro"></a>Aby wygenerować odtwarzania łącza

1. Przechwytywanie argumenty wiersza polecenia używane do konstruowania swoje odtwarzania, zgodnie z opisem w [zgłosić zawartość wiersza polecenia](#to-report-the-contents-of-the-command-line).

1. Otwórz **wiersz polecenia dla deweloperów** odpowiadającej architektury konfiguracji i wersji programu Visual Studio umożliwia kompilowanie projektu.

1. W oknie konsoli wiersza polecenia dla deweloperów przejdź do katalogu, zawierająca projekt Twojego odtwarzania.

1. Wprowadź **mkdir linkrepro** można utworzyć katalogu frazy odtwarz łącza.

1. Wprowadź polecenie **Ustaw link\_odtwarzania = linkrepro** można ustawić **łącze\_odtwarzania** zmiennej środowiskowej do katalogu, który został właśnie utworzony. Jeśli kompilacja jest uruchamiana z innego katalogu, jak często w przypadku bardziej złożonych projektów, wartość **łącze\_odtwarzania** na pełną ścieżkę do katalogu linkrepro zamiast tego.

1. Aby skompilować projekt odtwarzania w programie Visual Studio w oknie konsoli wiersza polecenia dla deweloperów, wprowadź polecenie **devenv**. Gwarantuje to, że wartość **łącze\_odtwarzania** zmienna środowiskowa jest widoczny dla programu Visual Studio. Aby skompilować projekt w wierszu polecenia, użyj argumentów wiersza polecenia, przechwycenie powyżej zduplikowane kompilacji odtwarzania.

1. Kompilowanie projektu odtwarzania i upewnij się, że wystąpił problem oczekiwane.

1. Zamknij program Visual Studio, jeśli używasz do przeprowadzania kompilacji.

1. W oknie konsoli wiersza polecenia dla deweloperów, wprowadź polecenie **Ustaw link\_odtwarzania =** wyczyść **łącze\_odtwarzania** zmiennej środowiskowej.

Na koniec pakiet odtwarzania poprzez kompresowanie całego linkrepro katalogu do pliku zip lub podobne i dołączyć go do raportu.

### <a name="other-repros"></a>Inne reprodukcje

Jeśli problem nie można zmniejszyć do pojedynczego źródła pliku lub odtworzenia wstępnie przetworzony, a problem nie wymaga odtwarzania łącze, firma Microsoft można zbadać projektu środowiska IDE. Wszystkie wskazówki dotyczące sposobu tworzenia dobrych odtwarzania jest nadal obowiązuje ograniczenie; Kod powinien być minimalna i niezależna, problem w przypadku wystąpienia w nasze najnowsze narzędzia i jeśli to stosowne, problem nie może być traktowany w innych kompilatorach.

Utwórz swoje odtwarzania jako projektu minimalnego środowiska IDE, a następnie spakujesz ją poprzez kompresowanie całej struktury katalogów w pliku zip lub podobne i dołączyć go do raportu.

## <a name="ways-to-send-your-report"></a>Sposoby, aby wysłać raport

Istnieje kilka sposobów uzyskać raport z nami. Można użyć wbudowanego programu Visual Studio [narzędzia Zgłoś Problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017), lub [społeczności deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/) stron. Można również uzyskać bezpośrednio do naszej społeczności deweloperów stron, wybierając **opinie o produkcie** znajdujący się u dołu tej strony. Wybór zależy, czy chcesz użyć narzędzia, wbudowanego w IDE do przechwytywania zrzutów ekranu i organizowanie raport do ogłaszania na stronach społeczności deweloperów, czy wolisz korzystać bezpośrednio z witryny internetowej.

> [!NOTE]
> Niezależnie od tego, jak możesz przesłać raport firma Microsoft szanuje Twoją prywatność. Firma Microsoft poświęca zgodności ze wszystkimi prawem ochrony danych i przepisów. Aby dowiedzieć się, jak będzie traktowany jak dane, które możesz wysłać do nas, zobacz [zasady zachowania poufności informacji firmy Microsoft](https://privacy.microsoft.com/privacystatement).

### <a name="use-the-report-a-problem-tool"></a>Raport narzędzia Problem

**Zgłoś Problem** narzędzia w programie Visual Studio jest sposobem użytkowników programu Visual Studio zgłosić szereg problemów za pomocą kilku kliknięć. Zapewnia prosty formularz, który służy do określania szczegółowe informacje dotyczące problemów, które wystąpiły, a następnie przesłać raport bez opuszczania środowiska IDE.

Zgłoszenie problemu za pomocą **Zgłoś Problem** narzędzie to można łatwo i wygodnie z poziomu środowiska IDE. Dostęp z paska tytułu, wybierając **Wyślij opinię** ikona obok pozycji **Szybkie uruchamianie** pola wyszukiwania, lub można znaleźć na pasku menu w **pomocy**  >  **Wyślij opinię** > **Zgłoś Problem**.

Po wybraniu opcji Zgłoś problem najpierw wyszukać społeczności deweloperów dla podobne problemy. Jeśli problem został zgłoszony, Zagłosuj temat i dodać komentarze o dodatkowe charakterystyce. Jeśli nie widzisz podobny problem, wybierz opcję **Zgłoś nowy problem** znajdujący się w dolnej części okna dialogowego programu Visual Studio Feedback i postępuj zgodnie z instrukcjami, aby zgłosić problem.

### <a name="use-the-visual-studio-developer-community-pages"></a>Użyj stron społeczności deweloperów programu Visual Studio

Strony społeczności deweloperów programu Visual Studio są innego wygodny sposób, aby zgłosić problemy i rozwiązania dla programu Visual Studio, kompilator języka C++, narzędzi i bibliotek. [Visual Studio pytania](https://developercommunity.visualstudio.com/spaces/8/index.html) strona to miejsce zgłosić problemy ze środowiskiem IDE lub instalacji. W przypadku problemów przy użyciu kompilatora, konsolidatora i innych narzędzi i bibliotek C++ [pytania C++](https://developercommunity.visualstudio.com/spaces/62/index.html) strony.

W społeczności deweloperów Baner u góry każdej strony jest pole wyszukiwania, używanej do znalezienia wpisy lub tematów, które zgłaszanie problemów podobnej do Twojej. Może się okazać rozwiązania lub inne przydatne informacje dotyczące tego problemu jest już dostępny w istniejącej tematu. Jeśli ktoś zgłosił ten sam problem, przed, Zagłosuj i komentarza, w tym temacie zamiast tworzyć nowy raport o problemie.

Jeśli problem nie został zgłoszony przed, wybierz opcję **Zgłoś problem** przycisk znajdujący się obok pola wyszukiwania na stronie społeczności deweloperów. Może być konieczne podanie do logowania się na swoje konto programu Visual Studio i zaakceptowanie przypisać społeczność deweloperów aplikacji dostęp do Twojego profilu. Gdy użytkownik jest zalogowany, możesz przejść bezpośrednio do strony gdzie możesz zgłosić problem. Może zawierać kod odtwarzania i wiersza polecenia, zrzuty ekranu, linki do pokrewnych dyskusjami i inne informacje, które Twoim zdaniem są istotne i przydatne.

> [!TIP]
> Dla innych rodzajów problemy mogą wystąpić w programie Visual Studio, które nie są związane z zestawu narzędzi (na przykład interfejsu użytkownika problemy, uszkodzenie funkcjonalności środowiska IDE lub awarie ogólne), **narzędzia Zgłoś Problem** może być szczególnie przydatne termin choice do jego zrzut ekranu wystąpiły funkcje i możliwości rekordu działania interfejsu użytkownika, które mogą prowadzić do problemu. Te rodzaje błędów mogą być również zgłaszane na [społeczności deweloperów](https://developercommunity.visualstudio.com/) lokacji.

### <a name="reports-and-privacy"></a>Raporty i ochrona prywatności

Domyślnie **wszystkie informacje w raportach i wszelkie komentarze i odpowiedzi są publicznie widoczne**. Zazwyczaj jest to korzyść, ponieważ zezwala ona na całej społeczności, aby wyświetlić problemy, rozwiązania i rozwiązania, które znaleziono innym użytkownikom. Jednak jeśli interesujące Cię ujawnianie Twoje dane lub tożsamość, dla prywatności lub z przyczyn własności intelektualnej, dostępne opcje.

Jeśli masz obawy przedstawiania swoją tożsamość, [Utwórz nowe konto Microsoft](https://signup.live.com/) nie ujawnia żadnych informacji o Tobie. Aby utworzyć raport, należy użyć tego konta. 

**Nie umieszczaj coś, co chcesz przechowywać prywatne w ramach tytułu lub zawartości elementu początkowego raportu, który nie jest publiczny.** Zamiast tego należy pamiętać, że szczegółów będzie wysyłać prywatnie w komentarzu do oddzielnych. Aby upewnić się, że raport jest kierowany do odpowiednich osób, obejmują **cppcompiler** w temacie Lista raport o problemie. Po utworzeniu raport o problemie, jest teraz możliwość określenia, kto może wyświetlać odpowiedzi i załączników.

#### <a name="to-create-a-problem-report-for-private-information"></a>Aby utworzyć raport o problemie informacji prywatnych

1. W raporcie, możesz utworzyć, wybierz **Dodaj komentarz** do utworzenia prywatnej opis problemu.

1. W edytorze odpowiedzi, należy użyć z rozwijanej listy formantów poniżej **przesyłania** i **anulować** przycisków, aby określić odbiorców w odpowiedzi. Tylko osoby, które określisz zobaczyć te prywatnej odpowiedzi i obrazów, łącza lub kod, który należy uwzględnić w nich. Wybierz **Viewable moderatorzy i oryginalnego plakat** Aby ograniczyć widoczność, aby pracownicy firmy Microsoft i samodzielnie.

1. Dodaj opis i wszelkie inne informacje, obrazy i załączniki plików potrzebnych do odtworzenia usługi. Wybierz **przesyłania** przycisk, aby wysyłać tych informacji przez użytkowników.

   Należy pamiętać, że jest ograniczona do 2GB dla dołączonych plików i maksymalnie 10 plików. Wszelkie większych przekazywania należy żądać adres URL przekazywania w komentarzu do prywatnego.

Wszystkie odpowiedzi w ramach tego komentarza ma taką samą widoczność ograniczone, wskazana. Ta zasada obowiązuje, nawet wtedy, gdy kontrolka listy rozwijanej w odpowiedzi nie pokazuje stan widoczności ograniczeniami poprawnie.

Ochrona prywatności i przechowywać poufne informacje z widoku publicznego, należy uważać, aby zachować wszystkie interakcje z firmą Microsoft do odpowiedzi w obszarze ograniczone komentarz. Odpowiadanie na komentarze innych może spowodować przypadkowe ujawnienie poufnych informacji.

## <a name="how-to-report-a-c-documentation-issue"></a>Jak zgłosić problem z dokumentacją języka C++

Problemy usługi GitHub są używane do śledzenia problemów zgłaszanych w naszej dokumentacji. Teraz można utworzyć usługi GitHub problemów bezpośrednio ze strony zawartości, dzięki czemu można wchodzić w interakcje w sposób znacznie bogatsze ze autorzy i zespołach produktu. Jeśli widzisz wystąpił problem z dokumentu, próbkę błędnym kodem, wyjaśnienie mylące, krytyczne pominięcie lub nawet po prostu błąd pisowni, możesz łatwo dać nam znać. Przewiń ekran do dolnej części strony i wybierz pozycję **Zaloguj się przekazać opinię dotyczącą dokumentacji**. Musisz utworzyć konto w usłudze GitHub, jeśli nie masz jeszcze takiego, ale po wykonaniu tej czynności możesz zobaczyć wszystkie problemy dotyczące naszej dokumentacji, ich stan i Otrzymuj powiadomienia, gdy zostaną wprowadzone zmiany do problemu, który zgłoszone przez Ciebie. Aby uzyskać więcej informacji, zobacz [nowe opinii pojawi się System docs.microsoft.com](/teamblog/a-new-feedback-system-is-coming-to-docs).

Po utworzeniu problem z dokumentacją w serwisie GitHub, korzystając z przycisku opinii dokumentacji problem zostanie automatycznie wypełniona niektóre informacje na temat strony, w której utworzono ten problem, aby było wiadomo, gdzie znajduje się problem. Nie Edytuj te informacje. Po prostu Dołącz szczegóły na temat co to jest problem i, jeśli chcesz sugerowanej poprawki. [Nasza dokumentacja jest typu open source](https://github.com/MicrosoftDocs/cpp-docs/), więc jeśli chcesz faktycznie wprowadzić poprawkę i proponuje samodzielnie, możesz to zrobić. Aby uzyskać więcej informacji na temat sposobu współtworzenia naszej dokumentacji, zobacz nasze [przewodnik Dodawanie](https://github.com/MicrosoftDocs/cpp-docs/blob/master/CONTRIBUTING.md) w witrynie GitHub.

