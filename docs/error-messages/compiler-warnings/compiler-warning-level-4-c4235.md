---
title: "Kompilatora (poziom 4) ostrzeżenie C4235 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4235
dev_langs:
- C++
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b0fea028932a48b9c7ee1a677a3e6dc8078edc35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4235"></a>Kompilator C4235 ostrzegawcze (poziom 4)
użyto niestandardowego rozszerzenia: słowo kluczowe "— słowo kluczowe" nie jest obsługiwane w tej architekturze  
  
 Kompilator nie obsługuje słowa kluczowego użytym.  
  
 To ostrzeżenie zostanie automatycznie podwyższony do wystąpił błąd. Jeśli chcesz zmienić to zachowanie, użyj [ostrzeżenie #pragma](../../preprocessor/warning.md). Na przykład aby C4235 do ostrzeżenia poziomu 2, należy użyć następującego kodu  
  
```  
#pragma warning(2:4235)  
```  
  
 w pliku kodu źródłowego.