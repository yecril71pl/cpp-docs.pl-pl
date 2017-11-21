---
title: "Błąd krytyczny C1091 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1091
dev_langs: C++
helpviewer_keywords: C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6c3fd2dae1f3258ce90d30c78792c498be75615a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1091"></a>Błąd krytyczny C1091
ograniczenie kompilatora: ciąg przekracza "length" bajtów długości  
  
 Stałą typu string przekracza bieżący limit długości ciągów.  
  
 Można podzielić ciąg statycznych zmiennych dwie (lub więcej) i używać [strcpy_s —](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) sprzęgać wynik w ramach deklaracji lub w czasie wykonywania.