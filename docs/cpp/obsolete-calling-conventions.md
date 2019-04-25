---
title: Przestarzałe konwencje wywoływania
ms.date: 11/04/2016
f1_keywords:
- __fortran
- __pascal
- __syscall
helpviewer_keywords:
- WINAPI [C++]
- __syscall keyword [C++]
- __pascal keyword [C++]
- __fortran keyword [C++]
- calling conventions, obsolete
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
ms.openlocfilehash: 86c75c779158d9f191dd015410cf16c9ce25690d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245037"
---
# <a name="obsolete-calling-conventions"></a>Przestarzałe konwencje wywoływania

## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft

**__Pascal**, **__fortran**, i **__syscall** konwencji wywoływania nie są już obsługiwane. Przy użyciu jednego z obsługiwanych Konwencje wywoływania i opcje konsolidatora w odpowiednie, może emulować ich funkcje.

\<Windows.h > obsługuje teraz makro WINAPI, co przekłada się na odpowiednie konwencja wywołania dla obiektu docelowego. Użyj WINAPI, na którym wcześniej używano PASCAL lub **__far \__pascal**.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)