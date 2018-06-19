---
title: -w,-W0,-W1, - W2, — W3, - W4,-w1, — w2, — w3, — w4, — Wall, -wd, — możemy -wo, -Wv, - WX (poziom ostrzegawczy) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/31/2018
ms.technology:
- cpp-tools
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 60fc8072a95787f9e6f50e7e5c50408ef66e3261
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379253"
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>/w, /W0, /W1, /W2, /W3, / W4, /w1, /w2, /w3, / W4, / Wall, /wd, / możemy /wo, /Wv, wx (poziom ostrzegawczy)

Określa, jak kompilator generuje ostrzeżenia dla danej kompilacji.

## <a name="syntax"></a>Składnia

> **/w**  
> **/W0**  
> **/W1**  
> **/W2**  
> **/W3**  
> **/W4**  
> **/Wall**  
> **/WV**\[**:**_wersji_]  
> **/WX**  
> **/W1**_ostrzeżenie_  
> **/W2**_ostrzeżenie_  
> **/W3**_ostrzeżenie_  
> **/ W4**_ostrzeżenie_  
> **/WD**_ostrzeżenie_  
> **/we**_ostrzeżenie_  
> **/WO**_ostrzeżenie_  

## <a name="remarks"></a>Uwagi

Opcje ostrzeżenie określić które ostrzeżenia kompilatora do wyświetlenia i zachowanie ostrzeżeń dla całej kompilacji.

W poniższej tabeli opisano opcje ostrzeżenie i argumenty pokrewne:

|Opcja|Opis|
------------|-----------------|
|**/w**|Pomija wszystkie ostrzeżenia kompilatora.|
|**/W0**<br /><br /> **/W1**<br /><br /> **/W2**<br /><br /> **/W3**<br /><br /> **/W4**|Określa poziom ostrzeżeń, które ma zostać wygenerowane przez kompilator. Ostrzeżenie prawidłowe poziomy zakresu od 0 do 4:<br />**/ W0** pomija wszystkie ostrzeżenia. Jest to równoważne **/w**.<br />**/ W1** Wyświetla (pociągnięcie) ostrzeżenia poziomu 1. **/ W1** jest ustawieniem domyślnym kompilatora wiersza polecenia.<br />**/ W2** Wyświetla poziom 1 i poziom 2 ostrzeżenia (znaczących).<br />**/ W3** Wyświetla poziom 1, poziom 2 i 3 ostrzeżenia (jakości produkcji) na poziomie. **/ W3** jest to domyślne ustawienie w środowisku IDE.<br />**/ W4** Wyświetla poziom 1 i poziom 2 i 3 ostrzeżenia poziomu oraz wszystkie poziomu 4 ostrzeżenia (informacyjne), które nie są wyłączane domyślnie. Firma Microsoft zaleca użycie tej opcji umożliwia zapewniają podobne wierszu ostrzeżenia. Dla nowego projektu, może być najlepiej użyć **/W4** we wszystkich kompilacjach; dzięki najmniejszej defektów możliwe kodu twarde do znalezienia.|
|**/Wall**|Wyświetla wszystkie ostrzeżenia wyświetlanego przez **/W4** i wszystkie inne ostrzeżenia który **/W4** nie obejmuje — na przykład ostrzeżenia, które są domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżeń czy są wyłączone przez domyślne](../../preprocessor/compiler-warnings-that-are-off-by-default.md).|
|**/WV**\[**:**_wersji_]|Wyświetla tylko ostrzeżenia wprowadzonych w wersji kompilatora *wersji* i starszych wersji. Można użyć tej opcji, pomijanie nowe ostrzeżeń w kodzie, w przypadku migracji do nowszej wersji kompilatora i zachowania istniejącego procesu kompilacji, gdy zostaną naprawione. Opcjonalny parametr *wersji* ma postać *nn*[. *mm*[. *bbbbb*]] gdzie *nn* jest numer wersji głównej *mm* jest opcjonalny podrzędny numer wersji, i *bbbbb* jest numer kompilacji opcjonalne Kompilator. Na przykład użyć */Wv:17* wyświetlane ostrzeżenia wprowadzone w programie Visual Studio 2012 (to znaczy w dowolnej wersji kompilatora, która ma numer wersji głównej 17) lub wcześniej, ale Pomijaj ostrzeżenia wprowadzone w programie Visual Studio 2013 (wersja główna 18) lub nowszy. Domyślnie **/Wv** używa bieżący numer wersji kompilatora i ostrzeżenia nie są pomijane. Aby uzyskać informacje o tym, które ostrzeżenia są pomijane przez wersję kompilatora, zobacz [ostrzeżeń kompilatora w wersji kompilatora](../../error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md).|
|**/WX**|Traktuje wszystkie ostrzeżenia kompilatora jako błędy. Dla nowego projektu, może być najlepiej użyć **wx** we wszystkich kompilacjach; rozwiązanie wszystkich ostrzeżeń zapewni najmniejszej defektów możliwe kodu twarde do znalezienia.<br /><br /> Ma również konsolidator **wx** opcji. Aby uzyskać więcej informacji, zobacz [/WX (Traktuj ostrzeżenia konsolidatora jako błędy)](../../build/reference/wx-treat-linker-warnings-as-errors.md).|
|**/W1**_nnnn_<br /><br /> **/W2**_nnnn_<br /><br /> **/W3**_nnnn_<br /><br /> **/ W4**_nnnn_|Ustawia poziom ostrzeżeń dla określonego przez numeru ostrzeżenia _nnnn_. Dzięki temu można zmienić zachowanie kompilatora tego ostrzeżenia, gdy ustawiono określony poziom ostrzeżenia. Te opcje w połączeniu z innymi opcjami ostrzeżenie umożliwia wymuszanie własnych kodowania standardy ostrzeżeń zamiast domyślnego jednego z dostarczanych przez program Visual Studio.<br /><br /> Na przykład **/w34326** powoduje, że C4326 ma zostać wygenerowane jako ostrzeżenia poziomu 3 zamiast poziomu 1. Jeśli kompilacja za pomocą obu **/w34326** opcji i **/W2** opcję ostrzeżenie C4326 nie jest generowany.|
|**/WD**_nnnn_|Pomijaj ostrzeżenia kompilatora, która jest określona przez _nnnn_.<br /><br /> Na przykład **/wd4326** pomija ostrzeżenie C4326 kompilatora.|
|**/we**_nnnn_|Traktuje ostrzeżenia kompilatora, która jest określona przez _nnnn_ jako błąd.<br /><br /> Na przykład **/we4326** powoduje, że numer ostrzeżenia C4326 traktowane jako błąd przez kompilator.|
|**/WO**_nnnn_|Raporty kompilatora ostrzeżenie oznacza to określone przez _nnnn_ tylko raz.<br /><br /> Na przykład **/wo4326** przyczyny ostrzeżenie C4326 były raportowane tylko raz, po raz pierwszy jest wystąpił przez kompilator.|

Jeśli przy użyciu jednej z opcji ostrzeżenia podczas tworzenia prekompilowanego nagłówka przy użyciu [/Yc](../../build/reference/yc-create-precompiled-header-file.md) opcję użycia prekompilowanego nagłówka przy użyciu [/Yu](../../build/reference/yu-use-precompiled-header-file.md) opcja powoduje, że te same opcje ostrzeżenie obowiązywać do ponownie. Można zastąpić opcje ostrzeżenie ustawić we prekompilowanym nagłówku przy użyciu innej opcji ostrzeżenie w wierszu polecenia.

Można użyć [ostrzeżenie #pragma](../../preprocessor/warning.md) dyrektywy kontrolować poziom ostrzeżenia, który jest zgłaszane w czasie kompilacji w plikach określonego źródła.

Dyrektywy pragma ostrzeżenie w kodzie źródłowym nie ma wpływu na **/w** opcji.

[Dokumentacji błędy kompilacji](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) opisuje ostrzeżenia oraz poziomy ostrzeżeń i wskazuje, dlaczego niektórych instrukcji nie może skompilować jako mają.

### <a name="to-set-the-compiler-options-in-the-visual-studio-development-environment"></a>Aby ustawić opcje kompilatora w środowisku projektowym Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Aby ustawić **/W0**, **/W1**, **/W2**, **/W3**, **/W4**, **/ścian**m **/Wv**, **wx** lub **/WX-** opcji wybierz **właściwości konfiguracji** > **C / C++** > **ogólne** strony właściwości.

   - Aby ustawić **/W0**, **/W1**, **/W2**, **/W3**, **/W4**, lub **/ścian** modyfikowanie opcji **poziom ostrzeżeń** właściwości.

   - Aby ustawić **wx** lub **/WX-** zmodyfikować opcje **Traktuj ostrzeżenia jako błędy** właściwości.

   - Aby ustawić wersji **/Wv** , należy wprowadzić numer wersji kompilatora w **wersji ostrzeżenie** właściwości.

1. Aby ustawić **/wd** lub **/we** opcji wybierz **właściwości konfiguracji** > **C/C++**  >   **Zaawansowane** strony właściwości.

   - Aby ustawić **/wd** wybierz **Wyłącz określone ostrzeżenia** właściwości listy rozwijanej sterowania, a następnie wybierz pozycję **Edytuj**. W polu edycji w **Wyłącz określone ostrzeżenia** okna dialogowego, wprowadź numer ostrzeżenia. Aby wprowadzić więcej niż jeden ostrzeżenie, oddziel wartości za pomocą średnika (**;**). Na przykład, aby wyłączyć zarówno C4001 i C4010, wprowadź **4001; 4010**. Wybierz **OK** Aby zapisać zmiany i wróć do **strony właściwości** okna dialogowego.

   - Aby ustawić **/we** opcji wybierz **Traktuj szczególne ostrzeżenia jako błędy** właściwości listy rozwijanej sterowania, a następnie wybierz pozycję **Edytuj**. W polu edycji w **Traktuj szczególne ostrzeżenia jako błędy** okna dialogowego, wprowadź numer ostrzeżenia. Aby wprowadzić więcej niż jeden ostrzeżenie, oddziel wartości za pomocą średnika (**;**). Na przykład traktuje zarówno C4001 i C4010 jako błędy, wprowadź **4001; 4010**. Wybierz **OK** Aby zapisać zmiany i wróć do **strony właściwości** okna dialogowego.

1. Aby ustawić **/wo** wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** strony właściwości. Wybierz opcję kompilatora w **dodatkowe opcje** pole.

1. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-the-compiler-option-programmatically"></a>Ustawianie opcji kompilatora programowo

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A>, i <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora](../../build/reference/compiler-options.md)  
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)  
