---
title: "-EP (wstępnie Przetwórz do stdout bez dyrektyw #line) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /ep
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFileNoLines
dev_langs:
- C++
helpviewer_keywords:
- copy preprocessor output to stdout
- preprocessor output, copy to stdout
- -EP compiler option [C++]
- EP compiler option [C++]
- /EP compiler option [C++]
ms.assetid: 6ec411ae-e33d-4ef5-956e-0054635eabea
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9d7b2a64ec8fa7565d17ab04683fec07c48aea3f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ep-preprocess-to-stdout-without-line-directives"></a>/EP (Wstępnie przetwórz do stdout bez dyrektyw #line)
Przetwarza wstępnie pliki źródłowe C i C++ i kopiuje wstępnie przetworzonych plików na urządzeniu standardowe dane wyjściowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
/EP  
```  
  
## <a name="remarks"></a>Uwagi  
 W procesie nie zostaną przeprowadzone wszystkie dyrektywy preprocesora, rozwinięcia makra są są wykonywane i komentarze zostaną usunięte. Aby zachować komentarzy w wstępnie przetworzonych danych wyjściowych, należy użyć [/C (Zachowaj komentarze podczas przetwarzania wstępnego)](../../build/reference/c-preserve-comments-during-preprocessing.md) opcję z **/EP**.  
  
 **/EP** opcja pomija kompilację. Należy ponownie przesłać wstępnie przetworzonych plików dla kompilacji. **/EP** również pomija pliki wyjściowe z **/FA**, **/Fa**, i **/Fm** opcje. Aby uzyskać więcej informacji, zobacz [/FA, /Fa (wyświetlanie listy plików)](../../build/reference/fa-fa-listing-file.md) i [/Fm (nazwa Mapfile)](../../build/reference/fm-name-mapfile.md).  
  
 Wygenerowane błędy podczas późniejszych etapach przetwarzania można znaleźć numery wierszy wstępnie przetworzonych plików, a nie plikiem źródłowym. Numery wierszy do odwoływania się do oryginalnego pliku źródłowego, należy użyć [/E (Przetwarzaj wstępnie do stdout)](../../build/reference/e-preprocess-to-stdout.md) zamiast tego. **/E** opcja dodaje `#line` dyrektywy do danych wyjściowych w tym celu.  
  
 Aby wysłać wstępnie przetworzonych danych wyjściowych z `#line` dyrektyw w pliku użyj [/P (Przetwarzaj wstępnie do pliku)](../../build/reference/p-preprocess-to-a-file.md) zamiast tego należy.  
  
 Aby wysłać wstępnie przetworzonych danych wyjściowych stdout, z `#line` użyj dyrektywy, **/P** i **/EP** ze sobą.  
  
 Nie można użyć prekompilowanych nagłówków z **/EP** opcji.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **preprocesora** strony właściwości.  
  
4.  Modyfikowanie **Generowanie pliku wstępnie przetworzony** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie w wierszu przetwarza wstępnie pliku `ADD.C`zachowuje komentarze i wyświetla wyniki na urządzeniu standardowe dane wyjściowe:  
  
```  
CL /EP /C ADD.C  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)