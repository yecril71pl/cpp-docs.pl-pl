---
title: "Ostrzeżenie NMAKE U4004 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U4004
dev_langs: C++
helpviewer_keywords: U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b629bd2910b2820cc703824a5a97bf3361ac54b6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-warning-u4004"></a>Ostrzeżenie NMAKE U4004
za dużo reguł dla docelowej "targetname"  
  
 Określono więcej niż jeden opis blok dla danego obiektu docelowego przy użyciu pojedynczego dwukropki (**:**) jako separatorów. NMAKE wykonać polecenia w pierwszym bloku opis i ignorowane nowsze bloków.  
  
 Aby określić tej samej wartości docelowej w wielu zależności, użyj podwójne dwukropki (`::`) jako separator w każdym wierszu zależności.