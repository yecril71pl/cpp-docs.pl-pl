---
title: Błąd kompilatora C2410
ms.date: 11/04/2016
f1_keywords:
- C2410
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
ms.openlocfilehash: e4d30ff0fbca7428fb1dcf252bcad50bd53488d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205706"
---
# <a name="compiler-error-c2410"></a>Błąd kompilatora C2410

"Identyfikator": niejednoznaczna nazwa składowej w "context"

Identyfikator jest członkiem więcej niż jednej struktury lub Unii w tym kontekście.

Użyj struktury lub specyfikatora Union dla operandu, który spowodował błąd. Specyfikator struktury lub Unii jest identyfikatorem typu `struct` lub `union` (nazwą `typedef` lub zmienną tego samego typu co struktura lub Unia, do której odwołuje się odwołanie). Specyfikator musi być lewym operandem pierwszego operatora wyboru elementu członkowskiego (.), aby użyć operandu.
