---
title: "Błąd krytyczny CVTRES CVT1100 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CVT1100
dev_langs: C++
helpviewer_keywords: CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ba8ea3fdfdea9ca5aa142a1f2a8f15c5d3ac536a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cvtres-fatal-error-cvt1100"></a>Błąd krytyczny CVTRES CVT1100
Zduplikowany zasób — typu: typ, nazwa: nazwa, języka: język, flag: flagi, rozmiar:  
  
 Danego zasobu został określony więcej niż raz.  
  
 Ten błąd można uzyskać, jeśli konsolidator tworzy bibliotekę typów i nie określono [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) i 1 już korzysta z zasobów w projekcie. W takim przypadku Określ /TLBID i określ inny numer do 65535.