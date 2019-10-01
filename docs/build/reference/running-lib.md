---
title: Uruchamianie LIB
description: Opisuje opcje wiersza polecenia, których można używać z lib. exe.
ms.date: 09/25/2019
f1_keywords:
- VC.Project.VCLibrarianTool.TargetMachine
- Lib
- VC.Project.VCLibrarianTool.PrintProgress
- VC.Project.VCLibrarianTool.SuppressStartupBanner
helpviewer_keywords:
- -MACHINE target platform option
- command files, LIB
- MACHINE target platform option
- colon command files
- VERBOSE library manager option
- /NOLOGO library manager option
- dash option specifier
- /MACHINE target platform option
- forward slash option specifier
- -NOLOGO library manager option
- LIB [C++], running LIB
- -VERBOSE library manager option
- /VERBOSE library manager option
- command files
- NOLOGO library manager option
- slash (/)
- semicolon, command files
- / command files
ms.assetid: d54f5c81-7147-4b2c-a8db-68ce6eb1eabd
ms.openlocfilehash: 0d65c8d8b3b0cd28c7cccda25bfd9512321172f9
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685545"
---
# <a name="running-lib"></a>Uruchamianie LIB

Do kontrolowania LIB można użyć różnych opcji wiersza polecenia.

## <a name="lib-command-line"></a>LIB — wiersz polecenia

Aby uruchomić LIB, wpisz polecenie `lib`, a następnie opcje i nazwy plików dla zadania, którego używasz LIB do wykonania. LIB również akceptuje dane wejściowe wiersza polecenia w plikach poleceń, które opisano w następnej sekcji. Biblioteka LIB nie używa zmiennej środowiskowej.

## <a name="lib-command-files"></a>Pliki poleceń LIB

Można przekazać argumenty wiersza polecenia do LIB w pliku polecenia, używając następującej składni:

> **LIB \@** <em>polecenia-plik</em>

Plik *polecenia* plik jest plikiem tekstowym. Między znakiem ( **\@** ) i nazwą pliku nie można używać spacji ani tabulatorów. Nazwa *pliku polecenia* nie ma domyślnego rozszerzenia; należy określić pełną nazwę pliku, łącznie z dowolnym rozszerzeniem. Nie można używać symboli wieloznacznych. Można określić ścieżkę bezwzględną lub względną z nazwą pliku.

W pliku poleceń argumenty mogą być oddzielone spacjami lub tabulatorami, tak jak w wierszu polecenia. Argumenty mogą być również oddzielone znakami nowego wiersza. Aby oznaczyć komentarz, użyj średnika ( **;** ). LIB ignoruje cały tekst od średnika do końca wiersza.

Można określić albo wszystkie lub część wiersza polecenia w pliku poleceń, i można użyć więcej niż jednego pliku polecenia w LIB polecenia. LIB akceptuje dane wejściowe z pliku polecenia, tak jakby zostały określone w tej lokalizacji w wierszu polecenia. Pliki poleceń nie mogą być zagnieżdżane. LIB echo zawartość plików poleceń, chyba że jest używana opcja **/nologo** .

## <a name="using-lib-options"></a>Korzystanie z opcji LIB

Opcja składa się ze specyfikatora opcji, który jest myślnikiem ( **-** ) lub ukośnikiem ( **/** ), po którym następuje nazwa opcji. Nazwy opcji nie mogą być skracane. Niektóre opcje przyjmują argument, określony po dwukropku ( **:** ). W specyfikacji opcji nie można używać spacji ani tabulatorów. Użyj co najmniej jednej spacji lub kart, aby oddzielić specyfikacje opcji w wierszu polecenia. Nazwy opcji i ich słowa kluczowego lub nazwy pliku nie są rozróżniane wielkością liter, ale identyfikatory używane jako argumenty są rozróżniane wielkości liter. LIB przetwarza opcje w kolejności określonej w wierszu polecenia i w plikach poleceń. Jeśli opcja jest powtarzana z innymi argumentami, ostatni z nich ma być przetworzony pierwszeństwo.

Następujące opcje mają zastosowanie do wszystkich trybów LIB:

> **/Errorreport** \[**Brak** &#124; **monitu o** &#124; &#124; **wysłanie**kolejki

Jeśli lib. exe nie powiedzie się w czasie wykonywania, można użyć **/errorreport** do wysłania informacji o tych błędach wewnętrznych do firmy Microsoft.

Aby uzyskać więcej informacji na temat **/errorreport**, zobacz [/errorreport (zgłaszaj wewnętrzne błędy kompilatora)](errorreport-report-internal-compiler-errors.md).

> **/LINKREPRO:** _ścieżka katalogu_ \
> **/LINKREPROTARGET:** _filename_

Aby pomóc firmie Microsoft zdiagnozować awarie pliku lib. exe i błędy wewnętrzne, można użyć opcji [/LINKREPRO](linkrepro.md) . Generuje on *Odtwórz linków*, zestaw artefaktów kompilacji, które umożliwiają firmie Microsoft odtwarzanie problemu występującego podczas operacji biblioteki. Opcja [/LINKREPROTARGET](linkreprotarget.md) może być używana z opcją **/LINKREPRO** . Generuje on tylko artefakty Odtwórz linków, gdy lib. exe tworzy określony plik. Aby uzyskać więcej informacji, zobacz [Jak zgłosić problem z zestawem narzędzi C++ firmy Microsoft](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

> **/LTCG**

"LTCG" oznacza *generowanie kodu w czasie konsolidacji*. Ta funkcja wymaga współpracy między kompilatorem ([CL. exe](compiler-options.md)), lib i konsolidatorem ([link](linker-options.md)) w celu zoptymalizowania kodu poza tym, co każdy składnik może zrobić.

W przypadku biblioteki LIB opcja **/LTCG** określa, że dane wejściowe z CL. exe obejmują pliki obiektów, które zostały wygenerowane przy użyciu opcji kompilatora [/GL](gl-whole-program-optimization.md) . Jeśli LIB napotka takie dane wejściowe i **/LTCG** nie jest określony, zostanie uruchomione ponownie z/LTCG włączony po wyświetleniu komunikatu informacyjnego. Inaczej mówiąc, nie jest konieczne jawne ustawienie tej opcji, ale przyspiesza to wydajność kompilacji, ponieważ LIB nie musi się ponownie uruchamiać.

W procesie kompilacji dane wyjściowe z LIB są wysyłane do LINKu. LINK ma własną oddzielną opcję **/LTCG** . Służy do wykonywania różnych optymalizacji, w tym optymalizacji całego programu oraz Instrumentacji optymalizacji opartej na profilach (PGO). Aby uzyskać więcej informacji na temat opcji LINK, zobacz [/LTCG](ltcg-link-time-code-generation.md).

> **/MACHINE**

Określa platformę docelową programu. Zwykle nie trzeba określać **/Machine**. LIB wnioskuje typ maszyny z plików. obj. Jednak w niektórych sytuacjach LIB nie może określić typu komputera i wygeneruje komunikat o błędzie. Jeśli wystąpi błąd, należy określić **/Machine**. W trybie **/Extract** ta opcja dotyczy tylko weryfikacji. Aby wyświetlić dostępne typy maszyn, użyj `lib /?` w wierszu polecenia.

> **/NOLOGO**

Pomija wyświetlanie komunikatu o prawach autorskich LIB i numeru wersji i uniemożliwia echo plików poleceń.

> **/VERBOSE**

Wyświetla szczegółowe informacje o postępie sesji, w tym nazwy plików. obj, które są dodawane. Informacje są wysyłane do wyjścia standardowego i mogą być przekierowywane do pliku.

> **/WX**[ **: No**]

Traktuj ostrzeżenia jako błędy. Aby uzyskać więcej informacji, zobacz [/WX (Traktuj ostrzeżenia konsolidatora jako błędy)](wx-treat-linker-warnings-as-errors.md).

Inne opcje mają zastosowanie tylko do określonych trybów LIB. Te opcje zostały omówione w sekcji opisującej poszczególne tryby.

## <a name="see-also"></a>Zobacz także

[Dokumentacja biblioteki LIB](lib-reference.md)
