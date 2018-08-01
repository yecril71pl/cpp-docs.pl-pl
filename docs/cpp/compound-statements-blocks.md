---
title: Instrukcje złożone (bloki) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '}'
- '{'
dev_langs:
- C++
helpviewer_keywords:
- blocks, about blocks
- compound statements
ms.assetid: 23855939-7430-498e-8936-0c70055ea701
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c85de0f147d0cfed873a091d17c46e56bf5758a9
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408528"
---
# <a name="compound-statements-blocks"></a>Instrukcje złożone (bloki)
Instrukcja złożona składa się z zero lub więcej instrukcji ujęta w nawiasy klamrowe (**{}**). Instrukcja złożona może służyć wszędzie tam, gdzie Oczekiwano instrukcji. Instrukcje złożone są często nazywane "blokuje".  
  
## <a name="syntax"></a>Składnia  
  
```  
{ [ statement-list ] }  
```  
  
## <a name="remarks"></a>Uwagi  
 W poniższym przykładzie użyto instrukcji złożonej jako *instrukcji* wchodzi w skład **Jeśli** — instrukcja (zobacz [if — instrukcja](../cpp/if-else-statement-cpp.md) szczegółowe informacje na temat składni):  
  
```cpp 
if( Amount > 100 )  
{  
    cout << "Amount was too large to handle\n";  
    Alert();  
}  
else  
{
    Balance -= Amount;  
}
```  
  
> [!NOTE]
>  Ponieważ deklaracja znajduje się zdanie, deklaracja może być jednym z instrukcji w *listy instrukcji*. W rezultacie nazwy zadeklarowane wewnątrz instrukcji złożonej, ale nie zostały jawnie zadeklarowane jako statyczne, mają zakres lokalny i (dla obiektów) okres istnienia. Zobacz [zakres](../cpp/scope-visual-cpp.md) szczegółowe informacje na temat przetwarzania nazw z zakresem lokalnym.  
  
## <a name="see-also"></a>Zobacz także  
 [Przegląd instrukcji C++](../cpp/overview-of-cpp-statements.md)