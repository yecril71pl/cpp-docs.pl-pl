---
title: "Błąd matematyczny M6202 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: M6202
dev_langs: C++
helpviewer_keywords: M6202
ms.assetid: 4d17045f-c6dc-4705-9512-e9af12c35fb4
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c23edcdcb48dcec16799224a6babfa09a04a1a95
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="math-error-m6202"></a>Błąd matematyczny M6202
"Funkcja": — błąd  
  
 Argument funkcji danego była wartością singularity dla tej funkcji. Funkcja nie jest zdefiniowany dla tego argumentu.  
  
 Ten błąd wywołania `_matherr` funkcji z nazwą funkcji, argumentów i typ błędu. Można ponownie napisać `_matherr` funkcji, aby dostosować obsługę niektórych błędów czasu wykonywania zmiennoprzecinkowej matematyczny.