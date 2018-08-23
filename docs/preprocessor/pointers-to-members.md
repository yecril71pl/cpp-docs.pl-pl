---
title: pointers_to_members | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
dev_langs:
- C++
helpviewer_keywords:
- class members, pointers to
- pragmas, pointers_to_members
- members, pointers to
- pointers_to_members pragma
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09b0fcd2a00806d075e70d1469b57ba0a0dd5332
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42464643"
---
# <a name="pointerstomembers"></a>pointers_to_members
**Określonego język C++**  
  
Określa, czy wskaźnik do składowej klasy może być zadeklarowany przed jego definicją klasy skojarzonej i jest używany do kontroli rozmiaru wskaźnika oraz kodu wymaganego do interpretacji wskaźnika.  
  
## <a name="syntax"></a>Składnia  
  
```    
#pragma pointers_to_members( pointer-declaration, [most-general-representation] )  
```  
  
## <a name="remarks"></a>Uwagi  
 
Możesz umieścić **pointers_to_members** dyrektywy w pliku źródłowym, jako alternatywa dla użycia [/vmx](../build/reference/vmb-vmg-representation-method.md) opcje kompilatora lub [słowa kluczowe dziedziczenia](../cpp/inheritance-keywords.md).  
  
*Deklaracji wskaźnika* argument określa, czy zadeklarowano wskaźnik do członka przed lub po definicji funkcji skojarzonej. *Deklaracji wskaźnika* argument jest jednym z dwóch następujących symboli:  
  
|Argument|Komentarze|  
|--------------|--------------|  
|*full_generality*|Generuje bezpieczny, czasem nieoptymalny kod. Możesz użyć *full_generality* jeżeli zadeklarowano dowolny wskaźnik do składowej przed zdefiniowaniem klasy skojarzonej. Ten argument zawsze używa reprezentacji wskaźnika określonej przez *most-general-representation* argumentu. Równoważny z /vmg.|  
|*best_case*|Generuje bezpieczny, optymalny kod przy użyciu reprezentacji najlepszego przypadku dla wszystkich wskaźników do członków. Wymaga zdefiniowania klasy przed zadeklarowaniem wskaźnika do składowej klasy. Wartość domyślna to *best_case*.|  
  
*Most-general-representation* argument określa reprezentację najmniejszego wskaźnika, który kompilator bezpiecznie umożliwia dowolny wskaźnik do składowej klasy w jednostce translacji. Argument może być jednym z następujących:  
  
|Argument|Komentarze|  
|--------------|--------------|  
|*single_inheritance*|Najbardziej ogólną reprezentacją jest pojedyncze dziedziczenie, wskaźnik do funkcji członkowskiej. Powoduje błąd, jeśli model dziedziczenia definicji klasy, do której zgłaszany jest wskaźnik do składowej, jest wielokrotny lub wirtualny.|  
|*multiple_inheritance*|Najbardziej ogólną reprezentacją jest wielokrotne dziedziczenie, wskaźnik do funkcji członkowskiej. Powoduje błąd, jeśli model dziedziczenia definicji klasy, do której zgłaszany jest wskaźnik do składowej, jest wirtualny.|  
|*virtual_inheritance*|Najbardziej ogólną reprezentacją jest wirtualne dziedziczenie, wskaźnik do funkcji członkowskiej. Nigdy nie powoduje błędu. To jest argument domyślny podczas `#pragma pointers_to_members(full_generality)` jest używany.|  
  
> [!CAUTION]
> Radzimy umieścić **pointers_to_members** pragma tylko w pliku kodu źródłowego, który chcesz mieć wpływ i tylko po dowolnej `#include` dyrektywy. Taka praktyka zmniejsza ryzyko, że pragma wpłynie na inne pliki i przypadkowo określi wiele definicji dla tej samej zmiennej, funkcji lub nazwy klasy.  
  
## <a name="example"></a>Przykład  
  
```  
//   Specify single-inheritance only  
#pragma pointers_to_members( full_generality, single_inheritance )  
```  
  
## <a name="end-c-specific"></a>KONIEC określonego języka C++  
  
## <a name="see-also"></a>Zobacz też  
 
[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)