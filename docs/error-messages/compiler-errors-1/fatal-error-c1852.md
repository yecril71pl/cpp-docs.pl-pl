---
title: Błąd krytyczny C1852 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1852
dev_langs:
- C++
helpviewer_keywords:
- C1852
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d11160eea5e978a0c1ef67255d4e96b48fe2d101
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199514"
---
# <a name="fatal-error-c1852"></a>Błąd krytyczny C1852
"Nazwa pliku" nie jest prawidłowym prekompilowanym plikiem nagłówkowym  
  
 Plik nie jest prekompilowanego nagłówka.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Nieprawidłowy plik określony za pomocą **/Yu** lub **#pragma hdrstop**.  
  
2.  Kompilator zakłada rozszerzenia pliku .pch, jeśli nie określono inaczej.