---
title: /w /W0, / W1, / W2, / W3, / W4, / W1, / W2, / W3, / W4, / Wall / wo, WV, /WX (poziom ostrzegawczy)
ms.date: 01/31/2018
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
ms.openlocfilehash: 7b5c19c95cff3058bb3dcc6640f8ab07cf01edd6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294242"
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>/w /W0, / W1, / W2, / W3, / W4, / W1, / W2, / W3, / W4, / Wall / wo, WV, /WX (poziom ostrzegawczy)

Określa, jak kompilator generuje ostrzeżenia dla danej kompilacji.

## <a name="syntax"></a>Składnia

> **/w**
>  **/W0**
>  **/W1**
>  **/W2**
>  **/W3** 
>  **/W4**
>  **/wall**
> **WV**\[**:**_wersji _] **/WX**
>  **/W1**_ostrzeżenie_
>  **/W2** _ Ostrzeżenie_
>  **/W3**_ostrzeżenie_
>  **/W4**_ostrzeżenie_ 
>  **/wd**_ostrzeżenie_
>  **/we**_ostrzeżenie_ 
>  **/wo**_ostrzeżenie_

## <a name="remarks"></a>Uwagi

Opcje ostrzeżenie określić które ostrzeżenia kompilatora do wyświetlenia i zachowanie ostrzeżeń dla całej kompilacji.

Ostrzeżenie opcje i argumenty powiązane są opisane w poniższej tabeli:

|Opcja|Opis|
------------|-----------------|
|**/w**|Wyłącza wszystkie ostrzeżenia kompilatora.|
|**/W0**<br /><br /> **/W1**<br /><br /> **/W2**<br /><br /> **/W3**<br /><br /> **/W4**|Określa poziom ostrzeżeń generowanej przez kompilator. Prawidłowe ostrzeżenie poziomów z zakresu od 0 do 4:<br />**/ W0** wyłącza wszystkie ostrzeżenia. Jest to równoważne **Wn**.<br />**/ W1** Wyświetla (poważny) ostrzeżenia poziomu 1. **/ W1** jest ustawieniem domyślnym w kompilatorze wiersza polecenia.<br />**/ W2** Wyświetla poziom 1 i poziom 2 (istotne) ostrzeżenia.<br />**/ W3** Wyświetla poziomu 1, na poziomie 2 i 3 ostrzeżenia (jakości produkcyjnej) na poziomie. **/ W3** jest ustawieniem domyślnym w środowisku IDE.<br />**/ W4** Wyświetla poziom 1 i poziom 2, a poziom ostrzeżeń 3 oraz wszystkich poziomu 4 ostrzeżenia (informacyjne), które nie są wyłączane domyślnie. Zalecamy użycie tej opcji zapewnienie lint przypominającej ostrzeżenia. Dla nowego projektu może być najlepiej użyć **/W4** we wszystkich kompilacjach; zapewni najmniejszą liczbą wad możliwe kodu twardych do znalezienia.|
|**/Wall**|Wyświetla wszystkie ostrzeżenia wyświetlanego przez **/W4** i wszystkie inne ostrzeżenia, **/W4** nie obejmuje — na przykład w przypadku ostrzeżenia, które są domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md).|
|**WV**\[**:**_wersji_]|Wyświetla tylko te ostrzeżenia, które wprowadzonych w wersji kompilatora *wersji* i starszych wersji. Można użyć tej opcji, Pomiń nowe ostrzeżenia w kodzie, w przypadku migracji do nowszej wersji kompilatora i obsługa istniejący proces kompilacji, gdy zostaną naprawione. Opcjonalny parametr *wersji* ma postać *nn*[. *mm*[. *bbbbb*]] gdzie *nn* to główny numer wersji, *mm* jest opcjonalny pomocniczy numer wersji, i *bbbbb* jest numerem kompilacji opcjonalne Kompilator. Na przykład użyć */Wv:17* wyświetlania ostrzeżenia wprowadzone w programie Visual Studio 2012 (czyli dowolna wersja kompilatora, który zawiera główny numer wersji 17) lub wcześniej, ale Pomiń ostrzeżenia wprowadzone w programie Visual Studio 2013 (wersja główna 18) lub nowszy. Domyślnie **WV** używa bieżący numer wersji kompilatora i żadne ostrzeżenia nie są pomijane. Aby uzyskać informacje o tym, które ostrzeżenia są pomijane przez wersję kompilatora, zobacz [ostrzeżenia kompilatora według wersji kompilatora](../../error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md).|
|**/WX**|Traktuje wszystkie ostrzeżenia kompilatora jako błędy. Dla nowego projektu może być najlepiej użyć **/WX** we wszystkich kompilacjach; rozwiązanie wszystkich ostrzeżeń zapewnia najmniejszą liczbą wad możliwe kodu twardych do znalezienia.<br /><br /> Ma również konsolidator **/WX** opcji. Aby uzyskać więcej informacji, zobacz [/WX (Traktuj ostrzeżenia konsolidatora jak błędy)](wx-treat-linker-warnings-as-errors.md).|
|**/w1**_nnnn_<br /><br /> **/w2**_nnnn_<br /><br /> **/w3**_nnnn_<br /><br /> **/ W4**_nnnn_|Ustawia poziom ostrzeżeń dla określonego przez numer ostrzeżenia _nnnn_. Dzięki temu można zmienić zachowanie kompilatora tego ostrzeżenia, gdy ustawiono określonego poziomu ostrzeżeń. Te opcje w połączeniu z innymi opcjami ostrzeżenie umożliwia wymuszanie własnych kodowania standardów ostrzeżenia, a nie domyślnej, jednego z dostarczanych przez program Visual Studio.<br /><br /> Na przykład **/w34326** powoduje, że C4326 zostanie wygenerowany jako włączonego ostrzeżenia poziomu 3 zamiast poziomu 1. Jeśli kompilujesz przy użyciu zarówno **/w34326** opcji i **/W2** opcji Ostrzeżenie C4326 nie są generowane.|
|**/WD**_nnnn_|Umożliwia pominięcie ostrzeżenia kompilatora, który jest określony przez _nnnn_.<br /><br /> Na przykład **/wd4326** pomija C4326 ostrzeżenia kompilatora.|
|**/we**_nnnn_|Traktuje ostrzeżenia kompilatora, który jest określony przez _nnnn_ jako błąd.<br /><br /> Na przykład **/we4326** powoduje, że numer ostrzeżenia C4326 być traktowane jako błąd przez kompilator.|
|**/WO**_nnnn_|Raporty kompilatora ostrzeżenie oznacza to określone przez _nnnn_ tylko raz.<br /><br /> Na przykład **/wo4326** powoduje, że ostrzeżenie C4326 należy podać tylko raz, po raz pierwszy jest napotkał przez kompilator.|

Jeśli przy użyciu jednej z opcji ostrzeżenia podczas tworzenia prekompilowanego nagłówka przy użyciu [/Yc](yc-create-precompiled-header-file.md) opcji każde użycie prekompilowanego nagłówka przy użyciu [/Yu](yu-use-precompiled-header-file.md) opcja powoduje, że te same opcje ostrzeżenie obowiązywać ponownie. Można zastąpić opcje ostrzeżenie, ustaw we prekompilowanym nagłówku, używając innej opcji ostrzeżenie w wierszu polecenia.

Możesz użyć [ostrzeżenie #pragma](../../preprocessor/warning.md) dyrektywy, aby kontrolować poziom ostrzeżenia, to znaczy zgłaszane w czasie kompilacji w plikach określonego źródła.

Dyrektywy pragma ostrzeżeń w kodzie źródłowym nie ma wpływu na **Wn** opcji.

[Tworzenie dokumentacji błędy](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) opisuje ostrzeżenia oraz poziomy ostrzeżeń i wskazuje, dlaczego niektóre instrukcje mogą nie można skompilować jako planowane.

### <a name="to-set-the-compiler-options-in-the-visual-studio-development-environment"></a>Aby ustawić opcje kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Aby ustawić **/W0**, **/W1**, **/W2**, **/W3**, **/W4**, **/Wall**, **WV**, **/WX** lub **/WX-** opcje, wybierz opcję **właściwości konfiguracji** > **C / C++**   >  **Ogólne** stronę właściwości.

   - Aby ustawić **/W0**, **/W1**, **/W2**, **/W3**, **/W4**, lub **/Wall** modyfikowanie opcji **poziom ostrzeżeń** właściwości.

   - Aby ustawić **/WX** lub **/WX-** zmodyfikować opcje **Traktuj ostrzeżenia jako błędy** właściwości.

   - Aby ustawić wersji dla **WV** opcji, należy wprowadzić numer wersji kompilatora w **wersja ostrzeżeń** właściwości.

1. Aby ustawić **/wd** lub **/we** opcje, wybierz opcję **właściwości konfiguracji** > **C/C++**  >   **Zaawansowane** stronę właściwości.

   - Aby ustawić **/wd** wybierz **Wyłącz określone ostrzeżenia** właściwość kontrolka listy rozwijanej, a następnie wybierz **Edytuj**. W polu edycji w **Wyłącz określone ostrzeżenia** okno dialogowe, wprowadź numer ostrzeżenia. Aby wprowadzić więcej niż jeden ostrzeżenie, oddziel wartości przy użyciu średnika (**;**). Na przykład, aby wyłączyć C4001 i C4010, wprowadź **4001; 4010**. Wybierz **OK** Aby zapisać zmiany i powrócić do **stron właściwości** okna dialogowego.

   - Można ustawić **/we** opcji wybierz **Traktuj konkretne ostrzeżenia jako błędy** właściwość kontrolka listy rozwijanej, a następnie wybierz **Edytuj**. W polu edycji w **Traktuj konkretne ostrzeżenia jako błędy** okno dialogowe, wprowadź numer ostrzeżenia. Aby wprowadzić więcej niż jeden ostrzeżenie, oddziel wartości przy użyciu średnika (**;**). Na przykład, aby traktować C4001 i C4010 jako błędy, wprowadź **4001; 4010**. Wybierz **OK** Aby zapisać zmiany i powrócić do **stron właściwości** okna dialogowego.

1. Aby ustawić **/wo** wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** Strona właściwości. Wpisz opcję kompilatora w **dodatkowe opcje** pole.

1. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-the-compiler-option-programmatically"></a>Aby programowo ustawić opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A>, i <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
