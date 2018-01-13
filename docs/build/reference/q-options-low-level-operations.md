---
title: -Q opcje (operacje na niskim poziomie) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /q
dev_langs: C++
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.assetid: 9fa738b9-630a-4bde-bc87-bdfa30552be4
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d970c2de5e34840ab2ed77f229c329db3c6f72fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="q-options-low-level-operations"></a>/Q Opcje (Operacje na niskim poziomie)
Można użyć **/Q** opcji kompilatora, aby wykonywać następujące operacje kompilatora niskiego poziomu:  
  
-   [/ Qfast_transcendentals (Wymuszaj Fast Transcendentals)](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md): generuje fast transcendentals.  
  
-   [/ QIfist (pomijanie _ftol)](../../build/reference/qifist-suppress-ftol.md): pomija `_ftol` podczas konwersji z typu zmiennoprzecinkowego do typu Liczba całkowita jest wymagana (tylko x86).  
  
-   [/ Qimprecise_fwaits (usuwanie fwaits wewnątrz bloków Try)](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): usuwa `fwait` poleceniach wewnątrz `try` bloków.  
  
-   [/ Qpar (automatyczny Paralelizator)](../../build/reference/qpar-auto-parallelizer.md): włącza automatyczna paralelizacja pętli, które są oznaczone ikoną z [#pragma loop()](../../preprocessor/loop.md) dyrektywy.  
  
-   [/ Qpar raport (poziom raportowania automatycznej Paralelizacji)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md): Włącza raportowanie poziomy automatyczna paralelizacja.  
  
-   [/ Qsafe_fp_loads](../../build/reference/qsafe-fp-loads.md): powoduje pominięcie optymalizacji liczb zmiennoprzecinkowych rejestru ładuje i dla ruchu między pamięcią i MMX rejestruje.  
  
-   [/ Qvec raport (poziom raportowania automatycznej Wektoryzacji)](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md): Włącza raportowanie poziomy vectorization automatycznego.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)