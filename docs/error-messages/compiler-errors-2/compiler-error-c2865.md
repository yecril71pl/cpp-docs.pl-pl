---
title: "C2865 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2865
dev_langs:
- C++
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 149ca019ef30d66dba63bc927d79064a269d8c70
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2865"></a>C2865 błąd kompilatora
"Funkcja": niedozwolone porównanie dla handle_or_pointer  
  
 Możesz porównać odwołania do [klas i struktur](../../windows/classes-and-structs-cpp-component-extensions.md) lub typy referencyjne tylko pod względem równości, aby zobaczyć, jeśli ich odwołują się do tego samego obiektu (==) lub do różnych obiektów zarządzanych (! =).  
  
 Nie można porównać je porządkowania, ponieważ środowisko uruchomieniowe platformy .NET mogą przenieść obiekty zarządzane w dowolnym momencie, zmiana wyniku testu.