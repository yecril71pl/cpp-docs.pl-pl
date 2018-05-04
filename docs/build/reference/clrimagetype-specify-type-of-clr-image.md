---
title: -CLRIMAGETYPE (określenie typu obrazu CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
dev_langs:
- C++
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 003286d9c1445dec40a6dc0f595eda42f39947aa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE (Określenie typu obrazu CLR)
```  
/CLRIMAGETYPE:{IJW|PURE|SAFE|SAFE32BITPREFERRED}  
```  
  
## <a name="remarks"></a>Uwagi  
 Konsolidator akceptuje obiektów macierzystych i również MSIL obiekty, które są kompilowane przy użyciu [/CLR](../../build/reference/clr-common-language-runtime-compilation.md). **/CLR: pure** i **/CLR: Safe** — opcje kompilatora były przestarzałe w programie Visual Studio 2015. Gdy mieszanych obiektów w tej samej kompilacji są przekazywane, możliwość weryfikacji wynikowego pliku wyjściowego jest, domyślnie równa najniższa możliwość wprowadzania modułów weryfikacji. Na przykład w przypadku przekazania obrazu macierzystego i obraz trybu mieszanego (skompilowana przy użyciu **/CLR**), obraz wynikowy będzie obrazu w trybie mieszanym.  
  
 Umożliwia clrimagetype Określ niższej możliwość weryfikacji, jeżeli jest to, co jest potrzebne.  
  
 Aby uzyskać informacje o tym, jak można ustalić typu obrazu CLR pliku, zobacz [/CLRHEADER](../../build/reference/clrheader.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzła.  
  
3.  Rozwiń węzeł **konsolidatora** węzła.  
  
4.  Wybierz **zaawansowane** strony właściwości.  
  
5.  Modyfikowanie **typu obrazu CLR** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)