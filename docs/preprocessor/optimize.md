---
title: Optymalizowanie | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 8222d909ad23157b4e3ed32a6920abadd77709b6
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465125"
---
# <a name="optimize"></a>optymalizuj
Określa optymalizacje wykonywane na podstawie funkcji przez funkcję.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma optimize( "[optimization-list]", {on | off} )  
```  
  
## <a name="remarks"></a>Uwagi  

**Zoptymalizować** pragma musi znajdować się poza funkcją i zaczyna obowiązywać przy pierwszej funkcji zdefiniowanych po pragmy jest widoczny. *Na* i *poza* argumenty Włącz opcje określone w *listy optymalizacji* lub wyłączyć.  
  
*Listy optymalizacji* może być zero lub jeden z parametrów pokazano w poniższej tabeli.  
  
### <a name="parameters-of-the-optimize-pragma"></a>Parametry optymalizacji Pragma  
  
|Parametry|Typ optymalizacji|  
|--------------------|--------------------------|  
|*g*|Włącz optymalizacje globalne.|  
|*s* lub *t*|Określ krótki i szybkie sekwencji kodu maszynowego.|  
|*y*|Generowanie wskaźników ramek na stosie program.|  
  
Są to tych samych liter, w ramach [/O](../build/reference/o-options-optimize-code.md) opcje kompilatora. Na przykład, następujące pragmy jest odpowiednikiem `/Os` — opcja kompilatora:  
  
```  
#pragma optimize( "ts", on )  
```  
  
Za pomocą **zoptymalizować** dyrektywę pusty ciąg (**""**) jest specjalną forma dyrektywy:  
  
Kiedy używasz *poza* parametr wyłącza optymalizacje, wymienione w tabeli wcześniej w tym temacie wyłączanie.  
  
Kiedy używasz *na* parametru resetuje Optymalizacje te, które określono [/O](../build/reference/o-options-optimize-code.md) — opcja kompilatora.  
  
```  
#pragma optimize( "", off )  
.  
.  
.  
#pragma optimize( "", on )   
```  
  
## <a name="see-also"></a>Zobacz też  
 
[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)