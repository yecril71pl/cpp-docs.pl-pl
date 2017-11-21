---
title: "-TLBID (Określ identyfikator ID zasobu dla TypeLib) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /tlbid
- VC.Project.VCLinkerTool.TypeLibraryResourceID
dev_langs: C++
helpviewer_keywords:
- tlb files, specifying resource ID
- -TLBID linker option
- .tlb files, specifying resource ID
- /TLBID linker option
- TLBID linker option
- type libraries, specifying resource ID
ms.assetid: 434b28a2-4656-4d52-ac82-8b18bf486fb2
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9a260882b7e4623149e9e82a3a635f7230b6985a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="tlbid-specify-resource-id-for-typelib"></a>/TLBID (Określ identyfikator ID zasobu dla TypeLib)
```  
/TLBID:id  
```  
  
## <a name="remarks"></a>Uwagi  
 gdzie:  
  
 `id`  
 Wartość określonego przez użytkownika w bibliotece typów utworzonych przez konsolidator. Zastępuje domyślny identyfikator zasobu 1.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku kompilowania kodu program, który używa atrybutów, konsolidator utworzy biblioteki typów. Konsolidator przypisze identyfikator zasobu, 1 do biblioteki typów.  
  
 Jeśli ten identyfikator zasobu powoduje konflikt z jednym z istniejących zasobów, można określić z /TLBID inny identyfikator. Zakres wartości, które można przekazać do `id` od 1 do 65 535.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **osadzonych IDL** strony właściwości.  
  
4.  Modyfikowanie **identyfikator zasobu biblioteki typów** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryResourceID%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)