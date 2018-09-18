---
title: C2410 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2410
dev_langs:
- C++
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba4c2b57bcae062ccf811e33cf1deaea45f83737
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052455"
---
# <a name="compiler-error-c2410"></a>C2410 błąd kompilatora

"identyfikator": niejednoznaczna nazwa składowej w "context"

Identyfikator jest członkiem więcej niż jednej struktury lub Unii w tym kontekście.

W przypadku argumentu operacji, które spowodowały błąd, należy użyć specyfikatora struktury lub Unii. Specyfikator struktury lub Unii jest identyfikatorem typu `struct` lub `union` ( `typedef` nazwy lub zmienną typu tej samej struktury lub Unii, do którego nastąpiło odwołanie). Specyfikator musi być lewy operand pierwszy operator wyboru elementów członkowskich (.) do użycia operandu.