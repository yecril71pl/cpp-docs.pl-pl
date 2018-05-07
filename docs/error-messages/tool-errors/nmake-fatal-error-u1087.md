---
title: Błąd krytyczny NMAKE U1087 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1087
dev_langs:
- C++
helpviewer_keywords:
- U1087
ms.assetid: 5236ab54-e117-484d-99c3-852b061fd3d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f07309c64066b0a17aab110035c700c229c439df
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1087"></a>Błąd krytyczny NMAKE U1087
nie może mieć: i:: elementów zależnych dla tego samego obiektu docelowego  
  
 Nie można określić obiektu docelowego w obu jednym dwukropkiem (**:**) i podwójnego dwukropka (`::`) zależności.  
  
 Aby określić cel w blokach opisów, użyj `::` w każdym wierszu zależności.