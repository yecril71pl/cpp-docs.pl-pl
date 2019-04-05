---
title: Błąd kompilatora C3550
ms.date: 11/04/2016
f1_keywords:
- C3550
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
ms.openlocfilehash: 106ac93496eebb25ee603251d84680053e1310b7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59032340"
---
# <a name="compiler-error-c3550"></a>Błąd kompilatora C3550

tylko zwykły elementu "decltype(auto)" jest dozwolony w tym kontekście

Jeśli `decltype(auto)` jest używana jako symbol zastępczy dla zwracanego typu funkcji musi być użyty samodzielnie. Nie można używać jako część deklaracji wskaźnika (`decltype(auto*)`), deklaracja odwołania (`decltype(auto&)`), lub inne takie kwalifikacji.

## <a name="see-also"></a>Zobacz także

[auto](../../cpp/auto-cpp.md)