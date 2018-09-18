---
title: Błąd kompilatora C2865 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2865
dev_langs:
- C++
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc0a49f8e6ab42f7e607cd5f4f7cc91f6895abe0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035171"
---
# <a name="compiler-error-c2865"></a>Błąd kompilatora C2865

'Funkcja': niedozwolone porównanie dla handle_or_pointer

Możesz porównać odwołania do [klas i struktur](../../windows/classes-and-structs-cpp-component-extensions.md) lub typów referencyjnych tylko pod kątem równości, aby zobaczyć, jeśli odnoszą się do tego samego obiektu (==) lub do różnych obiektów zarządzanych (! =).

Nie można porównać ich do ustalania kolejności, ponieważ środowisko uruchomieniowe platformy .NET mogą przenieść obiekty zarządzane w dowolnym momencie, zmieniając wynik testu.