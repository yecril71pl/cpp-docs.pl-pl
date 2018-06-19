---
title: Błąd narzędzi konsolidatora LNK1164 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1164
dev_langs:
- C++
helpviewer_keywords:
- LNK1164
ms.assetid: da89765c-affa-4f88-b170-6d6b19a577cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f85ad1c223c9d4b22e3763f1d24a6c2631f6342d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297423"
---
# <a name="linker-tools-error-lnk1164"></a>Błąd narzędzi konsolidatora LNK1164
sekcja wyrównanie sekcji (numer) większa niż wartość opcji/align  
  
 Rozmiar wyrównania dla podanej sekcji w pliku obiektu przekracza wartość określony za pomocą [/ALIGN](../../build/reference/align-section-alignment.md) opcji. **/ALIGN** wartość musi być potęgą liczby 2 i musi być równa lub przekracza wyrównanie sekcji podany w pliku obiektu.  
  
 Albo Skompiluj ponownie z mniejszym wyrównanie sekcji lub zwiększ **/ALIGN** wartość.