---
title: Kompilatora (poziom 4) ostrzeżenie C4234 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4234
dev_langs:
- C++
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8d5b7a2999b77c0b34ee925f5dd85a0a27c63f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4234"></a>Kompilator C4234 ostrzegawcze (poziom 4)
użyto niestandardowego rozszerzenia: słowo kluczowe "— słowo kluczowe" zarezerwowane do użytku w przyszłości  
  
 Kompilator nie implementuje jeszcze słowo kluczowe, które są używane.  
  
 To ostrzeżenie zostanie automatycznie podwyższony do wystąpił błąd. Jeśli chcesz zmienić to zachowanie, użyj [ostrzeżenie #pragma](../../preprocessor/warning.md). Na przykład, aby przekształcić C4234 ostrzeżenie poziom 4 problem  
  
```  
#pragma warning(2:4234)  
```  
  
 w pliku kodu źródłowego.