---
title: . PDB, pliki jako dane wejściowe konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6707be955b5c4a332d1162f53b1cb854391a2ce
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32370179"
---
# <a name="pdb-files-as-linker-input"></a>Pliki .Pdb — Wejście konsolidatora
Obiekt skompilowana przy użyciu opcji/zi plików (.obj) zawiera nazwę bazy danych programu (PDB). Nie określono nazwy pliku PDB obiektu do konsolidatora; ŁĄCZE o nazwie osadzonych można znaleźć pliku PDB, jeśli jest to potrzebne. Dotyczy to również możliwością debugowania obiektów zawartych w bibliotece; plik PDB dla biblioteki możliwością debugowania musi być dostępny do konsolidatora wraz z biblioteki.  
  
 ŁĄCZE używa również pliku PDB do przechowywania informacji o debugowaniu dla pliku .exe lub .dll. PDB programu jest zarówno w pliku wyjściowego, jak i w pliku wejściowym, ponieważ łącze aktualizuje pliku PDB, gdy jego odtwarza program.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki wyjściowe LINK](../../build/reference/link-input-files.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)