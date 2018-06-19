---
title: Kompilatora (poziom 4) ostrzeżenie C4513 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4513
dev_langs:
- C++
helpviewer_keywords:
- C4513
ms.assetid: 6877334a-f30a-4184-9483-dac3348737a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92c3e89204ec30f9c96a5ea03ede5093dd013d0c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292899"
---
# <a name="compiler-warning-level-4-c4513"></a>Kompilator C4513 ostrzegawcze (poziom 4)
"class": nie można wygenerować — destruktor  
  
 Kompilator nie może wygenerować destruktora domyślny dla danej klasy; destruktor nie został utworzony. Destruktor jest w klasie podstawowej, która nie jest dostępna dla klasy pochodnej. Klasa podstawowa ma destruktor prywatne, aby go publiczne lub chronione.