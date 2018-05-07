---
title: Błąd narzędzi konsolidatora LNK1223 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1223
dev_langs:
- C++
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e50d29af6ac563fadd3a52e5b1d3d15201289083
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1223"></a>Błąd narzędzi konsolidatora LNK1223
nieprawidłowy lub uszkodzony plik: plik zawiera nieprawidłowe elementy wnoszone .pdata  
  
 W przypadku platform RISC używających pdata ten błąd wystąpi, jeśli kompilator wysyłanego sekcji .pdata zapisami nieposortowana.  
  
 Aby rozwiązać ten problem, spróbuj kompilowanie bez [/GL (optymalizacja całego programu)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) włączone. W niektórych przypadkach ciało funkcji jest puste może powodować również tego błędu.