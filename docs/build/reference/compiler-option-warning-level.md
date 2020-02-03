---
title: /w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Poziom ostrzeżeń)
description: Dokumentacja języka Microsoft C/C++ kompilatora:/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/wo,/WV i/WX.
ms.date: 01/31/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.DisableSpecificWarnings
- VC.Project.VCCLCompilerTool.WarningLevel
- VC.Project.VCCLWCECompilerTool.DisableSpecificWarnings
- VC.Project.VCCLCompilerTool.WarnAsError
- VC.Project.VCCLWCECompilerTool.WarnAsError
- /wx
- VC.Project.VCCLWCECompilerTool.WarningLevel
- /wall
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- /Wv
- /w0
- /w1
- /w2
- /w3
- /w4
- /wd
- /we
- /wo
helpviewer_keywords:
- /W1 compiler option [C++]
- w compiler option [C++]
- -wo compiler option [C++]
- Warning Level compiler option
- W1 compiler option [C++]
- -we compiler option [C++]
- /WX compiler option [C++]
- -wd compiler option [C++]
- WX compiler option [C++]
- wo compiler option [C++]
- Wall compiler option [C++]
- /w compiler option
- W2 compiler option [C++]
- -W2 compiler option [C++]
- wd compiler option [C++]
- /we compiler option [C++]
- we compiler option [C++]
- -W1 compiler option [C++]
- -W4 compiler option [C++]
- -Wall compiler option [C++]
- /Wall compiler option [C++]
- -W0 compiler option [C++]
- W0 compiler option [C++]
- -WX compiler option [C++]
- /wo compiler option [C++]
- W4 compiler option [C++]
- W3 compiler option [C++]
- /wd compiler option [C++]
- warnings, as errors compiler option
- /W3 compiler option [C++]
- /W0 compiler option [C++]
- /W4 compiler option [C++]
- -W3 compiler option [C++]
- -w compiler option [C++]
- /W2 compiler option [C++]
- /Wv compiler option [C++]
ms.openlocfilehash: 80b6d0c1fe684de9af62683a75f0fd1107a94089
ms.sourcegitcommit: ba4180a2d79d7e391f2f705797505d4aedbc2a5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2020
ms.locfileid: "76972172"
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Poziom ostrzeżeń)

Określa sposób, w jaki kompilator generuje ostrzeżenia dla danej kompilacji.

## <a name="syntax"></a>Składnia

> **/w**\
> **/W0**\
> **/W1**\
> **/W2**\
> **/W3**\
> **/W4**\
> **/Wall**\
> **/WV**\[ **:** _wersja_] \
> **/WX**\
> \_ostrzegawczy_ **/W1**
> \_ostrzegawczy_ **/W2**
> \_ostrzegawczy_ **/W3**
> \_ostrzegawczy_ **/W4**
> \_ostrzegawczy_ **/WD**
> \_ostrzegawczy_ **/we**
> _Ostrzeżenie_ /wo

## <a name="remarks"></a>Uwagi

Opcje ostrzeżeń określają, które ostrzeżenia kompilatora mają być wyświetlane, oraz zachowanie ostrzegawcze dla całej kompilacji.

Opcje ostrzeżeń i powiązane argumenty są opisane w następujących tabelach:

Opcja | Opis
------ | -----------
**/w** | Pomija wszystkie ostrzeżenia kompilatora.
**/W0**<br /><br /> **/W1**<br /><br /> **/W2**<br /><br /> **/W3**<br /><br /> **/W4** | Określa poziom ostrzeżeń generowanych przez kompilator. Prawidłowe poziomy ostrzeżeń mieszczą się w zakresie od 0 do 4:<br />**/W0** pomija wszystkie ostrzeżenia. Jest to odpowiednik **/w**.<br />**/W1** wyświetla ostrzeżenie poziomu 1 (poważny). **/W1** jest domyślnym ustawieniem w kompilatorze wiersza polecenia.<br />**/W2** Wyświetla ostrzeżenia poziomu 1 i 2 (duże).<br />**/W3** Wyświetla ostrzeżenia poziomu 1, poziomu 2 i 3 (jakość produkcji). **/W3** jest domyślnym ustawieniem w IDE.<br />**/W4** Wyświetla ostrzeżenia poziomów 1, 2 i 3 oraz wszystkie ostrzeżenia poziomu 4 (informacje), które nie są domyślnie wyłączone. Zalecamy użycie tej opcji w celu zapewnienia ostrzeżeń przypominających lint. W przypadku nowego projektu najlepiej jest używać **/W4** we wszystkich kompilacjach. Ta opcja pomaga zapewnić możliwie najmniejszą liczbę wad w kodzie.
**/Wall** | Wyświetla wszystkie ostrzeżenia wyświetlane przez **/W4** i wszystkie inne ostrzeżenia, które nie obejmują **/W4** , na przykład ostrzeżenia, które są domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
**/WV**\[ **:** _wersja_] | Wyświetla tylko ostrzeżenia wprowadzone w wersji kompilatora *wersji* i starszych. Tej opcji można użyć, aby pominąć nowe ostrzeżenia w kodzie podczas migracji do nowszej wersji kompilatora. Pozwala ona zachować istniejący proces kompilacji podczas ich rozwiązywania. Opcjonalna *wersja* parametru przyjmuje postać *NN*\[. *mm*\[. *BBBBB*]], gdzie *NN* jest głównym numerem wersji, *mm* to opcjonalny numer wersji pomocniczej, a *BBBBB* to opcjonalny numer kompilacji kompilatora. Na przykład można użyć **/WV: 17** do wyświetlania tylko ostrzeżeń wprowadzonych w programie Visual Studio 2012 (wersja główna 17) lub wcześniejsza. Oznacza to, że wyświetla ostrzeżenia z dowolnej wersji kompilatora, która ma główny numer wersji 17 lub mniejszej. Pomija ostrzeżenia wprowadzone w Visual Studio 2013 (wersja główna 18) i nowsze. Domyślnie **/WV** korzysta z bieżącego numeru wersji kompilatora, a żadne ostrzeżenia nie są pomijane. Aby uzyskać informacje o tym, które ostrzeżenia są pomijane przez wersję kompilatora, zobacz [ostrzeżenia kompilatora według wersji kompilatora](../../error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md).
**/WX** | Traktuje wszystkie ostrzeżenia kompilatora jako błędy. W przypadku nowego projektu najlepiej jest używać **/WX** we wszystkich kompilacjach. rozwiązanie wszystkich ostrzeżeń zapewnia możliwie trudne do znalezienia wady kodu.<br /><br /> Konsolidator ma również opcję **/WX** . Aby uzyskać więcej informacji, zobacz [/WX (Traktuj ostrzeżenia konsolidatora jako błędy)](wx-treat-linker-warnings-as-errors.md).

Poniższe opcje wzajemnie się wykluczają. Ostatnia opcja określona w tej grupie jest zastosowana:

Opcja | Opis
------ | -----------
**/W1**_nnnn_<br /><br /> **/W2**_nnnn_<br /><br /> **/W3**_nnnn_<br /><br /> **/W4**_nnnn_ | Ustawia poziom ostrzeżeń dla ostrzegawczego numeru określonego przez _nnnn_. Te opcje umożliwiają zmianę zachowania kompilatora dla tego ostrzeżenia w przypadku ustawienia określonego poziomu ostrzeżenia. Możesz użyć tych opcji w połączeniu z innymi opcjami ostrzeżenia, aby wymusić własne standardy kodowania dla ostrzeżeń, a nie domyślne, które są udostępniane przez program Visual Studio.<br /><br /> Na przykład **/w34326** powoduje generowanie C4326 jako ostrzeżenia poziomu 3 zamiast poziomu 1. Jeśli kompilujesz przy użyciu opcji **/w34326** i opcji **/W2** , ostrzeżenie C4326 nie jest generowane.
**/WD**_nnnn_ | Pomija ostrzeżenie kompilatora określone przez _nnnn_.<br /><br /> Na przykład **/wd4326** pomija ostrzeżenia kompilatora C4326.
**/we**_nnnn_ | Traktuje Ostrzeżenie kompilatora, który jest określony przez _nnnn_ jako błąd.<br /><br /> Na przykład **/we4326** powoduje, że numer ostrzeżenia C4326 jest traktowany jako błąd przez kompilator.
**/wo**_nnnn_ | Raportuje Ostrzeżenie kompilatora, który jest określony przez _nnnn_ tylko raz.<br /><br /> Na przykład **/wo4326** powoduje, że ostrzeżenie C4326 jest raportowane tylko raz, przy pierwszym napotkaniu przez kompilator.

Jeśli podczas tworzenia prekompilowanego nagłówka używasz dowolnej opcji ostrzegawczej, te ustawienia są zachowywane. Użycie prekompilowanego nagłówka powoduje ponowne zastosowanie tych samych opcji ostrzeżenia. Aby zastąpić opcje ostrzeżeń prekompilowanego nagłówka, ustaw inną opcję ostrzeżenia w wierszu polecenia.

Za pomocą dyrektywy [ostrzegawczej #pragma](../../preprocessor/warning.md) można kontrolować poziom ostrzeżeń raportowany w czasie kompilacji w określonych plikach źródłowych.

Opcja **/w** nie ma wpływ na dyrektywy pragma ostrzeżenia w kodzie źródłowym.

[Dokumentacja dotycząca błędów kompilacji](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) zawiera opis ostrzeżeń i poziomów ostrzeżeń oraz wskazuje, dlaczego niektóre instrukcje mogą nie zostać skompilowane zgodnie z oczekiwaniami.

### <a name="to-set-the-compiler-options-in-the-visual-studio-development-environment"></a>Aby ustawić opcje kompilatora w środowisku deweloperskim programu Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Aby ustawić opcje **/W0**, **/W1**, **/W2**, **/W3**, **/W4**, **/Wall**, **/WV**, **/WX**lub **/WX-** , wybierz pozycję **Właściwości konfiguracji** > **C/C++**  > **Ogólne**.

   - Aby ustawić opcje **/W0**, **/W1**, **/W2**, **/W3**, **/W4**lub **/Wall** , zmodyfikuj Właściwość **poziom ostrzeżeń** .

   - Aby ustawić opcje **/WX** lub **/WX-** , zmodyfikuj Właściwość **Traktuj ostrzeżenia jako błędy** .

   - Aby ustawić wersję dla opcji **/WV** , wprowadź numer wersji kompilatora we właściwości **Ostrzeżenie o wersji** .

1. Aby ustawić opcje **/WD** lub **/we** , wybierz opcję **Właściwości konfiguracji** > **C/C++**  > **zaawansowanej** strony właściwości.

   - Aby ustawić opcję **/WD** , wybierz formant listy rozwijanej **Wyłącz określone ostrzeżenia** , a następnie wybierz pozycję **Edytuj**. W polu edycji okna dialogowego **wyłączanie określonych ostrzeżeń** wprowadź numer ostrzegawczy. Aby wprowadzić więcej niż jedno ostrzeżenie, rozdziel wartości przy użyciu średnika ( **;** ). Na przykład aby wyłączyć zarówno C4001, jak i C4010, wprowadź **4001; 4010**. Wybierz **przycisk OK** , aby zapisać zmiany i powrócić do okna dialogowego **strony właściwości** .

   - Aby ustawić opcję **/we** , wybierz formant listy rozwijanej **Traktuj określone ostrzeżenia jako błędy** , a następnie wybierz pozycję **Edytuj**. W polu edycji w oknie dialogowym **Traktuj określone ostrzeżenia jako błędy** wprowadź numer ostrzegawczy. Aby wprowadzić więcej niż jedno ostrzeżenie, rozdziel wartości przy użyciu średnika ( **;** ). Na przykład, aby traktować zarówno C4001, jak i C4010 jako błędy, wprowadź **4001; 4010**. Wybierz **przycisk OK** , aby zapisać zmiany i powrócić do okna dialogowego **strony właściwości** .

1. Aby ustawić opcję **/wo** , wybierz pozycję **Właściwości konfiguracji** > **CC++ /**  > strony właściwości **wiersza polecenia** . Wprowadź opcję kompilatora w polu **dodatkowe opcje** .

1. Wybierz **przycisk OK** , aby zapisać zmiany.

### <a name="to-set-the-compiler-option-programmatically"></a>Aby programowo ustawić opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A>i <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)\
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
