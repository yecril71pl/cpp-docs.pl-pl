---
title: "D9026 dla wiersza ostrzeżenie polecenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: D9026
dev_langs: C++
helpviewer_keywords: D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: eead2bc96a24fd86b123ab4853bfc8ea01166804
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="command-line-warning-d9026"></a>Ostrzeżenie D9026 dla wiersza polecenia
opcje odnoszą się do całego wiersza polecenia  
  
 Określono opcję polecenia po określono nazwę pliku. Opcja została zastosowana do pliku, który poprzedzające go.  
  
 Na przykład w poleceniu  
  
```  
CL verdi.c /G5 puccini.c  
```  
  
 będzie można skompilować pliku VERDI.c za pomocą opcji /G5 nie domyślne /G4.  
  
 To zachowanie różni się od niektórych poprzednich wersji, które są stosowane tylko do podanych opcji przed nazwę pliku, co powoduje VERDI.c jest kompilowane przy użyciu/G4 i PUCCINI.c jest kompilowane przy użyciu /G5.