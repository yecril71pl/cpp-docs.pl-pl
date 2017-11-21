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
ms.openlocfilehash: a2efd868160e3ec7e5bf356603cc821a0b07f149
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2030"></a>Błąd kompilatora C2030
destruktor z ułatwieniami dostępu z "protected private" nie może być elementem członkowskim klasy zadeklarowanej jako "sealed"  
  
 Klasa środowiska uruchomieniowego systemu Windows jest zadeklarowany jako `sealed` nie może mieć destruktora prywatnej chronionych. Tylko publiczne wirtualnego i prywatnych destruktory-virtual są dozwolone w typach zapieczętowanych. Aby uzyskać więcej informacji, zobacz [Ref klas i struktur](../../cppcx/ref-classes-and-structs-c-cx.md).  
  
 Aby naprawić ten błąd, zmień dostępność elementu destruktor.