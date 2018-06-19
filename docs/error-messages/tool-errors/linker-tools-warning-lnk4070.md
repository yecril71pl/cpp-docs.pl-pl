---
title: Ostrzeżenie LNK4070 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4070
dev_langs:
- C++
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e4599e96552f1b98ef0b1af8d38995ebbe5a83e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302506"
---
# <a name="linker-tools-warning-lnk4070"></a>Ostrzeżenie LNK4070 narzędzi konsolidatora
Dyrektywa /out:filename w. EXP różni się od nazwy pliku wyjściowego "filename"; ignorowanie dyrektywy  
  
 `filename` Określony w [nazwa](../../build/reference/name-c-cpp.md) lub [biblioteki](../../build/reference/library.md) instrukcji podczas tworzenia pliku .exp różni się od danych wyjściowych `filename` który został domyślnie zakłada, że lub określony za pomocą [/OUT](../../build/reference/out-output-file-name.md) opcji.  
  
 Zostanie wyświetlone to ostrzeżenie, jeśli zmieniasz nazwę pliku wyjściowego w środowisku programistycznym i gdzie plik .def projektu nie zostało zaktualizowane. Ręcznie zaktualizuj plik .def, aby rozwiązać to ostrzeżenie.  
  
 Program kliencki, który używa wynikowa Biblioteka DLL mogą wystąpić problemy.