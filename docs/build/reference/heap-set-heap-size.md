---
title: -HEAP (Ustaw rozmiar stosu) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.HeapCommitSize
- /heap
- VC.Project.VCLinkerTool.HeapReserveSize
dev_langs: C++
helpviewer_keywords:
- -HEAP linker option
- heap allocation, setting heap size
- /HEAP linker option
- HEAP linker option
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 702b8dfa6561d79f8ea9bf496e9652f89c8d34f5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="heap-set-heap-size"></a>/HEAP (Ustaw rozmiar sterty)
```  
/HEAP:reserve[,commit]  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcja /HEAP ustawia rozmiar sterty w bajtach. Ta opcja jest tylko do użytku podczas kompilowania pliku .exe.  
  
 *Zarezerwować* argument określa alokacji sterty całkowitej pamięci wirtualnej. Domyślny rozmiar sterty to 1 MB. Konsolidator Zaokrągla wartość w górę określonej wartości najbliższej 4 bajty.  
  
 Opcjonalny `commit` argument podlega interpretacji przez system operacyjny. W systemie Windows NT/Windows 2000 określa ilość pamięci fizycznej do przydzielenia naraz. Zadeklarowanej pamięci wirtualnej spowoduje, że miejsca, które mają zostać zarezerwowane w pliku stronicowania. Wyższy `commit` wartość zaoszczędzić czas podczas aplikacji wymaga więcej miejsca na stercie, ale zwiększa wymagania dotyczące pamięci i być może czas uruchamiania.  
  
 Określ *zarezerwować* i `commit` wartości dziesiętne lub notacji języka C.  
  
 Ta funkcja jest również dostępny za pośrednictwem pliku definicji modułu z [HEAPSIZE](../../build/reference/heapsize.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **systemu** strony właściwości.  
  
4.  Modyfikowanie **zatwierdzić rozmiar stosu** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)