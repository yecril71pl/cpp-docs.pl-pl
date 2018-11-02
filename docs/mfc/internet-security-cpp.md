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
ms.openlocfilehash: e7892793a82f2b030a99465a712e33e1b9ef4673
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486102"
---
# <a name="internet-security-c"></a>Zabezpieczenia internetowe (C++)

Kod bezpieczeństwa jest poważnym problemem dla programistów i użytkowników aplikacji internetowych. Ryzyko: złośliwego kodu, kod, który został zmodyfikowany i kodu z nieznanego witryn lub autorów.

Istnieją dwa podstawowe podejścia do zabezpieczeń podczas tworzenia dla Internetu. Pierwszy jest nazywany "piaskownicy". W tym podejściu aplikacji jest ograniczony do określonego zestawu interfejsów API i wykluczone z potencjalnie niebezpiecznych usług, na przykład plik we/wy, których program może spowodować utratę danych na komputerze użytkownika. Drugim jest implementowany przy użyciu podpisów cyfrowych. To podejście jest określane jako "shrinkwrap" do korzystania z Internetu. Kod jest weryfikowany i podpisany przy użyciu prywatnego klucza/public kluczowych technologii. Przed uruchomieniem kodu podpis cyfrowy jest weryfikowany aby upewnić się, że kod jest ze znanego źródła uwierzytelnionego i że kod nie została zmieniona, ponieważ jest on podpisany.

W pierwszym przypadku ufasz, że aplikacja nie będzie żadnych szkód i zaufania punkt początkowy aplikacji. W drugim podpisy cyfrowe są używane w celu sprawdzenia autentyczności. Cyfrowe podpisywanie jest standardem branżowym, który umożliwia identyfikowanie i zawierają szczegółowe informacje o wydawcy kodu. Technologie jest oparta na standardach, w tym RSA i X.509. Przeglądarki zwykle zezwala użytkownikom na wybór, czy chce pobierać i uruchamiać kodem nieznanego pochodzenia.

## <a name="see-also"></a>Zobacz też

[MFC — zadania związane z programowaniem Internetu](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)

