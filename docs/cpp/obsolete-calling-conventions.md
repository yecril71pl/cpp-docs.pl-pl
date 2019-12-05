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
ms.openlocfilehash: 7f059afe02cbbad77920fd8c4a0e6cb7c958e992
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857362"
---
# <a name="obsolete-calling-conventions"></a>Przestarzałe konwencje wywoływania

**Microsoft Specific**

Konwencje wywoływania **__pascal**, **__fortran**i **__syscall** nie są już obsługiwane. Można emulować ich funkcje przy użyciu jednej z obsługiwanych konwencji wywoływania i odpowiednich opcji konsolidatora.

\<Windows. h > obsługuje teraz makro WINAPI, które tłumaczy do odpowiedniej konwencji wywoływania dla elementu docelowego. Użyj WINAPI, w której wcześniej użyto języka PASCALa lub **__far \__pascal**.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)