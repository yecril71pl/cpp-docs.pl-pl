---
title: ". EXP, pliki jako dane wejściowe konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- exporting functions
- import libraries, linker files
- linking [C++], exports
- exporting functions, information about exported functions
- exporting data, export (.exp) files
- functions [C++], exporting
- .exp files [C++]
- EXP files
ms.assetid: 399f5636-0a4d-462e-b500-5f5b9ae5ad22
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5cd6351623b230e3be1e432bd6ee0fb760da5abd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="exp-files-as-linker-input"></a>Pliki .Exp — Wejście konsolidatora
Pliki eksportu (.exp) zawierają informacje o wyeksportowanej funkcji i danych elementów. Gdy LIB tworzy bibliotekę importowaną, również tworzy plik EXP. Plik EXP można użyć podczas połączyć program, który eksportuje do, a także importuje z innego programu, bezpośrednio lub pośrednio. Jeśli łączysz się przy użyciu pliku .exp łącze nie tworzy biblioteki importowanej, ponieważ przyjęto założenie, że biblioteka już utworzone. Aby uzyskać więcej informacji o .exp — pliki i biblioteki importu, zobacz [Praca z bibliotekami importowania i eksportowania plików](../../build/reference/working-with-import-libraries-and-export-files.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki wyjściowe LINK](../../build/reference/link-input-files.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)