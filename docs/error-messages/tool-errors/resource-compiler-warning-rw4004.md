---
title: "Ostrzeżenie RW4004 kompilatora zasobów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RW4004
dev_langs:
- C++
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0249f7d01ee344f0fa17bdc39e58e9fce26c9b25
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-warning-rw4004"></a>Ostrzeżenie RW4004 kompilatora zasobów
Nie są równoważne wirtualnego kod klucza znaków ASCII  
  
 Literał ciągu została użyta dla wirtualnego kodu klucza skrótów typu VIRTKEY.  
  
 To ostrzeżenie pozwala kontynuować, ale należy pamiętać, klawisze skrótów wygenerowany może nie odpowiadać wskazana ciąg. (VIRTKEYs użyć różnych kodów klucza niż ASCII akceleratorów).  
  
 Literały ciągu są nieprawidłową składnię, użytkownik może tylko mieć pewność, że akceleratora przy użyciu **VK_\* #define** wartości WINDOWS.h.