---
title: Błąd kompilatora C3550
ms.date: 11/04/2016
f1_keywords:
- C3550
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
ms.openlocfilehash: dbed14b9f2fa0f2163484edd8b5dfa330af9cbf1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498890"
---
# <a name="compiler-error-c3550"></a>Błąd kompilatora C3550

tylko zwykły elementu "decltype(auto)" jest dozwolony w tym kontekście

Jeśli `decltype(auto)` jest używana jako symbol zastępczy dla zwracanego typu funkcji musi być użyty samodzielnie. Nie można używać jako część deklaracji wskaźnika (`decltype(auto*)`), deklaracja odwołania (`decltype(auto&)`), lub inne takie kwalifikacji.

## <a name="see-also"></a>Zobacz też

[auto](../../cpp/auto-cpp.md)