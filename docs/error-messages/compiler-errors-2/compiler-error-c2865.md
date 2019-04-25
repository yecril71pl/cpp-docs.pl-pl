---
title: Błąd kompilatora C2865
ms.date: 11/04/2016
f1_keywords:
- C2865
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
ms.openlocfilehash: 38b7dd86a57c3cd89811c6489e51fb4271fd7b79
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165158"
---
# <a name="compiler-error-c2865"></a>Błąd kompilatora C2865

'Funkcja': niedozwolone porównanie dla handle_or_pointer

Możesz porównać odwołania do [klas i struktur](../../extensions/classes-and-structs-cpp-component-extensions.md) lub typów referencyjnych tylko pod kątem równości, aby zobaczyć, jeśli odnoszą się do tego samego obiektu (==) lub do różnych obiektów zarządzanych (! =).

Nie można porównać ich do ustalania kolejności, ponieważ środowisko uruchomieniowe platformy .NET mogą przenieść obiekty zarządzane w dowolnym momencie, zmieniając wynik testu.