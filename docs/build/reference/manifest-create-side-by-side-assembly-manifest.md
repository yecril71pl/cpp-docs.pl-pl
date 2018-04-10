---
title: -MANIFEST (Tworzenie manifestu zestawu Side-by-Side) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.GenerateManifest
dev_langs:
- C++
helpviewer_keywords:
- -MANIFEST linker option
- /MANIFEST linker option
- MANIFEST linker option
ms.assetid: 98c52e1e-712c-4f49-b149-4d0a3501b600
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bb26957109a558b48d6252e042e9082f7357fbd7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="manifest-create-side-by-side-assembly-manifest"></a>/MANIFEST (Tworzenie manifestu dla aplikacji wykonywanych jednocześnie)
```  
/MANIFEST[:{EMBED[,ID=#]|NO}]  
```  
  
## <a name="remarks"></a>Uwagi  
 / MANIFEST Określa, że konsolidator powinien utworzyć side-by-side pliku manifestu. Aby uzyskać więcej informacji o plikach manifestu, zobacz [odwołania pliki manifestu](http://msdn.microsoft.com/library/aa375632).  
  
 Wartość domyślna to /MANIFEST.  
  
 /MANIFEST: OSADZANIE opcja określa, że konsolidator powinien Osadź pliku manifestu w obrazie jako zasobu typu RT_MANIFEST. Opcjonalny `ID` parametr jest identyfikator zasobu do użycia dla manifest. Użyj wartości 1 dla pliku wykonywalnego. Aby umożliwić określenie prywatnej zależności, należy użyć wartość 2 dla biblioteki DLL. Jeśli `ID` parametr nie zostanie określony, wartość domyślna to 2, jeśli ustawiona jest opcja/dll; w przeciwnym razie wartość domyślna to 1.  
  
 Pliki manifestu dla plików wykonywalnych, począwszy od programu Visual Studio 2008, zawiera sekcja, która określa informacje kontroli konta użytkownika (UAC). Jeśli określono /MANIFEST, ale nie określono [/MANIFESTUAC](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md) ani [/dll](../../build/reference/dll-build-a-dll.md), fragment UAC domyślny, który ma ustawiony poziom kontroli konta użytkownika do *asInvoker* zostaną wstawione do manifestu. Aby uzyskać więcej informacji na temat poziomów funkcji Kontrola konta użytkownika, zobacz [/MANIFESTUAC (osadza informacje UAC w manifeście)](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md).  
  
 Aby zmienić domyślne zachowanie dla funkcji Kontrola konta użytkownika, wykonaj jedną z nich:  
  
-   Określ opcję /MANIFESTUAC i ustawić poziom kontroli konta użytkownika na żądaną wartość.  
  
-   Lub wybierz opcję: No, jeśli nie chcesz wygenerować fragmentu UAC w manifeście.  
  
 Jeśli nie określono /MANIFEST, ale określono [/MANIFESTDEPENDENCY](../../build/reference/manifestdependency-specify-manifest-dependencies.md) komentarzy i utworzeniu pliku manifestu. Jeśli określisz /MANIFEST:NO, nie jest tworzony plik manifestu.  
  
 Jeśli określisz /MANIFEST, nazwa pliku manifestu jest taka sama jak nazwa pliku wyjściowego, ale manifest dodanym na końcu nazwy pliku. Na przykład jeśli nazwa pliku wyjściowego jest MyFile.exe, nazwa pliku manifestu jest MyFile.exe.manifest.  Jeśli określisz /MANIFESTFILE:*nazwa*, nazwa manifestu jest, określ w *nazwa*.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzła.  
  
3.  Rozwiń węzeł **konsolidatora** węzła.  
  
4.  Wybierz **plik manifestu** strony właściwości.  
  
5.  Modyfikowanie **Generuj Manifest** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateManifest%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)