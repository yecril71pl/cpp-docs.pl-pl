---
title: -IMPLIB (Nazwij bibliotekę importowaną) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /implib
- VC.Project.VCLinkerTool.ImportLIbrary
dev_langs:
- C++
helpviewer_keywords:
- IMPLIB linker option
- /IMPLIB linker option
- -IMPLIB linker option
- import libraries, overriding default name
ms.assetid: fe8f71ab-7055-41b5-8ef8-2b97cfa4a432
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72edc0fcb1b216319d6f6c9924cb92a165b3196b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="implib-name-import-library"></a>/IMPLIB (Nazwij bibliotekę importowaną)
  
> / IMPLIB:*filename*  
  
## <a name="parameters"></a>Parametry  
  
*Nazwa pliku*  
Użytkownik określił nazwę biblioteki importu. Zastępuje ona nazwę domyślną.  
  
## <a name="remarks"></a>Uwagi  
  
Opcja /IMPLIB przesłania domyślną nazwę biblioteki importu, która tworzy łącze podczas tworzenia programu, który zawiera eksportu. Domyślna nazwa został utworzony z podstawowej nazwy pliku wyjściowego głównego i rozszerzenia. lib. Program zawiera eksportu, jeśli nie określono co najmniej jeden z następujących czynności:  
  
-   [__Declspec(dllexport)](../../cpp/dllexport-dllimport.md) — słowo kluczowe w kodzie źródłowym  
  
-   [EKSPORTY](../../build/reference/exports.md) instrukcji w plik .def  
  
-   [/EXPORT](../../build/reference/export-exports-a-function.md) Specyfikacja polecenia łącza  
  
 ŁĄCZA zignoruje /IMPLIB podczas importowania biblioteki nie jest tworzony. Jeśli nie określono żadnego eksportu, LINK nie powoduje utworzenia biblioteki importu. Jeśli używany jest plik eksportu w kompilacji, LINK przyjęto założenie, że biblioteki importowanej już istnieje i nie tworzy jeden. Aby uzyskać informacje na bibliotekami importowanymi oraz plikami eksportowanymi, zobacz [odwołanie do biblioteki LIB](../../build/reference/lib-reference.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **zaawansowane** strony właściwości.  
  
4.  Modyfikowanie **biblioteki importu** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ImportLibrary%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)