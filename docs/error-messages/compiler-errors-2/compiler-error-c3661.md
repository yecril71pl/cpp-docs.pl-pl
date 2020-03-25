---
title: Błąd kompilatora C3661
ms.date: 11/04/2016
f1_keywords:
- C3661
helpviewer_keywords:
- C3661
ms.assetid: 50793fd1-1829-4b29-ad0d-094ef2068b43
ms.openlocfilehash: 5edda7eaf50dc4fca60f47128dc97de5d3a1a395
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200380"
---
# <a name="compiler-error-c3661"></a>Błąd kompilatora C3661

Lista jawnego przesłaniania nie znalazła żadnych metod do przesłonięcia

Jawne przesłonięcie określiło jedną lub więcej nazw typów.  Jednak w typach, które pasują do sygnatury funkcji przesłaniania, nie było żadnej funkcji z niezbędnym podpisem.  Jeśli próbujesz przesłonić na podstawie nazwy typu, musi istnieć co najmniej jedna funkcja wirtualna w określonych typach, która pasuje do sygnatury funkcji zastępującej.

Aby uzyskać więcej informacji, zobacz [jawne zastąpienia](../../extensions/explicit-overrides-cpp-component-extensions.md).
