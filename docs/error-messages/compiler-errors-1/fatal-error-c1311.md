---
title: Błąd krytyczny C1311 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1311
dev_langs:
- C++
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53b3759a5fec4b072f9a9b300670d61cb0d101c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226681"
---
# <a name="fatal-error-c1311"></a>Błąd krytyczny C1311
COFF format statycznie nie może zainicjować "var" z numerów bajtem(ów) adresu  
  
 Adres, którego wartość nie jest znany w czasie kompilacji nie statycznie przypisane do zmiennej, którego typ ma magazynu mniej niż cztery bajtów.  
  
 Ten błąd może wystąpić na kod, który jest prawidłowy C++.  
  
 W poniższym przykładzie przedstawiono jeden warunek, który może spowodować C1311.  
  
```  
char c = (char)"Hello, world";   // C1311  
char *d = (char*)"Hello, world";   // OK  
```