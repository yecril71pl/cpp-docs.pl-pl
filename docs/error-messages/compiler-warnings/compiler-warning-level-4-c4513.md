---
title: "Kompilatora (poziom 4) ostrzeżenie C4513 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4513
dev_langs:
- C++
helpviewer_keywords:
- C4513
ms.assetid: 6877334a-f30a-4184-9483-dac3348737a4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c07828569b789c6035b5ea28d47d7fd026341026
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4513"></a>Kompilator C4513 ostrzegawcze (poziom 4)
"class": nie można wygenerować — destruktor  
  
 Kompilator nie może wygenerować destruktora domyślny dla danej klasy; destruktor nie został utworzony. Destruktor jest w klasie podstawowej, która nie jest dostępna dla klasy pochodnej. Klasa podstawowa ma destruktor prywatne, aby go publiczne lub chronione.