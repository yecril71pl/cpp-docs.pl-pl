---
title: Właściwości konsolidatora projektu Clang (Android C++)
ms.date: 10/23/2017
ms.assetid: 66e88848-116c-4eb0-bc57-183394d35b57
f1_keywords:
- VC.Project.VCLinkerTool.Clang.OutputFile
- VC.Project.VCLinkerTool.Clang.Soname
- VC.Project.VCLinkerTool.Clang.ShowProgress
- VC.Project.VCLinkerTool.Clang.Version
- VC.Project.VCLinkerTool.Clang.VerboseOutput
- VC.Project.VCLinkerTool.Clang.IncrementalLink
- VC.Project.VCLinkerTool.Clang.SharedLibrarySearchPath
- VC.Project.VCLinkerTool.Clang.AdditionalLibraryDirectories
- VC.Project.VCLinkerTool.Clang.UnresolvedReferences
- VC.Project.VCLinkerTool.Clang.OptimizeForMemory
- VC.Project.VCLinkerTool.Clang.IgnoreDefaultLibraryNames
- VC.Project.VCLinkerTool.Clang.ForceSymbolReferences
- VC.Project.VCLinkerTool.Clang.ForceFileOutput
- VC.Project.VCLinkerTool.Clang.OmitDebuggerSymbolInformation
- VC.Project.VCLinkerTool.Clang.GenerateMapFile
- VC.Project.VCLinkerTool.Clang.Relocation
- VC.Project.VCLinkerTool.Clang.FunctionBinding
- VC.Project.VCLinkerTool.Clang.NoExecStackRequired
- VC.Project.VCLinkerTool.Clang.WholeArchive
- VC.Project.VCLinkerTool.Clang.AdditionalOptionsPage
- VC.Project.VCLinkerTool.Clang.AdditionalDependencies
- VC.Project.VCLinkerTool.Clang.LibraryDependencies
ms.openlocfilehash: 55b944040157d13741b992f4ec66c35d1b117d95
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446528"
---
# <a name="clang-linker-properties-android-c"></a>Właściwości konsolidatora Clang ( C++Android)

| Właściwość | Opis | Decyzji |
|--|--|--|
| Plik wyjściowy | Opcja zastępuje domyślną nazwę i lokalizację programu tworzonego przez konsolidatora. (-o) |
| Pokaż postęp | Drukuje wiadomości dotyczące postępu konsolidatora. |
| Wersja | Opcja-Version nakazuje konsolidatorowi umieszczenie numeru wersji w nagłówku pliku wykonywalnego. |
| Włącz pełne dane wyjściowe | Opcja-verbose nakazuje konsolidatorowi wyprowadzanie pełnych komunikatów na potrzeby debugowania. |
| Włącz konsolidację przyrostową | Opcja nakazuje konsolidatorowi włączenie konsolidacji przyrostowej. |
| Ścieżka wyszukiwania biblioteki udostępnionej | Zezwala użytkownikowi na wypełnienie ścieżki wyszukiwania biblioteki udostępnionej. |
| Dodatkowe katalogi biblioteki | Zezwala użytkownikowi na przesłanianie ścieżki biblioteki środowiskowej. (-L folder). |
| Zgłoś nierozpoznane odwołania do symboli | Ta opcja umożliwia zgłaszanie nierozpoznanych odwołań do symboli. |
| Optymalizuj pod kątem użycia pamięci | Optymalizuj pod kątem użycia pamięci przez odczytanie tabel symboli stosownie do potrzeb. |
| Ignoruj określone biblioteki domyślne | Określa co najmniej jedną nazwę bibliotek domyślnych do zignorowania. |
| Wymuszaj odwołania do symboli | Wymuś wprowadzenie symbolu w pliku wyjściowym jako niezdefiniowanego symbolu. |
| Informacje o symbolach debugera | Informacje o symbolach debugera z pliku wyjściowego. | **Uwzględnij wszystko**<br /><br />**Pomiń niepotrzebne symbole na potrzeby przetwarzania relokacji**<br /><br />**Pomiń tylko informacje o symbolach debugera**<br /><br />**Pomiń wszystkie informacje o symbolach** |
| Informacje o symbolach debugera pakietów | Rozpakuj informacje o symbolach debugera przed opakowaniem.  Kopia oryginalnego pliku binarnego jest używana do debugowania. |
| Nazwa pliku mapy | Opcja map nakazuje konsolidatorowi utworzenie pliku mapy o nazwie określonej przez użytkownika. |
| Oznacz zmienne jako tylko do odczytu po relokacji | Ta opcja oznacza zmienne jako tylko do odczytu po relokacji. |
| Włącz natychmiastowe powiązanie funkcji | Ta opcja oznacza obiekt do natychmiastowego powiązania funkcji. |
| Wymagaj stosu wykonywalnego | Ta opcja oznacza dane wyjściowe jako niewymagające stosu wykonywalnego. |
| Całe archiwum | Całe archiwum używa całego kodu ze źródeł i dodatkowych zależności. |
| Opcje dodatkowe | Opcje dodatkowe. |
| {1&gt;Dodatkowe zależności&lt;1} | Określa dodatkowe elementy do dodania do wiersza polecenia konsolidacji. |
| Zależności biblioteki | Ta opcja umożliwia określenie dodatkowych bibliotek, które mają zostać dodane do wiersza polecenia konsolidatora. Dodatkowe biblioteki są dodawane na końcu wiersza polecenia konsolidatora z *biblioteki lib* i kończyć z rozszerzeniem. *a* lub *.*  (-lFILE) |
