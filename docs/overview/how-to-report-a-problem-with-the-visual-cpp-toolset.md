---
title: Jak zgłosić problem z zestawem narzędzi Microsoft C++
description: Jak utworzyć dobry raport o problemie i informacje o repropro dla zestawu narzędzi Microsoft C++.
ms.date: 09/24/2019
ms.technology: cpp-ide
author: corob-msft
ms.author: corob
ms.openlocfilehash: 350e902501aca5cbe2b4022ec1f977719844644b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "71685703"
---
# <a name="how-to-report-a-problem-with-the-microsoft-c-toolset-or-documentation"></a>Jak zgłosić problem z zestawem narzędzi lub dokumentacją programu Microsoft C++

Jeśli znajdziesz problemy w kompilatorze Microsoft C++(MSVC), konsolidatorze lub innych narzędziach i bibliotekach, chcemy wiedzieć o nich. Gdy problem znajduje się w naszej dokumentacji, chcemy o tym wiedzieć.

## <a name="how-to-report-a-c-toolset-issue"></a>Jak zgłosić problem z zestawem narzędzi języka C++

Najlepszym sposobem, aby poinformować nas o problemie, jest przesłanie nam raportu zawierającego opis wykrytego problemu. Powinien mieć wszystkie szczegóły dotyczące sposobu tworzenia programu. I powinien zawierać *repro*, kompletny przypadek testowy możemy użyć do odtworzenia problemu na naszych własnych maszynach. Te informacje pozwalają nam szybko sprawdzić, czy problem istnieje w naszym kodzie i nie jest lokalny dla Twojego środowiska. Pomaga nam określić, czy wpływa na inne wersje kompilatora i zdiagnozować jego przyczynę.

W poniższych sekcjach przeczytasz o tym, co sprawia, że dobry raport. Opisujemy, jak wygenerować reprodukcję dla tego rodzaju znalezionego problemu i jak wysłać raport do zespołu produktu. Twoje raporty są ważne dla nas i dla innych programistów, takich jak Ty. Dziękujemy za pomoc w ulepszaniu systemu Microsoft C++!

## <a name="how-to-prepare-your-report"></a>Jak przygotować raport

Ważne jest, aby utworzyć raport wysokiej jakości, ponieważ trudno nam odtworzyć znaleziony problem bez pełnych informacji. Im lepszy jest twój raport, tym skuteczniej możemy odtworzyć i zdiagnozować problem.

Co najmniej raport powinien zawierać:

- Pełne informacje o wersji używanego zestawu narzędzi.

- Pełny wiersz polecenia cl.exe używany do tworzenia kodu.

- Szczegółowy opis znalezionego problemu.

- Repro: kompletny, uproszczony, samodzielny przykład kodu źródłowego, który pokazuje problem.

Czytaj dalej, aby dowiedzieć się więcej o konkretnych informacjach, których potrzebujemy i gdzie można je znaleźć, oraz jak stworzyć dobry repro.

### <a name="the-toolset-version"></a>Wersja zestawu narzędzi

Potrzebujemy pełnych informacji o wersji i architektury docelowej zestawu narzędzi, która powoduje problem. Dzięki temu możemy przetestować twój repro na tym samym zestawie narzędzi na naszych maszynach. Jeśli możemy odtworzyć problem, informacje te dają nam również punkt wyjścia do zbadania, które inne wersje zestawu narzędzi mają ten sam problem.

#### <a name="to-report-the-full-version-of-your-compiler"></a>Aby zgłosić pełną wersję kompilatora

1. Otwórz **wiersz polecenia dewelopera,** który pasuje do wersji programu Visual Studio i architektury konfiguracji używanej do tworzenia projektu. Na przykład w przypadku tworzenia przy użyciu programu Visual Studio 2017 w x64 dla obiektów docelowych x64 wybierz **x64 Natywne narzędzia wiersza polecenia dla programu VS 2017**. Aby uzyskać więcej informacji, zobacz [Skróty wiersza polecenia dewelopera](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts).

1. W oknie konsoli wiersza polecenia dewelopera wprowadź polecenie **cl /Bv**.

Dane wyjściowe powinny wyglądać podobnie do:

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

Skopiuj i wklej całe dane wyjściowe do raportu.

### <a name="the-command-line"></a>Wiersz polecenia

Potrzebujemy dokładnego wiersza polecenia, cl.exe i wszystkich jego argumentów, używanych do tworzenia kodu. Dzięki niemu możemy go zbudować dokładnie w ten sam sposób na naszych maszynach. Jest to ważne, ponieważ znaleziony problem może istnieć tylko podczas tworzenia z określonym argumentem lub kombinacją argumentów.

Najlepszym miejscem, aby znaleźć te informacje jest w dzienniku kompilacji natychmiast po wystąpić problem. Zapewnia, że wiersz polecenia zawiera dokładnie te same argumenty, które mogą przyczynić się do problemu.

#### <a name="to-report-the-contents-of-the-command-line"></a>Aby zgłosić zawartość wiersza polecenia

1. Znajdź plik **CL.command.1.tlog** i otwórz go. Domyślnie ten plik znajduje się w \\folderze\\Dokumenty w *wersji*\\programu Visual Studio Projects\\ \\\\\\\\\\*SolutionName ProjectName*\\*Configuration*\\*ProjectName ProjectName*.tlog CL.command.1.tlog lub w folderze User w obszarze Źródło Repos*SolutionName**SolutionName*\\*ProjectName*\\*Konfiguracja*\\*ProjectName*.tlog CL.command.1.tlog. Może znajdować się w innej lokalizacji, jeśli używasz innego systemu kompilacji lub jeśli zmieniono domyślną lokalizację dla projektu.

   Wewnątrz tego pliku znajdziesz nazwy plików kodu źródłowego, a następnie argumenty wiersza polecenia używane do ich kompilacji, każdy w oddzielnych wierszach.

1. Znajdź wiersz zawierający nazwę pliku kodu źródłowego, w którym występuje problem. Wiersz poniżej zawiera odpowiednie argumenty polecenia cl.exe.

Skopiuj i wklej cały wiersz polecenia do raportu.

### <a name="a-description-of-the-problem"></a>Opis problemu

Potrzebujemy szczegółowego opisu znalezionego problemu. Dzięki czemu możemy sprawdzić, czy widzimy ten sam wpływ na nasze maszyny. Czasami warto też wiedzieć, co próbujesz osiągnąć i czego się spodziewałeś.

Dobry opis zawiera **dokładne komunikaty o błędach** podane przez zestaw narzędzi lub dokładne zachowanie środowiska uruchomieniowego, które widzisz. Te informacje są nam potrzebne do sprawdzenia, czy problem został prawidłowo odtworzony. Uwzględnij **wszystkie** dane wyjściowe kompilatora, a nie tylko ostatni komunikat o błędzie. Musimy zobaczyć wszystko, co doprowadziło do problemu, który zgłaszasz. Jeśli można powielić problem przy użyciu kompilatora wiersza polecenia, że dane wyjściowe kompilatora jest preferowane. IDE i inne systemy kompilacji może filtrować komunikaty o błędach, które widzisz, lub tylko przechwycić pierwszy wiersz komunikatu o błędzie.

Jeśli problem polega na tym, że kompilator akceptuje nieprawidłowy kod i nie generuje diagnostyki, dołącz to w raporcie.

Aby zgłosić problem zachowania środowiska uruchomieniowego, należy dołączyć **dokładną kopię** tego, co program drukuje i co można oczekiwać, aby zobaczyć. Najlepiej, jeśli osadzić go w instrukcji wyjściowej, `printf("This should be 5: %d\n", actual_result);`na przykład. Jeśli program ulega awarii lub zawiesza się, należy wspomnieć, że również.

Dodaj inne szczegóły, które mogą pomóc nam zdiagnozować znaleziony problem, takie jak wszelkie wykryte obejście. Staraj się nie powtarzać informacji znalezionych w innym miejscu w raporcie.

### <a name="the-repro"></a>Repro

*Repro* to kompletny, samodzielny przykład kodu źródłowego. Odtwarzalnie pokazuje problem, który znalazłeś, stąd nazwa. Potrzebujemy repro, abyśmy mogli odtworzyć błąd na naszych komputerach. Kod powinien być wystarczający sam w sobie, aby utworzyć podstawowy plik wykonywalny, który kompiluje i uruchamia. Lub, *would* że skompilować i uruchomić, jeśli nie dla problemu, który znalazłeś. Repro nie jest fragment kodu. Powinien mieć pełne funkcje i klasy i zawierać wszystkie niezbędne dyrektywy #include, nawet dla standardowych nagłówków.

#### <a name="what-makes-a-good-repro"></a>Co sprawia, że dobry repro

Dobrym repro jest:

- **Minimalne.** Repros powinny być tak małe, jak to możliwe, ale nadal wykazać dokładnie problem, który znalazłeś. Repros nie muszą być skomplikowane ani realistyczne. Muszą tylko pokazać kod, który jest zgodny ze standardem lub do implementacji kompilatora udokumentowane. W przypadku brakującej diagnostyki repro powinien wyświetlać kod, który nie jest zgodny. Proste, do punktu repros, które zawierają tylko tyle kodu, aby zademonstrować problem są najlepsze. Jeśli można wyeliminować lub uprościć kod i pozostać zgodne, a także pozostawić problem bez zmian, a następnie to zrobić. Nie trzeba dołączać przykłady przeciwduszków kodu, który działa.

- **Samodzielny.** Repros należy unikać niepotrzebnych zależności. Jeśli można odtworzyć problem bez bibliotek innych firm, a następnie to zrobić. Jeśli można odtworzyć problem bez kodu biblioteki oprócz prostych `puts("this shouldn't compile");` `std::cout << value;`instrukcji `printf("%d\n", value);`wyjściowych (na przykład , , i ), a następnie to zrobić. Jest to idealne rozwiązanie, jeśli przykład może być skondensowany do pliku kodu źródłowego, bez odwoływania się do nagłówków użytkownika. Zmniejszenie ilości kodu, który musimy wziąć pod uwagę jako możliwy czynnik przyczyniający się do problemu, jest dla nas niezwykle pomocne.

- **W stosunku do najnowszej wersji kompilatora.** Repros należy użyć najnowszej aktualizacji do najnowszej wersji zestawu narzędzi, gdy tylko jest to możliwe. Możesz też użyć najnowszej wersji wstępnej następnej aktualizacji lub następnej wersji głównej. Problemy, które można znaleźć w starszych wersjach zestawu narzędzi, często zostały naprawione w nowszych wersjach. Poprawki są backported do starszych wersji tylko w wyjątkowych okolicznościach.

- W razie potrzeby **porównywane z innymi kompilatorami.** Repros, które obejmują przenośny kod C++ należy zweryfikować zachowanie względem innych kompilatorów, jeśli to możliwe. Standard C++ ostatecznie określa poprawność programu, a żaden kompilator nie jest doskonały. Jednak gdy Clang i GCC zaakceptować kod bez diagnostyki, a MSVC nie, prawdopodobnie znalazłeś błąd w naszym kompilatorze. (Inne możliwości obejmują różnice w zachowaniu uniksu i systemu Windows lub różnych poziomach implementacji standardów C++ i tak dalej). Gdy wszystkie kompilatory odrzucają kod, jest prawdopodobne, że kod jest niepoprawny. Wyświetlanie różnych komunikatów o błędach może pomóc w samodzielnym zdiagnozowaniu problemu.

   Można znaleźć listy kompilatorów online do testowania kodu w [online kompilatorów C++](https://isocpp.org/blog/2013/01/online-c-compilers) w witrynie iso C++ lub tej wyselekcjonowanej [listy kompilatorów online C++](https://arnemertz.github.io/online-compilers/) na GitHub. Niektóre konkretne przykłady to [Wandbox](https://wandbox.org/), [Eksplorator kompilatora](https://godbolt.org/)i [Coliru](https://coliru.stacked-crooked.com/).

   > [!NOTE]
   > Witryny sieci Web kompilatora online nie są powiązane z firmą Microsoft. Wiele witryn kompilatora online są uruchamiane jako projekty osobiste. Niektóre z tych witryn mogą być niedostępne podczas czytania tego, ale wyszukiwanie powinno znaleźć inne, z których możesz korzystać.

Problemy w kompilatorze, konsolidatorze i bibliotekach mają tendencję do pokazywalenia się w określony sposób. Rodzaj problemu, który znajdziesz, określi, jaki rodzaj repro należy uwzględnić w raporcie. Bez odpowiedniego repro, nie mamy nic do zbadania. Oto kilka rodzajów problemów, które możesz zobaczyć. Zawieramy instrukcje dotyczące generowania rodzaju repro, którego należy użyć do zgłaszania każdego rodzaju problemu.

#### <a name="frontend-parser-crash"></a>Awaria frontendu (analizatora)

Awarie frontendu występują podczas fazy analizy kompilatora. Zazwyczaj kompilator emituje [błąd krytyczny C1001](../error-messages/compiler-errors-1/fatal-error-c1001.md)i odwołuje się do pliku kodu źródłowego i numeru wiersza, na którym wystąpił błąd. Często wspomina o pliku o nazwie msc1.cpp, ale można zignorować ten szczegół.

Dla tego rodzaju awarii, podaj [wstępnie przetworzone repro](#preprocessed-repros).

Oto przykładowe dane wyjściowe kompilatora dla tego rodzaju awarii:

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

#### <a name="backend-code-generation-crash"></a>Awaria wewnętrznej bazy danych (generowanie kodu)

Awarie wewnętrznej bazy danych występują podczas fazy generowania kodu kompilatora. Zazwyczaj kompilator emituje [błąd krytyczny C1001](../error-messages/compiler-errors-1/fatal-error-c1001.md)i może nie odwoływać się do pliku kodu źródłowego i numeru wiersza skojarzonego z problemem. Często wspomina o\\kompilatorze\\plików\\utc src p2\\main.c, ale można zignorować ten szczegół.

W przypadku tego rodzaju awarii należy podać [repro łącza,](#link-repros) jeśli używasz generowania kodu czasu łącza (LTCG), włączoną przez argument wiersza polecenia **/GL** cl.exe. Jeśli nie, zamiast tego podaj [wstępnie przetworzoną repro.](#preprocessed-repros)

Oto przykładowe dane wyjściowe kompilatora dla awarii wewnętrznej bazy danych, w której LTCG nie jest używany. Jeśli dane wyjściowe kompilatora wygląda następująco, należy podać [wstępnie przetworzone repro.](#preprocessed-repros)

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

Jeśli wiersz, który zaczyna się od **błędu modułu kompilatora wewnętrznego** wspomina link.exe, a nie cl.exe, LTCG została włączona. Podaj [repro link w](#link-repros) tym przypadku. Gdy nie jest jasne, czy LTCG została włączona z komunikatu o błędzie kompilatora, sprawdź argumenty wiersza polecenia. Skopiowano je z dziennika kompilacji w poprzednim kroku dla argumentu wiersza polecenia **/GL.**

#### <a name="linker-crash"></a>Awaria konsolidatora

Awarie konsolidatora występują podczas fazy łączenia, po uruchomieniu kompilatora. Zazwyczaj konsolidator emituje [błąd narzędzia konsolidacyjne LNK1000](../error-messages/tool-errors/linker-tools-error-lnk1000.md).

> [!NOTE]
> Jeśli dane wyjściowe wspomina C1001 lub obejmuje generowanie kodu czasu łącza, zamiast tego należy odwołać się do [awarii wewnętrznej bazy danych (generowania kodu).](#backend-code-generation-crash)

Dla tego rodzaju awarii, podaj [link repro](#link-repros).

Oto przykład danych wyjściowych kompilatora dla tego rodzaju awarii:

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

Jeśli łączenie przyrostowe jest włączone, a awaria wystąpiła dopiero po pomyślnym łączu początkowym, to znaczy, że dopiero po pierwszym pełnym łączu, na którym znajduje się późniejsze łącze przyrostowe, należy również podać kopię plików obiektu (obj) i biblioteki (lib), które odpowiadają plikom źródłowym zmodyfikowanym po zakończeniu początkowego łącza.

#### <a name="bad-code-generation"></a>Złe generowanie kodu

Złe generowanie kodu jest rzadkością. Występuje, gdy kompilator omyłkowo generuje niepoprawny kod, który powoduje awarię aplikacji w czasie wykonywania. Zamiast tego należy wygenerować poprawny kod lub wykryć problem w czasie kompilacji. Jeśli uważasz, że znaleziony problem powoduje generowanie nieprawidłowego kodu, potraktuj raport tak samo jak [awarię wewnętrznej bazy danych (generowania kodu).](#backend-code-generation-crash)

W przypadku tego rodzaju awarii należy podać [repro łącza,](#link-repros) jeśli używasz argumentu wiersza polecenia **/GL** do cl.exe. Podaj [wstępnie przetworzony repro,](#preprocessed-repros) jeśli nie.

## <a name="how-to-generate-a-repro"></a>Jak wygenerować repro

Aby pomóc nam wyśledzić źródło problemu, [dobry repro](#what-makes-a-good-repro) jest niezbędna. Przed wykonać którykolwiek z kroków opisanych poniżej dla określonych rodzajów repros, spróbuj skondensować kod, który pokazuje problem jak najwięcej. Spróbuj wyeliminować lub zminimalizować zależności, wymagane nagłówki i biblioteki. Jeśli to możliwe, ogranicz opcje kompilatora i definicje preprocesora.

Poniżej znajdują się instrukcje generowania różnych rodzajów repros, które będą używane do zgłaszania różnego rodzaju problemów.

### <a name="preprocessed-repros"></a>Wstępnie przetworzone repros

*Wstępnie przetworzony repro* jest pojedynczym plikiem źródłowym, który demonstruje problem. Jest generowany na podstawie danych wyjściowych preprocesora C. Aby go utworzyć, użyj opcji kompilatora **/P** w oryginalnym pliku źródłowym odtworzenia. Ta opcja inlines dołączone nagłówki, aby usunąć zależności od dodatkowych plików źródłowych i nagłówkowych. Opcja rozwiązuje również makra, #ifdef stanów warunkowych i innych poleceń preprocesora, które mogą zależeć od środowiska lokalnego.

> [!NOTE]
> Wstępnie przetworzone reprosy nie są tak przydatne w przypadku problemów, które mogą być wynikiem błędów w naszej implementacji biblioteki standardowej, ponieważ często będziemy chcieli zastąpić naszą najnowszą implementację w toku, aby sprawdzić, czy już rozwiązaliśmy problem. W takim przypadku nie należy wstępnie przetwarzać repro, a jeśli nie można zmniejszyć problem do jednego pliku źródłowego, spakować kod do pliku zip lub podobne lub rozważyć użycie projektu IDE repro. Aby uzyskać więcej informacji, zobacz [Inne repros](#other-repros).

#### <a name="to-preprocess-a-source-code-file"></a>Aby wstępnie przetworzyć plik kodu źródłowego

1. Przechwyć argumenty wiersza polecenia używane do tworzenia repro, zgodnie z opisem w [Aby zgłosić zawartość wiersza polecenia](#to-report-the-contents-of-the-command-line).

1. Otwórz **wiersz polecenia dewelopera,** który pasuje do wersji programu Visual Studio i architektury konfiguracji używanej do tworzenia projektu.

1. Zmień katalog zawierający projekt repro.

1. W oknie konsoli wiersza polecenia dewelopera wprowadź polecenie **cl /P** *arguments* *filename.cpp*. W przypadku *argumentów*należy użyć listy argumentów przechwyconych powyżej. *nazwa pliku.cpp* to nazwa pliku źródłowego repro. To polecenie replikuje wiersz polecenia użyty do odtworzenia, ale zatrzymuje kompilację po przekazaniu preprocesora. Następnie zapisuje wstępnie przetworzony kod źródłowy do *filename.i*.

Jeśli wstępnie przetwarzasz plik kodu źródłowego języka C++/CX lub korzystasz z funkcji Moduły języka C++, wymagane są dodatkowe kroki. Aby uzyskać więcej informacji, zobacz sekcje poniżej.

Po wygenerowaniu wstępnie przetworzonego pliku warto upewnić się, że problem nadal występuje podczas kompilowania wstępnie przetworzonego pliku.

#### <a name="to-confirm-the-preprocessed-file-still-repros-the-error"></a>Aby potwierdzić, że wstępnie przetworzony plik nadal ponownie pojawia się błąd

1. W oknie konsoli wiersza polecenia dewelopera wprowadź *argumenty* **polecenia cl** **/TP** *filename.i,* aby poinformować cl.exe o skompilowaniu wstępnie przetworzonego pliku jako pliku źródłowego języka C++. *Argumenty* są te same argumenty przechwycone powyżej, ale z wszelkich **/D** i **/I** argumenty usunięte. To dlatego, że zostały one już uwzględnione w wstępnie przetworzonym pliku. *nazwa filename.i* to nazwa wstępnie przetworzonego pliku.

1. Upewnij się, że problem został odtworzony.

Na koniec dołącz wstępnie przetworzoną *nazwę pliku*repro .i do raportu.

### <a name="preprocessed-ccx-winrtuwp-code-repros"></a>Wstępnie przetworzone repros kodu C++/CX WinRT/UWP

Jeśli używasz C++/CX do tworzenia pliku wykonywalnego, istnieje kilka dodatkowych kroków wymaganych do utworzenia i sprawdzania poprawności wstępnie przetworzonej repro.

#### <a name="to-preprocess-ccx-source-code"></a>Aby wstępnie przetworzyć kod źródłowy C++/CX

1. Utwórz wstępnie przetworzony plik źródłowy zgodnie z opisem w [aby wstępnie przetworzyć plik kodu źródłowego](#to-preprocess-a-source-code-file).

1. Wyszukaj wygenerowany plik _.i,_ aby **uzyskać #using** dyrektyw.

1. Zrób listę wszystkich plików, do których istnieje odwołanie. Pozostaw\*wszystkie pliki .winmd systemu Windows, pliki platform.winmd i mscorlib.dll.

Aby przygotować się do sprawdzenia, czy wstępnie przetworzony plik nadal odtwarza problem,

1. Utwórz nowy katalog dla wstępnie przetworzonego pliku i skopiuj go do nowego katalogu.

1. Skopiuj pliki .winmd z listy **#using** do nowego katalogu.

1. Utwórz pusty plik vccorlib.h w nowym katalogu.

1. Edytuj wstępnie przetworzony plik, aby usunąć wszelkie **dyrektywy #using** dla pliku mscorlib.dll.

1. Edytuj wstępnie przetworzony plik, aby zmienić wszystkie ścieżki bezwzględne na tylko nazwy plików nieosłoniętych dla skopiowanych plików .winmd.

Upewnij się, że wstępnie przetworzony plik nadal odtwarza problem, jak powyżej.

### <a name="preprocessed-c-modules-repros"></a>Wstępnie przetworzone repros modułów C++

Jeśli używasz funkcji Moduły kompilatora C++, istnieje kilka różnych kroków wymaganych do utworzenia i sprawdzania poprawności wstępnie przetworzonej repro.

#### <a name="to-preprocess-a-source-code-file-that-uses-a-module"></a>Aby wstępnie przetworzyć plik kodu źródłowego, który używa modułu

1. Przechwyć argumenty wiersza polecenia używane do tworzenia repro, zgodnie z opisem w [Aby zgłosić zawartość wiersza polecenia](#to-report-the-contents-of-the-command-line).

1. Otwórz **wiersz polecenia dewelopera,** który pasuje do wersji programu Visual Studio i architektury konfiguracji używanej do tworzenia projektu.

1. Zmień katalog zawierający projekt repro.

1. W oknie konsoli wiersza polecenia dewelopera wprowadź polecenie **cl /P** *arguments* *filename.cpp*. *Argumenty* są argumenty przechwycone powyżej i *filename.cpp* jest nazwą pliku źródłowego, który zużywa moduł.

1. Zmień katalog zawierający projekt repro, który zbudował interfejs modułu (dane wyjściowe .ifc).

1. Przechwyć argumenty wiersza polecenia używane do tworzenia interfejsu modułu.

1. W oknie konsoli wiersza polecenia dewelopera wprowadź polecenie **cl /P** *arguments* *modulename.ixx*. *Argumenty* są argumenty przechwycone powyżej i *modulename.ixx* jest nazwą pliku, który tworzy interfejs modułu.

Po wygenerowaniu wstępnie przetworzonych plików warto upewnić się, że problem nadal występuje podczas korzystania z wstępnie przetworzonego pliku.

#### <a name="to-confirm-the-preprocessed-file-still-repros-the-error"></a>Aby potwierdzić, że wstępnie przetworzony plik nadal ponownie pojawia się błąd

1. W oknie konsoli dewelopera zmień z powrotem do katalogu zawierającego projekt repro.

1. Wprowadź argumenty **cl** *arguments* polecenia **/TP** *nazwa pliku*.i jak wyżej, aby skompilować wstępnie przetworzony plik tak, jakby był to plik źródłowy języka C++.

1. Upewnij się, że problem jest nadal powielany przez wstępnie przetworzony plik.

Na koniec dołącz wstępnie przetworzone pliki repro *(nazwa pliku*.i i *nazwa modułu*.i) wraz z wyjściem .ifc do raportu.

### <a name="link-repros"></a>Link repros

*Repro łącza* jest zawartość wygenerowana przez konsolidator katalogu, określona przez zmienną środowiskową **\_repro łącza** lub jako argument do opcji konsolidatora [/LINKREPRO.](../build/reference/linkrepro.md) Zawiera artefakty kompilacji, które wspólnie demonstrują problem, który występuje w czasie łącza. Przykłady obejmują awarię wewnętrznej bazy danych z udziałem generowania kodu czasu łącza (LTCG) lub awarię konsolidatora. Te artefakty kompilacji są te potrzebne jako dane wejściowe konsolidatora, dzięki czemu problem może być odtworzony. Repro łącza można łatwo utworzyć przy użyciu tej zmiennej środowiskowej. Umożliwia wbudowane możliwości generowania funkcji ponownego generowania konsolidatora.

#### <a name="to-generate-a-link-repro-using-the-link_repro-environment-variable"></a>Aby wygenerować repro łącza przy użyciu zmiennej link_repro środowiska

1. Przechwyć argumenty wiersza polecenia używane do tworzenia repro, zgodnie z opisem w [Aby zgłosić zawartość wiersza polecenia](#to-report-the-contents-of-the-command-line).

1. Otwórz **wiersz polecenia dewelopera,** który pasuje do wersji programu Visual Studio i architektury konfiguracji używanej do tworzenia projektu.

1. W oknie konsoli wiersza polecenia dewelopera zmień katalog zawierający projekt repro.

1. Wprowadź **mkdir linkrepro,** aby utworzyć katalog o nazwie *linkrepro* dla repro łącza. Aby przechwycić inny link repro, można użyć innej nazwy.

1. Wprowadź **polecenie set\_link repro=linkrepro,** aby ustawić zmienną środowiskową **repro łącza\_** na utworzony katalog. Jeśli kompilacja jest uruchamiana z innego katalogu, jak to często bywa w przypadku bardziej złożonych projektów, zamiast tego ustaw **łącze\_repro** do pełnej ścieżki do katalogu repro łącza.

1. Aby utworzyć projekt repro w programie Visual Studio, w oknie konsoli wiersza polecenia dewelopera wprowadź polecenie **devenv**. Zapewnia, że wartość zmiennej środowiskowej **repro łącza\_** jest widoczny dla programu Visual Studio. Aby utworzyć projekt w wierszu polecenia, użyj argumentów wiersza polecenia przechwyconych powyżej, aby zduplikować kompilację repro.

1. Skompiluj swój projekt repro i upewnij się, że wystąpił oczekiwany problem.

1. Zamknij visual studio, jeśli użyto go do wykonania kompilacji.

1. W oknie konsoli wiersza polecenia dewelopera wprowadź polecenie **set link\_repro=,** aby wyczyścić zmienną środowiskową **repro łącza.\_**

Na koniec spakować repro, kompresując cały katalog linkrepro do pliku .zip lub podobnego i dołącz go do raportu.

Opcja konsolidatora **/LINKREPRO** ma taki sam efekt jak zmienna środowiskowa **repro łącza.\_** Za pomocą opcji [/LINKREPROTARGET](../build/reference/linkreprotarget.md) można określić nazwę do filtrowania dla wygenerowanego łącza repro. Aby użyć **/LINKREPROTARGET**, należy również określić opcję **/OUT.**

#### <a name="to-generate-a-link-repro-using-the-linkrepro-option"></a>Aby wygenerować repro łącza przy użyciu opcji /LINKREPRO

1. Utwórz katalog, aby pomieścić repro link. Będziemy odwoływać się do pełnej ścieżki katalogu, którą tworzysz jako _ścieżka katalogu_. Użyj cudzysłowów wokół ścieżki, jeśli zawiera ona spacje.

1. Dodaj polecenie **/LINKREPRO:**_directory-path_ do wiersza polecenia konsolidatora. W programie Visual Studio otwórz okno dialogowe **Strony właściwości** dla projektu. Wybierz stronę właściwości**wiersza polecenia wiersza**  > **konsolidatora** >  **właściwości konfiguracji.** Następnie wprowadź opcję **/LINKREPRO:**_directory-path_ w polu **Opcje dodatkowe.** Wybierz **przycisk OK,** aby zapisać zmiany.

1. Skompiluj swój projekt repro i upewnij się, że wystąpił oczekiwany problem.

Na koniec spakować repro przez kompresję całego katalogu repro łącza _ścieżki katalogu_ do pliku zip lub podobne, i dołączyć go do raportu.

### <a name="other-repros"></a>Inne repros

Jeśli nie można zmniejszyć problem do jednego pliku źródłowego lub wstępnie przetworzone repro, a problem nie wymaga repro łącza, możemy zbadać projekt IDE. Wszystkie wskazówki dotyczące tworzenia dobrego repro nadal ma zastosowanie: Kod powinien być minimalny i samowystarczany. Problem powinien wystąpić w naszych najnowszych narzędzi, a jeśli dotyczy, nie powinny być widoczne w innych kompilatorów.

Utwórz repro jako minimalny projekt IDE, a następnie spakować go przez kompresję całej struktury katalogów do pliku zip lub podobne i dołączyć go do raportu.

## <a name="ways-to-send-your-report"></a>Sposoby wysyłania raportu

Masz kilka dobrych sposobów, aby otrzymać raport do nas. Można użyć wbudowanego [narzędzia Zgłaszanie problemów](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)w programie Visual Studio lub stron [społeczności deweloperów programu Visual Studio.](https://developercommunity.visualstudio.com/) U dołu tej strony znajduje się również przycisk **Opinie o produkcie.** Wybór zależy od tego, czy chcesz używać wbudowanych narzędzi w IDE do przechwytywania zrzutów ekranu i organizowania raportu. Jeśli nie chcesz, możesz korzystać bezpośrednio z witryny społeczności deweloperów.

> [!NOTE]
> Niezależnie od sposobu przesyłania raportu firma Microsoft szanuje prywatność użytkownika. Firma Microsoft zobowiązuje się do przestrzegania wszystkich przepisów i regulacji dotyczących prywatności danych. Aby uzyskać informacje o tym, jak traktujemy przesyłane nam dane, zapoznaj się z [Zasadami zachowania poufności informacji firmy Microsoft.](https://privacy.microsoft.com/privacystatement)

### <a name="use-the-report-a-problem-tool"></a>Korzystanie z narzędzia Zgłoś problem

Narzędzie **Zgłoś problem** w programie Visual Studio jest sposobem dla użytkowników programu Visual Studio do zgłaszania problemów za pomocą zaledwie kilku kliknięć. Wyskakuje prosty formularz, aby wysłać szczegółowe informacje o znalezionym problemie. Następnie można przesłać raport bez opuszczania IDE.

Zgłaszanie problemu za pomocą narzędzia **Zgłoś problem** jest łatwe i wygodne z IDE. Dostęp do niego można uzyskać na pasku tytułu, wybierając ikonę **Wyślij opinię** obok pola wyszukiwania **Szybkie uruchamianie.** Możesz też znaleźć go na pasku menu w **pomocy** > wyślij opinię**Zgłoś****Send Feedback** > problem .

Gdy zdecydujesz się zgłosić problem, najpierw wyszukaj w społeczności deweloperów podobne problemy. W przypadku, gdy problem został zgłoszony wcześniej, przegłosuj raport i dodaj komentarze z dodatkowymi szczegółami. Jeśli nie widzisz podobnego problemu, wybierz przycisk **Zgłoś nowy problem** u dołu okna dialogowego Opinie programu Visual Studio i wykonaj kroki, aby zgłosić problem.

### <a name="use-the-visual-studio-developer-community-pages"></a>Korzystanie ze stron społeczności deweloperów programu Visual Studio

Strony społeczności deweloperów programu Visual Studio to kolejny wygodny sposób zgłaszania problemów i znajdowania rozwiązań dla programu Visual Studio i kompilatora, narzędzi i bibliotek w programie C++. Istnieją określone strony społeczności deweloperów dla [programu Visual Studio,](https://developercommunity.visualstudio.com/spaces/8/index.html) [Visual Studio dla komputerów Mac](https://developercommunity.visualstudio.com/spaces/41/index.html), [.NET](https://developercommunity.visualstudio.com/spaces/61/index.html), [C++](https://developercommunity.visualstudio.com/spaces/62/index.html), [usługi Azure DevOps](https://developercommunity.visualstudio.com/spaces/21/index.html)i [TFS](https://developercommunity.visualstudio.com/spaces/22/index.html).

Pod kartami społeczności, u góry każdej strony, znajduje się pole wyszukiwania. Możesz go użyć do znajdowania postów, które zgłaszają problemy podobne do Twoich. Możesz znaleźć rozwiązanie lub inne przydatne informacje związane z problemem są już dostępne. Jeśli ktoś zgłosił ten sam problem wcześniej, a następnie upvote i komentarz do tego raportu, a nie utworzyć nowy raport problem. Aby skomentować, zagłosować lub zgłosić nowy problem, może zostać poproszony o zalogowanie się na konto programu Visual Studio. Przy pierwszym loguchisz się musisz wyrazić zgodę na przyznanie aplikacji społeczności deweloperów dostępu do Twojego profilu.

W przypadku problemów z kompilatorem C++, konsolidatorem i innymi narzędziami i bibliotekami należy użyć strony [Języka C++.](https://developercommunity.visualstudio.com/spaces/62/index.html) Jeśli wyszukujesz problem, który nie został wcześniej zgłoszony, wybierz przycisk **Zgłoś problem** obok pola wyszukiwania. Możesz dołączyć kod repro i wiersz polecenia, zrzuty ekranu, linki do powiązanych dyskusji i wszelkie inne informacje, które uważasz za istotne i przydatne.

> [!TIP]
> W przypadku innych rodzajów problemów, które mogą znaleźć w programie Visual Studio, które nie są związane z zestawem narzędzi C++ (na przykład problemy z interfejsem użytkownika, przerwane funkcje IDE lub ogólne awarie), użyj narzędzia **Zgłoś problem** w środowisku IDE. Jest to najlepszy wybór, ze względu na jego możliwości zrzutu ekranu i jego zdolność do rejestrowania akcji interfejsu użytkownika, które prowadzą do znalezionego problemu. Tego rodzaju błędy można również sprawdzić w witrynie [społeczności deweloperów.](https://developercommunity.visualstudio.com/) Aby uzyskać więcej informacji, zobacz [Jak zgłosić problem z programem Visual Studio](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017).

### <a name="reports-and-privacy"></a>Raporty i prywatność

**Wszystkie informacje w raportach oraz wszelkie komentarze i odpowiedzi są domyślnie widoczne publicznie**. Zwykle jest to korzyść, ponieważ pozwala całej społeczności zobaczyć problemy, rozwiązania i obejścia innych użytkowników. Jeśli jednak obawiasz się upublicznienia swoich danych lub tożsamości ze względu na prywatność lub własność intelektualną, masz opcje.

Jeśli obawiasz się ujawnienia swojej tożsamości, [utwórz nowe konto Microsoft,](https://signup.live.com/) które nie ujawnia żadnych szczegółów na Twój temat. Użyj tego konta, aby utworzyć raport.

**Nie umieszczaj niczego, co chcesz zachować jako prywatne w tytule lub treści początkowego raportu, który jest publiczny.** Zamiast tego załóż, że wyślesz szczegóły prywatnie w osobnym komentarzu. Aby upewnić się, że raport jest kierowany do właściwych osób, dołącz **do** listy tematów raportu o problemie. Po utworzeniu raportu o problemie można teraz określić, kto może zobaczyć Twoje odpowiedzi i załączniki.

#### <a name="to-create-a-problem-report-for-private-information"></a>Aby utworzyć raport o problemach z informacjami prywatnymi

1. W utworzonym raporcie wybierz pozycję **Dodaj komentarz,** aby utworzyć prywatny opis problemu.

1. W edytorze odpowiedzi użyj formantu rozwijanego poniżej przycisków **Prześlij** i **Anuluj,** aby określić grupę odbiorców odpowiedzi. Tylko określone osoby mogą wyświetlać te prywatne odpowiedzi oraz wszelkie obrazy, linki lub kod, które w nich umieszczasz. Wybierz **pozycję Widoczne dla moderatorów i oryginalny plakat,** aby ograniczyć widoczność dla pracowników firmy Microsoft i dla siebie.

1. Dodaj opis i wszelkie inne informacje, obrazy i załączniki plików potrzebne do odtworzenia. Wybierz przycisk **Prześlij,** aby wysłać te informacje prywatnie.

   Istnieje limit 2 GB na dołączone pliki i maksymalnie 10 plików. W przypadku większych przesłanych wiadomości poproś o przesłanie adresu URL w prywatnym komentarzu.

Każda informacja wpływająca na to, że będzie ona miała taką samą widoczność. To prawda, nawet jeśli kontrolka listy rozwijanej w odpowiedziach nie pokazuje poprawnie stanu ograniczonej widoczności.

Aby zachować prywatność i zachować poufne informacje z widoku publicznego, należy zachować ostrożność. Zachowaj wszelką interakcję z firmą Microsoft, aby udzielać odpowiedzi pod komentarzem z ograniczeniami. Odpowiedzi na inne komentarze mogą spowodować przypadkowe ujawnienie poufnych informacji.

## <a name="how-to-report-a-c-documentation-issue"></a>Jak zgłosić problem z dokumentacją języka C++

Używamy problemów z gitHubem do śledzenia problemów zgłoszonych w naszej dokumentacji. Teraz można tworzyć problemy z usługą GitHub bezpośrednio ze strony zawartości, co umożliwia interakcję w znacznie bogatszy sposób z pisarzami i zespołami produktów. Jeśli widzisz problem z dokumentem, zły przykład kodu, mylące wyjaśnienie, krytyczne pominięcie, a nawet tylko literówkę, możesz łatwo nas o tym poinformować. Przewiń do dołu strony i wybierz pozycję **Zaloguj się, aby przekazać opinię o dokumentacji**. Musisz utworzyć konto GitHub, jeśli jeszcze go nie masz. Gdy masz konto GitHub, możesz zobaczyć wszystkie nasze problemy z dokumentacją i ich status. Otrzymasz również powiadomienia o wprowadzeniu zmian dotyczących zgłoszonego problemu. Aby uzyskać więcej informacji, zobacz [Nowy system opinii zbliża się do docs.microsoft.com](/teamblog/a-new-feedback-system-is-coming-to-docs).

Problem z dokumentacją w usłudze GitHub można utworzyć podczas korzystania z przycisku opinii o dokumentacji. Problem jest automatycznie wypełniany z niektórych informacji o stronie, na której utworzono problem. W ten sposób wiemy, gdzie znajduje się problem, więc nie edytuj tych informacji. Wystarczy dołączyć szczegóły dotyczące tego, co jest nie tak, a jeśli chcesz, sugerowana poprawka. [Nasze dokumenty C++ są open source,](https://github.com/MicrosoftDocs/cpp-docs/)więc jeśli chcesz przesłać poprawkę samodzielnie, możesz. Aby uzyskać więcej informacji o tym, jak możesz przyczynić się do naszej dokumentacji, zobacz nasz [przewodnik przyczyniający się](https://github.com/MicrosoftDocs/cpp-docs/blob/master/CONTRIBUTING.md) do gitHub.
