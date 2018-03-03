---
title: "Błąd narzędzi konsolidatora LNK1223 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1223
dev_langs:
- C++
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c330077e8de73b8eeb71b0a418eb89d2ec0ebfdc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1223"></a>Błąd narzędzi konsolidatora LNK1223
nieprawidłowy lub uszkodzony plik: plik zawiera nieprawidłowe elementy wnoszone .pdata  
  
 W przypadku platform RISC używających pdata ten błąd wystąpi, jeśli kompilator wysyłanego sekcji .pdata zapisami nieposortowana.  
  
 Aby rozwiązać ten problem, spróbuj kompilowanie bez [/GL (optymalizacja całego programu)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) włączone. W niektórych przypadkach ciało funkcji jest puste może powodować również tego błędu.