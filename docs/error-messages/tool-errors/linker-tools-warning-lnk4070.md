---
title: "Ostrzeżenie LNK4070 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4070
dev_langs: C++
helpviewer_keywords: LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1c3c683593b9019851b1a330a613adcf7a18c4a1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4070"></a>Ostrzeżenie LNK4070 narzędzi konsolidatora
Dyrektywa /out:filename w. EXP różni się od nazwy pliku wyjściowego "filename"; ignorowanie dyrektywy  
  
 `filename` Określony w [nazwa](../../build/reference/name-c-cpp.md) lub [biblioteki](../../build/reference/library.md) instrukcji podczas tworzenia pliku .exp różni się od danych wyjściowych `filename` który został domyślnie zakłada, że lub określony za pomocą [/OUT](../../build/reference/out-output-file-name.md) opcji.  
  
 Zostanie wyświetlone to ostrzeżenie, jeśli zmieniasz nazwę pliku wyjściowego w środowisku programistycznym i gdzie plik .def projektu nie zostało zaktualizowane. Ręcznie zaktualizuj plik .def, aby rozwiązać to ostrzeżenie.  
  
 Program kliencki, który używa wynikowa Biblioteka DLL mogą wystąpić problemy.