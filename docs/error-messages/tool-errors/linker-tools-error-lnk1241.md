---
title: "Błąd narzędzi konsolidatora LNK1241 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1241
dev_langs:
- C++
helpviewer_keywords:
- LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bb256607f6babbba90fbd17ae89bfbdfcfb48138
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1241"></a>Błąd narzędzi konsolidatora LNK1241
Plik zasobów 'Plik zasobów' już określony  
  
 Ten błąd jest generowany po uruchomieniu **cvtres** ręcznie z poziomu wiersza polecenia i jeśli następnie przekazać .obj wynikowego pliku do konsolidatora dodatkowo do innych plików .res.  
  
 Aby określić wiele plików .res, należy przekazać je wszystkie do konsolidatora jako pliki .res, nie za pomocą plików .obj utworzony przez **cvtres**.