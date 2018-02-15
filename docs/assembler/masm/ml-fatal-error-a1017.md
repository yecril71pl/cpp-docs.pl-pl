---
title: "Błąd krytyczny ML A1017 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- A1017
dev_langs:
- C++
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3f77f6d2905d70614735beb6cbcefeeb7e07b491
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="ml-fatal-error-a1017"></a>Błąd krytyczny ML A1017
**Brak nazwy pliku źródłowego**  
  
 ML nie można odnaleźć pliku złóż lub przekazywane do konsolidatora.  
  
 Ten błąd jest generowany po uruchomieniu ML opcje wiersza polecenia bez określania nazwy pliku działanie. Aby utworzyć pliki, które nie mają rozszerzenia .asm, użyj **/Ta** opcji wiersza polecenia.  
  
 Ten błąd może być również generowany przez wywołanie ML bez parametrów, jeśli ML — zmienna środowiskowa zawiera opcje wiersza polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)