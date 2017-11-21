---
title: "Błąd narzędzi konsolidatora LNK1201 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1201
dev_langs: C++
helpviewer_keywords: LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 344f56eb3097bad447d9a0b12a0c5aac6f68b119
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1201"></a>Błąd narzędzi konsolidatora LNK1201
Błąd podczas zapisywania do bazy danych programu "filename"; Sprawdź, czy brakuje miejsca na dysku, nieprawidłowa ścieżka lub niewystarczające uprawnienia  
  
 ŁĄCZE nie można zapisać do bazy danych programu (PDB) dla pliku wyjściowego.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Plik jest uszkodzony. Usuń plik PDB i połącz ponownie.  
  
2.  Nie ma wystarczającej ilości miejsca na dysku do zapisania pliku.  
  
3.  Dysk nie jest dostępny, prawdopodobnie z powodu problem z siecią.  
  
4.  Debuger jest aktywna na program, który próbujesz się połączyć.  
  
5.  Za mało miejsca na stercie.  Zobacz [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) Aby uzyskać więcej informacji.