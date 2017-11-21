---
title: "Kompilatora (poziom 1) ostrzeżenie C4627 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4627
dev_langs: C++
helpviewer_keywords: C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7290a7b85be1c27fd33b11507bb2b2994ed5aaad
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4627"></a>Kompilator C4627 ostrzegawcze (poziom 1)
"\<identyfikator >": pominięto podczas wyszukiwania użycia prekompilowanego nagłówka  
  
 Podczas wyszukiwania lokalizacji, w których jest używany prekompilowanego nagłówka, kompilator napotkano `#include` dyrektywy dla  *\<identyfikator >* dołączyć plik. Kompilator ignoruje `#include` dyrektywy, ale generuje ostrzeżenie **C4627** Jeśli prekompilowanego nagłówka nie zawiera już  *\<identyfikator >* dołączyć plik.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie prekompilowanych plików nagłówka](../../build/reference/creating-precompiled-header-files.md)