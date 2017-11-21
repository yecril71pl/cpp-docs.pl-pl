---
title: "Błąd krytyczny C1067 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1067
dev_langs: C++
helpviewer_keywords: C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7ef424de5d375f2d198a5f358976d058d556c506
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1067"></a>Błąd krytyczny C1067
ograniczenie kompilatora: Przekroczono limit 64 KB rozmiaru typu rekordu  
  
 Ten błąd może wystąpić, jeśli symbol ma nazwę ozdobione przekraczającej 247 znaków.  Aby rozwiązać, Skróć nazwę symbolu.  
  
 Gdy kompilator generuje informacje o debugowaniu, emituje rekordów typu do definiowania typów Napotkano w kodzie źródłowym.  Rejestruje typ zawierają na przykład struktury proste i listy argumentów funkcji.  Niektóre z tych rekordów typu może być dużych list.  
  
 Istnieje limit 64 KB rozmiaru dowolnego typu rekordu.  Jeśli zostanie przekroczony limit 64K ten błąd zostanie przeprowadzona.  
  
 C1067 może również wystąpić, jeśli istnieje wiele symboli o długich nazwach lub jeśli klasy, struktury lub związku ma zbyt wiele elementów członkowskich.