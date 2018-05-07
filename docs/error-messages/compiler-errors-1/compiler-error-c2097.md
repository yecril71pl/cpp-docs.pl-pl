---
title: C2097 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2097
dev_langs:
- C++
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa4b867c7f043d796f208fdc7100509893147daf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2097"></a>C2097 błąd kompilatora
niedozwolone inicjowanie  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Inicjowanie przy użyciu nieunikatowego wartości zmiennej.  
  
2.  Inicjowanie Krótki adres z długi adres.  
  
3.  Inicjowanie lokalnych struktury, Unią lub tablicy za pomocą wyrażenia nieunikatowego podczas kompilowania za pomocą **/Za**.  
  
4.  Inicjacja za pomocą wyrażenia zawierającego operator przecinka.  
  
5.  Inicjowanie z wyrażeniem, które nie jest stałą ani symbolicznych.