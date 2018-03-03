---
title: "Błąd narzędzi konsolidatora LNK1164 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1164
dev_langs:
- C++
helpviewer_keywords:
- LNK1164
ms.assetid: da89765c-affa-4f88-b170-6d6b19a577cf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b5c1a62430397f95f33a5a4bd6f5845b1746557d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1164"></a>Błąd narzędzi konsolidatora LNK1164
sekcja wyrównanie sekcji (numer) większa niż wartość opcji/align  
  
 Rozmiar wyrównania dla podanej sekcji w pliku obiektu przekracza wartość określony za pomocą [/ALIGN](../../build/reference/align-section-alignment.md) opcji. **/ALIGN** wartość musi być potęgą liczby 2 i musi być równa lub przekracza wyrównanie sekcji podany w pliku obiektu.  
  
 Albo Skompiluj ponownie z mniejszym wyrównanie sekcji lub zwiększ **/ALIGN** wartość.