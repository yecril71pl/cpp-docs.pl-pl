---
title: pseudoinstrukcja _emit | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _emit
dev_langs: C++
helpviewer_keywords:
- byte defining (inline assembly)
- _emit pseudoinstruction
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 00cd8425b4c6a9f7333f77f8bab4dc210528a352
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="emit-pseudoinstruction"></a>Pseudoinstrukcja _emit
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 **Pseudoinstrukcja** _emit definiuje jednego bajtu w bieżącej lokalizacji w bieżącym segmencie tekstu. **Pseudoinstrukcja** podobny _emit [DB](../../assembler/masm/db.md) dyrektywę MASM.  
  
 Poniższy fragment umieszcza bajtów 0x4A, 0x43 i 0x4B w kodzie:  
  
```  
#define randasm __asm _emit 0x4A __asm _emit 0x43 __asm _emit 0x4B  
 .  
 .  
 .  
__asm {  
     randasm  
     }  
```  
  
> [!CAUTION]
>  Jeśli `_emit` generuje instrukcje które modyfikują rejestrów i skompilować aplikację z optymalizacji, kompilator nie może określić, jakie rejestrów dotyczy problem. Na przykład jeśli `_emit` generuje instrukcja modyfikuje **rax** rejestru, kompilator nie wie, że **rax** została zmieniona. Kompilator następnie może spowodować nieprawidłowe założenie o wartości w tym zarejestrować po wykonaniu kodu asemblera wbudowanego. W związku z tym aplikacja może działać nieprzewidywalne zachowanie podczas uruchamiania.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z języka asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)