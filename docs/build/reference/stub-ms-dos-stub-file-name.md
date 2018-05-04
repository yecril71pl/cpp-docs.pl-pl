---
title: -STUB (nazwa pliku klasy zastępczej MS-DOS) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /stub
- VC.Project.VCLinkerTool.DosStub
dev_langs:
- C++
helpviewer_keywords:
- Win32 [C++], attaching MS-DOS stub program
- STUB linker option
- MS-DOS stub file name linker option
- /STUB linker option
- Windows API [C++], attaching MS-DOS stub program
- -STUB linker option
ms.assetid: 65221ffe-4f9a-4a14-ac69-3cfb79b40b5f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4302040f7d18dcffc07ddd054c34b62c22e400d2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="stub-ms-dos-stub-file-name"></a>/STUB (Nazwa pliku klasy zastępczej MS-DOS)
```  
/STUB:filename  
```  
  
## <a name="remarks"></a>Uwagi  
 gdzie:  
  
 *Nazwa pliku*  
 Aplikacja systemu MS-DOS.  
  
## <a name="remarks"></a>Uwagi  
 Opcja/stub dołącza program szczątkowy systemu MS-DOS do programu systemu Win32.  
  
 Program szczątkowy jest wywoływana, jeśli plik zostanie wykonany w systemu MS-DOS. Zwykle wyświetla odpowiedni komunikat; Jednak wszystkie prawidłową aplikacją systemu MS-DOS można program szczątkowy.  
  
 Określ *filename* programu klasy zastępczej po dwukropkiem (:) w wierszu polecenia. Sprawdzanie konsolidatora *filename* i generuje komunikat o błędzie, jeśli plik nie jest plikiem wykonywalnym. Program musi być pliku .exe; plik .com jest nieprawidłowa dla programu klasy zastępczej.  
  
 Jeśli ta opcja nie jest używana, konsolidator dołącza domyślny program szczątkowy, który wystawia następujący komunikat:  
  
```  
This program cannot be run in MS-DOS mode.  
```  
  
 Podczas kompilowania sterownik urządzenia wirtualnego *filename* umożliwia użytkownikowi określenie nazwy pliku, która zawiera struktura IMAGE_DOS_HEADER (zdefiniowany w Windows NT. H) do użycia w VXD zamiast domyślnego nagłówka.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji do **dodatkowe opcje** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)