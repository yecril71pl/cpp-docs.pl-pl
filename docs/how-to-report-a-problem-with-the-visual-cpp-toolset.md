---
title: "Jak zgłosić Problem z zestawu narzędzi programu Visual C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: ec24a49c-411d-47ce-aa4b-8398b6d3e8f6
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4a669b2935e4c21421d0c760e6de0c5c7340bed4
ms.sourcegitcommit: 1b480aa74886930b3bd0435d71cfcc3ccda36424
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="how-to-report-a-problem-with-the-visual-c-toolset"></a>Jak zgłosić Problem z zestawu narzędzi programu Visual C++

Jeśli wystąpią problemy z kompilatora Visual C++, konsolidatora lub innych narzędzi, chcemy się dowiedzieć się o nich.

Najlepszy sposób, aby poinformować nas o problemie jest aby wysłać nam raport zawierający opis problemu, który został napotkany szczegółowe informacje dotyczące sposobu tworzysz programu, a niektóre kodu, który możemy użyć do odtworzenia problemu na własnych maszynach. Te informacje ułatwiają szybko sprawdzić, czy problem istnieje i nie jest lokalny dla danego środowiska, określić, czy ma to wpływ na inne wersje kompilatora i zdiagnozować jego przyczyna.

W tym dokumencie będzie temat

- [Jak przygotować raport](#prepare), i co sprawia, że dobrej raportu.

- [Sposoby wysyłania raportu](#send), i co sprawia, że ich inną.

- [Sposób generowania reprodukcja](#generate)oraz różne rodzaje reprodukcje.

Raporty są ważne dla nas i innymi deweloperami jak. Dziękujemy za pomoc nam w ulepszeniu programu Visual C++!

## <a name="prepare"></a>Jak przygotować raport

Tworzenie raportu wysokiej jakości ważne jest, ponieważ jego bardzo trudne do odtworzenia problemu napotkał na własnych maszynach bez pełne informacje. Jest raport lepsze, im bardziej efektywnie jesteśmy stanie Utwórz i zdiagnozować problem.

Co najmniej powinna zawierać raportu

- Informacje o wersji pełny zestaw narzędzi, którego używasz.

- Cl.exe pełny wiersz polecenia używany do tworzenia kodu.

- Szczegółowy opis napotkany problem.

- Reprodukcja — źródła kodu, który demonstruje problem.

W dalszej dowiedzieć się więcej o konkretnych informacji możemy potrzeby i gdzie go znaleźć.

### <a name="the-toolset-version"></a>Wersja zestawu narzędzi

Potrzebujemy informacji pełnej wersji zestawu narzędzi używanego tak, aby Twoje reprodukcja względem tego samego zestawu narzędzi można było przetestować na naszych maszyny. Jeśli firma Microsoft może odtworzyć problem, te informacje udostępnia także punkt wyjścia do badania które inne wersje zestawu narzędzi zawiera ten sam problem.

#### <a name="to-report-the-full-version-of-the-compiler-youre-using"></a>Do pełnej wersji kompilatora, którego używasz raportu

1. Na klawiaturze naciśnij klawisz systemu Windows i rozpocznij wpisywanie `Developer Command Prompt`.

1. Wybierz **wiersza polecenia dewelopera** zgodna z wersją programu Visual Studio używanej wersji pojawiają się w listy dopasowań.

1. W **wiersza polecenia dewelopera** konsoli, wpisz polecenie `cl /Bv /CLR`.

Dane wyjściowe powinny wyglądać podobnie do poniższego:

```Output
C:\Compiler>cl /Bv /CLR
Microsoft (R) C/C++ Optimizing Compiler Version 18.00.40209
for Microsoft (R) .NET Framework version 4.00.30319.34014
Copyright (C) Microsoft Corporation.  All rights reserved.

Compiler Passes:
 C:\WinCComp\binaries.x86chk\bin\i386\cl.exe:        Version 18.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\c1.dll:        Version 18.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\c1xx.dll:      Version 18.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\c2.dll:        Version 18.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\link.exe:      Version 12.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\mspdb120.dll:  Version 12.00.40209.0
 C:\WinCComp\binaries.x86chk\bin\i386\1033\clui.dll: Version 18.00.40209.0
 Common Language Runtime:                            Version  4.00.30319.34014

cl : Command line error D8003 : missing source filename
```

Skopiuj i Wklej całego dokumentu w raporcie.

### <a name="the-command-line"></a>W wierszu polecenia

Potrzebujemy pełny wiersz polecenia (cl.exe i argumenty) używany do tworzenia kodu, dzięki czemu można oprzemy się go w taki sam sposób na naszych maszyny. Jest to ważne, ponieważ został napotkany problem może istnieć tylko podczas kompilowania z określonego argumentu lub kombinacja argumentów.

Dziennik kompilacji jest najlepszym miejscem, aby znaleźć te informacje bezpośrednio po ten problem. Dzięki temu, że wiersz polecenia zawiera dokładnie te same argumenty, które mogą przyczyniać się do problemu.

#### <a name="to-report-the-contents-of-the-command-line"></a>Aby zgłosić zawartość wiersza polecenia

1. Zlokalizuj **CL.command.1.tlog** pliku i otwórz go. Domyślnie ten plik znajduje się w \\...\Visual Studio Version\Projects\SolutionName\ProjectName\Config\ProjectName.tlog\CL.command.1.tlog.

   Wewnątrz tego pliku znajdują się nazwy plików kodu źródłowego, a następnie używana do kompilowania nimi w osobnych wierszach argumenty wiersza polecenia.

1. Odszukaj wiersz, który zawiera nazwę pliku źródła kodu, w którym występuje problem; wiersz poniżej zawiera odpowiednie polecenie cl.exe i jego argumenty.

Skopiuj i Wklej pełny wiersz polecenia w raporcie.

### <a name="a-description-of-the-problem"></a>Opis problemu

Potrzebujemy, aby uzyskać szczegółowy opis problemu, który został napotkano, dzięki czemu można sprawdzić, czy widzimy ten sam efekt na naszych maszyny; jego również czasami przydatne firmie Microsoft w celu próbowano wykonać, a oczekiwano niepożądane.

Podaj dokładne komunikaty przez zestaw narzędzi, krótki opis próbowano wykonać, aby pomóc nam poznać kod reprodukcja i inne szczegółowe informacje, które mogą pomóc nam zdiagnozować problem wystąpił, takich jak dowolnego obejścia możesz może mieć znaleziono. Należy unikać powtarzania informacje znajdujące się w innym miejscu w raporcie.

### <a name="the-repro"></a>Reprodukcja

Potrzebujemy *reprodukcja*, przykładowego kodu źródłowego niezależne demonstrujący problem został napotkany, tak, aby firma Microsoft odtwarzania błędu na naszych maszyny. Rodzaju problemy, które wystąpią określi, jakiego rodzaju reprodukcja należy uwzględnić w raporcie. Bez odpowiedniego reprodukcja nie mamy nic do badania.

Krótkie, niezależne reprodukcje może obejmować bezpośrednio w tekście raportu, ale większych reprodukcje kod źródłowy musi być podłączona do raportu. Reprodukcje, których nie można zmniejszyć do pliku kodu jednego źródła powinna być opakowane przez kompresowanie katalog zawierający wszystkie pliki do pliku zip lub podobną, a dołączone do raportu. Dodatkowe informacje specyficzne dla scenariusza zawsze powinna być uwzględniane w tekście raportu, nigdy nie w kodzie źródłowym.

Jest najlepszym rodzaj reprodukcja możesz wysłać nam *minimalnego reprodukcja*. Jest to jeden, niezależny pliku kodu źródłowego (bez odwołania do użytkownika nagłówki) zawierający wystarczającego kod, aby zademonstrować problem. Jeśli podasz reprodukcja tego formularza, do raportu; dołącza pliku kodu źródłowego jego wszystkie potrzebne.

Jeśli nie można zmniejszyć problemu na minimalnym reprodukcja bez zależności, można znaleźć w poniższych sekcjach, aby określić rodzajem reprodukcja, które powinny być uwzględnione w raporcie.

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

#### <a name="backend_crash"></a>Awaria wewnętrznej bazy danych (generowania kodu)

Występują awarie wewnętrznej bazy danych podczas kodu generowania faza kompilatora. Zazwyczaj kompilator będzie emitować [krytyczny błąd C1001](error-messages/compiler-errors-1/fatal-error-c1001.md)i może nie odwołanie do źródła plików kodu i skojarzone z tym problemem numer wiersza; często zaznaczyć compiler\utc\src\p2\main.c pliku, ale możesz zignorować ten szczegółów.

Dla tego typu awarii (Crash) podaj [reprodukcja łącze](#link-repros) Jeśli używasz łącza — czas generowania kodu (LTCG) lub na [wstępnie przetworzony reprodukcja](#preprocessed-repros) , jeśli nie. LTGC jest włączana przez `/GL` cl.exe argument wiersza polecenia.

Oto przykładowe dane wyjściowe kompilatora dla tego typu awarii, w którym jest LTCG **nie** używane. Jeśli dane wyjściowe kompilatora wygląda następująco należy zapewnić [wstępnie przetworzony reprodukcja](#preprocessed-repros).

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

Jeśli wiersz, który rozpoczyna się **wewnętrzny błąd KOMPILATORA** wymienia link.exe zamiast cl.exe, LTCG został włączony i powinien zawierać [reprodukcja łącze](#link-repros). Jeśli nie jest on jasne, czy LTCG została włączona w komunikacie o błędzie kompilatora, konieczne może być zbadać dziennika argumenty wiersza polecenia, które zostały skopiowane z kompilacji w poprzednim kroku dla `/GL` argumentu wiersza polecenia.

#### <a name="linker-crash"></a>Awaria konsolidatora

Awarie konsolidatora występują w fazie połączeń, po uruchomieniu przez kompilator. Zazwyczaj będzie emitować konsolidator [błąd narzędzi konsolidatora LNK1000](error-messages/tool-errors/linker-tools-error-lnk1000.md).

> [!NOTE]
> Jeśli dane wyjściowe wymienia C1001 lub obejmuje generowanie kodu w czasie konsolidacji, zapoznaj się [awarii wewnętrznej bazy danych (generowania kodu)](#backend_crash) zamiast niego uzyskać więcej informacji.

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

Jeśli konsolidowania przyrostowego jest włączona i awarii wystąpił tylko po początkowej Łączenie — oznacza to, że tylko po pierwszym pełnej konsolidacji jest oparty kolejnych konsolidowania przyrostowego — również Podaj kopię obiektu (.obj) i biblioteki plików (lib), które odpowiadają do plików źródłowych, które zostały zmodyfikowane po początkowej połączenie zostało zakończone.

#### <a name="bad-code-generation"></a>Wygenerowanie złego kodu

Wygenerowanie złego kodu jest rzadko, ale występuje, gdy kompilator generuje przez pomyłkę niepoprawny kod, który spowoduje, że aplikacja do awarii na środowisko uruchomieniowe nie wykrycia tego problemu w czasie kompilacji. Jeśli podejrzewasz problem występuje wyniki w wygenerowanie złego kodu, raport będzie traktowany takie same [awarii wewnętrznej bazy danych (generowania kodu)](#backend_crash).

Dla tego typu awarii (Crash) podaj [reprodukcja łącze](#link-repros) Jeśli używasz łącza — czas generowania kodu (LTCG) lub na [wstępnie przetworzony reprodukcja](#preprocessed-repros) , jeśli nie. LTGC jest włączana przez `/GL` cl.exe argument wiersza polecenia.

## <a name="send"></a>Sposoby wysyłania raportu

Istnieje kilka sposobów umożliwiająca pobranie raportu. Można użyć wbudowanych programu Visual Studio [Zgłoś Problem narzędzie](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017), lub napisz do nas. Najlepszym rozwiązaniem dla raportu zależy od rodzaju problem już wystąpił, sposób interakcji z inżynierów, którzy sprawdzi raportu i określa, czy chcesz śledzić postęp lub udostępnić raport ze społecznością.

> [!NOTE]
> Niezależnie od tego, jak możesz przesłać raport firma Microsoft szanuje Twoją prywatność. Aby dowiedzieć się, jak będzie traktowany jak dane, które możesz wysłać do nas, zobacz [Microsoft Visual Studio produktów z rodziny Privacy Statement](https://www.visualstudio.com/dn948229).

### <a name="send-an-email"></a>Wyślij wiadomość E-mail

Poczta e-mail jest inny sposób, aby wysłać raport bezpośrednio do zespołu Visual C++; Możesz uzyskiwać dostęp do nas [ compilercrash@microsoft.com ](mailto:compilercrash@microsoft.com).

Jeśli zdecydujesz się wysłać raport pocztą e-mail, używając następującego szablonu jako treść wiadomości e-mail. Nie zapomnij dołączyć kodu źródłowego lub innych plików, jeśli te informacje nie są tym w treści wiadomości e-mail.

```Example
To: compilercrash@microsoft.com
Subject: Visual C++ Error Report
-----

Compiler version:

CL.EXE command line:

Problem description:

Source code and repro steps:

```

### <a name="use-the-report-a-problem-tool"></a>Użyj narzędzia Problem raportu

Raport narzędzie Problem w programie Visual Studio jest sposób dla użytkowników programu Visual Studio zgłosić szerokiej gamy problemów za pomocą kilku kliknięć. Udostępnia prosty formularz, który służy do określania szczegółowe informacje o problemie został napotkany, a następnie przesłać raport bez opuszczania IDE.

Raportowanie problemu za pomocą raportu narzędzie Problem jest rzadko rodzaje problemów zestawu narzędzi omówiony w niniejszym dokumencie; Niemniej jednak jego opcję można wybrać, jeśli jego mechanizmów swoje preferencje.

> [!TIP]
> Dla innych rodzajów problemów występujących w programie Visual Studio, które nie są związane z zestawu narzędzi (na przykład interfejsu użytkownika problemy, przerwane funkcji IDE lub ogólne awarii) raport narzędzia Problem może być szczególnie użyteczna z powodu jego możliwości zrzut ekranu i napotkano możliwości rejestrowanie akcji interfejsu użytkownika, które mogą prowadzić do problemu. Nigdy nie Zgłoś te inne rodzaje błędów, wysyłając wiadomość e-mail na adres compilercrash@microsoft.com.

## <a name="generate"></a>Generowanie reprodukcja

Reprodukcja podano przykładowy kod kompletny, niezależny, demonstrujący problem, który jest raportowania. Reprodukcja jest **nie** fragment kodu — musi być z pełnym przykładem kompiluje i uruchamia (lub czy, z wyjątkiem utworzonego przez problem w przypadku raportowania błędów). Ta lista powinna zawierać wszystkie niezbędne # dyrektyw, nawet w przypadku standardowych nagłówków include.

Ponadto jest dobrym reprodukcja

- **Minimalny.** Reprodukcje powinna być możliwie jak najmniejszy podczas nadal prezentacja napotkany problem. Nie trzeba być złożony lub realistyczne reprodukcje — proste, aby punkt reprodukcje są lepsze. Ich nie trzeba podawać zaradczych przykłady kodu, który działa, ale może, jeśli jest opisowy; niezbędne jest tylko przykładowy kod, który powoduje, że problem.

- **Niezależne.** Reprodukcje Unikaj niepotrzebnych zależności. Jeśli można odtworzyć problem bez bibliotek innych firm, należy to zrobić. Czy można odtworzyć problem bez żadnego kodu biblioteki (`std::out`, `printf()` są ok), należy to zrobić. Zmniejszenie ilości kodu, który mamy można rozważyć jako możliwych współtwórca tego problemu jest enormously NAS.

- **W najnowszej wersji kompilatora.** Reprodukcje należy używać najnowszej wersji zestawu narzędzi, jeśli to możliwe. Bardzo często Naprawiono problemów, które nadal mogą wystąpić w starszych wersjach zestawu narzędzi w nowszej wersji.

- **Sprawdza, czy inne kompilatory**, w razie potrzeby. Reprodukcje obejmujących przenośnego kodu C++ powinien sprawdzić zachowanie przed inne kompilatory, jeśli to możliwe.

   Ten krok pozwala określić, czy kod jest prawidłowy, jak kiedy MSVC nie zgadza się z Clang i GCC lub niepoprawne, gdy MSVC, Clang i GCC oświadczasz, że kodu powoduje błąd.

Poniżej znajdują się instrukcje dotyczące generowania różne rodzaje reprodukcje, które będą używane do raportu różne rodzaje problemów.

### <a name="preprocessed-repros"></a>Wstępnie przetworzony reprodukcje

Wstępnie przetworzony reprodukcja to plik jednego źródła, który pokazuje problem i został wygenerowany z danych wyjściowych preprocesora C przez przetwarzanie oryginalnego pliku źródłowego. Ten proces inlines dołączany nagłówków, aby usunąć zależności dodatkowe źródła i pliki nagłówkowe i rozwiązuje również makra, #ifdefs i innych poleceń preprocesora, zależne środowisku lokalnym.

> [!NOTE]
> Należy zauważyć, że wstępnie przetworzonych reprodukcje najmniej wygodny dla problemów, które może być skutkiem błędów w naszym biblioteki standardowej implementacji, ponieważ firma Microsoft będzie często mają zostać podstawione naszych najnowsze, trwa implementacji, aby zobaczyć, czy już problem został rozwiązany problem. W takim przypadku nie Przetwarzaj wstępnie reprodukcja i jeśli problemu nie można zmniejszyć pliku jednego źródła, pakietu kodu do pliku zip lub podobnych lub należy rozważyć użycie reprodukcja projektu IDE (zobacz [inne reprodukcje](#other-repros) poniżej).

#### <a name="to-preprocess-a-source-code-file"></a>Aby przetwarzanie wstępne pliku kodu źródłowego

1. Na klawiaturze naciśnij klawisz systemu Windows i rozpocznij wpisywanie `Developer Command Prompt`.

1. Wybierz **wiersza polecenia dewelopera** zgodna z wersją programu Visual Studio używanej wersji pojawiają się w listy dopasowań.

1. W **wiersza polecenia dewelopera** oknie konsoli, wpisz polecenie `cl /P argumentsfilename.cpp`.

Po utworzeniu wstępnie przetworzonych plików (teraz filename.i) jest dobrym pomysłem jest upewnij się, że reprodukcje nadal problem przy użyciu wstępnie przetworzonych plików. Można użyć `/TP` argument wiersza polecenia, aby sprawdzić cl.exe Aby pominąć krok preprocesora i spróbuj skompilować w zwykły sposób.

#### <a name="to-confirm-that-the-error-still-repros-with-the-preprocessed-file"></a>Aby upewnić się, że błąd nadal reprodukcje z wstępnie przetworzonych plików

1. Na klawiaturze naciśnij klawisz systemu Windows i rozpocznij wpisywanie `Developer Command Prompt`.

1. Wybierz **wiersza polecenia dewelopera** zgodna z wersją programu Visual Studio używanej wersji pojawiają się w listy dopasowań.

1. W **wiersza polecenia dewelopera** oknie konsoli, wpisz polecenie `cl arguments /TP filename.i`.

1. Upewnij się, że jest odtworzyć problem.

Na koniec należy dołączyć ten reprodukcja do raportu.

### <a name="link-repros"></a>Reprodukcje łącza

Reprodukcja łącze jest jeden katalog zawierający artefakty kompilacji, które zbiorczo wskazują problem, który występuje w momencie łącza, takiej jak awaria wewnętrznej bazy danych, w czasie konsolidacji generowania kodu (LTCG) lub awarii konsolidatora; Artefakty kompilacji uwzględnione są potrzebne konsolidatora danych wejściowych, dzięki czemu można odtworzyć problem. Łącze reprodukcje można łatwo utworzyć za pomocą przez konsolidator.

#### <a name="to-generate-a-link-repro"></a>Aby wygenerować reprodukcja łącza

1. Otwórz wiersz polecenia, a następnie wprowadź polecenie `mkdir directory` można utworzyć katalogu dla reprodukcja łącza.

1. Ustaw zmienną środowiskową link_repro do katalogu utworzonego; Wprowadź polecenie `set link_repro=directory`.

1. Jeśli chcesz wykonać kompilację od w programie Visual Studio, uruchomić go z wiersza polecenia przez wprowadzenie polecenia `devenv`. Dzięki temu, że wartość zmiennej środowiskowej link_repro jest widoczna dla programu Visual Studio.

1. Tworzenie aplikacji i upewnij się, że wystąpił problem oczekiwanego.

1. Jeśli zostanie uruchomione w kroku 3 teraz zamknąć program Visual Studio.

1. Wyczyść zmiennej środowiskowej link_repro; Wprowadź polecenie`set link_repro=`

Na koniec pakietu reprodukcja przez kompresowanie całego katalogu do pliku zip lub podobne i dołącz je do raportu.

### <a name="other-repros"></a>Inne reprodukcje

Jeśli problem nie można zmniejszyć pliku jednego źródła lub reprodukcja wstępnie przetworzony, a problem nie wymaga reprodukcja łącza, zbadanie i projektu IDE. Kodu wewnątrz projektu powinny być nadal minimalne i nadal mają zastosowanie wszystkie wskazówek z tego dokumentu.

Utwórz użytkownika reprodukcja jako minimalny projekt IDE, a następnie ją spakować przez kompresowanie całej struktury katalogów, do pliku zip lub podobne i dołączenie go do raportu.