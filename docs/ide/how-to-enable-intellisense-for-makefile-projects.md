---
title: 'Porady: włączenie funkcji IntelliSense dla projektów Makefile | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCNMakeTool.IntelliSense
dev_langs:
- C++
helpviewer_keywords:
- Makefile projects, IntelliSense
- IntelliSense, Makefile projects
ms.assetid: 9443f453-f18f-4f12-a9a1-ef9dbf8b188f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9de79d56c6e8b6e496c0e7988ada07ed7595ea70
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-intellisense-for-makefile-projects"></a>Porady: włączenie funkcji IntelliSense dla projektów plików reguł programu make
IntelliSense nie działają w IDE dla projektów Visual C++ makefile, gdy projekt niektórych ustawień lub opcji kompilatora jest nieprawidłowo skonfigurowana. Ta procedura umożliwia konfigurowanie projektów makefile Visual C++, dzięki czemu IntelliSense działa, gdy projekty pliku reguł programu make są otwarte w środowisku projektowym Visual Studio.  
  
### <a name="to-enable-intellisense-for-makefile-projects-in-the-ide"></a>Aby włączyć IntelliSense dla projektów makefile w środowisku IDE  
  
1.  Otwórz **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzła.  
  
3.  Wybierz **NMake** właściwości strony, a następnie zmodyfikuj właściwości pod **IntelliSense** odpowiednio.  
  
    -   Ustaw **definicje preprocesora** właściwości, aby zdefiniować żadnych symboli preprocesora projektu pliku reguł programu make. Zobacz [/D (definicje preprocesora)](../build/reference/d-preprocessor-definitions.md), aby uzyskać więcej informacji.  
  
    -   Ustaw **obejmują ścieżki wyszukiwania** właściwości w celu określenia listy katalogów, które kompilator będzie wyszukiwać można rozpoznać odwołania do pliku, które są przekazywane do dyrektywy preprocesora projektu pliku reguł programu make. Zobacz [/I (dodatkowe katalogi dołączenia)](../build/reference/i-additional-include-directories.md), aby uzyskać więcej informacji.  
  
         Dla projektów, które są tworzone przy użyciu CL. Ustaw EXE z okna polecenia **INCLUDE** zmiennej środowiskowej, aby określić katalogi, które kompilator będzie wyszukiwać można rozpoznać odwołania do pliku, które są przekazywane do dyrektywy preprocesora projektu pliku reguł programu make.  
  
    -   Ustaw **wymuszone obejmuje** właściwości w celu określenia, które nagłówki plików do procesu, podczas kompilowania projektu pliku reguł programu make. Zobacz [/FI (nazwij wymuszone obejmują plik)](../build/reference/fi-name-forced-include-file.md), aby uzyskać więcej informacji.  
  
    -   Ustaw **ścieżkę wyszukiwania zestawu** właściwości w celu określenia listy katalogów, które kompilator będzie wyszukiwać można rozpoznać odwołania do zestawów platformy .NET w projekcie. Zobacz [/AI (Określ katalogi metadanych)](../build/reference/ai-specify-metadata-directories.md), aby uzyskać więcej informacji.  
  
    -   Ustaw **wymuszone za pomocą zestawów** właściwości w celu określenia, które zestawów platformy .NET do przetworzenia podczas kompilowania projektu pliku reguł programu make. Zobacz [/FU (nazwij wymuszone #using)](../build/reference/fu-name-forced-hash-using-file.md), aby uzyskać więcej informacji.  
  
    -   Ustaw **dodatkowe opcje** właściwość, aby określić dodatkowe przełączniki kompilatora używane przez funkcję Intellisense, podczas analizowania plików C++.  
  
4.  Kliknij przycisk **OK** zamknąć strony właściwości.  
  
5.  Użyj **Zapisz wszystko** polecenie, aby zapisać ustawienia modyfikacji projektu.  
  
 Przy następnym otwarciu projektu pliku reguł programu make w środowisku projektowym Visual Studio, uruchom **czystą rozwiązania** polecenia, a następnie **Kompiluj rozwiązanie** na projektu pliku reguł programu make. IntelliSense powinny działać poprawnie w środowisku IDE.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z IntelliSense](/visualstudio/ide/using-intellisense)   
 [Odwołanie NMAKE](../build/nmake-reference.md)   
 [Instrukcje: tworzenie projektu C++ z istniejącego kodu](../ide/how-to-create-a-cpp-project-from-existing-code.md)