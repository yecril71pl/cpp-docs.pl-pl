---
title: "Błąd krytyczny NMAKE U1087 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1087
dev_langs: C++
helpviewer_keywords: U1087
ms.assetid: 5236ab54-e117-484d-99c3-852b061fd3d0
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f70d63a0161885c6286714b2c860c778d9598c34
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1087"></a>Błąd krytyczny NMAKE U1087
nie może mieć: i:: elementów zależnych dla tego samego obiektu docelowego  
  
 Nie można określić obiektu docelowego w obu jednym dwukropkiem (**:**) i podwójnego dwukropka (`::`) zależności.  
  
 Aby określić cel w blokach opisów, użyj `::` w każdym wierszu zależności.