---
title: -Fo (nazwa pliku obiektu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Fo
- VC.Project.VCCLCompilerTool.ObjectFile
- VC.Project.VCCLWCECompilerTool.ObjectFile
dev_langs:
- C++
helpviewer_keywords:
- Fo compiler option [C++]
- object files, naming
- /Fo compiler option [C++]
- -Fo compiler option [C++]
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ea552b149270b8e644140a4dd51f220648ef376e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374011"
---
# <a name="fo-object-file-name"></a>/Fo (Nazwa pliku obiektu)
Określa nazwę pliku obiektu (.obj) lub katalog do użycia zamiast domyślnej.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Fopathname  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ta opcja nie zostanie użyta, plik obiektu używa podstawowej nazwy pliku źródłowego i rozszerzeniem nazwy. Można użyć dowolnego nazwę i rozszerzenie ma, ale konwencją zalecane jest użycie. obiektu  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **pliki wyjściowe** strony właściwości.  
  
4.  Modyfikowanie **nazwy pliku obiektu** właściwości.  W środowisku programistycznym pliku obiektu musi mieć rozszerzenie. obiektu  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie w wierszu tworzy plik obiektu o nazwie THIS.obj w istniejącym katalogiem, \OBJECT, na dysku B.  
  
```  
CL /FoB:\OBJECT\ THIS.C  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Plik wyjściowy (/ F) opcje](../../build/reference/output-file-f-options.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [Określanie nazwy ścieżki](../../build/reference/specifying-the-pathname.md)