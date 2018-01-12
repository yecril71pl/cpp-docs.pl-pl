---
title: "Błąd kompilatora C2030 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2030
dev_langs: C++
helpviewer_keywords: C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c025fe57d411ae4744a10fe9bc062b336e189e83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2030"></a>Błąd kompilatora C2030
destruktor z ułatwieniami dostępu z "protected private" nie może być elementem członkowskim klasy zadeklarowanej jako "sealed"  
  
 Klasa środowiska uruchomieniowego systemu Windows jest zadeklarowany jako `sealed` nie może mieć destruktora prywatnej chronionych. Tylko publiczne wirtualnego i prywatnych destruktory-virtual są dozwolone w typach zapieczętowanych. Aby uzyskać więcej informacji, zobacz [Ref klas i struktur](../../cppcx/ref-classes-and-structs-c-cx.md).  
  
 Aby naprawić ten błąd, zmień dostępność elementu destruktor.