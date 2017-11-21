---
title: "Błąd narzędzi konsolidatora LNK1200 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1200
dev_langs: C++
helpviewer_keywords: LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 792c81e36b99bbac6c0417f0230bb1ea2bb1787c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1200"></a>Błąd narzędzi konsolidatora LNK1200
Błąd odczytu bazy danych programu "filename"  
  
 Nie można odczytać bazy danych programu (PDB).  
  
 Przyczyną tego błędu może być uszkodzenie pliku.  
  
 Jeśli `filename` jest pliku PDB dla pliku obiektu ponownie skompilować przy użyciu pliku obiektu [/zi](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
 Jeśli `filename` jest plik PDB dla pliku wyjściowego głównym, a ten błąd wystąpił podczas konsolidowania przyrostowego, usuń plik PDB i połącz ponownie.