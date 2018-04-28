---
title: Błąd krytyczny ML A1017 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1017
dev_langs:
- C++
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5fcb2d921a40b35c6022b2aca1e22adc2d8c45e
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="ml-fatal-error-a1017"></a>Błąd krytyczny ML A1017
**Brak nazwy pliku źródłowego**  
  
 ML nie można odnaleźć pliku złóż lub przekazywane do konsolidatora.  
  
 Ten błąd jest generowany po uruchomieniu ML opcje wiersza polecenia bez określania nazwy pliku działanie. Aby utworzyć pliki, które nie mają rozszerzenia .asm, użyj **/Ta** opcji wiersza polecenia.  
  
 Ten błąd może być również generowany przez wywołanie ML bez parametrów, jeśli ML — zmienna środowiskowa zawiera opcje wiersza polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)