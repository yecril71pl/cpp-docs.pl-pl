---
title: "Kompilatora (poziom 1) ostrzeżenie C4124 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4124
dev_langs: C++
helpviewer_keywords: C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3de13cb50444530fc0917330771b693f60a7e5f5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4124"></a>Kompilator C4124 ostrzegawcze (poziom 1)
__fastcall ze sprawdzeniem stosu jest nieefektywne  
  
 `__fastcall` Użyto słowa kluczowego ze sprawdzeniem stosu włączone.  
  
 `__fastcall` Konwencji generuje kod szybszy, ale sprawdzanie stosu powoduje, że kod wolniej. Korzystając z `__fastcall`, Wyłącz sprawdzanie stosu z **check_stack —** pragma lub/GS.  
  
 To ostrzeżenie zostanie wyświetlone tylko w przypadku pierwszej funkcji zadeklarowany w tych warunkach.