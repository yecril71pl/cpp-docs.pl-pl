---
title: "Kompilatora (poziom 1) ostrzeżenie C4951 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4951
dev_langs: C++
helpviewer_keywords: C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: efb4b4a283964230d191962db40c4d061a039dfd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4951"></a>Kompilator C4951 ostrzegawcze (poziom 1)
"Funkcja" został wyedytowany od profil, który został zebrany danych, dane profilu funkcji nie zostały użyte  
  
 Funkcja został zmodyfikowany w wejściowych modułu do [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), dzięki czemu dane profilu są obecnie nieprawidłowe. Moduł wejściowy został ponownie kompilowana po **/LTCG:PGINSTRUMENT** i ma funkcję (***funkcja***) dla różnych przepływu sterowania niż modułu w momencie **/LTCG:PGINSTRUMENT**  operacji.  
  
 To ostrzeżenie ma charakter informacyjny. Aby usunąć to ostrzeżenie, uruchom **/LTCG:PGINSTRUMENT**, powtórz test wszystkie działa, a następnie uruchom **/LTCG:PGOPTIMIZE**.  
  
 To ostrzeżenie będzie zastąpiony z powodu błędu, jeśli **/LTCG:PGOPTIMIZE** została użyta.