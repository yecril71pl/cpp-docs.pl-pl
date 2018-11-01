---
title: 'Porady: włączenie funkcji IntelliSense dla projektów plików reguł programu make'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCNMakeTool.IntelliSense
helpviewer_keywords:
- Makefile projects, IntelliSense
- IntelliSense, Makefile projects
ms.assetid: 9443f453-f18f-4f12-a9a1-ef9dbf8b188f
ms.openlocfilehash: 80a4696856fea46c7749cfeb120535dcdab86282
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434674"
---
# <a name="how-to-enable-intellisense-for-makefile-projects"></a>Porady: włączenie funkcji IntelliSense dla projektów plików reguł programu make

IntelliSense nie może działać w środowisku IDE dla projektów plików reguł programu make Visual C++, gdy projekt pewnych ustawień lub opcje kompilatora są nieprawidłowo skonfigurowana. Ta procedura umożliwia konfigurowanie projektów plików reguł programu make Visual C++, tak aby technologia IntelliSense działa w przypadku projektów plików reguł programu make otwarte w środowisku programowania Visual Studio.

### <a name="to-enable-intellisense-for-makefile-projects-in-the-ide"></a>Aby włączyć technologię IntelliSense dla projektów plików reguł programu make w środowisku IDE

1. Otwórz **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji** węzła.

1. Wybierz **NMake** właściwości strony, a następnie zmodyfikuj właściwości w obszarze **IntelliSense** odpowiednio.

   - Ustaw **definicje preprocesora** właściwości, aby zdefiniować wszystkie symbole, preprocesor w projekt pliku reguł programu make. Zobacz [/D (definicje preprocesora)](../build/reference/d-preprocessor-definitions.md), aby uzyskać więcej informacji.

   - Ustaw **obejmują ścieżkę wyszukiwania** właściwości w celu określenia listy katalogów, które kompilator będzie przeszukiwał, aby rozwiązać odwołania do plików, które są przekazywane do dyrektywy preprocesora do projektu pliku reguł programu make. Zobacz [/I (dodatkowe katalogi dołączenia)](../build/reference/i-additional-include-directories.md), aby uzyskać więcej informacji.

         For projects that are built using CL.EXE from a Command Window, set the **INCLUDE** environment variable to specify directories that the compiler will search to resolve file references that are passed to preprocessor directives in your makefile project.

   - Ustaw **wymuszone obejmuje** właściwości w celu określenia, który nagłówek plików do przetworzenia podczas kompilowania projektu pliku reguł programu make. Zobacz [/FI (nazwij wymuszone obejmują plik)](../build/reference/fi-name-forced-include-file.md), aby uzyskać więcej informacji.

   - Ustaw **ścieżkę wyszukiwania zestawu** właściwości w celu określenia listy katalogów, które kompilator będzie przeszukiwał, aby rozwiązać odwołania do zestawów .NET w projekcie. Zobacz [/AI (Określ katalogi metadanych)](../build/reference/ai-specify-metadata-directories.md), aby uzyskać więcej informacji.

   - Ustaw **wymuszone za pomocą zestawów** właściwości w celu określenia, które zestawy .NET do przetworzenia podczas kompilowania projektu pliku reguł programu make. Zobacz [/FU (nazwij wymuszone #using)](../build/reference/fu-name-forced-hash-using-file.md), aby uzyskać więcej informacji.

   - Ustaw **dodatkowe opcje** właściwość, aby określić dodatkowe przełączniki kompilatora ma być używany przez funkcję IntelliSense, podczas analizowania plików C++.

1. Kliknij przycisk **OK** zamknąć na stronach właściwości.

1. Użyj **Zapisz wszystko** polecenie, aby zapisać ustawienia modyfikacji projektu.

Przy następnym otwarciu projektu pliku reguł programu make w środowisku programowania Visual Studio Uruchom **czyste rozwiązanie** polecenia i następnie **Kompiluj rozwiązanie** polecenia projektu pliku reguł programu make. Funkcja IntelliSense powinny działać poprawnie w środowisku IDE.

## <a name="see-also"></a>Zobacz też

[Korzystanie z funkcji IntelliSense](/visualstudio/ide/using-intellisense)<br>
[NMAKE — dokumentacja](../build/nmake-reference.md)<br>
[Instrukcje: tworzenie projektu C++ z istniejącego kodu](../ide/how-to-create-a-cpp-project-from-existing-code.md)