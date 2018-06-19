---
title: Kompilatora (poziom 1) ostrzeżenie C4190 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4190
dev_langs:
- C++
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e62f6bcfaa499338d5fde1d09cb91574241ce8a0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277897"
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