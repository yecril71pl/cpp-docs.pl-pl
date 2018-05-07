---
title: Kompilatora (poziom 1) ostrzeżenie C4910 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 34ed2ec16f579b05a572cf6bfc236cd8d5743f63
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4910"></a>Kompilator C4910 ostrzegawcze (poziom 1)
"\<identyfikator >": deklaracje "__declspec(dllexport)" i "extern" są niezgodne z jawnym wystąpieniem  
  
 Utworzenie wystąpienia jawnego szablonu o nazwie  *\<identyfikator >* jest modyfikowany przez oba `__declspec(dllexport)` i `extern` słów kluczowych. Jednak te słowa kluczowe wzajemnie się wykluczają. `__declspec(dllexport)` — Słowo kluczowe oznacza utworzyć wystąpienia klasy szablonu podczas `extern` oznacza — słowo kluczowe nie automatycznie utworzyć wystąpienia klasy szablonu.  
  
## <a name="see-also"></a>Zobacz też  
 [Jawne tworzenie wystąpienia](../../cpp/explicit-instantiation.md)   
 [dllexport i dllimport](../../cpp/dllexport-dllimport.md)   
 [Ograniczenia i reguły ogólne](../../cpp/general-rules-and-limitations.md)