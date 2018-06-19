---
title: Optymalizacja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bff0e4cc40bfa0e355f348c02f01cb0c7445b596
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849252"
---
# <a name="optimize"></a>optymalizuj
Określa optymalizacje wykonywane na podstawie funkcja przez funkcję.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#pragma optimize( "[optimization-list]", {on | off} )  
```  
  
## <a name="remarks"></a>Uwagi  
 **Zoptymalizować** pragma musi występować poza funkcją i obowiązuje w pierwszej funkcji zdefiniowane po pragma jest widoczna. **Na** i **poza** argumenty włączyć opcje określone w *listy optymalizacji* lub wyłączyć.  
  
 *Listy optymalizacji* może być zero lub więcej parametrów pokazano w poniższej tabeli.  
  
### <a name="parameters-of-the-optimize-pragma"></a>Parametry Optymalizacja Pragma  
  
|Parametrów|Rodzaj optymalizacji|  
|--------------------|--------------------------|  
|**g**|Włącz optymalizacje globalne.|  
|**s** lub **t**|Określ krótka lub szybkiego sekwencji kod maszynowy.|  
|**y**|Generowanie wskaźników ramek na stosie programu.|  
  
 Są to te same litery używane z [/O](../build/reference/o-options-optimize-code.md) — opcje kompilatora. Na przykład następujące pragma jest odpowiednikiem **/OS** — opcja kompilatora:  
  
```  
#pragma optimize( "ts", on )  
```  
  
 Przy użyciu **zoptymalizować** pragma z pustym ciągiem (**""**) to specjalny rodzaj dyrektywy:  
  
 Jeśli używasz **poza** parametru włącza optymalizacje, wymienione w tabeli wcześniej w tym temacie wyłączanie.  
  
 Jeśli używasz **na** parametru, następuje zresetowanie optymalizacje do tych, które określono [/O](../build/reference/o-options-optimize-code.md) — opcja kompilatora.  
  
```  
#pragma optimize( "", off )  
.  
.  
.  
#pragma optimize( "", on )   
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)