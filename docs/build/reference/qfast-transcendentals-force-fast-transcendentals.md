---
title: -Qfast_transcendentals (Wymuszaj Fast Transcendentals) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /Qfast_transcendentals
dev_langs:
- C++
helpviewer_keywords:
- /Qfast_transcendentals
- Force Fast Transcendentals
ms.assetid: 4de24bd1-38e6-49d4-9a05-04c9937d24ac
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8d7e8de17c096d061653b469207352be4b9b8bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="qfasttranscendentals-force-fast-transcendentals"></a>/Qfast_transcendentals (Wymuszaj fast transcendentals)
Generuje kod wbudowanego przestępne funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Qfast_transcendentals  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja kompilatora wymusza przestępne funkcje, które ma zostać przekonwertowane na kodu wbudowanego w celu zwiększenia szybkości wykonywania. Tej opcji ma wpływ tylko wtedy, gdy łączyć się z **/FP: except** lub **/FP: precise**. Generowanie kodu wbudowanego przestępne funkcji jest już to zachowanie domyślne w obszarze **Fast**.  
  
 Ta opcja jest niezgodna z **/FP: strict**. Zobacz [/fp (określenie zachowania Floating-Point)](../../build/reference/fp-specify-floating-point-behavior.md) uzyskać więcej informacji o zmiennoprzecinkową opcje kompilatora punktu.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji kompilatora w **dodatkowe opcje** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [/Q opcje (operacje na niskim poziomie)](../../build/reference/q-options-low-level-operations.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)