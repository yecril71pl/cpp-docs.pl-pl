---
title: Kompilatora (poziom 1) ostrzeżenie C4951 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4951
dev_langs:
- C++
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3ebf012338bdf6b90cc943e754056335c6751a4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4951"></a>Kompilator C4951 ostrzegawcze (poziom 1)
"Funkcja" został wyedytowany od profil, który został zebrany danych, dane profilu funkcji nie zostały użyte  
  
 Funkcja został zmodyfikowany w wejściowych modułu do [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), dzięki czemu dane profilu są obecnie nieprawidłowe. Moduł wejściowy został ponownie kompilowana po **/LTCG:PGINSTRUMENT** i ma funkcję (***funkcja***) dla różnych przepływu sterowania niż modułu w momencie **/LTCG:PGINSTRUMENT**  operacji.  
  
 To ostrzeżenie ma charakter informacyjny. Aby usunąć to ostrzeżenie, uruchom **/LTCG:PGINSTRUMENT**, powtórz test wszystkie działa, a następnie uruchom **/LTCG:PGOPTIMIZE**.  
  
 To ostrzeżenie będzie zastąpiony z powodu błędu, jeśli **/LTCG:PGOPTIMIZE** została użyta.