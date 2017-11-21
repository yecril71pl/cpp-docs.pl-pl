---
title: ". PDB, pliki jako dane wejściowe konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a2f99bef901a09298404eabfe36f39bd1dd2b6bc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="pdb-files-as-linker-input"></a>Pliki .Pdb — Wejście konsolidatora
Obiekt skompilowana przy użyciu opcji/zi plików (.obj) zawiera nazwę bazy danych programu (PDB). Nie określono nazwy pliku PDB obiektu do konsolidatora; ŁĄCZE o nazwie osadzonych można znaleźć pliku PDB, jeśli jest to potrzebne. Dotyczy to również możliwością debugowania obiektów zawartych w bibliotece; plik PDB dla biblioteki możliwością debugowania musi być dostępny do konsolidatora wraz z biblioteki.  
  
 ŁĄCZE używa również pliku PDB do przechowywania informacji o debugowaniu dla pliku .exe lub .dll. PDB programu jest zarówno w pliku wyjściowego, jak i w pliku wejściowym, ponieważ łącze aktualizuje pliku PDB, gdy jego odtwarza program.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki wyjściowe LINK](../../build/reference/link-input-files.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)