---
title: -FD (minimalna ponowna kompilacja IDE) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /FD
dev_langs: C++
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5fac2b16d3a494c323a351ab0cb67f1940523649
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (Minimalna ponowna kompilacja IDE)
**/FD** nie jest widoczne dla użytkowników z wyjątkiem w [wiersza polecenia](../../ide/command-line-property-pages.md) strony właściwości projektu C++ **strony właściwości** okna dialogowego, w przypadku i tylko wtedy, gdy [/GM ponowną (Włącz minimalnego odbudować)](../../build/reference/gm-enable-minimal-rebuild.md) nie wybrano również. **/FD** nie obowiązuje, innego niż ze środowiska projektowego. **/FD** nie jest widoczna w danych wyjściowych **cl /?**.  
  
 Jeśli nie włączysz **/GM ponowną** w środowisku programistycznym **/FD** będą używane. **/FD** gwarantuje, że plik .idb ma wystarczające informacji o zależnościach. **/FD** jest używana tylko przez środowisko deweloperskie i nie powinna być używana z wiersza polecenia lub skryptu kompilacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Plik wyjściowy (/ F) opcje](../../build/reference/output-file-f-options.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)