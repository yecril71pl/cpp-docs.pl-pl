---
title: Kompilatora (poziom 4) ostrzeżenie C4221 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4221
dev_langs:
- C++
helpviewer_keywords:
- C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1e602eb662533207a1f2957d3b11a0823e4b83af
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293198"
---
# <a name="compiler-warning-level-4-c4221"></a>Kompilator C4221 ostrzegawcze (poziom 4)
użyto niestandardowego rozszerzenia: "identyfikator": nie można zainicjować przy użyciu adresu automatycznej zmiennej  
  
 Rozszerzenia Microsoft domyślne (/Ze), można zainicjować typu agregacji (**tablicy**, `struct`, lub **Unii**) przy użyciu adresu zmiennej lokalnej (Automatyczna).  
  
## <a name="example"></a>Przykład  
  
```  
// C4221.c  
// compile with: /W4  
struct S  
{  
   int *i;  
};  
  
void func()  
{  
   int j;  
   struct S s1 = { &j };   // C4221  
}  
  
int main()  
{  
}  
```  
  
 Takie inicjalizacji są nieprawidłowe w obszarze Zgodność ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).