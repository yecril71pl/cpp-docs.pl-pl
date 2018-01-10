---
title: "C2708 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2708
dev_langs: C++
helpviewer_keywords: C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 495fd9aeaad785edd8653e46ae666f60c337b12d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2708"></a>C2708 błąd kompilatora
'Identyfikator': rzeczywiste parametry długości w bajtach różni się od poprzedniego wywołania lub odwołania  
  
 A [__stdcall](../../cpp/stdcall.md) funkcja musi być poprzedzona prototypu. W przeciwnym razie kompilator interpretuje pierwszym wywołaniu funkcji jako prototyp i ten błąd występuje, gdy kompilator napotka wywołania, który nie jest zgodny.  
  
 Aby naprawić ten błąd, Dodaj prototyp funkcji.