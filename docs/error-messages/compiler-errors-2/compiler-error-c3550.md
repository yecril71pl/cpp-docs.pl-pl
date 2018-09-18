---
title: Błąd kompilatora C3550 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3550
dev_langs:
- C++
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08c22d7e371fda7a229b541f78d4385f2943ee54
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047788"
---
# <a name="compiler-error-c3550"></a>Błąd kompilatora C3550

tylko zwykły elementu "decltype(auto)" jest dozwolony w tym kontekście

Jeśli `decltype(auto)` jest używana jako symbol zastępczy dla zwracanego typu funkcji musi być użyty samodzielnie. Nie można używać jako część deklaracji wskaźnika (`decltype(auto*)`), deklaracja odwołania (`decltype(auto&)`), lub inne takie kwalifikacji.

## <a name="see-also"></a>Zobacz też

[auto](../../cpp/auto-cpp.md)