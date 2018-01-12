---
title: "Błąd krytyczny C1002 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1002
dev_langs: C++
helpviewer_keywords: C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d299c6793e106ce516a81a9a81312ef0a09c25bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1002"></a>Błąd krytyczny C1002
Kompilator za mało miejsca na stercie w przebiegu 2  
  
 Kompilator za mało miejsca w pamięci dynamicznej jego drugim przebiegu, prawdopodobnie z powodu program o zbyt wiele symboli lub złożonych wyrażeń.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem przy użyciu następujących możliwych rozwiązań  
  
1.  Dzielenie pliku źródłowego na kilka mniejszych plików.  
  
2.  Podziel wyrażenia na mniejszym zakresie.  
  
3.  Usuń inne programy i sterowniki, które używa pamięci.