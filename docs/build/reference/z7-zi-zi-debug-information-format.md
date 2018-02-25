---
title: "— - Zi, - ZI Z7, (Format informacji o debugowaniu) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/22/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.DebugInformationFormat
- /ZI
- /Zi
- /Z7
- VC.Project.VCCLWCECompilerTool.DebugInformationFormat
dev_langs:
- C++
helpviewer_keywords:
- C7 compatible compiler option [C++]
- Debug Information Format compiler option
- ZI compiler option
- -Zi compiler option [C++]
- /ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debug information files
- Zi compiler option [C++]
- /Zi compiler option [C++]
- program database compiler option [C++]
- full symbolic debugging information
- /Z7 compiler option [C++]
- line numbers only compiler option [C++]
- cl.exe compiler, debugging options
- -Z7 compiler option [C++]
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f6e3de89c5336cda98960b67b80932df8f67d183
ms.sourcegitcommit: 2cca90d965f76ebf1d741ab901693a15d5b8a4df
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/24/2018
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7, /Zi, /ZI (Format informacji o debugowaniu)

Określa typ informacji o debugowaniu stworzonej dla Twojego programu oraz czy te informacje są przechowywane w plikach obiektu lub plik programu (PDB) bazy danych.

## <a name="syntax"></a>Składnia

> **/Z**{**7**|**i**|**I**}  

## <a name="remarks"></a>Uwagi

W poniższych sekcjach opisano opcje format informacji debugowania.  
  
### <a name="none"></a>Brak

Domyślnie jeśli żadna opcja nie format informacji debugowania jest określona, kompilator tworzy żadnych informacji debugowania, więc kompilacji jest szybsze.  
  
### <a name="z7"></a>/Z7

**/Z7** opcji daje *pliku obiektu*, plik z rozszerzeniem nazwy zawierające pełne symboliczne informacje o debugowaniu do użycia z debugera. Symboliczna informacja o debugowaniu zawiera nazwy i rodzaje zmiennych, jak również funkcje i numery wierszy. Nie *pliku PDB*, jest generowany plik z rozszerzeniem .pdb.

Dystrybutorów bibliotek innych firm jest zaletą nie ma plików PDB. Jednak pliki obiektu prekompilowane nagłówki są niezbędne w fazie łącza, a także do debugowania. Jeśli istnieje tylko w .pch — pliki obiektu wpisz informacje (i żaden kod), należy również użyć [/Yl (Wstaw Odnośnik PCH dla bibliotek debugowania)](../../build/reference/yl-inject-pch-reference-for-debug-library.md) opcja, która jest domyślnie włączona.

### <a name="zi"></a>/Zi

**/Zi** opcji spowoduje utworzenie pliku PDB, który zawiera informacje o typie i symboliczną informację o debugowaniu do użycia z debugera. Symboliczna informacja o debugowaniu zawiera nazwy i rodzaje zmiennych, jak również funkcje i numery wierszy.

Użycie **/zi** nie ma wpływu na optymalizację. Jednak **/zi** oznacza **/debug**; zobacz [/Debug (generowanie informacji debugowania)](../../build/reference/debug-generate-debug-info.md) Aby uzyskać więcej informacji.

Gdy **/zi** określono informacji o typie znajduje się w pliku PDB, a nie w pliku obiektu.

Można użyć [/GM ponowną (Włącz minimalnego odbudować)](../../build/reference/gm-enable-minimal-rebuild.md) razem z **/zi**, ale **/GM ponowną** jest niedostępne podczas **/z7** określono.

Po określeniu zarówno **/zi** i **/CLR**, <xref:System.Diagnostics.DebuggableAttribute> atrybut nie jest umieszczany w metadanych zestawu. Jeśli chcesz, muszą określić go w kodzie źródłowym. Ten atrybut może wpłynąć na wydajność środowiska uruchomieniowego aplikacji. Aby uzyskać więcej informacji na temat sposobu **Debuggable** atrybutu wpływa na wydajność i można zmodyfikować jego wpływ na wydajność, zobacz [ułatwiając obraz do debugowania](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug).

### <a name="zi"></a>/ZI

**/Zi** opcji powoduje utworzenie pliku PDB w formacie, który obsługuje [Edytuj i Kontynuuj](/visualstudio/debugger/edit-and-continue-visual-cpp) funkcji. Jeśli chcesz użyć Edytuj i Kontynuuj, debugowanie, musi użyć tej opcji. Funkcja Edytuj i Kontynuuj jest przydatne w przypadku produktywność deweloperów, ale mogą powodować problemy w zgodność kompilatora, kod rozmiaru i wydajności. Ponieważ większość optymalizacje są niezgodne z opcją Edytuj i Kontynuuj, za pomocą **/zi** wyłączy wszystkie `#pragma optimize` instrukcje w kodzie. **/Zi** opcja również jest niezgodna z użyciem [&#95; &#95; WIERSZ &#95; &#95; wstępnie zdefiniowane makro](../../preprocessor/predefined-macros.md). Kodu skompilowanego z **/zi** nie można użyć **&#95; &#95; WIERSZ &#95; &#95;**  jako argument szablonu bez typu, chociaż **&#95; &#95; WIERSZ &#95; &#95;**  mogą być używane w rozwinięcia makra są.

**/Zi** opcja wymusza zarówno [/Gy (Włącz funkcję łączenia na poziomie)](../../build/reference/gy-enable-function-level-linking.md) i [/FC (pełna ścieżka z pliku kodu źródłowego w diagnostyce)](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md) opcje do użycia w Twojej kompilacji.

**/ Zi** nie jest zgodny z [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).

> [!NOTE]
> **/Zi** opcja jest dostępna tylko w kompilatory przeznaczonych dla procesorów x86 i x64; tej opcji kompilatora nie jest dostępna w kompilatory przeznaczonych dla procesorów ARM.

Kompilator nazwy pliku PDB *projektu*.pdb. Jeśli kompilacja pliku poza projektem, kompilator tworzy plik PDB o nazwie VC*x*0.pdb, gdzie *x* jest numer wersji głównej wersji programu Visual Studio w użyciu. Kompilator osadza nazwę pliku PDB w każdym pliku .obj utworzone za pomocą tej opcji, wskazujące debugera do lokalizacji informacje symboliczne i numerów wierszy. Tej opcji pliki .obj są mniejsze, ponieważ informacje o debugowaniu są przechowywane w pliku PDB, a nie w plikach .obj.

Jeśli z obiektów, które zostały skompilowane przy użyciu tej opcji tworzenia biblioteki, plik PDB skojarzone musi być dostępny powiązane biblioteki programu. W związku z tym jeśli dystrybucji biblioteki, musisz przeprowadzić dystrybucję pliku PDB.

Aby utworzyć bibliotekę, która zawiera informacje o debugowaniu bez użycia .pdb, pliki, należy wybrać kompilatora C 7.0 zgodnego (**/z7**) opcja. Jeśli używasz opcji prekompilowanych nagłówków informacji debugowania dla zarówno prekompilowanego nagłówka, jak i pozostałej części kodu źródłowego znajduje się w pliku PDB. **/Yd** opcja została zignorowana w przypadku wybrania opcji programu bazy danych.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Otwórz **właściwości konfiguracji** > **C/C++** > **ogólne** strony właściwości.

1. Modyfikowanie **Format informacji debugowania** właściwości. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora](../../build/reference/compiler-options.md)  
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)  

