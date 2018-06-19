---
title: Ostrzeżenie NMAKE U4004 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4004
dev_langs:
- C++
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 532abf2f62616d6e748c9a4e34f5c983f0853276
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317183"
---
# <a name="nmake-warning-u4004"></a>Ostrzeżenie NMAKE U4004
za dużo reguł dla docelowej "targetname"  
  
 Określono więcej niż jeden opis blok dla danego obiektu docelowego przy użyciu pojedynczego dwukropki (**:**) jako separatorów. NMAKE wykonać polecenia w pierwszym bloku opis i ignorowane nowsze bloków.  
  
 Aby określić tej samej wartości docelowej w wielu zależności, użyj podwójne dwukropki (`::`) jako separator w każdym wierszu zależności.