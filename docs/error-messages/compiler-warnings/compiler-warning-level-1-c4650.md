---
title: Kompilatora (poziom 1) ostrzeżenie C4650 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4650
dev_langs:
- C++
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6cb1c9979141e7958b6c2802aaf321efe41e9570
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283088"
---
# <a name="compiler-warning-level-1-c4650"></a>Kompilator C4650 ostrzegawcze (poziom 1)
informacje o debugowaniu nie znajduje się w prekompilowanym nagłówkiem; tylko symbole globalne nagłówka będą dostępne  
  
 Prekompilowanego pliku nagłówkowego nie został skompilowany z Microsoft symboliczna informacja o debugowaniu.  
  
 Gdy są połączone, wynikowy plik wykonywalny lub dołączanej biblioteki nie będzie zawierał informacji debugowania dla symboli lokalnych zawarte we prekompilowanym nagłówku.  
  
 To ostrzeżenie można uniknąć przez kompilację prekompilowanego pliku nagłówkowego z [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) opcji wiersza polecenia.