---
title: "Błąd narzędzi konsolidatora LNK1223 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1223
dev_langs: C++
helpviewer_keywords: LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 41d3de1080fd6b1cc3e8fbc5ca948482229f306e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1223"></a>Błąd narzędzi konsolidatora LNK1223
nieprawidłowy lub uszkodzony plik: plik zawiera nieprawidłowe elementy wnoszone .pdata  
  
 W przypadku platform RISC używających pdata ten błąd wystąpi, jeśli kompilator wysyłanego sekcji .pdata zapisami nieposortowana.  
  
 Aby rozwiązać ten problem, spróbuj kompilowanie bez [/GL (optymalizacja całego programu)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) włączone. W niektórych przypadkach ciało funkcji jest puste może powodować również tego błędu.