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
ms.openlocfilehash: 9a8823935ee2f871cdc033aec23f05fc108244e8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="compound-statements-blocks"></a>Instrukcje złożone (bloki)
Instrukcja złożona składa się zero lub więcej instrukcji ujętą w nawiasy klamrowe (**{}**). Instrukcja złożona może służyć wszędzie tam, gdzie Oczekiwano instrukcji. Instrukcje złożone są często nazywane "bloków."  
  
## <a name="syntax"></a>Składnia  
  
```  
  
{ [ statement-list ] }  
```  
  
## <a name="remarks"></a>Uwagi  
 W poniższym przykładzie użyto złożonej instrukcji jako *instrukcji* częścią **Jeśli** instrukcji (zobacz [if — instrukcja](../cpp/if-else-statement-cpp.md) szczegółowe informacje o składni):  
  
```  
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
>  Ponieważ deklaracji instrukcji, deklaracji może być jedną z instrukcji w *listy instrukcji*. W związku z tym nazwy deklarowane w złożonej instrukcji, ale nie zostało zadeklarowane jako statyczne, ma zakres lokalny (dla obiektów), a okres istnienia. Zobacz [zakres](../cpp/scope-visual-cpp.md) szczegółowe informacje na temat przetwarzania nazw z zakresem lokalnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd instrukcji C++](../cpp/overview-of-cpp-statements.md)