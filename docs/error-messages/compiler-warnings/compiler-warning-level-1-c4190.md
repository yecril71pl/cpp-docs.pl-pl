---
title: "Kompilatora (poziom 1) ostrzeżenie C4190 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4190
dev_langs: C++
helpviewer_keywords: C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1f01997ecd685942123b9e5c07db1a2dd59b6618
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4190"></a>Kompilator C4190 ostrzegawcze (poziom 1)
"identifier1" ma określone powiązanie C, ale zwraca UDT identifier2, co jest niezgodne z C  
  
 Funkcja lub wskaźnika do funkcji ma UDT (zdefiniowane przez użytkownika typ, który jest klasy, struktury, wyliczenia lub union) jako zwracany typ i `extern` powiązania "C". Jest to dozwolony jeśli:  
  
-   Wszystkie wywołania tej funkcji występują z C++.  
  
-   Definicja funkcji jest w języku C++.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// C4190.cpp  
// compile with: /W1 /LD  
struct X  
{  
   int i;  
   X ();  
   virtual ~X ();  
};  
  
extern "C" X func ();   // C4190  
```