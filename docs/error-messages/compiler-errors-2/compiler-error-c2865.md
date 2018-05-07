---
title: C2865 błąd kompilatora | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 70b2c6c831fde18f9054e139a120d834a75b6950
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2865"></a>C2865 błąd kompilatora
"Funkcja": niedozwolone porównanie dla handle_or_pointer  
  
 Możesz porównać odwołania do [klas i struktur](../../windows/classes-and-structs-cpp-component-extensions.md) lub typy referencyjne tylko pod względem równości, aby zobaczyć, jeśli ich odwołują się do tego samego obiektu (==) lub do różnych obiektów zarządzanych (! =).  
  
 Nie można porównać je porządkowania, ponieważ środowisko uruchomieniowe platformy .NET mogą przenieść obiekty zarządzane w dowolnym momencie, zmiana wyniku testu.