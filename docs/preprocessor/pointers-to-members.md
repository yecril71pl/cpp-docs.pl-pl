---
title: pointers_to_members | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
dev_langs: C++
helpviewer_keywords:
- class members, pointers to
- pragmas, pointers_to_members
- members, pointers to
- pointers_to_members pragma
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4fc108f6f4755319d500227d9163dc090847e2ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="pointerstomembers"></a>pointers_to_members
**Określonego języka C++**  
  
 Określa, czy wskaźnik do członka klasy może być zadeklarowany przed jego definicją klasy skojarzonej i jest używany do kontroli rozmiaru wskaźnika oraz kodu wymaganego do interpretacji wskaźnika.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#pragma pointers_to_members( pointer-declaration, [most-general-representation] )  
```  
  
## <a name="remarks"></a>Uwagi  
 Możesz umieścić **pointers_to_members** pragma w pliku źródłowego jako alternatywa dla użycia [/vmx](../build/reference/vmb-vmg-representation-method.md) — opcje kompilatora lub [słowa kluczowe dziedziczenia](../cpp/inheritance-keywords.md).  
  
 *Deklaracji wskaźnika* argument określa, czy należy zadeklarować wskaźnika do elementu członkowskiego przed lub po definicji funkcji skojarzone. *Deklaracji wskaźnika* argument jest jednym z dwóch następujących symboli:  
  
|Argument|Komentarze|  
|--------------|--------------|  
|**full_generality**|Generuje bezpieczny, czasem nieoptymalny kod. Możesz użyć **full_generality** zadeklarowana przed definicji klasy skojarzone żadnych wskaźnika do elementu członkowskiego. Ten argument zawsze używa reprezentacja wskaźnika określony przez *większość ogólna reprezentacja* argumentu. Równoważny z /vmg.|  
|**best_case**|Generuje bezpieczny, optymalny kod przy użyciu reprezentacji najlepszego przypadku dla wszystkich wskaźników do członków. Wymaga zdefiniowania klasy przed zadeklarowaniem wskaźnika do członka klasy. Wartość domyślna to **best_case**.|  
  
 *Większość ogólna reprezentacja* argument określa najmniejszy reprezentacja wskaźnika kompilator bezpiecznie umożliwia odwołanie wszelkich wskaźnika do elementu członkowskiego klasy w jednostce tłumaczenia. Argument może być jednym z następujących:  
  
|Argument|Komentarze|  
|--------------|--------------|  
|**pojedynczego dziedziczenia**|Najbardziej ogólną reprezentacją jest pojedyncze dziedziczenie, wskaźnik do funkcji członkowskiej. Powoduje błąd, jeśli model dziedziczenia definicji klasy, do której zgłaszany jest wskaźnik do członka jest wielokrotny lub wirtualny.|  
|**multiple_inheritance**|Najbardziej ogólną reprezentacją jest wielokrotne dziedziczenie, wskaźnik do funkcji członkowskiej. Powoduje błąd, jeśli model dziedziczenia definicji klasy, do której zgłaszany jest wskaźnik do członka jest wirtualny.|  
|**virtual_inheritance**|Najbardziej ogólną reprezentacją jest wirtualne dziedziczenie, wskaźnik do funkcji członkowskiej. Nigdy nie powoduje błędu. To jest argument domyślny po **#pragma pointers_to_members(full_generality)** jest używany.|  
  
> [!CAUTION]
>  Radzimy umieścić pragmę `pointers_to_members` tylko w pliku z kodem źródłowym, na który chcesz mieć wpływ i tylko po dowolnej dyrektywie `#include`. Taka praktyka zmniejsza ryzyko, że pragma wpłynie na inne pliki i przypadkowo określi wiele definicji dla tej samej zmiennej, funkcji lub nazwy klasy.  
  
## <a name="example"></a>Przykład  
  
```  
//   Specify single-inheritance only  
#pragma pointers_to_members( full_generality, single_inheritance )  
```  
  
## <a name="end-c-specific"></a>KOŃCOWY określonego języka C++  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)