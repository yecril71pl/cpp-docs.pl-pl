---
title: -Gw (Optymalizuj dane globalne) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Gw
dev_langs:
- C++
helpviewer_keywords:
- /Gw compiler option [C++]
- -Gw compiler option [C++]
ms.assetid: 6f90f4e9-5eb8-4c47-886e-631278a5a4a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 173b9499477ee02cbb1f052d3d85445a9ffb7732
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376442"
---
# <a name="gw-optimize-global-data"></a>/Gw (Optymalizuj dane globalne)
Pakiet danych globalnych w sekcji COMDAT optymalizacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Gw[-]  
```  
  
## <a name="remarks"></a>Uwagi  
 **/Gw** opcji powoduje, że kompilator pakietu danych globalnych w poszczególnych sekcji COMDAT. Domyślnie **/Gw** jest wyłączony, a musi być jawnie włączone. Aby jawnie ją wyłączyć, należy użyć **/Gw-**. Gdy zarówno **/Gw** i [/GL](../../build/reference/gl-whole-program-optimization.md) są włączone, konsolidator używa optymalizacji całego programu do porównania sekcje COMDAT wiele plików obiektów w celu wykluczenia nieużywane dane globalne lub scalania identyczne tylko do odczytu danych globalnych. Może to znacznie zmniejszyć rozmiar wynikowego pliku binarnego pliku wykonywalnego.  
  
 Podczas kompilowania i połączyć oddzielnie, można użyć [/OPT:REF](../../build/reference/opt-optimizations.md) — opcja konsolidatora do wykluczenia z pliku wykonywalnego nieużywane danych globalnych w plikach obiektu skompilowanego z **/Gw** opcji.  
  
 Można również użyć [/OPT: ICF](../../build/reference/opt-optimizations.md) i [opcję/LTCG](../../build/reference/ltcg-link-time-code-generation.md) opcje konsolidatora ze sobą w celu scalenia w pliku wykonywalnym żadnych identyczne tylko do odczytu danych globalnych między wiele plików obiektu skompilowanego z **/Gw** opcji.  
  
 Aby uzyskać więcej informacji, zobacz [wprowadzenie /Gw przełącznika kompilatora](http://blogs.msdn.com/b/vcblog/archive/2013/09/11/introducing-gw-compiler-switch.aspx) na blogu zespołu Visual C++.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **C/C++** folderu.  
  
3.  Wybierz **wiersza polecenia** strony właściwości.  
  
4.  Modyfikowanie **dodatkowe opcje** właściwości, aby uwzględnić **/Gw** , a następnie wybierz **OK**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)