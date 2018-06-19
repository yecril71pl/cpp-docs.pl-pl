---
title: Błąd krytyczny C1002 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1002
dev_langs:
- C++
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c63a8d399b3e8c781694d89825e7898fd1db4639
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225054"
---
# <a name="fatal-error-c1002"></a>Błąd krytyczny C1002
Kompilator za mało miejsca na stercie w przebiegu 2  
  
 Kompilator za mało miejsca w pamięci dynamicznej jego drugim przebiegu, prawdopodobnie z powodu program o zbyt wiele symboli lub złożonych wyrażeń.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem przy użyciu następujących możliwych rozwiązań  
  
1.  Dzielenie pliku źródłowego na kilka mniejszych plików.  
  
2.  Podziel wyrażenia na mniejszym zakresie.  
  
3.  Usuń inne programy i sterowniki, które używa pamięci.