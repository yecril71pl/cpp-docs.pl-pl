---
title: "-FUNCTIONPADMIN (Utwórz obraz możliwych) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /functionpadmin
dev_langs:
- C++
helpviewer_keywords:
- -FUNCTIONPADMIN linker option
- /FUNCTIONPADMIN linker option
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f737cdb412420ffb87664024b2314941e67b045b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN (Utwórz obraz możliwy do poprawiania w trakcie działania)
Przygotowuje obraz do poprawiania w trakcie działania.  
  
## <a name="syntax"></a>Składnia  
  
```  
/FUNCTIONPADMIN[:space]  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `space`(opcjonalnie)  
 Wielkość uzupełnienia do dodania na początku każdej funkcji, 5, 6 lub 16.  x86 obrazów wymaga pięciu bajtów dopełnienia x64 obrazów wymagają 6 bajtów i obrazów zbudowanych dla rodziny procesora Itanium wymagają 16 bajtów uzupełnienia na początku każdej funkcji.  
  
 Domyślnie kompilator doda poprawną ilość miejsca do obrazu na podstawie typu komputera obrazu.  
  
 Aby konsolidator, aby utworzyć obraz możliwych, pliki .obj musi zostały skompilowane z [/hotpatch (Utwórz obraz możliwych)](../../build/reference/hotpatch-create-hotpatchable-image.md).  
  
 Podczas kompilowania i połączyć obrazu z jednego wywołania cl.exe, **/hotpatch** oznacza **/functionpadmin**.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji do **dodatkowe opcje** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)