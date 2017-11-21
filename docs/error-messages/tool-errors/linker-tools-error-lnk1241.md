---
title: "Błąd narzędzi konsolidatora LNK1241 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1241
dev_langs: C++
helpviewer_keywords: LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3fee22549e7b5c831aa378dc5caffb9da69bff88
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1241"></a>Błąd narzędzi konsolidatora LNK1241
Plik zasobów 'Plik zasobów' już określony  
  
 Ten błąd jest generowany po uruchomieniu **cvtres** ręcznie z poziomu wiersza polecenia i jeśli następnie przekazać .obj wynikowego pliku do konsolidatora dodatkowo do innych plików .res.  
  
 Aby określić wiele plików .res, należy przekazać je wszystkie do konsolidatora jako pliki .res, nie za pomocą plików .obj utworzony przez **cvtres**.