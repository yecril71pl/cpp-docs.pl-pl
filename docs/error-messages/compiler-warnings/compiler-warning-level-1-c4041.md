---
title: Kompilatora (poziom 1) ostrzeżenie C4041 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4041
dev_langs:
- C++
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfd8c933522e523329c41ebe666a5a7e3c198cb0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4041"></a>Kompilator C4041 ostrzegawcze (poziom 1)
ograniczenie kompilatora: Kończenie wyświetlania wyników przeglądarki  
  
 Informacje o przeglądarce przekroczyła limit kompilatora.  
  
 To ostrzeżenie może być spowodowany kompilowania przy użyciu [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (w tym zmiennych lokalnych informacji przeglądarki).  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem przy użyciu następujących możliwych rozwiązań  
  
1.  Kompiluj z użyciem /Fr (informacje o przeglądarce bez zmiennych lokalnych).  
  
2.  Wyłącz wyników przeglądarki (Kompiluj bez /FR lub /Fr).