---
title: "C2097 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2097
dev_langs: C++
helpviewer_keywords: C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d6955a610e3109c3b16edf96913be4503ee4c647
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2097"></a>C2097 błąd kompilatora
niedozwolone inicjowanie  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Inicjowanie przy użyciu nieunikatowego wartości zmiennej.  
  
2.  Inicjowanie Krótki adres z długi adres.  
  
3.  Inicjowanie lokalnych struktury, Unią lub tablicy za pomocą wyrażenia nieunikatowego podczas kompilowania za pomocą **/Za**.  
  
4.  Inicjacja za pomocą wyrażenia zawierającego operator przecinka.  
  
5.  Inicjowanie z wyrażeniem, które nie jest stałą ani symbolicznych.