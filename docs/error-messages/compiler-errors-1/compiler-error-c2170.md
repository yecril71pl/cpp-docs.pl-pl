---
title: "C2170 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2170
dev_langs: C++
helpviewer_keywords: C2170
ms.assetid: d5c663f0-2459-4e11-a8bf-a52b62f3c71d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8520e9ea71d90e7f97c6296d4326abb1fd4c7609
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2170"></a>C2170 błąd kompilatora
'Identyfikator': nie zadeklarowano jako funkcja, nie może być wewnętrzne  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Pragma `intrinsic` jest używana dla elementu innego niż funkcji.  
  
2.  Pragma `intrinsic` służy do funkcji z żaden formularz wewnętrznej.