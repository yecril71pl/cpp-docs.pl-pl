---
title: /Z7, /Zi, /ZI (Format informacji o debugowaniu)
ms.date: 04/08/2019
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
ms.openlocfilehash: aeaf435874b6d6b9dbc8a3d12ec06d38bf33aaae
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078261"
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7, /Zi, /ZI (Format informacji o debugowaniu)

Określa typ informacji o debugowaniu utworzonych dla programu oraz tego, czy te informacje są przechowywane w plikach obiektów, czy w pliku bazy danych programu (PDB).

## <a name="syntax"></a>Składnia

> **/Z**{**7**|**i**|**i**}

## <a name="remarks"></a>Uwagi

Gdy kod jest kompilowany i skompilowany w trybie debugowania, kompilator tworzy nazwy symboli dla funkcji i zmiennych, informacje o typie i lokalizacje numerów wierszy do użycia przez debuger. Te informacje dotyczące debugowania symbolicznego mogą być zawarte w plikach obiektów (. obj) generowanych przez kompilator lub w osobnym pliku PDB (plik. pdb) dla pliku wykonywalnego.  Opcje formatu informacji debugowania są opisane w poniższych sekcjach.

### <a name="none"></a>None

Domyślnie, jeśli nie określono opcji Format informacji debugowania, kompilator nie tworzy informacji o debugowaniu, więc kompilacja jest szybsza.

### <a name="z7"></a>/Z7

Opcja **/Z7** tworzy pliki obiektów, które zawierają również pełne symboliczne informacje o debugowaniu do użycia z debugerem. Te pliki obiektów i skompilowany plik wykonywalny mogą być znacznie większe niż pliki, które nie mają informacji o debugowaniu. Symboliczne informacje debugowania obejmują nazwy i typy zmiennych, a także funkcje i numery wierszy. Nie jest tworzony żaden plik PDB.

W przypadku dystrybutorów wersji debugowania bibliotek innych firm istnieje możliwość, że nie ma pliku PDB. Jednak pliki obiektów dla wszystkich prekompilowanych nagłówków są niezbędne podczas fazy linku biblioteki i debugowania. Jeśli istnieje tylko informacja o typie (i brak kodu) w pliku obiektu PCH, należy również użyć opcji [/yl (wstrzyknięcie odwołania PCH dla biblioteki debugowania)](yl-inject-pch-reference-for-debug-library.md) , która jest domyślnie włączona podczas kompilowania biblioteki.

Przestarzała opcja [/GM (Włącz minimalną](gm-enable-minimal-rebuild.md) ponowną kompilację) nie jest dostępna, jeśli określono **/Z7** .

### <a name="zi"></a>/Zi

Opcja **/Zi** generuje oddzielny plik PDB, który zawiera wszystkie symboliczne informacje o debugowaniu do użycia z debugerem. Informacje o debugowaniu nie są zawarte w plikach obiektów lub pliku wykonywalnym, co sprawia, że są znacznie mniejsze.

Korzystanie z **/Zi** nie wpływa na optymalizacje. **/Zi** jest jednak oznacza **/Debug**; Aby uzyskać więcej informacji, zobacz [/debug (generowanie informacji o debugowaniu)](debug-generate-debug-info.md) .

Po określeniu zarówno **/Zi** , jak i **/CLR**atrybut <xref:System.Diagnostics.DebuggableAttribute> nie jest umieszczany w metadanych zestawu. Jeśli chcesz, musisz określić ją w kodzie źródłowym. Ten atrybut może mieć wpływ na wydajność środowiska uruchomieniowego aplikacji. Aby uzyskać więcej informacji o tym, jak atrybut **możliwością debugowania** ma wpływ na wydajność i jak można zmodyfikować wpływ na wydajność, zobacz [Ułatw debugowanie obrazu](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug).

Kompilator nazywa plik PDB pliku *Project*. pdb. Jeśli kompilujesz plik poza projektem, kompilator tworzy plik PDB o nazwie VC*x*. pdb, gdzie *x* jest konkatenacją głównego i pomocniczego numeru wersji używanej przez wersję kompilatora. Kompilator osadza nazwę PDB i identyfikujący podpis sygnatury czasowej w każdym pliku obiektu utworzonym za pomocą tej opcji, który wskazuje na lokalizację symboliczną i informacje o liczbie wierszy. Nazwa i podpis w pliku PDB muszą być zgodne z plikiem wykonywalnym dla symboli, które mają zostać załadowane w debugerze. Debuger WinDBG może załadować niezgodne symbole przy użyciu polecenia `.symopt+0x40`. Program Visual Studio nie ma podobnej opcji do ładowania niezgodnych symboli.

Jeśli utworzysz bibliotekę z obiektów, które zostały skompilowane przy użyciu **/Zi**, skojarzony plik. pdb musi być dostępny, gdy biblioteka jest połączona z programem. W ten sposób, jeśli dystrybuujesz bibliotekę, musisz również rozproszyć plik PDB. Aby utworzyć bibliotekę, która zawiera informacje o debugowaniu bez używania plików PDB, należy wybrać opcję **/Z7** . Jeśli używasz opcji prekompilowanych nagłówków, informacje debugowania dla prekompilowanego nagłówka i reszty kodu źródłowego są umieszczane w pliku PDB.

### <a name="zi"></a>/ZI

Opcja **/Zi** jest podobna do **/Zi**, ale tworzy plik PDB w formacie, który obsługuje funkcję [Edytuj i Kontynuuj](/visualstudio/debugger/edit-and-continue-visual-cpp) . Aby korzystać z funkcji Edytuj i Kontynuuj debugowanie, należy użyć tej opcji. Funkcja Edytuj i Kontynuuj jest przydatna w przypadku produktywności dla deweloperów, ale może powodować problemy w rozmiarze kodu, wydajności i zgodności kompilatora. Ponieważ większość optymalizacji jest niezgodna z funkcją Edytuj i Kontynuuj, użycie **/Zi** wyłącza wszystkie instrukcje `#pragma optimize` w kodzie. Opcja **/Zi** jest również niezgodna z użyciem [ &#95; &#95;wstępnie zdefiniowanego&#95; &#95; makra wiersza](../../preprocessor/predefined-macros.md); kod skompilowany za pomocą elementu **/Zi** nie może używać **&#95; &#95;linii&#95;** jako argumentu szablonu bez typu,  **&#95; &#95;chociaż&#95; wiersz** może być używany w rozwinięcia makra.

Opcja **/Zi** wymusza zarówno [/Gy (Włącz łączenie na poziomie funkcji)](gy-enable-function-level-linking.md) , jak i [/FC (pełną ścieżkę pliku kodu źródłowego w diagnostyce)](fc-full-path-of-source-code-file-in-diagnostics.md) , który będzie używany w kompilacji.

**/Zi** nie jest zgodna z [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](clr-common-language-runtime-compilation.md).

> [!NOTE]
> Opcja **/Zi** jest dostępna tylko w kompilatorach przeznaczonych dla procesorów x86 i x64; Ta opcja kompilatora nie jest dostępna w kompilatorach przeznaczonych dla procesorów ARM.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Otwórz okno **Właściwości konfiguracji** > **C/C++**  > **Ogólne** strony właściwości.

1. Zmodyfikuj właściwość **Format informacji o debugowaniu** . Wybierz **przycisk OK** , aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
