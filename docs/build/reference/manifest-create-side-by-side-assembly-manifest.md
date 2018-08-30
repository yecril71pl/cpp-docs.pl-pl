---
title: -MANIFEST (Tworzenie manifestu Side-by-Side) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateManifest
dev_langs:
- C++
helpviewer_keywords:
- -MANIFEST linker option
- /MANIFEST linker option
- MANIFEST linker option
ms.assetid: 98c52e1e-712c-4f49-b149-4d0a3501b600
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7cdf0f5d1d736635af3d7bf1a853e9002e072ef5
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43199116"
---
# <a name="manifest-create-side-by-side-assembly-manifest"></a>/MANIFEST (Tworzenie manifestu dla aplikacji wykonywanych jednocześnie)
```  
/MANIFEST[:{EMBED[,ID=#]|NO}]  
```  
  
## <a name="remarks"></a>Uwagi  
 / MANIFEST Określa, że konsolidator powinien utworzyć plik manifestu side-by-side. Aby uzyskać więcej informacji na temat plików manifestu, zobacz [odwołania plików manifestu](/windows/desktop/SbsCs/manifest-files-reference).  
  
 Wartość domyślna to /MANIFEST.  
  
 /MANIFEST: OSADZANIE opcja określa konsolidator należy osadzić pliku manifestu na obrazie, jako zasobu typu RT_MANIFEST. Opcjonalny `ID` parametr jest identyfikator zasobu do użycia dla manifestu. Użyj wartości 1 dla pliku wykonywalnego. Umożliwiają wartość 2 dla bibliotek DLL z nim do określania prywatnych zależności. Jeśli `ID` parametr nie jest określony, wartość domyślna to 2, jeśli ustawiono opcję/dll; w przeciwnym razie wartość domyślna to 1.  
  
 Począwszy od programu Visual Studio 2008 plików manifestu dla plików wykonywalnych zawiera sekcja, która określa informacje kontroli konta użytkownika (UAC). Jeśli określono /MANIFEST, ale nie określono [/MANIFESTUAC](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md) ani [/dll](../../build/reference/dll-build-a-dll.md), fragment funkcji Kontrola konta użytkownika domyślnego, który ma ustawiony poziom kontroli konta użytkownika do *asInvoker* zostaną wstawione do manifestu. Aby uzyskać więcej informacji na temat poziomów funkcji Kontrola konta użytkownika, zobacz [/MANIFESTUAC (osadza informacje UAC w manifeście)](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md).  
  
 Aby zmienić domyślne zachowanie dla funkcji Kontrola konta użytkownika, wykonaj jeden z nich:  
  
-   Wybierz opcję /MANIFESTUAC, a także Ustaw poziom funkcji Kontrola konta użytkownika na żądaną wartość.  
  
-   Lub wybierz opcję: No, jeśli nie chcesz wygenerować fragmentu UAC w manifeście.  
  
 Jeśli nie określono /MANIFEST, ale określono [/MANIFESTDEPENDENCY](../../build/reference/manifestdependency-specify-manifest-dependencies.md) komentarze, tworzony jest plik manifestu. Nie jest tworzony plik manifestu, jeśli określisz /MANIFEST:NO.  
  
 Jeśli określisz /MANIFEST, nazwa pliku manifestu jest taka sama jak nazwa pliku wyjściowego, ale manifest dodanym na końcu nazwy pliku. Na przykład jeśli nazwa pliku wyjściowego jest MyFile.exe, nazwa pliku manifestu jest MyFile.exe.manifest.  Jeśli określisz /MANIFESTFILE:*nazwa*, nazwa manifestu to określić w *nazwa*.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń **właściwości konfiguracji** węzła.  
  
3.  Rozwiń **konsolidatora** węzła.  
  
4.  Wybierz **pliku manifestu** stronę właściwości.  
  
5.  Modyfikowanie **Generuj Manifest** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateManifest%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)