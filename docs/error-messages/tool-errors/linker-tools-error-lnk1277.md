---
title: Błąd narzędzi konsolidatora LNK1277 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1277
dev_langs:
- C++
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec8f00793fcda748c60d9d8ea775611e3d025cd9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298733"
---
# <a name="linker-tools-error-lnk1277"></a>Błąd narzędzi konsolidatora LNK1277
Nie znaleziono w pliku pgd (nazwa pliku) rekordu obiektu  
  
 Korzystając z [/LTCG:PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md), ścieżka jednego z plików .obj, .lib i def wejściowych była inna niż ścieżka, na którym została odnaleziona podczas /LTCG:PGINSTRUMENT. Po /LTCG:PGINSTRUMENT to może wyjaśnić przez zmianę w zmiennej środowiskowej LIB. Pełna ścieżka do plików wejściowych jest przechowywany w pliku .pgd.  
  
 /LTCG:PGOPTIMIZE wymaga taki sam jak faza /LTCG:PGINSTRUMENT dane wejściowe.  
  
 Aby usunąć to ostrzeżenie, wykonaj jedną z następujących czynności:  
  
-   Uruchom /LTCG:PGINSTRUMENT, wykonaj ponownie wszystkie uruchomień testów i uruchom /LTCG:PGOPTIMIZE.  
  
-   Zmień lib — zmienna środowiskowa, jakie były po uruchomieniu /LTCG:PGINSTRUMENT.  
  
 Aby obejść LNK1277 przy użyciu /LTCG:PGUPDATE nie jest zalecane.