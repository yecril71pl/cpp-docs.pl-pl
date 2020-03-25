---
title: Błąd krytyczny C1026
ms.date: 11/04/2016
f1_keywords:
- C1026
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
ms.openlocfilehash: a7c7a5da01c8b4a44c307a00f53530acb12a8009
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204656"
---
# <a name="fatal-error-c1026"></a>Błąd krytyczny C1026

przepełnienie stosu parsera, zbyt skomplikowany program

Miejsce wymagane do przeanalizowania programu spowodowało przepełnienie stosu kompilatora.

Zmniejsz złożoność wyrażeń przez:

- Zmniejszenie zagnieżdżenia w `for` i `switch` instrukcji. Umieść bardziej głęboko zagnieżdżone instrukcje w osobnych funkcjach.

- Przerywanie długich wyrażeń, które obejmują operatory przecinkowe lub wywołania funkcji.
