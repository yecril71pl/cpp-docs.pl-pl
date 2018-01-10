---
title: "Przestarzałe Konwencje wywoływania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __fortran
- __pascal
- __syscall
dev_langs: C++
helpviewer_keywords:
- WINAPI [C++]
- __syscall keyword [C++]
- __pascal keyword [C++]
- __fortran keyword [C++]
- calling conventions, obsolete
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 325a9a98ec536eaabedef3a93fbe38ccc2016cd9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="obsolete-calling-conventions"></a>Przestarzałe konwencje wywoływania
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 **__Pascal**, **__fortran**, i **__syscall** konwencji wywoływania nie są już obsługiwane. Za pomocą jednego z obsługiwanych konwencji wywoływania i opcje konsolidatora odpowiednie, możesz emulować ich funkcje.  
  
 SYSTEMU WINDOWS. Obsługuje teraz H **WINAPI** makra, co oznacza odpowiednie Konwencja wywoływania dla elementu docelowego. Użyj **WINAPI** gdzie wcześniej używane **PASCAL** lub **__far \__pascal**.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)