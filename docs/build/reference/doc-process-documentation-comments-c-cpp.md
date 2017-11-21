---
title: -doc (przetwarzanie komentarzy dokumentacji) (C/C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- /doc
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
dev_langs: C++
helpviewer_keywords:
- /doc compiler option [C++]
- comments, C++ code
- XML documentation, comments in source files
- -doc compiler option [C++]
ms.assetid: b54f7e2c-f28f-4f46-9ed6-0db09be2cc63
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 083eb8742308f986e3261711039bbd29a914d97e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="doc-process-documentation-comments-cc"></a>/doc (Przetwarzaj komentarze dokumentacji) (C/C++)
Powoduje, że kompilator przetwarzanie komentarzy dokumentacji w plików kodu źródłowego oraz do tworzenia pliku .xdc dla każdego pliku źródła kodu, który ma komentarzy do dokumentacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
/doc[name]  
```  
  
## <a name="arguments"></a>Argumenty  
 `name`  
 Nazwa pliku .xdc, który zostanie utworzony przez kompilator. Prawidłowy tylko wtedy, gdy jeden plik .cpp jest przekazywany w kompilacji.  
  
## <a name="remarks"></a>Uwagi  
 W pliku XML z xdcmake.exe przetwarzania plików xdc. Aby uzyskać więcej informacji, zobacz [xdcmake — odwołanie](../../ide/xdcmake-reference.md).  
  
 Komentarze dokumentacji można dodawać do plików kodu źródłowego. Aby uzyskać więcej informacji, zobacz [tagi zalecane dla komentarzy do dokumentacji](../../ide/recommended-tags-for-documentation-comments-visual-cpp.md).  
  
 Plik XML wygenerowanych za pomocą funkcji IntelliSense, aby nazwa pliku jest taka sama jak zestawu, który chcesz obsługiwać i umieścić plik XML w tym samym katalogu co zestaw pliku XML. W przypadku zestawu odwołuje się projekt programu Visual Studio, znajduje się także plik XML. Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](/visualstudio/ide/using-intellisense) i [dostarczanie komentarze w kodzie XML](/visualstudio/ide/supplying-xml-code-comments).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzła.  
  
3.  Rozwiń węzeł **C/C++** węzła.  
  
4.  Wybierz **pliki wyjściowe** strony właściwości.  
  
5.  Modyfikowanie **generować pliki dokumentacji XML** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GenerateXMLDocumentationFiles%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)