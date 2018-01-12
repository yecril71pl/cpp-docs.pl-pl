---
title: "Błąd krytyczny C1352 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1352
dev_langs: C++
helpviewer_keywords: C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2f2a5c42eaa5afc609f1b8ee1c09875db8bff9c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1352"></a>Błąd krytyczny C1352
Nieprawidłowe lub uszkodzone MSIL w funkcji "function" z modułu 'Plik'.  
  
 Przekazano modułu .netmodule do kompilatora, ale kompilator wykryła uszkodzenie w pliku.  Poproś osobę, która wyprodukowanych modułu .netmodule do sprawdzania, czy.  
  
 Kompilator nie sprawdza modułu .netmodule plików dla wszystkich typów uszkodzenia.  Jednak Sprawdź, czy wszystkie ścieżki kontroli w funkcji zawiera instrukcję return.  
  
 Aby uzyskać więcej informacji, zobacz [modułu .netmodule pliki jako dane wejściowe konsolidatora](../../build/reference/netmodule-files-as-linker-input.md).