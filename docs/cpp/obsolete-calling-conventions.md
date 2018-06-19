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
ms.openlocfilehash: 9d2a6188cf9d8c8283a6c03a2ca6c701e28baf0d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32419849"
---
# <a name="obsolete-calling-conventions"></a>Przestarzałe konwencje wywoływania
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 **__Pascal**, **__fortran**, i **__syscall** konwencji wywoływania nie są już obsługiwane. Za pomocą jednego z obsługiwanych konwencji wywoływania i opcje konsolidatora odpowiednie, możesz emulować ich funkcje.  
  
 \<Windows.h > obsługuje teraz **WINAPI** makra, co oznacza odpowiednie Konwencja wywoływania dla elementu docelowego. Użyj **WINAPI** gdzie wcześniej używane **PASCAL** lub **__far \__pascal**.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)