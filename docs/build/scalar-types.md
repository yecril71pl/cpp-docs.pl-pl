---
title: Typy skalarne | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 07c9195e-b6c7-4083-8ef0-8a93032e4d1e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 279c4eefb072c6caab85a61bba3abc73be22d3a7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="scalar-types"></a>Typy skalarne
Mimo że dostępu do danych mogą wynikać z wyrównanie, zaleca się, że dane być dostosowane do jego granic fizycznych, aby uniknąć utraty wydajności (lub jej wielokrotność). Typy wyliczeniowe są stałe całkowite i są traktowane jako 32-bitowych liczb całkowitych. W poniższej tabeli opisano definicji typu i zalecane magazynu dla niego w odniesieniu do dostosowania przy użyciu następujących wartości wyrównania:  
  
-   Byte — 8 bitów  
  
-   Word — 16 bitów  
  
-   Double Word - 32-bitowy  
  
-   Word Quad - 64-bitowy  
  
-   Word ośmiu - 128 bitów  
  
|||||  
|-|-|-|-|  
|Typ skalarne|C — typ danych|Rozmiar magazynu (w bajtach)|Zalecane wyrównania|  
|**INT8**|`char`|1|Byte|  
|**UINT8**|`unsigned char`|1|Byte|  
|**INT16**|**krótki**|2|Word|  
|**UINT16**|**short bez znaku**|2|Word|  
|**INT32**|**int, długi**|4|Bitowego|  
|**UINT32**|**unsigned int, long bez znaku**|4|Bitowego|  
|**INT64**|`__int64`|8|Quadword|  
|**UINT64 —**|**__int64 bez znaku**|8|Quadword|  
|**FP32 (pojedynczy dokładności)**|**float**|4|Bitowego|  
|**FP64 (Podwójna precyzja)**|**podwójne**|8|Quadword|  
|**WSKAŹNIK**|**\***|8|Quadword|  
|`__m64`|**__m64 — struktura**|8|Quadword|  
|`__m128`|**__m128 — struktura**|16|Octaword|  
  
## <a name="see-also"></a>Zobacz też  
 [Typy i Magazyn](../build/types-and-storage.md)