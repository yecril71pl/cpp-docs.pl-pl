---
title: Obsługa modelu zmiennoprzecinkowego w przypadku starszego kodu (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a2a26b96-7bc2-418a-981a-51aa1a0294a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd7cbf955fbf795d06d9cd2448d0736dc435f3b5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="floating-point-support-for-older-code-visual-c"></a>Obsługa modelu zmiennoprzecinkowego w przypadku starszego kodu (Visual C++)
MMX i rejestrów zmiennoprzecinkowych stosu (MM0-MM7/ST0-ST7) są zachowywane między przełączeń kontekstu.  Nie ma żadnych jawnej konwencji wywoływania dla tych rejestrów.  Użyj tych rejestrów jest zabronione w kod trybu jądra.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencja wywoływania](../build/calling-convention.md)