---
title: Błąd kompilatora C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: 00952e55f1b732bd9af3733f5c0ec575a39116fe
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202115"
---
# <a name="compiler-error-c2818"></a>Błąd kompilatora C2818

Aplikacja przeciążonego "operator->" jest rekursywna za poorednictwem typu "Type"

Ponowna definicja operatora dostępu do składowej klasy zawiera cykliczną instrukcję `return`. Aby ponownie zdefiniować operator `->` z rekursją, należy przenieść procedurę cykliczną do osobnej funkcji o nazwie z funkcji przesłaniania operatora.
