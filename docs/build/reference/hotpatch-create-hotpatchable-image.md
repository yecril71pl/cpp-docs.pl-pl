---
title: "-hotpatch (Utwórz obraz możliwych) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /hotpatch
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs: C++
helpviewer_keywords:
- hot patching
- -hotpatch compiler option [C++]
- /hotpatch compiler option [C++]
- hotpatching
ms.assetid: aad539b6-c053-4c78-8682-853d98327798
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ad7ab4e6450d33923b728f20c8a35185edd2b05e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="hotpatch-create-hotpatchable-image"></a>/hotpatch (Utwórz obraz możliwy do poprawiania w trakcie działania)
Przygotowuje obraz do poprawiania.  
  
## <a name="syntax"></a>Składnia  
  
```  
/hotpatch  
```  
  
## <a name="remarks"></a>Uwagi  
 Gdy **/hotpatch** jest używany w kompilacji, kompilator zapewnia, że pierwsza instrukcja każdej funkcji jest co najmniej dwa bajty, co jest wymagane do poprawiania.  
  
 Do ukończenia przygotowania do wprowadzania możliwych obraz, po użyciu **/hotpatch** Aby skompilować, należy użyć [/FUNCTIONPADMIN (Utwórz obraz możliwych)](../../build/reference/functionpadmin-create-hotpatchable-image.md) do połączenia. Podczas kompilowania i łączenie obrazu za pomocą jednego wywołania cl.exe, **/hotpatch** oznacza **/functionpadmin**.  
  
 Ponieważ instrukcje są zawsze dwa bajty lub większym na architekturze ARM i dlatego x64 kompilacji jest zawsze traktowany tak, jakby **/hotpatch** został określony, nie trzeba określać **/hotpatch** podczas Kompiluj dla tych celów; jednak nadal należy połączyć za pomocą **/functionpadmin** do tworzenia obrazów możliwych dla nich. **/Hotpatch** kompilacji wpływa na x86 tylko opcję kompilatora.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **C/C++** folderu.  
  
3.  Wybierz **wiersza polecenia** strony właściwości.  
  
4.  Dodaj opcję kompilatora **dodatkowe opcje** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="guidance"></a>Wskazówki  
 Aby uzyskać więcej informacji na temat zarządzania aktualizacjami, zobacz "Wskazówki dotyczące zabezpieczeń do zarządzania aktualizacji" w [http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx](http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx).  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)