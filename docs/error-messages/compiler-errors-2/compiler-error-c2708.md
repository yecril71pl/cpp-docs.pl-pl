---
title: C2708 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2708
dev_langs:
- C++
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d30b2e5c1856a604ae314316cd71d6acc00a7c74
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234763"
---
# <a name="compiler-error-c2708"></a>C2708 błąd kompilatora
'Identyfikator': rzeczywiste parametry długości w bajtach różni się od poprzedniego wywołania lub odwołania  
  
 A [__stdcall](../../cpp/stdcall.md) funkcja musi być poprzedzona prototypu. W przeciwnym razie kompilator interpretuje pierwszym wywołaniu funkcji jako prototyp i ten błąd występuje, gdy kompilator napotka wywołania, który nie jest zgodny.  
  
 Aby naprawić ten błąd, Dodaj prototyp funkcji.