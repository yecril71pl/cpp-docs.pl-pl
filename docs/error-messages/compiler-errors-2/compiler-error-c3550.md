---
title: Błąd kompilatora C3550
ms.date: 11/04/2016
f1_keywords:
- C3550
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
ms.openlocfilehash: 106ac93496eebb25ee603251d84680053e1310b7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032340"
---
# <a name="compiler-error-c3550"></a>Błąd kompilatora C3550

tylko zwykły elementu "decltype(auto)" jest dozwolony w tym kontekście

Jeśli `decltype(auto)` jest używana jako symbol zastępczy dla zwracanego typu funkcji musi być użyty samodzielnie. Nie można używać jako część deklaracji wskaźnika (`decltype(auto*)`), deklaracja odwołania (`decltype(auto&)`), lub inne takie kwalifikacji.

## <a name="see-also"></a>Zobacz także

[auto](../../cpp/auto-cpp.md)