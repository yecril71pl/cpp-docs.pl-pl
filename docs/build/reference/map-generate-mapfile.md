---
title: -MAP (Generuj plik mapy) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /map
- VC.Project.VCLinkerTool.MapFileName
- VC.Project.VCLinkerTool.GenerateMapFile
dev_langs:
- C++
helpviewer_keywords:
- mapfiles, creating linker
- generate mapfile linker option
- mapfile linker option
- mapfiles, information about program being linked
- MAP linker option
- -MAP linker option
- mapfiles, specifying file name
- /MAP linker option
ms.assetid: 9ccce53d-4e36-43da-87b0-7603ddfdea63
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10f4b23cf8f1c05fb8bd196dc9a6cd54971b1572
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374674"
---
# <a name="map-generate-mapfile"></a>/MAP (Generuj plik mapy)
```  
/MAP[:filename]  
```  
  
## <a name="remarks"></a>Uwagi  
 gdzie:  
  
 *Nazwa pliku*  
 Określone przez użytkownika nazwa mapfile. Zastępuje ona nazwę domyślną.  
  
## <a name="remarks"></a>Uwagi  
 Opcja/map informuje konsolidator, aby utworzył plik mapowania.  
  
 Domyślnie konsolidator nazwa mapfile z podstawowej nazwy programu i .map rozszerzenia. Opcjonalny *filename* pozwala zastąpić domyślną nazwę pliku mapowania.  
  
 Plik mapowania to plik tekstowy, który zawiera następujące informacje o podłączanym:  
  
-   Nazwa modułu jest podstawową nazwą pliku  
  
-   Sygnatura czasowa z nagłówka pliku programu (nie z systemu plików)  
  
-   Lista grup w programie z każdej grupy adres początkowy (jako *sekcji*:*przesunięcie*), długość nazwy grupy i klasy  
  
-   Lista symboli publicznych, przy każdym adresu (jako *sekcji*:*przesunięcie*), symbol nazwa, adres płaski i pliku .obj, którym jest zdefiniowany symbol  
  
-   Punkt wejścia (jako *sekcji*:*przesunięcie*)  
  
 [/MapInfo](../../build/reference/mapinfo-include-information-in-mapfile.md) opcja określa dodatkowe informacje, które mają zostać uwzględnione w pliku mapowania.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **debugowania** strony właściwości.  
  
4.  Modyfikowanie **Generowanie pliku mapy** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateMapFile%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapFileName%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)