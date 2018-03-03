---
title: "Kompilatora (poziom 1) ostrzeżenie C4650 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4650
dev_langs:
- C++
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: af10d05562c0c60c6a010e105441533362d058df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4650"></a>Kompilator C4650 ostrzegawcze (poziom 1)
informacje o debugowaniu nie znajduje się w prekompilowanym nagłówkiem; tylko symbole globalne nagłówka będą dostępne  
  
 Prekompilowanego pliku nagłówkowego nie został skompilowany z Microsoft symboliczna informacja o debugowaniu.  
  
 Gdy są połączone, wynikowy plik wykonywalny lub dołączanej biblioteki nie będzie zawierał informacji debugowania dla symboli lokalnych zawarte we prekompilowanym nagłówku.  
  
 To ostrzeżenie można uniknąć przez kompilację prekompilowanego pliku nagłówkowego z [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) opcji wiersza polecenia.