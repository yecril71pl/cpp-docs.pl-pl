---
title: Zabezpieczenia internetowe (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4454eceae2cc5f2e6b46510fe95889c664a568a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="internet-security-c"></a>Zabezpieczenia internetowe (C++)
Kod bezpieczeństwa jest głównych problem dla deweloperów i użytkowników aplikacji internetowych. Istnieje ryzyko: złośliwego kodu, kod, który został zmodyfikowany i kod z nieznanej witryny lub autorów.  
  
 Istnieją dwa podstawowe podejścia do zabezpieczeń podczas opracowywania obsługę sieci Internet. Pierwszy jest nazywany "sandboxing." W takie podejście aplikacja jest ograniczony do określonego zestawu interfejsów API i wykluczone z tych potencjalnie niebezpiecznych, takich jak plik we/wy, których program może spowodować utratę danych na komputerze użytkownika. Drugim jest implementowane za pomocą podpisów cyfrowych. Ta metoda jest określana jako "shrinkwrap" w Internecie. Kod jest weryfikowany i podpisany przy użyciu technologii klucza publicznego klucza i prywatnej. Przed uruchomieniem kodu sprawdza podpis cyfrowy się upewnij się, że kod jest ze znanego uwierzytelnionego źródła i czy kod nie została zmieniona, ponieważ jest on podpisany.  
  
 W pierwszym przypadku ufasz, że aplikacja nie ma żadnych problemów i zaufania punkt początkowy aplikacji. W ciągu sekundy podpisy cyfrowe są używane w celu sprawdzenia autentyczności. Cyfrowe podpisywanie jest standardem branżowym, który umożliwia identyfikowanie i zawierają szczegółowe informacje o wydawcy kodu. Jego technologii jest oparta na standardach, w tym RSA i X.509. Przeglądarki zwykle zezwala użytkownikom na wybranie, czy chce pobierać i uruchamiać kodem nieznanego pochodzenia.  
  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania związane z programowaniem Internetu MFC](../mfc/mfc-internet-programming-tasks.md)   
 [MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)

