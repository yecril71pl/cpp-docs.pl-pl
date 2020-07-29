---
title: Błąd kompilatora C2410
ms.date: 11/04/2016
f1_keywords:
- C2410
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
ms.openlocfilehash: 7e6e07fb90827fb28fcdde2f723a36c4529a1868
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225491"
---
# <a name="compiler-error-c2410"></a>Błąd kompilatora C2410

"Identyfikator": niejednoznaczna nazwa składowej w "context"

Identyfikator jest członkiem więcej niż jednej struktury lub Unii w tym kontekście.

Użyj struktury lub specyfikatora Union dla operandu, który spowodował błąd. Specyfikator struktury lub Unii jest identyfikatorem typu **`struct`** lub **`union`** ( **`typedef`** nazwą lub zmienną tego samego typu co struktura lub Unia, do której się odwołuje). Specyfikator musi być lewym operandem pierwszego operatora wyboru elementu członkowskiego (.), aby użyć operandu.
