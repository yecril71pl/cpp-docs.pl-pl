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
ms.openlocfilehash: 156482a395c7dfc8711e273141a09a37ea3e135d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188561"
---
# <a name="obsolete-calling-conventions"></a>Przestarzałe konwencje wywoływania

**Specyficzne dla firmy Microsoft**

Konwencje wywoływania **__pascal**, **__fortran**i **__syscall** nie są już obsługiwane. Można emulować ich funkcje przy użyciu jednej z obsługiwanych konwencji wywoływania i odpowiednich opcji konsolidatora.

\<Windows. h > obsługuje teraz makro WINAPI, które tłumaczy do odpowiedniej konwencji wywoływania dla elementu docelowego. Użyj WINAPI, w której wcześniej użyto języka PASCALa lub **__far \__pascal**.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)
