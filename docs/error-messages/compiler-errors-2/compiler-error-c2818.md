---
title: Błąd kompilatora C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: 786a38aca2c3b9674969018d9e5766eed29c358c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212673"
---
# <a name="compiler-error-c2818"></a>Błąd kompilatora C2818

Aplikacja przeciążonego "operator->" jest rekursywna za poorednictwem typu "Type"

Ponowna definicja operatora dostępu do składowej klasy zawiera instrukcję cykliczną **`return`** . Aby ponownie zdefiniować `->` operator z rekursją, należy przenieść procedurę cykliczną do osobnej funkcji o nazwie z funkcji przesłaniania operatora.
