---
title: /Z7, /Zi, /ZI (Format informacji o debugowaniu)
ms.date: 07/06/2020
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
ms.openlocfilehash: bc3fd9c065219a128e29290084b1e1fb51fc773e
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058597"
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7, /Zi, /ZI (Format informacji o debugowaniu)

**`/Z7`** **`/Zi`** Opcje kompilatora, i **`/ZI`** określają typ informacji o debugowaniu utworzonych dla programu oraz informacje o tym, czy są one przechowywane w plikach obiektów czy w pliku bazy danych programu (PDB).

## <a name="syntax"></a>Składnia

> **`/Z7`**\
> **`/Zi`**\
> **`/ZI`**

## <a name="remarks"></a>Uwagi

Po określeniu opcji debugowania kompilator tworzy nazwy symboli dla funkcji i zmiennych, informacje o typie i lokalizacje wierszy do użycia przez debuger. Te informacje dotyczące debugowania symbolicznego mogą być zawarte w plikach obiektów ( *`.obj`* plików) tworzonych przez kompilator lub w osobnym pliku PDB ( *`.pdb`* pliku) dla pliku wykonywalnego. Opcje formatu informacji debugowania są opisane w poniższych sekcjach.

### <a name="none"></a>Brak

Domyślnie, jeśli nie określono opcji Format informacji debugowania, kompilator nie tworzy informacji o debugowaniu, więc kompilacja jest szybsza.

### <a name="z7"></a>/Z7

**`/Z7`** Opcja generuje pliki obiektów, które zawierają również pełne informacje symboliczne debugowania do użycia z debugerem. Te pliki obiektów i wszystkie biblioteki skompilowane z nich mogą być znacznie większe niż pliki, które nie mają informacji o debugowaniu. Symboliczne informacje debugowania obejmują nazwy i typy zmiennych, funkcje i numery wierszy. Kompilator nie tworzy pliku PDB. Jednak plik PDB można nadal generować z tych plików lub bibliotek obiektów, jeśli konsolidator jest przekazaniem **`/DEBUG`** opcji.

W przypadku dystrybutorów wersji debugowania bibliotek innych firm istnieje możliwość, że nie ma pliku PDB. Jednak pliki obiektów dla wszystkich prekompilowanych nagłówków są niezbędne podczas fazy linku biblioteki i debugowania. Jeśli w pliku obiektu nie ma informacji o typie (i w kodzie) *`.pch`* , należy również użyć opcji [ `/Yl` (wstrzyknięcie odwołania PCH dla biblioteki debugowania)](yl-inject-pch-reference-for-debug-library.md) , która jest domyślnie włączona podczas kompilowania biblioteki.

Opcja przestarzałe [ `/Gm` (Włącz minimalną](gm-enable-minimal-rebuild.md) ponowną kompilację) jest niedostępna, gdy **`/Z7`** jest określony.

### <a name="zi"></a>/Zi

**`/Zi`** Opcja generuje oddzielny plik PDB, który zawiera wszystkie symboliczne informacje o debugowaniu do użycia z debugerem. Informacje o debugowaniu nie są zawarte w plikach obiektów lub pliku wykonywalnym, co sprawia, że są znacznie mniejsze.

Użycie **`/Zi`** nie wpływa na optymalizacje. Jednak **`/Zi`** jest to oznacza **`/debug`** . Aby uzyskać więcej informacji, zobacz [ `/DEBUG` (generowanie informacji o debugowaniu)](debug-generate-debug-info.md).

W przypadku określenia obu **`/Zi`** i **`/clr`** <xref:System.Diagnostics.DebuggableAttribute> atrybut nie jest umieszczany w metadanych zestawu. Jeśli chcesz, musisz określić ją w kodzie źródłowym. Ten atrybut może mieć wpływ na wydajność środowiska uruchomieniowego aplikacji. Aby uzyskać więcej informacji o tym `Debuggable` , jak atrybut ma wpływ na wydajność i jak można zmodyfikować wpływ na wydajność, zobacz [Ułatw debugowanie obrazu](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug).

Kompilator nazywa plik PDB *`<project>.pdb`* , gdzie *`<project>`* jest nazwą projektu. Jeśli kompilujesz plik poza projektem, kompilator tworzy plik PDB o nazwie *`VC<x>.pdb`* , gdzie *`<x>`* jest konkatenacją głównego i pomocniczego numeru wersji używanej przez wersję kompilatora. Kompilator osadza nazwę PDB i identyfikujący podpis sygnatury czasowej w każdym pliku obiektu utworzonym przy użyciu tej opcji. Ta nazwa i sygnatura wskazują na lokalizację symboliczną i informacje o numerze wiersza. Nazwa i podpis w pliku PDB muszą być zgodne z plikiem wykonywalnym dla symboli, które mają zostać załadowane w debugerze. Debuger WinDBG może ładować niezgodne symbole przy użyciu **`.symopt+0x40`** polecenia. Program Visual Studio nie ma podobnej opcji do ładowania niezgodnych symboli.

Jeśli utworzysz bibliotekę z obiektów, które zostały skompilowane przy użyciu **`/Zi`** , skojarzony plik PDB musi być dostępny, gdy biblioteka jest połączona z programem. Oznacza to, że w przypadku dystrybucji biblioteki należy również rozproszyć plik PDB. Aby utworzyć bibliotekę, która zawiera informacje o debugowaniu bez używania plików PDB, należy wybrać **`/Z7`** opcję. Jeśli używasz opcji prekompilowanych nagłówków, informacje debugowania dla prekompilowanego nagłówka i reszty kodu źródłowego są umieszczane w pliku PDB.

### <a name="zi"></a>/ZI

**`/ZI`** Opcja jest podobna do **`/Zi`** , ale tworzy plik PDB w formacie, który obsługuje funkcję [Edytuj i Kontynuuj](/visualstudio/debugger/edit-and-continue-visual-cpp) . Aby korzystać z funkcji Edytuj i Kontynuuj debugowanie, należy użyć tej opcji. Funkcja Edytuj i Kontynuuj jest przydatna w przypadku produktywności dla deweloperów, ale może powodować problemy w rozmiarze kodu, wydajności i zgodności kompilatora. Ponieważ większość optymalizacji jest niezgodna z funkcją Edytuj i Kontynuuj, użycie **`/ZI`** powoduje wyłączenie wszelkich `#pragma optimize` instrukcji w kodzie. **`/ZI`** Opcja jest również niezgodna z użyciem [ `__LINE__` wstępnie zdefiniowanego makra](../../preprocessor/predefined-macros.md); kod skompilowany za pomocą **`/ZI`** nie może używać `__LINE__` jako argumentu szablonu bez typu, chociaż `__LINE__` może być używany do rozwinięcia makra.

**`/ZI`** Opcja wymusza użycie opcji [ `/Gy` (Włącz łączenie na poziomie funkcji)](gy-enable-function-level-linking.md) i [ `/FC` (Pełna ścieżka pliku kodu źródłowego w diagnostyce)](fc-full-path-of-source-code-file-in-diagnostics.md) , który ma być używany w kompilacji.

**`/ZI`** jest niezgodny z [ `/clr` (Kompilacja środowiska uruchomieniowego języka wspólnego)](clr-common-language-runtime-compilation.md).

> [!NOTE]
> Ta **`/ZI`** opcja jest dostępna tylko w kompilatorach przeznaczonych dla procesorów x86 i x64. Ta opcja kompilatora nie jest dostępna w kompilatorach przeznaczonych dla procesorów ARM.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Otwórz **Configuration Properties**  >  stronę właściwości ogólne**C/C++** właściwości konfiguracji  >  **General** .

1. Zmodyfikuj właściwość **Format informacji o debugowaniu** . Wybierz **przycisk OK** , aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
