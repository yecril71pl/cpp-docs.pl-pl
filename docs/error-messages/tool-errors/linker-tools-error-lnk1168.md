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
ms.openlocfilehash: 9437b88b67254a63babf5b72379a760d1ab86062
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464837"
---
# <a name="linker-tools-error-lnk1168"></a>Błąd narzędzi konsolidatora LNK1168
nie można otworzyć pliku do zapisu  
  
 Nie można zapisać konsolidator `filename`. Plik może być używany i jego uchwyt jest zablokowany przez inny proces lub nie masz uprawnienia do zapisu dla pliku lub katalogu lub udziału sieciowego, w którym się on znajduje. Ten błąd jest często spowodowane przez stan przejściowy — na przykład blokadę nałożoną przez program antywirusowy, proces indeksowania wyszukiwania pliku lub opóźnienie w zwolnieniu blokady utrzymywane przez system kompilacji programu Visual Studio.  
  
 Aby rozwiązać ten problem, upewnij się, że `filename` dojście do pliku nie jest zablokowany i czy masz uprawnienia do zapisu dla pliku. Jeśli jest to plik wykonywalny, sprawdź, czy nie jest uruchomiony.  
  
 Można użyć narzędzi Windows SysInternals [obsługi](http://technet.microsoft.com/sysinternals/bb896655.aspx) lub [Eksplorator procesów](http://technet.microsoft.com/sysinternals/bb896653) ustalenie, który proces nałożył blokadę na uchwyt pliku `filename`. Przy użyciu Eksploratora procesów możesz zwalniać blokady uchwytów otwartego pliku. Aby uzyskać informacje dotyczące sposobu korzystania z tych narzędzi, przeczytaj pliki pomocy, które są z nimi dostarczane.  
  
 Jeśli plik jest zablokowany przez program antywirusowy, można naprawić ten problem poprzez wykluczenie katalogów danych wyjściowych kompilacji z funkcji automatycznego skanowania przez program antywirusowy. Tworzenie nowych plików w systemie plików często wyzwala skanery antywirusowe, które w trakcie skanowania nakładają blokady na pliki. Szczegółowe informacje na temat wykluczania określonych katalogów ze skanowania można znaleźć w dokumentacji programu antywirusowego.  
  
 Jeśli plik jest zablokowany przez usługę indeksowania wyszukiwania, można naprawić ten problem poprzez wykluczenie katalogów danych wyjściowych kompilacji z automatycznego indeksowania. Aby uzyskać więcej informacji, zobacz dokumentację dotyczącą usługi indeksowania. Aby zmienić usługę indeksowania wyszukiwania Windows, użyj **opcje indeksowania** w Windows **Panelu sterowania**. Aby uzyskać więcej informacji, zobacz [poprawić Windows wyszukuje przy użyciu indeksu: często zadawane pytania dotyczące](http://windows.microsoft.com/en-us/windows/improve-windows-searches-using-index-faq#1TC=windows-7).  
  
 Jeśli plik wykonywalny nie może zostać zastąpiony przez proces kompilacji, może być zablokowany przez Eksplorator plików. Jeśli **doświadczenie z aplikacji** usługa została wyłączona, Eksplorator plików może nałożyć do blokady dojście do pliku wykonywalnego przez dłuższy czas. Aby rozwiązać ten problem, uruchom **services.msc** , a następnie otwórz **właściwości** okno dialogowe **doświadczenie z aplikacji** usługi. Zmiana **uruchamiana** z **wyłączone** do **ręczne**.  
  
## <a name="see-also"></a>Zobacz też  
 [Może zostać wyświetlony "Błąd PRJ0008" lub "Fatal error LNK1168" błąd podczas próby tworzenia rozwiązania lub projektu ActiveX w programie Visual C++](http://support.microsoft.com/kb/308358)