---
title: Przestarzałe Konwencje wywoływania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 922103e808541e2829350749a04d6004ba36577f
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403423"
---
# <a name="obsolete-calling-conventions"></a>Przestarzałe konwencje wywoływania
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 **__Pascal**, **__fortran**, i **__syscall** konwencji wywoływania nie są już obsługiwane. Przy użyciu jednego z obsługiwanych Konwencje wywoływania i opcje konsolidatora w odpowiednie, może emulować ich funkcje.  
  
 \<Windows.h > obsługuje teraz makro WINAPI, co przekłada się na odpowiednie konwencja wywołania dla obiektu docelowego. Użyj WINAPI, na którym wcześniej używano PASCAL lub **__far \__pascal**.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz także  
 [Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)