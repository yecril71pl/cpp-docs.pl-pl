---
title: "-STACK (twórz stos z alokacji) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.StackReserveSize
- VC.Project.VCLinkerTool.StackCommitSize
- /stack
dev_langs: C++
helpviewer_keywords:
- STACK linker option
- -STACK linker option
- memory allocation, stack
- /STACK linker option
- stack, setting size
ms.assetid: 73283660-e4bd-47cc-b5ca-04c5d739034c
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e44c9920e2725bc70d3b8abe385b94961486e945
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="stack-stack-allocations"></a>/STACK (Twórz stos z alokacji)
```  
/STACK:reserve[,commit]  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcja /STACK ustawia rozmiar stosu w bajtach. Użyj tej opcji tylko wtedy, gdy tworzenie pliku .exe.  
  
 `reserve` Wartość określa alokacji całkowita stosu w pamięci wirtualnej. Dla ARM, x86 i [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] maszyny, rozmiar stosu domyślna to 1 MB.  
  
 `commit`podlega interpretacji przez system operacyjny. W systemie Windows, Windows RT określa ilość pamięci fizycznej do przydzielenia naraz. Zadeklarowanej pamięci wirtualnej spowoduje, że miejsca, które mają zostać zarezerwowane w pliku stronicowania. Wyższy `commit` wartość zaoszczędzić czas podczas aplikacji wymaga więcej miejsca na stosie, ale zwiększa wymagania dotyczące pamięci i być może czas uruchamiania. Dla ARM, x86 i [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] maszyny, zatwierdzania wartość domyślna to 4 KB.  
  
 Określ `reserve` i `commit` wartości dziesiętne lub notacji języka C.  
  
 Ustaw rozmiar stosu innym sposobem jest użycie [STACKSIZE](../../build/reference/stacksize.md) instrukcji w pliku definicji modułu (.def). **STACKSIZE** zastępuje alokacji stosu (/ STACK) opcja, jeśli określono oba. Rozmiar stosu można zmienić po utworzeniu pliku .exe przy użyciu [polecenia EDITBIN](../../build/reference/editbin-reference.md) narzędzia.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **konsolidatora** folderu.  
  
3.  Wybierz **systemu** strony właściwości.  
  
4.  Zmień jedną z następujących właściwości:  
  
    -   **Zaalokowany rozmiar stosu**  
  
    -   **Zarezerwowany rozmiar stosu**  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackCommitSize%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackReserveSize%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)