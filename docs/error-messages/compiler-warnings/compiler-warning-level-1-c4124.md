---
title: Kompilatora (poziom 1) ostrzeżenie C4124 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4124
dev_langs:
- C++
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: accd58c123bcd74e54176eed5eb974c3df33dbab
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279321"
---
# <a name="compiler-warning-level-1-c4124"></a>Kompilator C4124 ostrzegawcze (poziom 1)
__fastcall ze sprawdzeniem stosu jest nieefektywne  
  
 `__fastcall` Użyto słowa kluczowego ze sprawdzeniem stosu włączone.  
  
 `__fastcall` Konwencji generuje kod szybszy, ale sprawdzanie stosu powoduje, że kod wolniej. Korzystając z `__fastcall`, Wyłącz sprawdzanie stosu z **check_stack —** pragma lub/GS.  
  
 To ostrzeżenie zostanie wyświetlone tylko w przypadku pierwszej funkcji zadeklarowany w tych warunkach.