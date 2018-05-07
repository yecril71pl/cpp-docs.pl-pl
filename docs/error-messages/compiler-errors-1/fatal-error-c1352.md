---
title: Błąd krytyczny C1352 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1352
dev_langs:
- C++
helpviewer_keywords:
- C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 524b0bf5d25953c5c38cbe0e23dc5c7d9f3cb7be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1352"></a>Błąd krytyczny C1352
Nieprawidłowe lub uszkodzone MSIL w funkcji "function" z modułu 'Plik'.  
  
 Przekazano modułu .netmodule do kompilatora, ale kompilator wykryła uszkodzenie w pliku.  Poproś osobę, która wyprodukowanych modułu .netmodule do sprawdzania, czy.  
  
 Kompilator nie sprawdza modułu .netmodule plików dla wszystkich typów uszkodzenia.  Jednak Sprawdź, czy wszystkie ścieżki kontroli w funkcji zawiera instrukcję return.  
  
 Aby uzyskać więcej informacji, zobacz [modułu .netmodule pliki jako dane wejściowe konsolidatora](../../build/reference/netmodule-files-as-linker-input.md).