---
title: Błąd krytyczny C1126 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1126
dev_langs:
- C++
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a3ff02d69679074186e593d5e1c16bdf56d1052
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225917"
---
# <a name="fatal-error-c1126"></a>Błąd krytyczny C1126
'Identyfikator': automatyczne przydzielanie przekracza rozmiar  
  
 Ilość miejsca przydzielonego dla zmiennych lokalnych funkcji (i ograniczoną ilość miejsca używanego przez kompilator, takich jak dodatkowe 20 bajtów dla funkcji swap) przekracza limit.  
  
 Aby rozwiązać ten problem, należy użyć `malloc` lub `new` przydzielić dużych ilości danych.