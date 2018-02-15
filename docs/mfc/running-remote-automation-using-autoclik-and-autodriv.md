---
title: "Uruchamianie automatyzacji zdalnej przy użyciu aplikacji AUTOCLIK i AUTODRIV | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- AUTOCLIK sample [MFC]
ms.assetid: 8900c0de-8dba-4f0a-8d9e-7db77a1f4f46
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 791655047eaf07732e1e006e8cc3ea8e7dec4727
ms.sourcegitcommit: fa7a6dccddce3747389c91277a53e296f905305c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="running-remote-automation-using-autoclik-and-autodriv"></a>Uruchamianie automatyzacji zdalnej przy użyciu aplikacji AUTOCLIK i AUTODRIV
Aplikacji AUTOCLIK jest proste automatyzacji serwera przykładowej aplikacji, która służy jako podstawowy, z którego można dowiedzieć się więcej na temat automatyzacji zdalnej. AUTODRIV jest prostą aplikację klienta automatyzacji, która dyski aplikacji AUTOCLIK. Można używać ich, aby zademonstrować automatyzacji zdalnej.  
  
#### <a name="to-install-autoclikexe-on-two-machines-and-drive-it-using-remote-automation"></a>Do zainstalowania aplikacji AUTOCLIK. EXE na dwóch maszyn i dysk przy użyciu automatyzacji zdalnej  
  
1.  Zainstaluj [aplikacji AUTOCLIK](../visual-cpp-samples.md) Przykładowa aplikacja na komputerze deweloperskim.  
  
2.  Tworzenie aplikacji AUTOCLIK. WYWOŁANIE PLIKU EXE.  
  
3.  Uruchamianie aplikacji AUTOCLIK. EXE w autonomicznym programie sposób, a następnie wyłącz ją. Spowoduje to Zarejestruj jako serwer automatyzacji.  
  
4.  Skopiuj aplikacji AUTOCLIK. EXE z komputerem zdalnym, uruchom go istnieje, a następnie zamknij go.  
  
5.  Uruchom AUTODRIV. EXE na lokalnym komputerze, a następnie sprawdź, czy uruchomienie jej uruchamiania aplikacji AUTOCLIK. WYWOŁANIE PLIKU EXE. Aby dowiedzieć się więcej na temat AUTODRIV. EXE, zobacz [aplikacji AUTOCLIK](../visual-cpp-samples.md).  
  
6.  Na komputerze zdalnym Uruchom AUTMGR32. EXE (Menedżer automatyzacji).  
  
7.  Na komputerze zdalnym Uruchom RACMGR32. EXE (Menedżer połączeń automatyzacji zdalnej).  
  
8.  W Menedżer połączeń automatyzacji zdalnej, wybierz AutoClik.Document z **klasy OLE** listy.  
  
9. Wybierz zasady zabezpieczeń systemu na podstawie **dostępu klienta** kartę, aby udzielić dostępu klienta AutoClik.Document.  
  
10. Na komputerze lokalnym Uruchom RACMGR32. EXE i wybierz AutoClik.Document z **klasy OLE** listy.  
  
11. Z **połączenie z serwerem** , wybierz pozycję Adres sieciowy odpowiednich protokołów sieci i komputera zdalnego.  
  
12. Z AutoClik.Document nadal wybrany w **klasy OLE** pola listy, wybierz **zdalnego** polecenie `Register` menu.  
  
13. Na komputerze lokalnym Uruchom AUTODRIV. Plik EXE lub równoważne aplikacji AUTOCLIK. Projektu MAK języka Visual Basic, jeśli chcesz mieć języka Visual Basic, zamiast MFC klienta.  
  
 Na komputerze zdalnym teraz należy widoczne aplikacji AUTOCLIK wykonywania poleceń inicjowane z lokalnego klienta.  
  
## <a name="see-also"></a>Zobacz też  
 [Automatyzacja zdalna](../mfc/remote-automation.md)

