---
title: Błąd kompilatora C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: f6e33d0e0ee139138df7d8e11357100b3ec3a1a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388699"
---
# <a name="compiler-error-c2818"></a>Błąd kompilatora C2818

Aplikacja przeciążonego "operator ->" jest rekursywna za pośrednictwem typu "type"

Ponowne zdefiniowanie operatora dostępu do składowej klasy zawiera cykliczne `return` instrukcji. Ponowne zdefiniowanie `->` operator rekursji, należy przenieść procedury cykliczne do oddzielnych funkcję o nazwie od operatora przesłonić funkcji.