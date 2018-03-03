---
title: "Kompilatora (poziom 1) ostrzeżenie C4124 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4124
dev_langs:
- C++
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 38588fb242b5b4167984e15d101594d1b015ec86
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4124"></a>Kompilator C4124 ostrzegawcze (poziom 1)
__fastcall ze sprawdzeniem stosu jest nieefektywne  
  
 `__fastcall` Użyto słowa kluczowego ze sprawdzeniem stosu włączone.  
  
 `__fastcall` Konwencji generuje kod szybszy, ale sprawdzanie stosu powoduje, że kod wolniej. Korzystając z `__fastcall`, Wyłącz sprawdzanie stosu z **check_stack —** pragma lub/GS.  
  
 To ostrzeżenie zostanie wyświetlone tylko w przypadku pierwszej funkcji zadeklarowany w tych warunkach.