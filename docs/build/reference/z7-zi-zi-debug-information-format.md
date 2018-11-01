---
title: /Z7, /Zi, /ZI (Format informacji o debugowaniu)
ms.date: 02/22/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.DebugInformationFormat
- /ZI
- /Zi
- /Z7
- VC.Project.VCCLWCECompilerTool.DebugInformationFormat
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
ms.openlocfilehash: 43ffbe76092b9675be1610e58c65c0034955634f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479052"
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7, /Zi, /ZI (Format informacji o debugowaniu)

Określa typ informacji o debugowaniu utworzonych dla programu, czy te informacje są przechowywane w plikach obiektowych lub w pliku bazy danych (PDB) programu.

## <a name="syntax"></a>Składnia

> **/Z**{**7**|**i**|**I**}

## <a name="remarks"></a>Uwagi

Gdy kod jest skompilowany i wbudowane w trybie debugowania, kompilator generuje nazwy symboli dla funkcji i zmiennych, informacje o typie i lokalizacje numeru wiersza na potrzeby używania przez debuger. Ta symboliczne informacje debugowania można dołączyć, w plikach obiektowych (.obj pliki) generowany przez kompilator lub w oddzielnym pliku PDB (plik .pdb) dla pliku wykonywalnego.  W poniższych sekcjach opisano opcje formatu informacji debugowania.

### <a name="none"></a>Brak

Domyślnie jeśli określono żadnej opcji formatu informacji debugowania, kompilator generuje nie informacji o debugowaniu, więc kompilacja jest szybsza.

### <a name="z7"></a>/Z7

**/Z7** opcja tworzy plików obiektów, które również zawierać pełne symboliczne informacje debugowania do użytku z debugerem. Tych plików obiektów i wbudowanych pliku wykonywalnego może być znacznie większe niż pliki, których żadnych informacji debugowania. Symboliczne informacje debugowania zawierają nazwy i typy zmiennych, jak również funkcje i numery wierszy. Plik PDB nie jest generowany.

Dla dystrybutorów bibliotek innych firm wersje do debugowania ma swoją zaletę nieposiadanie pliku PDB. Jednak pliki obiektów dla dowolnego wstępnie skompilowanych nagłówków są niezbędne w fazie biblioteki, a także do debugowania. Jeśli jest tylko typ informacji (i nie ma kodu) w pliku obiektu .pch, musisz również użyć [/Yl (wstrzyknąć Odnośnik PCH dla bibliotek debugowania)](../../build/reference/yl-inject-pch-reference-for-debug-library.md) opcja, która jest domyślnie włączone, podczas kompilowania biblioteki.

[/Gm (Włącz minimalną ponowną kompilację)](../../build/reference/gm-enable-minimal-rebuild.md) opcja jest niedostępna, gdy **/z7** jest określony.

### <a name="zi"></a>/Zi

**/Zi** opcja generuje oddzielny plik PDB, który zawiera wszystkie symboliczne informacje debugowania do użytku z debugerem. Informacje o debugowaniu nie znajduje się w plikach obiektowych lub pliku wykonywalnego, co sprawia, że ich znacznie mniejszy.

Korzystanie z **/zi** nie wpływa na optymalizację. Jednak **/zi** oznaczają **/debug**; zobacz [/Debug (generowanie informacji debugowania)](../../build/reference/debug-generate-debug-info.md) Aby uzyskać więcej informacji.

Po określeniu zarówno **/zi** i **/CLR**, <xref:System.Diagnostics.DebuggableAttribute> atrybut nie jest umieszczany w metadanych zestawu. Jeśli chcesz go, należy określić go w kodzie źródłowym. Ten atrybut może wpłynąć na wydajność wykonywania aplikacji. Aby uzyskać więcej informacji o tym, jak **Debuggable** atrybut ma wpływ na wydajność i jak można zmodyfikować ten wpływ na wydajność, zobacz [ułatwianie obrazu do debugowania](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug).

Kompilator nazywa plik PDB *projektu*.pdb. Jeśli skompilujesz plik spoza projektu, kompilator tworzy plik PDB o nazwie VC*x*.pdb, gdzie *x* jest łączenie numer wersji głównych i pomocniczych używanej wersji kompilatora. Kompilator osadza nazwę PDB i identyfikujące podpisu oznaczony sygnaturą czasową w każdym pliku obiektów utworzonych za pomocą tej opcji, które wskazuje debugera do lokalizacji informacje symboliczne i numer wiersza. Nazwa i podpis w pliku PDB musi być zgodny plik wykonywalny dla symboli, które zostały załadowane w debugerze. Debuger WinDBG załadować symbole niedopasowanych przy użyciu `.symopt+0x40` polecenia. Program Visual Studio nie ma opcji podobny, aby załadować symbole niezgodne.

Jeśli tworzysz bibliotekę z obiektów, które zostały skompilowane przy użyciu **/zi**, skojarzony plik .pdb musi być dostępny, gdy biblioteka jest połączone z programem. W związku z tym jeśli rozpowszechniasz bibliotekę, musisz również rozpowszechniać pliku PDB. Aby utworzyć bibliotekę, która zawiera informacje o debugowaniu bez używania plików PDB, należy wybrać **/z7** opcji. Jeśli używasz opcji wstępnie skompilowanych nagłówków, debugowanie informacji zarówno dla prekompilowanego pliku nagłówkowego i pozostałej części kodu źródłowego jest umieszczany w pliku PDB.

### <a name="zi"></a>/ZI

**/Zi** opcja jest podobna do **/zi**, ale tworzy plik PDB w formacie, który obsługuje [Edytuj i Kontynuuj](/visualstudio/debugger/edit-and-continue-visual-cpp) funkcji. Aby użyć polecenia Edytuj i Kontynuuj debugowanie funkcji, należy użyć tej opcji. Funkcja Edytuj i Kontynuuj jest przydatne w przypadku pracy deweloperskiej, ale mogą powodować problemy w zgodności rozmiar, wydajności i kompilator kodu. Ponieważ większość optymalizacji jest niezgodnych z funkcją Edytuj i Kontynuuj, za pomocą **/zi** wyłącza wszelkie `#pragma optimize` instrukcji w kodzie. **/Zi** opcja również jest niezgodna z użyciem [ &#95; &#95;wiersza&#95; &#95; wstępnie zdefiniowane makro](../../preprocessor/predefined-macros.md); kodu skompilowanego z **/zi** nie można użyć **&#95; &#95;Wiersza&#95; &#95;** jako argument szablonu bez typu, mimo że **&#95; &#95;wiersza&#95; &#95;** mogą być używane w makrze rozszerzenia.

**/Zi** opcja wymusza zarówno [/Gy (Włącz łączenie poziomie funkcji)](../../build/reference/gy-enable-function-level-linking.md) i [/FC (pełna ścieżka z pliku kodu źródłowego w diagnostyce)](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md) opcje, które zostaną użyte w kompilacji.

**/ Zi** nie jest zgodny z [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).

> [!NOTE]
> **/Zi** opcja jest dostępna tylko w kompilatorach przeznaczonych dla procesorów x86 i x64; tę opcję kompilatora nie jest dostępna w kompilatorach przeznaczonych dla procesorów ARM.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Otwórz **właściwości konfiguracji** > **C/C++** > **ogólne** stronę właściwości.

1. Modyfikowanie **formatu informacji debugowania** właściwości. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)

