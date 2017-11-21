---
title: "C2696 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2696
dev_langs: C++
helpviewer_keywords: C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 70ccaf34a0191f0bd69c95d2cb110f6e6542a6d1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2696"></a>C2696 błąd kompilatora
Nie można utworzyć tymczasowego obiektu typu zarządzanego 'type'  
  
Odwołuje się do `const` w programie niezarządzane spowodować, że kompilator, aby wywołać konstruktora i utworzyć tymczasowego obiektu na stosie. Jednak zarządzanej klasy nigdy nie mogą być tworzone na stosie.  
  
C2696 jest tylko przy użyciu opcji kompilatora przestarzałe **: oldsyntax**.  
