---
title: Błąd kompilatora C2865
ms.date: 11/04/2016
f1_keywords:
- C2865
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
ms.openlocfilehash: dd4374c1a577c4c39c5dec107ed5025d7cdc79c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201699"
---
# <a name="compiler-error-c2865"></a>Błąd kompilatora C2865

"Function": niedozwolone porównanie dla handle_or_pointer

Odwołania do [klas i struktur](../../extensions/classes-and-structs-cpp-component-extensions.md) lub typów odwołań zarządzanych można porównać tylko dla równości, aby sprawdzić, czy odwołują się do tego samego obiektu (= =) lub do różnych obiektów (! =).

Nie można porównać ich do uporządkowania, ponieważ środowisko uruchomieniowe platformy .NET może przenosić obiekty zarządzane w dowolnym momencie, zmieniając wyniki testu.
