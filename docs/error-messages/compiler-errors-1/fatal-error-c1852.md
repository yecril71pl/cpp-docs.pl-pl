---
title: "Błąd krytyczny C1852 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1852
dev_langs: C++
helpviewer_keywords: C1852
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cd7168c6ffa653af54404bf81cdc4d308a76783a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1852"></a>Błąd krytyczny C1852
"Nazwa pliku" nie jest prawidłowym prekompilowanym plikiem nagłówkowym  
  
 Plik nie jest prekompilowanego nagłówka.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Nieprawidłowy plik określony za pomocą **/Yu** lub **#pragma hdrstop**.  
  
2.  Kompilator zakłada rozszerzenia pliku .pch, jeśli nie określono inaczej.