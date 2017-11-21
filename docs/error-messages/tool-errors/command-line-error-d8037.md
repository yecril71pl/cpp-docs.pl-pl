---
title: "Błąd d8037 wiersza polecenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: D8037
dev_langs: C++
helpviewer_keywords: D8037
ms.assetid: acddaaa0-bd84-426f-a37b-8f680b379c9d
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c4178f723f455bd945e1804e9203def34dc0ead3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="command-line-error-d8037"></a>Błąd D8037 wiersza polecenia
Nie można utworzyć pliku tymczasowego il; wyczyścić katalog temp starych plików il  
  
 Nie jest wystarczająco dużo miejsca, aby utworzyć tymczasowy kompilatora plików pośrednich. Aby rozwiązać ten błąd, należy usunąć wszystkie stare pliki MSIL w katalogu określonym przez **TMP** zmiennej środowiskowej. Te pliki zostaną z _CL_hhhhhhhh.ss formularza, gdzie h reprezentuje losowe szesnastkową wartością cyfrową, a ss reprezentuje typ pliku IL. Ponadto należy zaktualizować komputer z najnowszych poprawek systemu operacyjnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy wiersza polecenia od D8000 do D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)