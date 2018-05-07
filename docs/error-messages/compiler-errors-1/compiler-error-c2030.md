---
title: Błąd kompilatora C2030 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2030
dev_langs:
- C++
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ceccc1088e32382167e7e6400360b30de07fde1d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2030"></a>Błąd kompilatora C2030
destruktor z ułatwieniami dostępu z "protected private" nie może być elementem członkowskim klasy zadeklarowanej jako "sealed"  
  
 Klasa środowiska uruchomieniowego systemu Windows jest zadeklarowany jako `sealed` nie może mieć destruktora prywatnej chronionych. Tylko publiczne wirtualnego i prywatnych destruktory-virtual są dozwolone w typach zapieczętowanych. Aby uzyskać więcej informacji, zobacz [Ref klas i struktur](../../cppcx/ref-classes-and-structs-c-cx.md).  
  
 Aby naprawić ten błąd, zmień dostępność elementu destruktor.