---
title: Błąd kompilatora C2865
ms.date: 11/04/2016
f1_keywords:
- C2865
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
ms.openlocfilehash: e95714f7a10c1c25562e8b12025ede486e66cff8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532754"
---
# <a name="compiler-error-c2865"></a>Błąd kompilatora C2865

'Funkcja': niedozwolone porównanie dla handle_or_pointer

Możesz porównać odwołania do [klas i struktur](../../windows/classes-and-structs-cpp-component-extensions.md) lub typów referencyjnych tylko pod kątem równości, aby zobaczyć, jeśli odnoszą się do tego samego obiektu (==) lub do różnych obiektów zarządzanych (! =).

Nie można porównać ich do ustalania kolejności, ponieważ środowisko uruchomieniowe platformy .NET mogą przenieść obiekty zarządzane w dowolnym momencie, zmieniając wynik testu.