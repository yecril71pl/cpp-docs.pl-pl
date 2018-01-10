---
title: __alignof operator | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- alignas_cpp
- __alignof_cpp
- alignof_cpp
dev_langs: C++
helpviewer_keywords:
- alignas [C++]
- alignment of structures
- __alignof keyword [C++]
- alignof [C++]
- types [C++], alignment requirements
ms.assetid: acb1eed7-6398-40bd-b0c5-684ceb64afbc
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 50a8d6e524847d46d62b5f1da134332f35edcf92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="alignof-operator"></a>Operator __alignof
Wprowadza c ++ 11 `alignof` operator, który zwraca wyrównania w bajtach określonego typu. Przenośności maksymalna należy użyć operatora alignof zamiast operator __alignof specyficzne dla firmy Microsoft.  
  
 **Dotyczące firmy Microsoft**  
  
 Zwraca wartość typu **size_t** oznacza to wymaganie wyrównania typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      __alignof(   
   type    
)  
```  
  
## <a name="remarks"></a>Uwagi  
 Na przykład:  
  
|Wyrażenie|Wartość|  
|----------------|-----------|  
|**__alignof (char)**|1|  
|**__alignof (short)**|2|  
|**__alignof (int)**|4|  
|**__alignof ( \__int64)**|8|  
|**__alignof (float)**|4|  
|**__alignof (o podwójnej precyzji)**|8|  
|**__alignof (char\* )**|4|  
  
 `__alignof` Wartość jest taka sama jak wartość `sizeof` dla typów podstawowych. Należy wziąć pod uwagę, jednak w tym przykładzie:  
  
```  
typedef struct { int a; double b; } S;  
// __alignof(S) == 8  
```  
  
 W takim przypadku `__alignof` wartość jest wymaganie wyrównanie elementu największy w strukturze.  
  
 Podobnie dla  
  
```  
typedef __declspec(align(32)) struct { int a; } S;  
```  
  
 `__alignof(S)`jest równa `32`.  
  
 Użycie jednego `__alignof` byłoby jako parametr do jednego z własnych procedur alokacji pamięci. Na przykład, biorąc pod uwagę następujące zdefiniowane struktury `S`, można wywołać procedury alokacji pamięci o nazwie `aligned_malloc` można przydzielić pamięci na granicy wyrównania konkretnego.  
  
```  
typedef __declspec(align(32)) struct { int a; double b; } S;  
int n = 50; // array size  
S* p = (S*)aligned_malloc(n * sizeof(S), __alignof(S));  
```  
  
 Aby uzyskać więcej informacji na temat modyfikowania wyrównania zobacz:  
  
-   [pakiet](../preprocessor/pack.md)  
  
-   [Dopasuj](../cpp/align-cpp.md)  
  
-   [__unaligned](../cpp/unaligned.md)  
  
-   [/ZP (wyrównanie członka struktury)](../build/reference/zp-struct-member-alignment.md)  
  
-   [Przykłady wyrównania struktury](../build/examples-of-structure-alignment.md) (x64 określonych)  
  
 Aby uzyskać więcej informacji na temat różnic w wyrównania w kodzie x86 i x64 zobacz:  
  
-   [Konflikty z kompilatorem x86](../build/conflicts-with-the-x86-compiler.md)  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia z operatorami Jednoargumentowymi](../cpp/expressions-with-unary-operators.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)