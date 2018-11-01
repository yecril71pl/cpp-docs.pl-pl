---
title: Konsekwencje dostosowania związane z zabezpieczeniami
ms.date: 11/04/2016
helpviewer_keywords:
- security, MFC Feature Pack
- MFC Feature Pack, security
ms.assetid: 9be96b12-be38-43bd-a133-5d671265f7a1
ms.openlocfilehash: cdb8e0d39a76f749011ca3c680e25b86212b6519
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434428"
---
# <a name="security-implications-of-customization"></a>Konsekwencje dostosowania związane z zabezpieczeniami

W tym temacie omówiono potencjalnych słabość zabezpieczeń w MFC.

## <a name="potential-security-weakness"></a>Potencjalne osłabienia zabezpieczeń

MFC umożliwia użytkownikowi dostosowywanie wyglądu interfejs użytkownika aplikacji, na przykład wygląd przycisków i ikon. Biblioteka MFC obsługuje narzędzia zdefiniowane przez użytkownika, które umożliwiają użytkownikowi wykonanie poleceń powłoki. Luki w zabezpieczeniach pojawia się, ponieważ dostosowane ustawienia aplikacji są zapisywane w profilu użytkownika w rejestrze. Każdy, kto może uzyskać dostępu do rejestru można edytować te ustawienia i zmienić wygląd aplikacji i zachowania. Na przykład administrator na komputerze może personifikować użytkownika, powodując użytkownika aplikacji do wykonywania dowolnych programów (nawet z udziału sieciowego).

## <a name="workarounds"></a>Rozwiązania

Zaleca się jeden z następujących trzech sposobów zamknąć luk w zabezpieczeniach w rejestrze:

- Szyfruj dane, które są przechowywane

- Store danych w bezpiecznej pliku zamiast w rejestrze.

   Aby wykonać te pierwsze dwa sposoby, należy wyprowadzić klasę z [klasa CSettingsStore](../mfc/reference/csettingsstore-class.md) i zastąp jego metody do zaimplementowania szyfrowanie lub magazyn poza rejestru.

- Można również wyłączyć dostosowań w aplikacji.

## <a name="see-also"></a>Zobacz też

[Dostosowywanie na potrzeby MFC](../mfc/customization-for-mfc.md)

