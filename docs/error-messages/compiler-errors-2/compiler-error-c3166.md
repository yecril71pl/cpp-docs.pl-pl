---
title: Błąd kompilatora C3166
ms.date: 11/04/2016
f1_keywords:
- C3166
helpviewer_keywords:
- C3166
ms.assetid: ec3e330d-c15d-4158-8268-09101486c566
ms.openlocfilehash: 1915d58f73ce8d16135951b359c3f0fd48aea3ac
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230873"
---
# <a name="compiler-error-c3166"></a>Błąd kompilatora C3166

> "wskaźnik": nie można zadeklarować wskaźnika do wewnętrznego wskaźnika __gc jako elementu członkowskiego "Type"

Kompilator znalazł nieprawidłową deklarację wskaźnika ( **`__nogc`** wskaźnik do **`__gc`** wskaźnika).

C3166 jest osiągalna tylko przy użyciu przestarzałej opcji kompilatora **`/clr:oldSyntax`** .
