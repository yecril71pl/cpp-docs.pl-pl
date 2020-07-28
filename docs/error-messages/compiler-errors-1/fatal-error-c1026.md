---
title: Błąd krytyczny C1026
ms.date: 11/04/2016
f1_keywords:
- C1026
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
ms.openlocfilehash: 9ea97bef16bebb8fc0e765ed708e54baee9a64de
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220343"
---
# <a name="fatal-error-c1026"></a>Błąd krytyczny C1026

przepełnienie stosu parsera, zbyt skomplikowany program

Miejsce wymagane do przeanalizowania programu spowodowało przepełnienie stosu kompilatora.

Zmniejsz złożoność wyrażeń przez:

- Zmniejszenie zagnieżdżenia w **`for`** **`switch`** instrukcjach i. Umieść bardziej głęboko zagnieżdżone instrukcje w osobnych funkcjach.

- Przerywanie długich wyrażeń, które obejmują operatory przecinkowe lub wywołania funkcji.
