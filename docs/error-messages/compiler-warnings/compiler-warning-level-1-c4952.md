---
title: "Kompilatora (poziom 1) ostrzeżenie C4952 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4952
dev_langs: C++
helpviewer_keywords: C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ffe150b84c297ef747836863d0da4306f0623665
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4952"></a>Kompilator C4952 ostrzegawcze (poziom 1)
"Funkcja": nie znaleziono danych profilowych w bazie danych programu "pgd_file"  
  
 Korzystając z [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), kompilator wykryto moduł wejściowy kompilowanej po `/LTCG:PGINSTRUMENT` i zawiera nową funkcję (***funkcja***) obecny.  
  
 To ostrzeżenie ma charakter informacyjny. Aby usunąć to ostrzeżenie, uruchom `/LTCG:PGINSTRUMENT`, powtórz test wszystkie działa, a następnie uruchom `/LTCG:PGOPTIMIZE`.  
  
 To ostrzeżenie będzie zastąpiony z powodu błędu, jeśli `/LTCG:PGOPTIMIZE` została użyta.