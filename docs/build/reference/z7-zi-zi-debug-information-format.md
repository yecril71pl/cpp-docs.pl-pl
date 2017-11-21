---
title: "— - Zi, - ZI Z7, (Format informacji o debugowaniu) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.DebugInformationFormat
- /zi
- /z7
- VC.Project.VCCLWCECompilerTool.DebugInformationFormat
dev_langs: C++
helpviewer_keywords:
- C7 compatible compiler option [C++]
- -Zl compiler option [C++]
- Debug Information Format compiler option
- ZI compiler option
- -Zi compiler option [C++]
- /ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debug information files
- Zi compiler option [C++]
- none compiler option [C++]
- /Zi compiler option [C++]
- program database compiler option [C++]
- full symbolic debugging information
- /Z7 compiler option [C++]
- line numbers only compiler option [C++]
- cl.exe compiler, debugging options
- -Z7 compiler option [C++]
ms.assetid: ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 782420e674d6101f49e2b361c888a8f4b0b4c1ec
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7, /Zi, /ZI (Format informacji o debugowaniu)
Wybierz typ informacji o debugowaniu stworzonej dla Twojego programu oraz czy te informacje są przechowywane w plikach obiektu (.obj) lub w bazie danych programu (PDB).  
  
## <a name="syntax"></a>Składnia  
  
```  
/Z{7|i|I}  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcje zostały opisane w poniższej tabeli.  
  
 Brak  
 Tworzy żadnych informacji debugowania, więc kompilacji jest szybsze.  
  
 **/ Z7**  
 Tworzy plik .obj zawierający pełne symboliczne informacje o debugowaniu do użycia z debugera. Symboliczna informacja o debugowaniu zawiera nazwy i rodzaje zmiennych, jak również funkcje i numery wierszy. Plik PDB nie jest generowany.  
  
 Dystrybutorów bibliotek innych firm jest zaletą nie ma plików PDB. Pliki .obj prekompilowane nagłówki są jednak niezbędne w fazie łącza i debugowania. Jeśli istnieje tylko w .pch — pliki obiektu wpisz informacje (i żaden kod), również należy skompilować z [/Yl (Wstaw Odnośnik PCH dla bibliotek debugowania)](../../build/reference/yl-inject-pch-reference-for-debug-library.md).  
  
 **/ Zi**  
 Tworzy bazę danych programu (PDB) zawierający informacje o typie i symboliczną informację o debugowaniu do użycia z debugera. Symboliczna informacja o debugowaniu zawiera nazwy i rodzaje zmiennych, jak również funkcje i numery wierszy.  
  
 **/ Zi** nie ma wpływu na optymalizację. Jednak **/zi** oznacza **/debug**; zobacz [/Debug (generowanie informacji debugowania)](../../build/reference/debug-generate-debug-info.md) Aby uzyskać więcej informacji.  
  
 Informacje o typie znajduje się w pliku PDB, a nie w pliku obj..  
  
 Można użyć [/GM ponowną (Włącz minimalnego odbudować)](../../build/reference/gm-enable-minimal-rebuild.md) z **/zi**, podczas gdy **/GM ponowną** nie jest dostępna podczas kompilowania za pomocą **/z7**.  
  
 Podczas kompilowania za pomocą **/zi** i **/CLR**, <xref:System.Diagnostics.DebuggableAttribute> atrybutu nie zostaną umieszczone w metadanych zestawu; należy określić go w kodzie źródłowym, jeśli chcesz. Ten atrybut może wpłynąć na wydajność środowiska uruchomieniowego aplikacji. Aby uzyskać więcej informacji o sposobie atrybut Debugowalny wpływa na wydajność i jak można zmodyfikować jego wpływ na wydajność, zobacz [ułatwiając obraz do debugowania](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug).  
  
 **/ ZI**  
 Tworzy bazę danych programu, jak opisano powyżej, w formacie, który obsługuje funkcję Edytuj i Kontynuuj. Jeśli chcesz użyć Edytuj i Kontynuuj, debugowanie, musi użyć tej opcji. Ponieważ większość optymalizacje są niezgodne z opcją Edytuj i Kontynuuj, za pomocą **/zi** wyłączy wszystkie `#pragma optimize` instrukcje w kodzie.  
  
 **/ Zi** powoduje, że [/Gy (Włącz funkcję łączenia na poziomie)](../../build/reference/gy-enable-function-level-linking.md) i [/FC (pełna ścieżka z pliku kodu źródłowego w diagnostyce)](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md) do użycia w Twojej kompilacji.  
  
 **/ Zi** nie jest zgodny z [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
> [!NOTE]
>  **/ Zi** jest dostępna tylko w kompilatory przeznaczonych dla procesorów x86 i x64; tej opcji kompilatora nie jest dostępna w kompilatory przeznaczonych dla procesorów ARM.  
  
 Kompilator nazwy bazy danych programu *projektu*.pdb. Jeśli kompilacja pliku bez projektu kompilator tworzy bazę danych o nazwie VC*x*0.pdb. gdy *x* jest wersja główna [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] w użyciu. Kompilator osadza nazwę pliku PDB w każdym pliku .obj utworzone za pomocą tej opcji, wskazujące debugera do lokalizacji informacje symboliczne i numerów wierszy. Tej opcji pliki .obj będzie mniejsza, ponieważ informacje o debugowaniu są przechowywane w pliku PDB, a nie w plikach .obj.  
  
 Jeśli z obiektów, które zostały skompilowane przy użyciu tej opcji tworzenia biblioteki, plik PDB skojarzone musi być dostępny powiązane biblioteki programu. W związku z tym jeśli dystrybucji biblioteki, musisz przeprowadzić dystrybucję pliku PDB.  
  
 Aby utworzyć bibliotekę, która zawiera informacje o debugowaniu bez użycia .pdb, pliki, należy wybrać kompilatora C 7.0 zgodnego (**/z7**) opcja. Jeśli używasz opcji prekompilowanych nagłówków informacji debugowania dla zarówno prekompilowanego nagłówka, jak i pozostałej części kodu źródłowego znajduje się w pliku PDB. **/Yd** opcja została zignorowana w przypadku wybrania opcji programu bazy danych.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **ogólne** strony właściwości.  
  
4.  Modyfikowanie **Format informacji debugowania** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)