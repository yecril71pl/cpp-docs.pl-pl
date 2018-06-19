---
title: Kompilatora (poziom 4) ostrzeżenie C4214 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4214
dev_langs:
- C++
helpviewer_keywords:
- C4214
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0efe0666ded5428dcc40a1900f263cfc522a1502
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292925"
---
# <a name="compiler-warning-level-4-c4214"></a>Kompilator C4214 ostrzegawcze (poziom 4)
użyto niestandardowego rozszerzenia: typy pól inne niż int bitowych  
  
 Rozszerzenia Microsoft do domyślnego (/Ze) elementy członkowskie struktury bitfield mogą być dowolnego typu Liczba całkowita.  
  
## <a name="example"></a>Przykład  
  
```  
// C4214.c  
// compile with: /W4  
struct bitfields  
{  
   unsigned short j:4;  // C4214  
};  
  
int main()  
{  
}  
```  
  
 Takie pól bitowych są nieprawidłowe w obszarze Zgodność ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).