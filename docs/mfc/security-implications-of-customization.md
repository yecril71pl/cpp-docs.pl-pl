---
title: Zabezpieczenia konsekwencje dostosowania związane z | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- security, MFC Feature Pack
- MFC Feature Pack, security
ms.assetid: 9be96b12-be38-43bd-a133-5d671265f7a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1416a586af479ea7b476a6c85d45992ba18873ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="security-implications-of-customization"></a>Konsekwencje dostosowania związane z zabezpieczeniami
W tym temacie omówiono potencjalnych osłabienia zabezpieczeń w MFC.  
  
## <a name="potential-security-weakness"></a>Potencjalne osłabienia zabezpieczeń  
 MFC pozwala użytkownikowi dostosowywanie wyglądu interfejs użytkownika aplikacji, na przykład wygląd przycisków i ikon. MFC obsługuje również narzędzia zdefiniowane przez użytkownika, które umożliwiają użytkownikom wykonywanie poleceń powłoki. Luki w zabezpieczeniach pojawia się, ponieważ dostosowane ustawienia aplikacji są zapisywane w profilu użytkownika w rejestrze. Każdy, kto może uzyskać dostępu do rejestru można edytować tych ustawień i zmienić wygląd aplikacji lub zachowanie. Na przykład administrator na komputerze można personifikować użytkownika, powodując użytkownika aplikacji do wykonywania dowolnych programów (nawet z udziału sieciowego).  
  
## <a name="workarounds"></a>Rozwiązania  
 Firma Microsoft zaleca żadnego z tych trzech sposobów zamknąć luk w zabezpieczeniach w rejestrze:  
  
-   Szyfruj dane, które są przechowywane  
  
-   Dane można przechowywać w bezpiecznej pliku zamiast w rejestrze.  
  
     Aby osiągnąć te pierwsze dwa sposoby, klasa wyprowadzona z [klasy CSettingsStore](../mfc/reference/csettingsstore-class.md) i zastąp jego metody służące do implementacji szyfrowania lub magazynu poza rejestru.  
  
-   Można również wyłączyć dostosowań w aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie na potrzeby MFC](../mfc/customization-for-mfc.md)

