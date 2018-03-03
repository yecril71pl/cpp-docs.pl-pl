---
title: "Błąd narzędzi konsolidatora LNK1277 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1277
dev_langs:
- C++
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3606207afc197dc26ac0540d476b74f52c0dc0a9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1277"></a>Błąd narzędzi konsolidatora LNK1277
Nie znaleziono w pliku pgd (nazwa pliku) rekordu obiektu  
  
 Korzystając z [/LTCG:PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md), ścieżka jednego z plików .obj, .lib i def wejściowych była inna niż ścieżka, na którym została odnaleziona podczas /LTCG:PGINSTRUMENT. Po /LTCG:PGINSTRUMENT to może wyjaśnić przez zmianę w zmiennej środowiskowej LIB. Pełna ścieżka do plików wejściowych jest przechowywany w pliku .pgd.  
  
 /LTCG:PGOPTIMIZE wymaga taki sam jak faza /LTCG:PGINSTRUMENT dane wejściowe.  
  
 Aby usunąć to ostrzeżenie, wykonaj jedną z następujących czynności:  
  
-   Uruchom /LTCG:PGINSTRUMENT, wykonaj ponownie wszystkie uruchomień testów i uruchom /LTCG:PGOPTIMIZE.  
  
-   Zmień lib — zmienna środowiskowa, jakie były po uruchomieniu /LTCG:PGINSTRUMENT.  
  
 Aby obejść LNK1277 przy użyciu /LTCG:PGUPDATE nie jest zalecane.