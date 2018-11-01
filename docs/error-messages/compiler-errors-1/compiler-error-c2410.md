---
title: C2410 błąd kompilatora
ms.date: 11/04/2016
f1_keywords:
- C2410
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
ms.openlocfilehash: 8b01a2f7b9c55fb57c880df5033538f4e45f76b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643693"
---
# <a name="compiler-error-c2410"></a>C2410 błąd kompilatora

"identyfikator": niejednoznaczna nazwa składowej w "context"

Identyfikator jest członkiem więcej niż jednej struktury lub Unii w tym kontekście.

W przypadku argumentu operacji, które spowodowały błąd, należy użyć specyfikatora struktury lub Unii. Specyfikator struktury lub Unii jest identyfikatorem typu `struct` lub `union` ( `typedef` nazwy lub zmienną typu tej samej struktury lub Unii, do którego nastąpiło odwołanie). Specyfikator musi być lewy operand pierwszy operator wyboru elementów członkowskich (.) do użycia operandu.