---
title: Obsługa modelu zmiennoprzecinkowego w przypadku starszego kodu (Visual C++)
ms.date: 11/04/2016
ms.assetid: a2a26b96-7bc2-418a-981a-51aa1a0294a2
ms.openlocfilehash: 2340a4d136dee3438a47ce06793ed9274035250d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509646"
---
# <a name="floating-point-support-for-older-code-visual-c"></a>Obsługa modelu zmiennoprzecinkowego w przypadku starszego kodu (Visual C++)

MMX i rejestruje stosu zmiennoprzecinkowego (MM0-MM7/ST0-ST7) są zachowywane między przełączeń kontekstu.  Nie ma żadnych jawnej konwencji wywoływania dla tych rejestrów.  Korzystanie z tych rejestrów jest bezwzględnie zabronione w kod trybu jądra.

## <a name="see-also"></a>Zobacz też

[Konwencja wywoływania](../build/calling-convention.md)