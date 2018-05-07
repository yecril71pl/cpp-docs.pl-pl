---
title: Błąd narzędzi konsolidatora LNK1241 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1241
dev_langs:
- C++
helpviewer_keywords:
- LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b02b1d9d06706c70478d958dd3c2af8dbc9c2c03
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1241"></a>Błąd narzędzi konsolidatora LNK1241
Plik zasobów 'Plik zasobów' już określony  
  
 Ten błąd jest generowany po uruchomieniu **cvtres** ręcznie z poziomu wiersza polecenia i jeśli następnie przekazać .obj wynikowego pliku do konsolidatora dodatkowo do innych plików .res.  
  
 Aby określić wiele plików .res, należy przekazać je wszystkie do konsolidatora jako pliki .res, nie za pomocą plików .obj utworzony przez **cvtres**.