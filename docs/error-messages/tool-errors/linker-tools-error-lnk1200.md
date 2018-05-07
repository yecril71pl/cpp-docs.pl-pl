---
title: Błąd narzędzi konsolidatora LNK1200 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1200
dev_langs:
- C++
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ab32939c55dce5e27f907f3d23e639b24741cdc3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1200"></a>Błąd narzędzi konsolidatora LNK1200
Błąd odczytu bazy danych programu "filename"  
  
 Nie można odczytać bazy danych programu (PDB).  
  
 Przyczyną tego błędu może być uszkodzenie pliku.  
  
 Jeśli `filename` jest pliku PDB dla pliku obiektu ponownie skompilować przy użyciu pliku obiektu [/zi](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
 Jeśli `filename` jest plik PDB dla pliku wyjściowego głównym, a ten błąd wystąpił podczas konsolidowania przyrostowego, usuń plik PDB i połącz ponownie.