---
title: Błąd kompilatora C3550
ms.date: 11/04/2016
f1_keywords:
- C3550
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
ms.openlocfilehash: 17c90aa68b29c9490deb8d49895162e8a6bdefec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200775"
---
# <a name="compiler-error-c3550"></a>Błąd kompilatora C3550

w tym kontekście jest dozwolony tylko zwykły element "decltype (Auto)"

Jeśli `decltype(auto)` jest używany jako symbol zastępczy dla zwracanego typu funkcji, musi być używany przez samą siebie. Nie można jej użyć jako części deklaracji wskaźnika (`decltype(auto*)`), deklaracji odwołania (`decltype(auto&)`) ani żadnych innych kwalifikacji.

## <a name="see-also"></a>Zobacz też

[auto](../../cpp/auto-cpp.md)
