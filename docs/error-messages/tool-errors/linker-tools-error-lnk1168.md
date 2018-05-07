---
title: Błąd narzędzi konsolidatora LNK1168 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1168
dev_langs:
- C++
helpviewer_keywords:
- LNK1168
ms.assetid: 97ead151-fd99-46fe-9a1d-7e84dc0b8cc8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc3a7c06779cb409a39a930080199b3caf6891ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1168"></a>Błąd narzędzi konsolidatora LNK1168
nie można otworzyć pliku do zapisu  
  
 Nie można zapisać konsolidator `filename`. Plik może być używany i jego uchwyt jest zablokowany przez inny proces lub nie masz uprawnienia do zapisu dla pliku lub katalogu lub udziału sieciowego, w którym się on znajduje. Przyczyną tego błędu jest często stan przejściowy — na przykład blokady w posiadaniu programu antywirusowego pliku wyszukiwania procesu indeksowania lub opóźnienia podczas zwalniania blokady w posiadaniu [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] systemu kompilacji.  
  
 Aby rozwiązać ten problem, sprawdź, czy `filename` dojście do pliku nie jest zablokowany, i czy masz uprawnienia do zapisu dla pliku. Jeśli jest to plik wykonywalny, sprawdź, czy nie jest uruchomiony.  
  
 Można użyć narzędzia Windows SysInternals [obsługi](http://technet.microsoft.com/sysinternals/bb896655.aspx) lub [Eksploratora procesów](http://technet.microsoft.com/sysinternals/bb896653) do określenia procesu, który ma obsługiwać blokady w pliku `filename`. Przy użyciu Eksploratora procesów możesz zwalniać blokady uchwytów otwartego pliku. Aby uzyskać informacje dotyczące sposobu korzystania z tych narzędzi, przeczytaj pliki pomocy, które są z nimi dostarczane.  
  
 Jeśli plik jest zablokowany przez program antywirusowy, można naprawić ten problem poprzez wykluczenie katalogów danych wyjściowych kompilacji z funkcji automatycznego skanowania przez program antywirusowy. Tworzenie nowych plików w systemie plików często wyzwala skanery antywirusowe, które w trakcie skanowania nakładają blokady na pliki. Szczegółowe informacje na temat wykluczania określonych katalogów ze skanowania można znaleźć w dokumentacji programu antywirusowego.  
  
 Jeśli plik jest zablokowany przez usługę indeksowania wyszukiwania, można naprawić ten problem poprzez wykluczenie katalogów danych wyjściowych kompilacji z automatycznego indeksowania. Aby uzyskać więcej informacji, zobacz dokumentację dotyczącą usługi indeksowania. Aby zmienić Windows search indeksowanie usługi, użyj **opcje indeksowania** w oknach **Panelu sterowania**. Aby uzyskać więcej informacji, zobacz [poprawić system Windows będzie wyszukiwać przy użyciu indeksu: często zadawane pytania](http://windows.microsoft.com/en-us/windows/improve-windows-searches-using-index-faq#1TC=windows-7).  
  
 Jeśli plik wykonywalny nie może zostać zastąpiony przez proces kompilacji, może być zablokowany przez Eksplorator plików. Jeśli **środowisko aplikacji** usługa została wyłączona, Eksploratora plików może zatrzymać blokady dojście do pliku wykonywalnego przez dłuższy czas. Aby rozwiązać ten problem, uruchom **services.msc** , a następnie otwórz **właściwości** okno dialogowe **środowisko aplikacji** usługi. Zmień **uruchamiana** z **wyłączone** do **ręcznego**.  
  
## <a name="see-also"></a>Zobacz też  
 [Może pojawić się "Błąd PRJ0008" lub "Błąd krytyczny LNK1168" błąd podczas próby kompilacji rozwiązania lub projektu ActiveX w programie Visual C++](http://support.microsoft.com/kb/308358)