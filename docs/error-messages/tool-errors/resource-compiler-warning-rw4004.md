---
title: Ostrzeżenie RW4004 kompilatora zasobów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW4004
dev_langs:
- C++
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 94bd1c043ac5660c5cb8fc8b2bfa1dd2f6968b55
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-warning-rw4004"></a>Ostrzeżenie RW4004 kompilatora zasobów
Nie są równoważne wirtualnego kod klucza znaków ASCII  
  
 Literał ciągu została użyta dla wirtualnego kodu klucza skrótów typu VIRTKEY.  
  
 To ostrzeżenie pozwala kontynuować, ale należy pamiętać, klawisze skrótów wygenerowany może nie odpowiadać wskazana ciąg. (VIRTKEYs użyć różnych kodów klucza niż ASCII akceleratorów).  
  
 Literały ciągu są nieprawidłową składnię, użytkownik może tylko mieć pewność, że akceleratora przy użyciu **VK_\* #define** wartości WINDOWS.h.