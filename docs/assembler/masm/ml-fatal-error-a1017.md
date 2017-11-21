---
title: "Błąd krytyczny ML A1017 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A1017
dev_langs: C++
helpviewer_keywords: A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ec10e14920572bd8001cf07676c4659bc08a4acc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ml-fatal-error-a1017"></a>Błąd krytyczny ML A1017
**Brak nazwy pliku źródłowego**  
  
 ML nie można odnaleźć pliku złóż lub przekazywane do konsolidatora.  
  
 Ten błąd jest generowany po uruchomieniu ML opcje wiersza polecenia bez określania nazwy pliku działanie. Aby utworzyć pliki, które nie mają rozszerzenia .asm, użyj **/Ta** opcji wiersza polecenia.  
  
 Ten błąd może być również generowany przez wywołanie ML bez parametrów, jeśli ML — zmienna środowiskowa zawiera opcje wiersza polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)