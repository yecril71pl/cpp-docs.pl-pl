---
title: Kompilatora (poziom 1) ostrzeżenie C4627 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4627
dev_langs:
- C++
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dcde9e6707465fd95dbcb10e073a852624f0de0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4627"></a>Kompilator C4627 ostrzegawcze (poziom 1)
"\<identyfikator >": pominięto podczas wyszukiwania użycia prekompilowanego nagłówka  
  
 Podczas wyszukiwania lokalizacji, w których jest używany prekompilowanego nagłówka, kompilator napotkano `#include` dyrektywy dla  *\<identyfikator >* dołączyć plik. Kompilator ignoruje `#include` dyrektywy, ale generuje ostrzeżenie **C4627** Jeśli prekompilowanego nagłówka nie zawiera już  *\<identyfikator >* dołączyć plik.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie prekompilowanych plików nagłówka](../../build/reference/creating-precompiled-header-files.md)