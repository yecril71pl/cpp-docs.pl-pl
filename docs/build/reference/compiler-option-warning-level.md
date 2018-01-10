---
title: "-w,-W0,-W1, - W2, — W3, - W4,-w1, — w2, — w3, — w4, — Wall, -wd, — możemy -wo, -Wv, - WX (poziom ostrzegawczy) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
ms.assetid: d6bc7bf5-c754-4879-909c-8e3a67e2629f
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4f38328f94fd68b3b5402d08ddb6d2bd97e3de76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>/w, /W0, /W1, /W2, /W3, / W4, /w1, /w2, /w3, / W4, / Wall, /wd, / możemy /wo, /Wv, wx (poziom ostrzegawczy)
Określa, jak kompilator generuje ostrzeżenia dla danej kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
/w  
/W0  
/W1  
/W2  
/W3  
/W4  
/Wall  
/Wv[<version>]  
/WX  
/w1<warning>   
/w2<warning>   
/w3<warning>   
/w4<warning>   
/wd<warning>   
/we<warning>   
/wo<warning>  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcje ostrzeżenie określić które ostrzeżenia kompilatora do wyświetlenia i zachowanie ostrzeżeń dla całej kompilacji.  
  
 W poniższej tabeli opisano opcje ostrzeżenie i argumenty pokrewne:  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/w**|Pomija wszystkie ostrzeżenia kompilatora.|  
|**/ W0**<br /><br /> **/ W1**<br /><br /> **/ W2**<br /><br /> **/ W3**<br /><br /> **/ W4**|Określa poziom ostrzeżeń, które ma zostać wygenerowane przez kompilator. Ostrzeżenie prawidłowe poziomy zakresu od 0 do 4:<br /><br /> -   **/ W0** pomija wszystkie ostrzeżenia.<br />-   **/ W1** Wyświetla (pociągnięcie) ostrzeżenia poziomu 1. **/ W1** jest ustawieniem domyślnym.<br />-   **/ W2** Wyświetla poziom 1 i poziom 2 ostrzeżenia (znaczących).<br />-   **/ W3** Wyświetla poziom 1, poziom 2 i 3 ostrzeżenia (jakości produkcji) na poziomie.<br />-   **/ W4** Wyświetla poziom 1 i poziom 2 i 3 ostrzeżenia poziomu oraz wszystkie poziomu 4 ostrzeżenia (informacyjne), które nie są wyłączane domyślnie. Zalecane jest użycie tej opcji tylko w celu zapewnienia podobnej wierszu ostrzeżenia. Jednak dla nowego projektu, może być najlepiej użyć **/W4** we wszystkich kompilacjach; dzięki najmniejszej defektów możliwe kodu twarde do znalezienia.|  
|**/ Wall**|Wyświetla wszystkie ostrzeżenia wyświetlanego przez **/W4** i wszystkie inne ostrzeżenia który **/W4** nie obejmuje — na przykład ostrzeżenia, które są domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżeń czy są wyłączone przez domyślne](../../preprocessor/compiler-warnings-that-are-off-by-default.md).|  
|**/WV**`:version`|Pomijaj ostrzeżenia wprowadzone w nowszej wersji kompilatora `version`. Ta opcja służy do ustalenia, czy są nowe ostrzeżenia w kodzie, który skompilowany bez ostrzeżenia, gdy używasz starszej wersji kompilatora i tymczasowo pominąć nowego ostrzeżenia w procesie kompilacji, gdy zostaną naprawione. Opcjonalny parametr `version` ma postać `nn`[.`mm` [. `bbbbb`]] gdzie `nn` jest numer wersji głównej `mm` jest opcjonalny podrzędny numer wersji, i `bbbbb` jest numer kompilacji opcjonalne kompilatora. Na przykład użyć `/Wv:17.00.00000` do pomijania ostrzeżenia wprowadzone w programie Visual C++ 2012 i nowszych. Domyślnie **/Wv** używa bieżący numer wersji kompilatora i ostrzeżenia nie są pomijane. Aby uzyskać informacje o tym, które ostrzeżenia są pomijane przez wersję kompilatora, zobacz [ostrzeżeń kompilatora w wersji kompilatora](../..//error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md).|  
|**WX**|Traktuje wszystkie ostrzeżenia kompilatora jako błędy. Dla nowego projektu, może być najlepiej użyć **wx** we wszystkich kompilacjach; rozwiązanie wszystkich ostrzeżeń zapewni najmniejszej defektów możliwe kodu twarde do znalezienia.<br /><br /> Ma również konsolidator **wx** opcji. Aby uzyskać więcej informacji, zobacz [/WX (Traktuj ostrzeżenia konsolidatora jako błędy)](../../build/reference/wx-treat-linker-warnings-as-errors.md).|  
|**/W1**`n`<br /><br /> **/W2**`n`<br /><br /> **/W3**`n`<br /><br /> **/ W4**`n`|Ustawia poziom ostrzeżeń dla określonego przez numeru ostrzeżenia `n`. Dzięki temu można zmienić zachowanie kompilatora tego ostrzeżenia, gdy ustawiono określony poziom ostrzeżenia. Te opcje w połączeniu z innymi opcjami ostrzeżenie umożliwia wymuszanie własnych kodowania standardy ostrzeżeń zamiast domyślnego jednego z dostarczanych przez program Visual Studio.<br /><br /> Na przykład `/w34326` powoduje, że C4326 ma zostać wygenerowane jako ostrzeżenia poziomu 3 zamiast poziomu 1. Jeśli kompilacja za pomocą obu `/w34326` opcji i `/W2` opcję ostrzeżenie C4326 nie jest generowany.|  
|**/WD**`n`|Pomijaj ostrzeżenia kompilatora, która jest określona przez `n`.<br /><br /> Na przykład `/wd4326` pomija ostrzeżenie C4326 kompilatora.|  
|**/we**`n`|Traktuje ostrzeżenia kompilatora, która jest określona przez `n` jako błąd.<br /><br /> Na przykład `/we4326` powoduje, że numer ostrzeżenia C4326 traktowane jako błąd przez kompilator.|  
|**/WO**`n`|Raporty kompilatora ostrzeżenie oznacza to określone przez `n` tylko raz.<br /><br /> Na przykład `/wo4326` przyczyny ostrzeżenie C4326 były raportowane tylko raz, po raz pierwszy jest wystąpił przez kompilator.|  
  
 Jeśli przy użyciu jednej z opcji ostrzeżenia podczas tworzenia prekompilowanego nagłówka przy użyciu [/Yc](../../build/reference/yc-create-precompiled-header-file.md) opcję użycia prekompilowanego nagłówka przy użyciu [/Yu](../../build/reference/yu-use-precompiled-header-file.md) opcja powoduje, że te same opcje ostrzeżenie obowiązywać do ponownie. Można zastąpić opcje ostrzeżenie ustawić we prekompilowanym nagłówku przy użyciu innej opcji ostrzeżenie w wierszu polecenia.  
  
 Można użyć [ostrzeżenie #pragma](../../preprocessor/warning.md) dyrektywy kontrolować poziom ostrzeżenia, który jest zgłaszane w czasie kompilacji w plikach określonego źródła.  
  
 Pragma — dyrektywy ostrzeżenie w kodzie źródłowym nie ma wpływu na **/w** opcji.  
  
 [Dokumentacji błędy kompilacji](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) opisuje ostrzeżenia oraz poziomy ostrzeżeń i wskazuje, dlaczego niektórych instrukcji nie może skompilować jako mają.  
  
### <a name="to-set-the-compiler-option-in-the-visual-studio-development-environment"></a>Ustawianie opcji kompilatora w środowisku projektowym Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **C/C++**.  
  
3.  Na **ogólne** właściwości strony, zmodyfikuj **poziom ostrzeżeń** lub **Traktuj ostrzeżenia jako błędy** właściwości.  
  
4.  Na **zaawansowane** właściwości strony, zmodyfikuj **Wyłącz określone ostrzeżenia** właściwości.  
  
5.  Dla pozostałych opcji na **wiersza polecenia** właściwości wpisz opcję kompilatora w **dodatkowe opcje** pole.  
  
### <a name="to-set-the-compiler-option-programmatically"></a>Ustawianie opcji kompilatora programowo  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A>, i <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)