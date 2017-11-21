---
title: "Błąd krytyczny C1054 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1054
dev_langs: C++
helpviewer_keywords: C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d02d8eb05633d7250dc3f7ee85dd78ccf4153052
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1054"></a>Błąd krytyczny C1054
ograniczenie kompilatora: inicjatory są zagnieżdżone zbyt głęboko  
  
 Kod przekracza limit zagnieżdżania inicjatory (w zależności od kombinację typów inicjowany poziomy 10 – 15).  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem przy użyciu następujących możliwych rozwiązań  
  
1.  Uproszczenie inicjowany, aby zmniejszyć zagnieżdżanie typów danych.  
  
2.  Inicjowanie zmiennych w osobnych instrukcji po deklaracji.