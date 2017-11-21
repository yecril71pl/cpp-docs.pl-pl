---
title: "Kompilatora (poziom 1) ostrzeżenie C4910 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f0402e03d77968de3b4c1addf58c481ec85a61b8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4910"></a>Kompilator C4910 ostrzegawcze (poziom 1)
"\<identyfikator >": deklaracje "__declspec(dllexport)" i "extern" są niezgodne z jawnym wystąpieniem  
  
 Utworzenie wystąpienia jawnego szablonu o nazwie  *\<identyfikator >* jest modyfikowany przez oba `__declspec(dllexport)` i `extern` słów kluczowych. Jednak te słowa kluczowe wzajemnie się wykluczają. `__declspec(dllexport)` — Słowo kluczowe oznacza utworzyć wystąpienia klasy szablonu podczas `extern` oznacza — słowo kluczowe nie automatycznie utworzyć wystąpienia klasy szablonu.  
  
## <a name="see-also"></a>Zobacz też  
 [Jawne tworzenie wystąpienia](../../cpp/explicit-instantiation.md)   
 [dllexport i dllimport](../../cpp/dllexport-dllimport.md)   
 [Ograniczenia i reguły ogólne](../../cpp/general-rules-and-limitations.md)