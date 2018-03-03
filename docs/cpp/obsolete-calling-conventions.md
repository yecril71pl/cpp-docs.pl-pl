---
title: "Przestarzałe Konwencje wywoływania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __fortran
- __pascal
- __syscall
dev_langs:
- C++
helpviewer_keywords:
- WINAPI [C++]
- __syscall keyword [C++]
- __pascal keyword [C++]
- __fortran keyword [C++]
- calling conventions, obsolete
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ad065eb3f35080ff2e5743c0259b20ba72ee6175
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="obsolete-calling-conventions"></a>Przestarzałe konwencje wywoływania
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 **__Pascal**, **__fortran**, i **__syscall** konwencji wywoływania nie są już obsługiwane. Za pomocą jednego z obsługiwanych konwencji wywoływania i opcje konsolidatora odpowiednie, możesz emulować ich funkcje.  
  
 \<Windows.h > obsługuje teraz **WINAPI** makra, co oznacza odpowiednie Konwencja wywoływania dla elementu docelowego. Użyj **WINAPI** gdzie wcześniej używane **PASCAL** lub **__far \__pascal**.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)