---
title: Jak zgłosić problem z zestawu narzędzi Visual C++ | Dokumentacja firmy Microsoft
ms.date: 5/11/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0044a0da7b1ac4ad052eb120ccfb1f7425d2c0e
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34336336"
---
# <a name="how-to-report-a-problem-with-the-visual-c-toolset-or-documentation"></a>Jak zgłosić problem z zestawu narzędzi Visual C++ lub dokumentacji

Jeśli wystąpią problemy z kompilator Microsoft Visual C++, konsolidatora, lub inne narzędzia i biblioteki chcemy się dowiedzieć się o nich. Problem znajduje się w naszej dokumentacji, chcemy się dowiedzieć, zbyt.

## <a name="how-to-report-a-c-toolset-issue"></a>Jak zgłosić problem zestawu narzędzi języka C++

Najlepszy sposób, aby poinformować nas o problemie jest aby wysłać nam raport zawierający opis problemu został napotkany szczegółowe informacje o, jak w przypadku tworzenia programu, a *reprodukcja*, pełną przypadek testowy, możemy użyć do odtworzenia problem na własnych maszynach. Te informacje ułatwiają szybko sprawdzić, czy problem istnieje w naszym kodzie i nie jest lokalny dla danego środowiska, aby ustalić, czy ma to wpływ na inne wersje kompilatora i zdiagnozować jego przyczyna.

W poniższych sekcjach będzie temat co sprawia, że raport dobrej, sposób generowania reprodukcja dla rodzaju problem, które zostały znalezione i jak wysłać raport do zespołu produktu. Raporty są ważne dla nas i innymi deweloperami jak. Dziękujemy za pomoc nam w ulepszeniu programu Visual C++!

## <a name="how-to-prepare-your-report"></a>Jak przygotować raport

Tworzenie raportu wysokiej jakości jest ważne, ponieważ jest bardzo trudne do odtworzenia problemu, który napotkał na własnych maszynach bez pełne informacje. Jest raport lepsze, im bardziej efektywnie jesteśmy stanie Utwórz i zdiagnozować problem.

Co najmniej powinna zawierać raportu

- Informacje o wersji pełny zestaw narzędzi, którego używasz.

- Cl.exe pełny wiersz polecenia używany do tworzenia kodu.

- Szczegółowy opis napotkany problem.

- Reprodukcja: przykładowego kodu źródłowego pełną, uproszczona, niezależna demonstrujący problem.

W dalszej Dowiedz się więcej o konkretnych informacji, musimy i gdzie można znaleźć, a także tworzenie dobrej reprodukcja.

### <a name="the-toolset-version"></a>Wersja zestawu narzędzi

Potrzebujemy informacji pełnej wersji i Architektura docelowa zestawu narzędzi przyczyną problemu, aby Twoje reprodukcja względem tego samego zestawu narzędzi można było przetestować na naszych maszyny. Jeśli firma Microsoft może odtworzyć problem, te informacje udostępnia także punkt wyjścia do badania które inne wersje zestawu narzędzi zawiera ten sam problem.

#### <a name="to-report-the-full-version-of-the-compiler-youre-using"></a>Do pełnej wersji kompilatora, którego używasz raportu

1. Otwórz **wiersza polecenia dewelopera** odpowiadającego architektura konfiguracji i wersji programu Visual Studio używany do tworzenia projektu. Na przykład w przypadku tworzenia przy użyciu programu Visual Studio 2017 na x64 x64 wybierz elementy docelowe, **x64 natywnego narzędzia wiersza polecenia VS 2017**. Aby uzyskać więcej informacji, zobacz [skrótów wiersza polecenia dewelopera](build/building-on-the-command-line.md#developer-command-prompt-shortcuts).

1. W oknie konsoli dewelopera wiersza polecenia, wpisz polecenie **cl /Bv**.

Dane wyjściowe powinny wyglądać podobnie do poniższego:

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

Skopiuj i Wklej całego dokumentu w raporcie.

### <a name="the-command-line"></a>W wierszu polecenia

Potrzebujemy dokładny wiersz polecenia (cl.exe i wszystkie argumenty) używany do tworzenia kodu, dzięki czemu można oprzemy się go w taki sam sposób na naszych maszyny. Jest to ważne, ponieważ został napotkany problem może istnieć tylko podczas kompilowania z określonego argumentu lub kombinacja argumentów.

Dziennik kompilacji jest najlepszym miejscem, aby znaleźć te informacje bezpośrednio po ten problem. Dzięki temu, że wiersz polecenia zawiera dokładnie te same argumenty, które mogą przyczyniać się do problemu.

#### <a name="to-report-the-contents-of-the-command-line"></a>Aby zgłosić zawartość wiersza polecenia

1. Zlokalizuj **CL.command.1.tlog** pliku i otwórz go. Domyślnie ten plik znajduje się w folderze dokumenty w \\programu Visual Studio *wersji*\\projekty\\*Nazwa rozwiązania* \\ *ProjectName*\\*konfiguracji*\\*ProjectName*.tlog\\CL.command.1.tlog, lub w folderze użytkownika w obszarze \\Źródła\\repozytoriów\\*Nazwa rozwiązania*\\*ProjectName*\\*konfiguracji* \\ *ProjectName*.tlog\\CL.command.1.tlog. Jeśli używasz innej system kompilacji lub zmiana domyślnej lokalizacji dla projektu może być w innej lokalizacji.

   Wewnątrz tego pliku znajdują się nazwy plików kodu źródłowego, a następnie używana do kompilowania nimi w osobnych wierszach argumenty wiersza polecenia.

1. Odszukaj wiersz, który zawiera nazwę pliku źródła kodu, w którym występuje problem; wiersz poniżej zawiera odpowiednie argumenty polecenia cl.exe.

Skopiuj i Wklej pełny wiersz polecenia w raporcie.

### <a name="a-description-of-the-problem"></a>Opis problemu

Potrzebujemy, aby uzyskać szczegółowy opis problemu, który został napotkano, dzięki czemu można sprawdzić, czy widzimy ten sam efekt na naszych maszyny; jego również czasami przydatne firmie Microsoft w celu próbowano wykonać, a oczekiwano niepożądane.

Podaj **dokładne komunikaty o błędach** podane przez zestaw narzędzi lub dokładną działanie zostanie wyświetlony. Potrzebujemy tych informacji, aby sprawdzić, czy możemy zostały prawidłowo odtworzyć problem. Dołącz **wszystkie** danych wyjściowych kompilatora nie tylko ostatni komunikat o błędzie. Potrzebujemy wyświetlić wszystkie elementy, które doprowadziły do problemu, który można raportować. Jeśli ten problem można duplikować przy użyciu kompilatora wiersza polecenia, że dane wyjściowe kompilatora jest preferowana; IDE i innych systemów kompilacji mogą filtrować komunikaty o błędach Zobacz lub przechwytywać tylko pierwszego wiersza komunikatu o błędzie.

Jeśli problem jest, że kompilator akceptuje nieprawidłowy kod i nie generuje diagnostyki, zwróć uwagę na to w raporcie.

Aby zgłosić problem zachowanie środowiska uruchomieniowego obejmują **dokładnie kopiowania** program drukuje i powinny być widoczne. Najlepiej, jeśli to jest osadzony w danych wyjściowych instrukcji, na przykład `printf("This should be 5: %d\n", actual_result);`. Jeśli program ulegnie awarii, zawiesza się mówią, że również.

Dodaj inne szczegóły, które mogą pomóc nam zdiagnozować problem, który wystąpił, takich jak dowolnego obejść znalezionego może. Należy unikać powtarzania informacje znajdujące się w innym miejscu w raporcie.

### <a name="the-repro"></a>Reprodukcja

Reprodukcja podano przykładowy kod źródłowy kompletny, niezależny odtwarzalnie demonstrujący problem już wystąpił (stąd nazwa). Potrzebujemy reprodukcja, dzięki czemu możemy odtwarzania błędu na naszych maszyny. Kod powinien być wystarczające samodzielnie utworzyć prosty plik wykonywalny, który kompiluje i uruchamia lub czy skompilować i uruchomić w przeciwnym razie problemu, które zostały znalezione. Reprodukcja nie jest fragment kodu; powinien mieć pełną funkcje i klas i zawiera wszystkie niezbędne # dyrektyw, nawet w przypadku standardowych nagłówków include.

#### <a name="what-makes-a-good-repro"></a>Co sprawia, że reprodukcja dobra

Dobrym reprodukcja jest:

- **Minimalny.** Reprodukcje powinien być możliwie jak najmniejszy jeszcze nadal pokazują napotkany problem. Reprodukcje musi być złożony lub realistyczne; potrzebna jest tylko do wyświetlenia kodu, który odpowiada standardowej implementacji kompilatorem udokumentowany lub w przypadku braku diagnostycznych, kod, który nie jest zgodna. Najlepiej nadają się proste, aby punkt reprodukcje zawierających wystarczającego kod, aby zademonstrować problem. Jeśli można wyeliminować lub uprościć kod i pozostają zgodność i pozostanie bez zmian problem, należy to zrobić. Nie trzeba przeprowadzać obejmują zaradczych przykłady kodu, który działa.

- **Self-Contained.** Reprodukcje Unikaj niepotrzebnych zależności. Jeśli można odtworzyć problem bez bibliotek innych firm, należy to zrobić. Jeśli można odtworzyć problem bez dowolny kod biblioteki oprócz instrukcje prosty wyjściowy (na przykład `puts("this shouldn't compile");`, `std::cout << value;`, i `printf("%d\n", value);` zgadzasz), należy to zrobić. Jest idealne rozwiązanie w przykładzie można zmniejszenia do pliku kodu jednego źródła bez odwołania do żadnych nagłówków użytkownika. Zmniejszenie ilości kodu, który mamy można rozważyć jako możliwych współtwórca tego problemu jest enormously NAS.

- **W najnowszej wersji kompilatora.** Reprodukcje należy używać najnowszej aktualizacji do najnowszej wersji zestawu narzędzi lub najnowszej wersji wstępnej Następna aktualizacja lub kolejna główna wersja, jeśli to możliwe. Bardzo często Naprawiono problemów, które mogą wystąpić w starszych wersjach zestawu narzędzi w nowszej wersji. Poprawki są backported do starszych wersji tylko w wyjątkowych okolicznościach.

- **Sprawdza, czy inne kompilatory** w razie potrzeby. Reprodukcje obejmujących przenośnego kodu C++ powinien sprawdzić zachowanie przed inne kompilatory, jeśli to możliwe. Standardowe określa poprawność programu i kompilator nie jest to doskonałe rozwiązanie, ale podczas Clang oraz GCC zaakceptować kodu bez Diagnostyka, a nie jest MSVC, istnieje duże prawdopodobieństwo, patrzy na usterkę w naszym kompilatora. (Inne możliwości obejmują różnic działania systemu Unix i systemu Windows lub różne poziomy implementacji standardów języka C++ i tak dalej). Z drugiej strony wszystkie kompilatory odrzucenia kodu, następnie jest prawdopodobne, że kod jest nieprawidłowa. Wyświetlanie różnych komunikatów o błędach mogą pomóc zdiagnozować problem samodzielnie.

   Można znaleźć listy online kompilatory do testowania kodu przed w [kompilatory Online C++](https://isocpp.org/blog/2013/01/online-c-compilers) ISO C++ witryny sieci Web lub to wyselekcjonowanych [listy kompilatory C++ Online](https://arnemertz.github.io/online-compilers/) w witrynie GitHub. Oto kilka przykładów obejmują [Wandbox](https://wandbox.org/), [Explorer kompilatora](https://godbolt.org/), i [Coliru](http://coliru.stacked-crooked.com/).

   > [!NOTE]
   > Kompilator online witryny sieci Web nie są powiązane z firmą Microsoft. Wiele witryn sieci Web online kompilatora są uruchamiane jako osobiste projektów, a niektóre z tych witrynach mogą być niedostępne po to odczytu, ale wyszukiwania stwierdzi, że inne osoby, których można używać.

Problemy z kompilatora, konsolidatora i w bibliotekach, często pojawiają się w szczególności sposobów. Rodzaju problemy, które wystąpią określi, jakiego rodzaju reprodukcja należy uwzględnić w raporcie. Bez odpowiedniego reprodukcja nie mamy nic do badania. Poniżej przedstawiono niektóre rodzaje problemów, które mogą zobaczyć i instrukcje dotyczące generowania rodzaje reprodukcje musi być używane do zgłaszania każdego rodzaju problemów.

#### <a name="frontend-parser-crash"></a>Awaria serwera sieci Web (analizator)

Awarie frontonu wystąpić podczas fazy analizy kompilatora. Zazwyczaj kompilator będzie emitować [krytyczny błąd C1001](error-messages/compiler-errors-1/fatal-error-c1001.md) i referencyjne źródła plików i wierszy kod na którym wystąpił błąd; często zaznaczyć msc1.cpp pliku, ale możesz zignorować ten szczegółów.

Dla tego typu awarii (Crash), podaj [wstępnie przetworzony reprodukcja](#preprocessed-repros).

Oto przykładowe dane wyjściowe kompilatora dla tego typu awarii (Crash):

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

#### <a name="backend-code-generation-crash"></a>Awaria wewnętrznej bazy danych (generowania kodu)

Występują awarie wewnętrznej bazy danych podczas kodu generowania faza kompilatora. Zazwyczaj kompilator będzie emitować [krytyczny błąd C1001](error-messages/compiler-errors-1/fatal-error-c1001.md)i nie może być odwoływania się do pliku kodu źródłowego i skojarzone z tym problemem numer wiersza; często zaznaczyć kompilatora pliku\\utc\\src\\p2\\main.c, ale można zignorować ten szczegółów.

Dla tego typu awarii (Crash), podaj [reprodukcja łącze](#link-repros) Jeśli używasz łącza — czas generowania kodu (LTCG), są włączane przez **/GL** cl.exe argument wiersza polecenia. Jeśli nie, Dodaj [wstępnie przetworzony reprodukcja](#preprocessed-repros) zamiast tego.

Oto przykładowe dane wyjściowe kompilatora dla awarii wewnętrznej bazy danych, w którym LTCG nie jest używany. Jeśli dane wyjściowe kompilatora wygląda następująco należy zapewnić [wstępnie przetworzony reprodukcja](#preprocessed-repros).

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

Jeśli wiersz, który rozpoczyna się **wewnętrzny błąd KOMPILATORA** wymienia link.exe zamiast cl.exe, LTCG został włączony i powinien zawierać [reprodukcja łącze](#link-repros). Jeśli nie jest on jasne, czy LTCG została włączona w komunikacie o błędzie kompilatora, konieczne może być zbadać dziennika argumenty wiersza polecenia, które zostały skopiowane z kompilacji w poprzednim kroku dla **/GL** argumentu wiersza polecenia.

#### <a name="linker-crash"></a>Awaria konsolidatora

Awarie konsolidatora występują w fazie połączeń, po uruchomieniu przez kompilator. Zazwyczaj będzie emitować konsolidator [błąd narzędzi konsolidatora LNK1000](error-messages/tool-errors/linker-tools-error-lnk1000.md).

> [!NOTE]
> Jeśli dane wyjściowe wymienia C1001 lub obejmuje generowanie kodu w czasie konsolidacji, zapoznaj się [awarii wewnętrznej bazy danych (generowania kodu)](#backend-code-generation-crash) zamiast niego uzyskać więcej informacji.

Dla tego typu awarii (Crash), podaj [reprodukcja łącze](#link-repros).

Oto przykładowe dane wyjściowe kompilatora dla tego typu awarii (Crash).

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

Jeśli konsolidowania przyrostowego jest włączona i awarii wystąpił dopiero po pomyślnym łącze początkowej, (oznacza to, że tylko po pierwszym pełnej konsolidacji jest oparty kolejnych konsolidowania przyrostowego) Podaj również kopię obiektu (.obj) i pliki biblioteki (lib) odpowiadają plików źródłowych, które zostały zmodyfikowane po początkowej łącze zostało ukończone.

#### <a name="bad-code-generation"></a>Wygenerowanie złego kodu

Wygenerowanie złego kodu jest rzadko, ale występuje, gdy kompilator generuje przez pomyłkę niepoprawny kod, który spowoduje, że aplikacja do awarii na środowisko uruchomieniowe nie wykrycia tego problemu w czasie kompilacji. Jeśli podejrzewasz problem występuje wyniki w wygenerowanie złego kodu, raport będzie traktowany takie same [awarii wewnętrznej bazy danych (generowania kodu)](#backend-code-generation-crash).

Dla tego typu awarii (Crash) podaj [reprodukcja łącze](#link-repros) korzystając z łącza — czas generowania kodu (LTCG), są włączane przez **/GL** cl.exe argument wiersza polecenia. Podaj [wstępnie przetworzony reprodukcja](#preprocessed-repros) , jeśli nie.

## <a name="how-to-generate-a-repro"></a>Sposób generowania reprodukcja

Aby pomóc nam śledzenie źródło problemu, [reprodukcja dobrej](#what-makes-a-good-repro) jest ważna. Przed wykonaniem tych kroków opisanych poniżej dla określonych rodzajów reprodukcje spróbuj zmniejszyć kod, który demonstruje możliwie problem. Spróbuj wyeliminować lub zminimalizować zależności, wymagane nagłówków i bibliotek i ograniczyć opcje kompilatora i definicje preprocesora używane, jeśli to możliwe.

Poniżej znajdują się instrukcje dotyczące generowania różne rodzaje reprodukcje, które będą używane do raportu różne rodzaje problemów.

### <a name="preprocessed-repros"></a>Wstępnie przetworzony reprodukcje

A *wstępnie przetworzony reprodukcja* jest jednym pliku źródłowym demonstrujący problem, wygenerowany z danych wyjściowych preprocesora C za pomocą **/P** dla oryginalnego pliku źródłowego reprodukcja — opcja kompilatora. Tego inlines zawarta nagłówków, aby usunąć zależności dodatkowe źródła i pliki nagłówkowe, a także rozpoznaje makra, #ifdefs i innych poleceń preprocesora, zależne środowisku lokalnym.

> [!NOTE]
> Wstępnie przetworzony reprodukcje nie są jako przydatne w przypadku problemów, które może być skutkiem błędów w naszym implementacji biblioteki standardowej, ponieważ firma Microsoft będzie często mają zostać podstawione naszych najnowsze, trwa implementacji, aby zobaczyć, czy już problem został rozwiązany problem. W takim przypadku nie Przetwarzaj wstępnie reprodukcja i nie można zmniejszyć problem z plikiem jednego źródła pakietu kodu do pliku zip lub podobne, czy należy rozważyć użycie reprodukcja projektu IDE. Aby uzyskać więcej informacji, zobacz [innych reprodukcje](#other-repros).

#### <a name="to-preprocess-a-source-code-file"></a>Aby przetwarzanie wstępne pliku kodu źródłowego

1. Przechwyć argumenty wiersza polecenia używany do tworzenia sieci reprodukcja zgodnie z opisem w [zgłoszenia zawartość wiersza polecenia](#to-report-the-contents-of-the-command-line).

1. Otwórz **wiersza polecenia dewelopera** odpowiadającego architektura konfiguracji i wersji programu Visual Studio używany do tworzenia projektu.

1. Przejdź do katalogu zawierającego reprodukcja projektu.

1. W oknie konsoli dewelopera wiersza polecenia, wpisz polecenie **cl /P** *argumenty* *filename.cpp*, gdzie *argumenty* jest Lista argumentów przechwycić powyżej, i *filename.cpp* to nazwa pliku źródłowego reprodukcja. To polecenie replikuje wiersz polecenia używany do odtworzenia, ale zatrzymuje kompilację po przebiegu preprocesora i danych wyjściowych, aby kod źródłowy wstępnie przetworzonych *filename*. i.

Jeśli są przetwarzania wstępnego C + +/ pliku kodu źródłowego CX, lub jest używana funkcja modułów C++, wymagane są dodatkowe kroki. Aby uzyskać więcej informacji zobacz poniższe sekcje.

Po wygenerowaniu wstępnie przetworzonych plików jest dobrym pomysłem jest upewnij się, że reprodukcje nadal problem przy użyciu wstępnie przetworzonych plików.

#### <a name="to-confirm-that-the-error-still-repros-with-the-preprocessed-file"></a>Aby upewnić się, że błąd nadal reprodukcje z wstępnie przetworzonych plików

1. W oknie konsoli dewelopera wiersza polecenia, wpisz polecenie **cl** *argumenty* **/TP** *filename*.i mówić cl.exe do skompilowania Wstępnie przetworzony pliku jako pliku źródłowego języka C++, gdzie *argumenty* znajduje się lista argumentów przechwycić powyżej, ale ze wszystkimi **/D** i **/I** argumenty usunięte (dlatego już zostały umieszczone w pliku wstępnie przetworzonych); miejsce i *filename*.i jest nazwą pliku wstępnie przetworzony.

1. Upewnij się, że jest odtworzyć problem.

Na koniec dołączyć wstępnie przetworzonych reprodukcja *filename*.i do raportu.

### <a name="preprocessed-ccx-winrtuwp-code-repros"></a>Wstępnie przetworzony C + +/ CX WinRT/UWP reprodukcje kodu

Jeśli używasz C + +/ CX do tworzenia pliku wykonywalnego, istnieje kilka dodatkowych czynności wymagane do tworzenia i weryfikacji reprodukcja wstępnie przetworzony.

#### <a name="to-preprocess-ccx-source-code"></a>Aby wstępnie Przetwórz C + +/ CX kodu źródłowego

1. Utwórz plik wstępnie przetworzonych źródłowy zgodnie z opisem w [do przetwarzania wstępnego pliku kodu źródłowego](#to-preprocess-a-source-code-file).

1. Wyszukaj wygenerowany _filename_pliku .i **#using** dyrektywy.

1. Sporządź listę wszystkich plików, do którego istnieje odwołanie. Opuść oknami\*, plików winmd platform.winmd i mscorlib.dll.

Aby przygotować się do zweryfikowania, że wstępnie przetworzonych plików nadal powoduje odtworzenie problemu,

1. Utwórz nowy katalog dla pliku wstępnie przetworzonych i skopiuj go do nowego katalogu.

1. Skopiuj pliki winmd z Twojej **#using** listy do nowego katalogu.

1. Utwórz plik vccorlib.h pusta w nowego katalogu.

1. Edytuj plik wstępnie przetworzony, należy usunąć **#using** dyrektywy dla biblioteki mscorlib.dll.

1. Edytuj plik wstępnie przetworzonych można zmienić wszystkie ścieżki bezwzględnej na właśnie systemu od zera nazwy plików winmd skopiowanych plików.

Upewnij się, że wstępnie przetworzonych plików nadal powoduje odtworzenie problemu, jak powyżej.

### <a name="preprocessed-c-modules-repros"></a>Wstępnie przetworzony reprodukcje modułów C++

Jeśli używasz funkcji modułów kompilatora C++ są niektóre inne czynności wymagane do tworzenia i weryfikacji reprodukcja wstępnie przetworzony.

#### <a name="to-preprocess-a-source-code-file-that-uses-a-module"></a>Aby przetwarzanie wstępne pliku kodu źródłowego, który używa modułu

1. Przechwyć argumenty wiersza polecenia używany do tworzenia sieci reprodukcja zgodnie z opisem w [zgłoszenia zawartość wiersza polecenia](#to-report-the-contents-of-the-command-line).

1. Otwórz **wiersza polecenia dewelopera** odpowiadającego architektura konfiguracji i wersji programu Visual Studio używany do tworzenia projektu.

1. Przejdź do katalogu zawierającego reprodukcja projektu.

1. W oknie konsoli dewelopera wiersza polecenia, wpisz polecenie **cl /P** *argumenty* *filename.cpp*, gdzie *argumenty* jest Lista argumentów przechwycić powyżej, i *filename.cpp* to nazwa pliku źródłowego, który wykorzystuje moduł.

1. Przejdź do katalogu, który zawiera projekt reprodukcja wbudowanej interfejsu modułu (dane wyjściowe .ifc).

1. Przechwyć argumenty wiersza polecenia używane do tworzenia interfejsu modułu.

1. W oknie konsoli dewelopera wiersza polecenia, wpisz polecenie **cl /P** *argumenty* *modulename.ixx*, gdzie *argumenty* jest Lista argumentów przechwycić powyżej, i *modulename.ixx* jest nazwą pliku, który tworzy interfejs modułu.

Po wygenerowaniu wstępnie przetworzonych plików, to warto upewnić się, że reprodukcje nadal problem przy użyciu wstępnie przetworzonych plików.

#### <a name="to-confirm-that-the-error-still-repros-with-the-preprocessed-file"></a>Aby upewnić się, że błąd nadal reprodukcje z wstępnie przetworzonych plików

1. W oknie konsoli dewelopera zmiany do katalogu zawierającego reprodukcja projektu.

1. Wprowadź polecenie **cl** *argumenty* **/TP** *filename*.i jak powyżej, aby skompilować pliku wstępnie przetworzony, tak jakby był on plik źródłowy C++.

1. Upewnij się, że problem nadal jest odtworzony przez plik wstępnie przetworzony.

Na koniec Dołącz pliki reprodukcja wstępnie przetworzony (*filename*.i i *modulename*.i) wraz z danych wyjściowych .ifc do raportu.

### <a name="link-repros"></a>Reprodukcje łącza

A *link reprodukcja* jest generowanych przez konsolidator zawartość katalogu określonego przez **łącze\_reprodukcja** zmiennej środowiskowej. Zawiera ona artefaktów kompilacji, które zbiorczo wskazują problem, który występuje w momencie łącza, takie jak awaria wewnętrznej bazy danych obejmujących łącza — czas generowania kodu (LTCG) lub awarii konsolidatora. Tworzenie te artefakty mogą wymaganiom konsolidatora danych wejściowych, dzięki czemu można odtworzyć problem. Reprodukcja łącza mogą być tworzone łatwo za pomocą tej zmiennej środowiskowej, aby włączyć możliwości generowania wbudowanych reprodukcja konsolidator.

#### <a name="to-generate-a-link-repro"></a>Aby wygenerować reprodukcja łącza

1. Przechwyć argumenty wiersza polecenia używany do tworzenia sieci reprodukcja zgodnie z opisem w [zgłoszenia zawartość wiersza polecenia](#to-report-the-contents-of-the-command-line).

1. Otwórz **wiersza polecenia dewelopera** odpowiadającego architektura konfiguracji i wersji programu Visual Studio używany do tworzenia projektu.

1. W oknie konsoli dewelopera wiersza polecenia przejdź do katalogu zawierającego reprodukcja projektu.

1. Wprowadź **mkdir linkrepro** można utworzyć katalogu dla reprodukcja łącza.

1. Wprowadź polecenie **łącze zestawu\_reprodukcja = linkrepro** można ustawić **łącze\_reprodukcja** zmiennej środowiskowej do katalogu, który został utworzony.

1. Aby skompilować projekt reprodukcja w programie Visual Studio, w oknie konsoli dewelopera wiersza polecenia, wpisz polecenie **devenv**. Gwarantuje to, że wartość **łącze\_reprodukcja** zmiennej środowiskowej jest widoczny dla programu Visual Studio. Aby skompilować projekt w wierszu polecenia, użyj przechwycić powyżej mają zostać zduplikowane kompilacji reprodukcja argumenty wiersza polecenia.

1. Skompilowanie projektu reprodukcja i upewnij się, że wystąpił problem oczekiwanego.

1. Jeśli używasz do wykonywania kompilacji zamknij program Visual Studio.

1. W oknie konsoli dewelopera wiersza polecenia, wpisz polecenie **łącze zestawu\_reprodukcja =** wyczyść **łącze\_reprodukcja** zmiennej środowiskowej.

Na koniec pakietu reprodukcja przez kompresowanie cały linkrepro katalogu do pliku zip lub podobne i dołącz je do raportu.

### <a name="other-repros"></a>Inne reprodukcje

Jeśli problem nie można zmniejszyć pliku jednego źródła lub reprodukcja wstępnie przetworzony, a problem nie wymaga reprodukcja łącza, firma Microsoft zbadać projektu IDE. Nadal mają zastosowanie wszystkie wskazówki dotyczące sposobu tworzenia dobrej reprodukcja; Kod powinna być minimalna i samodzielną problem w przypadku wystąpienia w naszym najnowsze narzędzia i w razie potrzeby, problem nie jest widoczny w inne kompilatory.

Utwórz użytkownika reprodukcja jako minimalny projekt IDE, a następnie ją spakować przez kompresowanie całej struktury katalogów, do pliku zip lub podobne i dołączenie go do raportu.

## <a name="ways-to-send-your-report"></a>Sposoby wysyłania raportu

Istnieje kilka sposobów korzystać raportu. Można użyć wbudowanych programu Visual Studio [Zgłoś Problem narzędzie](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017), lub [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) stron. Można także uzyskać bezpośrednio do naszej społeczności deweloperów stron, wybierając **opinię o produkcie** u dołu tej strony. Wybór zależy, czy chcesz użyć narzędzi dostępnych w IDE przechwytywania zrzuty ekranu i organizowanie raportu dla publikowanie na stronach społeczności deweloperów Jeśli wolisz korzystać bezpośrednio witryny sieci Web.

> [!NOTE]
> Niezależnie od tego, jak możesz przesłać raport firma Microsoft szanuje Twoją prywatność. Firma Microsoft dba o zgodności ze wszystkimi przepisów dotyczących prywatności danych i przepisami. Aby dowiedzieć się, jak będzie traktowany jak dane, które możesz wysłać do nas, zobacz [Microsoft Visual Studio produktów z rodziny Privacy Statement](https://www.visualstudio.com/dn948229).

### <a name="use-the-report-a-problem-tool"></a>Użyj narzędzia Problem raportu

**Zgłosić Problem** narzędzia w programie Visual Studio jest sposób dla użytkowników programu Visual Studio zgłosić szerokiej gamy problemów za pomocą kilku kliknięć. Udostępnia prosty formularz, który służy do określania szczegółowe informacje o problemie został napotkany, a następnie przesłać raport bez opuszczania IDE.

Raportowanie problemu za pośrednictwem **zgłosić Problem** narzędzie jest łatwe i wygodne z IDE. Dostęp z paska tytułu, wybierając **Prześlij opinię** obok opcji **Szybkie uruchamianie** pole wyszukiwania, lub można znaleźć na pasku menu w **pomocy**  >  **Wysłać opinię** > **zgłosić Problem**.

Po wybraniu opcji Zgłoś problem najpierw wyszukać społeczność deweloperów dla podobnych problemów. Jeśli problem został zgłoszony przed, upvote temat i dodać komentarze dodatkowe informacje. Jeśli nie widzisz podobny problem, wybierz **problem nowy raport** znajdujący się u dołu okna dialogowego programu Visual Studio opinii i wykonaj kroki, aby zgłosić problem.

### <a name="use-the-visual-studio-developer-community-pages"></a>Użyj strony społeczności deweloperów usługi Visual Studio

Strony społeczności deweloperów usługi Visual Studio są innego wygodny sposób zgłaszanie problemów i rozwiązania Visual Studio, kompilator języka C++, narzędzia i biblioteki. [Programu Visual Studio pytania](https://developercommunity.visualstudio.com/spaces/8/index.html) strona jest miejsce na zgłaszanie problemów z IDE lub instalacji. W przypadku problemów z użyciem kompilatora, konsolidatora i inne narzędzia i biblioteki C++ [pytania C++](https://developercommunity.visualstudio.com/spaces/62/index.html) strony.

W społeczność deweloperów banerze w górnej części każdej strony jest pole wyszukiwania, które można odnaleźć wpisów lub tematy, które zgłosiły problemy podobne do potrzeb. Może się okazać, rozwiązania lub inne przydatne informacje dotyczące tego problemu jest już dostępna w temacie istniejących. Jeśli ktoś zgłosił ten sam problem, przed, upvote, a następnie komentarz dotyczący tego tematu zamiast tworzyć nowy raport o problemie.

Jeśli problem nie został zgłoszony przed, wybierz **zgłosić problem** przycisk obok pola wyszukiwania na stronie społeczności deweloperów. Opcjonalnie możemy Cię poprosić logować się do swojego konta programu Visual Studio i będą musieli się zgodzić udzielić dostępu aplikacji społeczność deweloperów do Twojego profilu. Gdy użytkownik jest zalogowany, możesz przejść bezpośrednio do strony gdzie możesz zgłosić problem. Może zawierać kod reprodukcja i wiersza polecenia, zrzutów ekranu, linki do pokrewnych dyskusji i inne informacje, które zdaniem użytkownika ma zastosowanie i jest przydatne.

> [!TIP]
> Dla innych rodzajów problemy mogą wystąpić w programie Visual Studio, które nie są związane z zestawu narzędzi (na przykład interfejsu użytkownika problemy, przerwane funkcji IDE lub ogólne awarii), **Zgłoś Problem narzędzie** może być szczególnie przydatne choice termin do jego zrzut ekranu napotkano już funkcje i możliwości rejestrowanie akcji interfejsu użytkownika, które mogą prowadzić do problemu. Tego rodzaju błędów mogą być również przedstawione na [społeczność deweloperów](https://developercommunity.visualstudio.com/) lokacji.

### <a name="reports-and-privacy"></a>Raporty i ochrona prywatności

Domyślnie **wszystkie informacje w raportach i wszelkie komentarze i odpowiedzi są widoczne publicznie**. Zazwyczaj jest to korzyść, ponieważ zezwala ona na całej Wspólnoty problemy, rozwiązań i rozwiązania innych użytkowników zostały znalezione. Jeśli masz obawy ujawnianie danych lub tożsamość, dla prywatności lub z przyczyn własności intelektualnej, jednak mieć opcje.

Jeśli masz obawy ujawniania swoją tożsamość, [Utwórz nowe konto Microsoft](https://signup.live.com/) nie ujawnia żadnych szczegółowe informacje o Tobie. Aby utworzyć raport, należy użyć tego konta. 

**Nie umieszczaj coś, co ma być prywatna w tytule lub zawartość początkowy raport, który nie jest publiczny.** Zamiast tego należy pamiętać, że szczegółów będzie wysyłać prywatnie w oddzielnych komentarza. Aby upewnić się, że raport jest kierowany do odpowiednich osób, obejmują **cppcompiler** w temacie Lista raport o problemie. Po utworzeniu raportu problem teraz jest można określić, kto może zobaczyć odpowiedzi i załączniki.

#### <a name="to-create-a-problem-report-for-private-information"></a>Aby utworzyć raport o problemie do poufnych informacji

1. Raport został utworzony, wybierz **Dodaj komentarz** do utworzenia prywatnej opis problemu.

1. w edytorze odpowiedzi formant listy rozwijanej poniżej **przesyłania** i **anulować** przyciski, aby określić odbiorców dla odpowiedzi. Tylko osoby, które określisz widoczny tych prywatnych odpowiedzi i wszystkie obrazy, łącza lub kodu, który je zawiera. Wybierz **Viewable moderatorów i oryginalnego plakat** Aby ograniczyć widoczność pracownikom firmy Microsoft i samodzielnie.

1. Dodaj opis i wszelkie inne informacje, obrazy i załączniki do plików potrzebnych do Twojej reprodukcja. Wybierz **przesyłania** przycisk, aby wysyłać tych informacji przez użytkowników.

   Należy pamiętać, że jest ograniczona do 2GB na załączonych plików i maksymalnie 10 plików. Żadnych większych przekazywania poproś adres URL przekazywania w prywatnej komentarz.

Wszystkie odpowiedzi pod ten komentarz mają taką samą widoczność ograniczone, określona. Dotyczy to nawet wtedy, gdy kontrolka listy rozwijanej w odpowiedzi nie pokazuje stan ograniczona widoczność poprawnie.

Ochrona prywatności i przechowywać poufnych informacji poza widok publiczny, należy zwrócić uwagę, aby zachować wszystkie interakcje z firmą Microsoft odpowiedzi w ograniczonym komentarz. Odpowiedzi na inne komentarze może spowodować przypadkowego ujawnienia informacji poufnych.

## <a name="how-to-report-a-c-documentation-issue"></a>Jak zgłosić problem dokumentacji C++

Używamy GitHub problemów do śledzenia problemów zgłaszanych w naszej dokumentacji. Można teraz utworzyć GitHub interakcję problemów bezpośrednio ze strony zawartości, co pozwala na znacznie bardziej rozbudowane sposób zapisywania i zespoły produktu. Jeśli widzisz problem z dokumentu, przykładowe zły kod, mylące wyjaśnienie, pominięcie krytycznych lub nawet po prostu Literówka można łatwo Poinformuj nas wiesz. Przewiń w dół strony i wybierz **Zaloguj się przekazać opinię o dokumentacji**. Musisz utworzyć konto GitHub, jeśli nie masz już, ale gdy to zrobisz, możesz wyświetlić wszystkich problemów z naszej dokumentacji, ich stan i otrzymywać powiadomienia, gdy zmian problemu, zgłoszonych. Aby uzyskać więcej informacji, zobacz [A nowego opinii o systemie pochodzi docs.microsoft.com](/teamblog/a-new-feedback-system-is-coming-to-docs).

Podczas tworzenia problemu dokumentacji w witrynie GitHub za pomocą przycisku opinia dokumentacji, problem jest automatycznie wypełniane niektóre informacje na temat strona, do której utworzono problem, aby było wiadomo, gdzie znajduje się problem. Nie należy edytować te informacje. Dołącz tylko szczegóły dotyczące co to jest problem i, jeśli chcesz sugerowanej poprawki. [Dokumentację dotyczącą jest typu open source](https://github.com/MicrosoftDocs/cpp-docs/), więc jeśli chcesz faktycznie poprawkę i proponuje samodzielnie, możesz to zrobić. Aby uzyskać więcej informacji o sposobie może przyczynić się do naszej dokumentacji, zobacz nasze [przewodnik Contributing](https://github.com/MicrosoftDocs/cpp-docs/blob/master/CONTRIBUTING.md) w witrynie GitHub.

