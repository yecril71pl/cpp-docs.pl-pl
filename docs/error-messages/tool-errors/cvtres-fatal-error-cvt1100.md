---
title: "Błąd krytyczny CVTRES CVT1100 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- CVT1100
dev_langs:
- C++
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 906e03b778276196d36a04e6b9e2f02a2d5944bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cvtres-fatal-error-cvt1100"></a>Błąd krytyczny CVTRES CVT1100
Zduplikowany zasób — typu: typ, nazwa: nazwa, języka: język, flag: flagi, rozmiar:  
  
 Danego zasobu został określony więcej niż raz.  
  
 Ten błąd można uzyskać, jeśli konsolidator tworzy bibliotekę typów i nie określono [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) i 1 już korzysta z zasobów w projekcie. W takim przypadku Określ /TLBID i określ inny numer do 65535.