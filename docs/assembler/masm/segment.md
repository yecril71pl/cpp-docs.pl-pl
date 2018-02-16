---
title: SEGMENT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- SEGMENT
dev_langs:
- C++
helpviewer_keywords:
- SEGMENT directive
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 253c3b389bd0411e6b5096e914b6a844c8f40805
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="segment"></a>SEGMENT
Określa segment program o nazwie *nazwa* o atrybuty segmentu  
  
## <a name="syntax"></a>Składnia  
  
```  
  
   name SEGMENT [[READONLY]] [[align]] [[combine]] [[use]] [[characteristics]] ALIAS(string) [['class']]  
statements  
name ENDS  
```  
  
#### <a name="parameters"></a>Parametry  
 *align*  
 Zakres adresów pamięci, z których można wybrać adres początkowy dla tego segmentu. Typ wyrównania może być jednym z następujących czynności:  
  
|Dopasuj typu|Adres początkowy|  
|----------------|----------------------|  
|**BAJTÓW**|Następny adres dostępnych bajtów.|  
|**WORD**|Następny adres dostępne word (2 bajty każdego wyrazu).|  
|**DWORD**|Następny adres dostępne word o podwójnej precyzji (4 bajty każdego wyrazu o podwójnej precyzji).|  
|**PARA**|Następny adres dostępne akapitu (16 bajtów na akapitu).|  
|**PAGE**|Następny adres dostępne strony (256 bajtów na stronie).|  
|**DOPASUJ**(*n*)|Następny dostępny  *n* th bajtowy adres. Więcej informacji podano w sekcji uwag.|  
  
 Jeśli ten parametr nie jest określony, **PARA** jest używany domyślnie.  
  
 *Łączenie*  
 **PUBLICZNY**, **STOSU**, **TYPOWE**, **pamięci**, **na *** adres*, **prywatnych**  
  
 *Użyj*  
 **USE16**, **USE32**, **PŁASKI**  
  
 `characteristics`  
 **Informacje o**, **odczytu**, **zapisu**, **EXECUTE**, **SHARED**, **NOPAGE**, **NOCACHE**, i **ODRZUCIĆ**  
  
 Te są obsługiwane tylko w COFF i odpowiada właściwości sekcji COFF o podobnej nazwie (na przykład **SHARED** odpowiada IMAGE_SCN_MEM_SHARED). Odczyt ustawia flagę IMAGE_SCN_MEM_READ. Przestarzałe flagi tylko do odczytu spowodował sekcji wyczyścić flagę IMG_SCN_MEM_WRITE. Jeśli istnieją `characteristics` są ustawione domyślne parametry nie są używane i obowiązują tylko określony programisty flagi.  
  
 `ALIAS(` `string` `)`  
 Ten ciąg jest używany jako nazwa sekcji emitowany obiektu COFF.  Tworzy wiele sekcji o takiej samej nazwie zewnętrznych z różnymi nazwami segmentu MASM.  
  
 Nieobsługiwane z **/omf**.  
  
 `class`  
 Określa, jak łączyć i uporządkowanych w pliku złożony segmentów. Typowe wartości to, `'DATA'`, `'CODE'`, `'CONST'` i `'STACK'`  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać `ALIGN(n)`, `n` może być dowolnym potęgą liczby 2 z zakresu od 1 do 8192; nie jest obsługiwany z **/omf**.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)