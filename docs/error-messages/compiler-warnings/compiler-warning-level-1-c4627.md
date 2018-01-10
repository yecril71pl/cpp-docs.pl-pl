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
ms.workload: cplusplus
ms.openlocfilehash: 66d199b8dede21f94a963113341eb6426f66a807
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4627"></a>Kompilator C4627 ostrzegawcze (poziom 1)
"\<identyfikator >": pominięto podczas wyszukiwania użycia prekompilowanego nagłówka  
  
 Podczas wyszukiwania lokalizacji, w których jest używany prekompilowanego nagłówka, kompilator napotkano `#include` dyrektywy dla  *\<identyfikator >* dołączyć plik. Kompilator ignoruje `#include` dyrektywy, ale generuje ostrzeżenie **C4627** Jeśli prekompilowanego nagłówka nie zawiera już  *\<identyfikator >* dołączyć plik.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie prekompilowanych plików nagłówka](../../build/reference/creating-precompiled-header-files.md)