---
title: Kompilatora (poziom 1) ostrzeżenie C4952 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4952
dev_langs:
- C++
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 42696dfae816742c958bca23e25e311e834dd62a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4952"></a>Kompilator C4952 ostrzegawcze (poziom 1)
"Funkcja": nie znaleziono danych profilowych w bazie danych programu "pgd_file"  
  
 Korzystając z [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), kompilator wykryto moduł wejściowy kompilowanej po `/LTCG:PGINSTRUMENT` i zawiera nową funkcję (***funkcja***) obecny.  
  
 To ostrzeżenie ma charakter informacyjny. Aby usunąć to ostrzeżenie, uruchom `/LTCG:PGINSTRUMENT`, powtórz test wszystkie działa, a następnie uruchom `/LTCG:PGOPTIMIZE`.  
  
 To ostrzeżenie będzie zastąpiony z powodu błędu, jeśli `/LTCG:PGOPTIMIZE` została użyta.