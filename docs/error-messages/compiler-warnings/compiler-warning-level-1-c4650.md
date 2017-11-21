---
title: "Kompilatora (poziom 1) ostrzeżenie C4650 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4650
dev_langs: C++
helpviewer_keywords: C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8671b72e244a29698fa31da40de8147cdd348130
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4650"></a>Kompilator C4650 ostrzegawcze (poziom 1)
informacje o debugowaniu nie znajduje się w prekompilowanym nagłówkiem; tylko symbole globalne nagłówka będą dostępne  
  
 Prekompilowanego pliku nagłówkowego nie został skompilowany z Microsoft symboliczna informacja o debugowaniu.  
  
 Gdy są połączone, wynikowy plik wykonywalny lub dołączanej biblioteki nie będzie zawierał informacji debugowania dla symboli lokalnych zawarte we prekompilowanym nagłówku.  
  
 To ostrzeżenie można uniknąć przez kompilację prekompilowanego pliku nagłówkowego z [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) opcji wiersza polecenia.