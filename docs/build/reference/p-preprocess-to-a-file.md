---
title: "-P (Przetwarzaj wstępnie do pliku) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFile
- /p
- VC.Project.VCCLWCECompilerTool.GeneratePreprocessedFile
dev_langs: C++
helpviewer_keywords:
- /P compiler option [C++]
- -P compiler option [C++]
- P compiler option [C++]
- output files, preprocessor
- preprocessing output files
ms.assetid: 123ee54f-8219-4a6f-9876-4227023d83fc
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9812f54e4fb886c721f2162aeac620ec4a02acd6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="p-preprocess-to-a-file"></a>/P (Przetwarzaj wstępnie do pliku)
Przetwarza wstępnie pliki źródłowe C i C++ i zapisuje wstępnie przetworzone produkty wyjściowe do pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
/P  
```  
  
## <a name="remarks"></a>Uwagi  
 Plik ma taką samą nazwę podstawową jak plik źródłowy i rozszerzenie .i. W procesie nie zostaną przeprowadzone wszystkie dyrektywy preprocesora, rozwinięcia makra są są wykonywane i komentarze zostaną usunięte. Aby zachować komentarzy w wstępnie przetworzonych danych wyjściowych, należy użyć [/C (Zachowaj komentarze podczas przetwarzania wstępnego)](../../build/reference/c-preserve-comments-during-preprocessing.md) opcji wraz z **/P**.  
  
 **/P** dodaje `#line` dyrektywy dane wyjściowe na początku i na końcu każdej dołączanego pliku i wokół wierszy usunięte przez dyrektywy preprocesora dla kompilacji warunkowej. Te dyrektywy numerowania wierszy wstępnie przetworzonych plików. W związku z tym wygenerowane błędy podczas późniejszych etapach przetwarzania można znaleźć numery wierszy oryginalnego pliku źródłowego, a nie wierszy w pliku wstępnie przetworzony. Aby pominąć Generowanie `#line` użyj dyrektywy, [/EP (wstępnie Przetwórz do stdout bez dyrektyw #line)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) oraz **/P**.  
  
 **/P** opcja pomija kompilację. Nie tworzy pliku obj, nawet jeśli używasz [/Fo (nazwa pliku obiektu)](../../build/reference/fo-object-file-name.md). Należy ponownie przesłać wstępnie przetworzonych plików dla kompilacji. **/P** również pomija pliki wyjściowe z **/FA**, **/Fa**, i **/Fm** opcje. Aby uzyskać więcej informacji, zobacz [/FA, /Fa (wyświetlanie listy plików)](../../build/reference/fa-fa-listing-file.md) i [/Fm (nazwa Mapfile)](../../build/reference/fm-name-mapfile.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **preprocesora** strony właściwości.  
  
4.  Modyfikowanie **Generowanie pliku wstępnie przetworzony** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.  
  
## <a name="example"></a>Przykład  
 Przetwarza wstępnie następujące polecenie w wierszu `ADD.C`, zachowuje komentarze, dodaje `#line` dyrektywy i zapisuje wyniki w pliku `ADD.I`:  
  
```  
CL /P /C ADD.C  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [/Fi (Przetwarzaj wstępnie nazwę pliku wyjściowego)](../../build/reference/fi-preprocess-output-file-name.md)