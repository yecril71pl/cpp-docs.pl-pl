---
title: Błąd d8037 wiersza polecenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8037
dev_langs:
- C++
helpviewer_keywords:
- D8037
ms.assetid: acddaaa0-bd84-426f-a37b-8f680b379c9d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 729a7fedbe1be3acbe7d68d9037b2f9c8b9f9806
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298814"
---
# <a name="command-line-error-d8037"></a>Błąd D8037 wiersza polecenia
Nie można utworzyć pliku tymczasowego il; wyczyścić katalog temp starych plików il  
  
 Nie jest wystarczająco dużo miejsca, aby utworzyć tymczasowy kompilatora plików pośrednich. Aby rozwiązać ten błąd, należy usunąć wszystkie stare pliki MSIL w katalogu określonym przez **TMP** zmiennej środowiskowej. Te pliki zostaną z _CL_hhhhhhhh.ss formularza, gdzie h reprezentuje losowe szesnastkową wartością cyfrową, a ss reprezentuje typ pliku IL. Ponadto należy zaktualizować komputer z najnowszych poprawek systemu operacyjnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy wiersza polecenia od D8000 do D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)