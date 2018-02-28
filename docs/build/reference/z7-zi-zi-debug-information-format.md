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
ms.openlocfilehash: 3b55c5ea77b752d4adac8d74abaed245b4d19821
ms.sourcegitcommit: 3038840ca6e4dea01accf733436b99d19ff6c930
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2018
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7, /Zi, /ZI (Format informacji o debugowaniu)

Określa typ informacji o debugowaniu stworzonej dla Twojego programu oraz czy te informacje są przechowywane w plikach obiektu lub plik programu (PDB) bazy danych.

## <a name="syntax"></a>Składnia

> **/Z**{**7**|**i**|**I**}  

## <a name="remarks"></a>Uwagi

Podczas kompilacji kodu i wbudowane w trybie debugowania, kompilator generuje nazwy symbolu funkcje i zmienne, informacje o typie i lokalizacje numer wiersza do użytku przez debuger. Ta symboliczna informacja o debugowaniu może być uwzględniane w plikach obiektu (.obj pliki) utworzone przez kompilator lub w oddzielnym pliku PDB (pliku .pdb) dla pliku wykonywalnego.  W poniższych sekcjach opisano opcje format informacji debugowania.  
  
### <a name="none"></a>Brak

Domyślnie jeśli żadna opcja nie format informacji debugowania jest określona, kompilator tworzy żadnych informacji debugowania, więc kompilacji jest szybsze.  
  
### <a name="z7"></a>/Z7

**/Z7** opcja tworzy pliki obiektów, zawierające pełne symboliczne informacje o debugowaniu do użycia z debugera. Te pliki obiektu i skompilowany plik wykonywalny może być znacznie większe niż pliki, które mają żadnych informacji debugowania. Symboliczna informacja o debugowaniu zawiera nazwy i rodzaje zmiennych, jak również funkcje i numery wierszy. Plik PDB nie jest generowany.

Dystrybutorów debugowania wersje bibliotek innych firm jest zaletą nie ma plików PDB. Jednak plików obiektów dla dowolnego prekompilowane nagłówki są niezbędne w fazie link biblioteki, a także do debugowania. Jeśli istnieje tylko w pliku obiektu .pch wpisz informacji (i żaden kod), należy również użyć [/Yl (Wstaw Odnośnik PCH dla bibliotek debugowania)](../../build/reference/yl-inject-pch-reference-for-debug-library.md) opcja, która jest włączana domyślnie podczas tworzenia biblioteki.

[/GM ponowną (Włącz minimalnego odbudować)](../../build/reference/gm-enable-minimal-rebuild.md) opcja jest niedostępna, gdy **/z7** jest określona.

### <a name="zi"></a>/Zi

**/Zi** opcja tworzy oddzielny plik PDB, który zawiera wszystkie symboliczna informacja o debugowaniu do użycia z debugera. Informacje o debugowaniu nie znajduje się w plikach obiektu lub pliku wykonywalnego, który sprawia, że ich znacznie mniejszy.

Użycie **/zi** nie ma wpływu na optymalizację. Jednak **/zi** oznacza **/debug**; zobacz [/Debug (generowanie informacji debugowania)](../../build/reference/debug-generate-debug-info.md) Aby uzyskać więcej informacji.


Po określeniu zarówno **/zi** i **/CLR**, <xref:System.Diagnostics.DebuggableAttribute> atrybut nie jest umieszczany w metadanych zestawu. Jeśli chcesz, muszą określić go w kodzie źródłowym. Ten atrybut może wpłynąć na wydajność środowiska uruchomieniowego aplikacji. Aby uzyskać więcej informacji na temat sposobu **Debuggable** atrybutu wpływa na wydajność i można zmodyfikować jego wpływ na wydajność, zobacz [ułatwiając obraz do debugowania](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug).

Kompilator nazwy pliku PDB *projektu*.pdb. Jeśli kompilacja pliku poza projektem, kompilator tworzy plik PDB o nazwie VC*x*.pdb, gdzie *x* jest złączeniem numer wersji głównej i pomocniczej wersji kompilatora w użyciu. Kompilator osadza nazwę pliku PDB i identyfikowania podpisu oznaczony znacznikiem czasowym w każdym pliku obiektu utworzone za pomocą tej opcji, wskazujący debugera do lokalizacji informacje symboliczne i numerów wierszy. Nazwy i podpisu w pliku PDB musi być zgodny plik wykonywalny dla symboli do załadowania w debugerze. Debuger WinDBG można załadować symboli niedopasowanych przy użyciu `.symopt+0x40` polecenia. Program Visual Studio nie ma opcji podobny załadować symbole niezgodne.

Jeśli tworzenie biblioteki z obiektów, które zostały skompilowane przy użyciu **/zi**, plik PDB skojarzone musi być dostępny, gdy biblioteka jest połączone z programem. W związku z tym jeśli dystrybucji biblioteki należy również rozproszyć pliku PDB. Aby utworzyć biblioteki, który zawiera informacje o debugowaniu bez użycia PDB, pliki, należy wybrać **/z7** opcji. Jeśli używasz opcji prekompilowanych nagłówków informacji debugowania dla zarówno prekompilowanego nagłówka, jak i pozostałej części kodu źródłowego znajduje się w pliku PDB.

### <a name="zi"></a>/ZI

**/Zi** opcja jest podobna do **/zi**, ale generuje plik PDB w formacie, który obsługuje [Edytuj i Kontynuuj](/visualstudio/debugger/edit-and-continue-visual-cpp) funkcji. Aby użyć Edytuj i Kontynuuj debugowanie funkcji, należy użyć tej opcji. Funkcja Edytuj i Kontynuuj jest przydatne w przypadku produktywność deweloperów, ale mogą powodować problemy w zgodność rozmiar, wydajności i kompilatora kodu. Ponieważ większość optymalizacje są niezgodne z opcją Edytuj i Kontynuuj, za pomocą **/zi** wyłączy wszystkie `#pragma optimize` instrukcje w kodzie. **/Zi** opcja również jest niezgodna z użyciem [&#95; &#95; WIERSZ &#95; &#95; wstępnie zdefiniowane makro](../../preprocessor/predefined-macros.md); kodu skompilowanego z **/zi** nie można użyć **&#95; &#95; WIERSZ &#95; &#95;**  jako argument szablonu bez typu, chociaż **&#95; &#95; WIERSZ &#95; &#95;**  mogą być używane w rozwinięcia makra są.

**/Zi** opcja wymusza zarówno [/Gy (Włącz funkcję łączenia na poziomie)](../../build/reference/gy-enable-function-level-linking.md) i [/FC (pełna ścieżka z pliku kodu źródłowego w diagnostyce)](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md) opcje do użycia w Twojej kompilacji.

**/ Zi** nie jest zgodny z [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).

> [!NOTE]
> **/Zi** opcja jest dostępna tylko w kompilatory przeznaczonych dla procesorów x86 i x64; tej opcji kompilatora nie jest dostępna w kompilatory przeznaczonych dla procesorów ARM.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Otwórz **właściwości konfiguracji** > **C/C++** > **ogólne** strony właściwości.

1. Modyfikowanie **Format informacji debugowania** właściwości. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora](../../build/reference/compiler-options.md)  
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)  

