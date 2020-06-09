---
title: Zabezpieczenia internetowe (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- code signing [MFC], Internet security
- sandboxing [MFC]
- digital signatures [MFC], Internet security
- code signing [MFC]
- Web application security [MFC]
- code access security [MFC], Internet security considerations
- security [MFC]
- security [MFC], Internet
- Internet applications [MFC], security
- Web application security [MFC], Internet security approaches
ms.assetid: bf0da697-81bc-41f0-83fa-d7f82ed83df8
ms.openlocfilehash: ce044014c5c2e13528cea8b982227b0ec8bc03fc
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621538"
---
# <a name="internet-security-c"></a>Zabezpieczenia internetowe (C++)

Bezpieczeństwo kodu to główny problem dla deweloperów i użytkowników aplikacji internetowych. Istnieją zagrożenia: złośliwy kod, kod, który został naruszony, i kod z nieznanych witryn lub autorów.

Istnieją dwa podstawowe podejścia do zabezpieczeń podczas opracowywania Internetu. Pierwszy nosi nazwę "piaskownicy". W tym podejściu aplikacja jest ograniczona do określonego zestawu interfejsów API i jest wykluczona z potencjalnie niebezpiecznych, takich jak pliki we/wy, gdzie program może zniszczyć dane na komputerze użytkownika. Druga jest implementowana przy użyciu podpisów cyfrowych. Takie podejście jest określane jako "shrinkwrap" dla Internetu. Kod jest weryfikowany i podpisywany przy użyciu technologii klucza prywatnego/klucza publicznego. Przed uruchomieniem kodu jego podpis cyfrowy zostanie zweryfikowany, aby upewnić się, że kod pochodzi z znanego uwierzytelnionego źródła i że kod nie został zmodyfikowany od czasu podpisania.

W pierwszym przypadku ufasz, że aplikacja nie podejmie żadnej szkody i ufasz pochodzeniu aplikacji. W drugim podpisy cyfrowe są używane do weryfikowania autentyczności. Podpisywanie cyfrowe jest standardem branżowym używanym do identyfikowania i dostarczania szczegółowych informacji o wydawcy kodu. Jego technologia jest oparta na standardach, w tym RSA i X. 509. Przeglądarki zwykle umożliwiają użytkownikom wybranie, czy chcą pobrać i uruchomić kod nieznanego źródła.

## <a name="see-also"></a>Zobacz też

[MFC — zadania związane z programowaniem Internetu](mfc-internet-programming-tasks.md)<br/>
[MFC — podstawy programowania Internetu](mfc-internet-programming-basics.md)
