---
title: "Kompilatora (poziom 1) ostrzeżenie C4041 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4041
dev_langs: C++
helpviewer_keywords: C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2ae98391c3c5bfb603afae684027a86c39c840b4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4041"></a>Kompilator C4041 ostrzegawcze (poziom 1)
ograniczenie kompilatora: Kończenie wyświetlania wyników przeglądarki  
  
 Informacje o przeglądarce przekroczyła limit kompilatora.  
  
 To ostrzeżenie może być spowodowany kompilowania przy użyciu [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (w tym zmiennych lokalnych informacji przeglądarki).  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem przy użyciu następujących możliwych rozwiązań  
  
1.  Kompiluj z użyciem /Fr (informacje o przeglądarce bez zmiennych lokalnych).  
  
2.  Wyłącz wyników przeglądarki (Kompiluj bez /FR lub /Fr).