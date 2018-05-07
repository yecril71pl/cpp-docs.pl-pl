---
title: Błąd d8027 wiersza polecenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8027
dev_langs:
- C++
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc93edb939001a1e1bed5d3f7a4113e8483e81dd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="command-line-error-d8027"></a>Błąd D8027 wiersza polecenia
Nie można wykonać "component"  
  
 Kompilator nie można uruchomić składnika danej kompilatora lub konsolidatora.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Za mało pamięci, aby załadować składnika. Jeśli NMAKE wywołać kompilatora, uruchom kompilatora poza pliku reguł programu make.  
  
2.  W bieżącym systemie operacyjnym nie można uruchomić składnika. Upewnij się, że punkty ścieżki plików wykonywalnych właściwe dla systemu operacyjnego.  
  
3.  Składnik był uszkodzony. Ponownie skopiować składnika z dysków dystrybucji przy użyciu Instalatora.  
  
4.  Opcja została określona nieprawidłowo. Na przykład:  
  
    ```  
    cl /B1 file1.c  
    ```