---
title: "Tworzenie programów korzystających z automatyzacji zdalnej | Dokumentacja firmy Microsoft"
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
- Remote Automation, creating programs
ms.assetid: 8eb31320-1037-4029-b1f3-fdc9406dbaf1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 86a9b9f4dccaaa3a97366dffb11955d3b148aff5
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="creating-programs-that-use-remote-automation"></a>Tworzenie programów korzystających z automatyzacji zdalnej
Dowolny obiekt automatyzacji i dowolny kontroler automatyzacji jest można używać bez zmian do kodu źródłowego, bez konieczności ponownej kompilacji i bez konieczności ponowne łączenie automatyzacji zdalnej. Po instalacji, który działa lokalnie (to znaczy, że na tym samym komputerze), należy przeprowadzić tylko kilka czynności, aby ją wykonać zdalnie.  
  
#### <a name="to-execute-the-remote-automation-object"></a>Do wykonania obiektu automatyzacji zdalnej  
  
1.  Zarejestrować aplikację na komputerze klienta lub maszyny.  
  
2.  Skonfiguruj dostęp klienta do używania serwera zdalnego.  
  
3.  Zainstaluj i Zarejestruj aplikację na komputerze serwera lub maszyny.  
  
4.  Skonfiguruj serwer w celu zezwolenia na aktywację zdalną.  
  
5.  Menedżer automatyzacji należy zainstalować na komputerów serwera.  
  
6.  Menedżer automatyzacji wykonywania na serwerach.  
  
7.  Uruchom aplikację na klientów.  
  
 Krok 1 najłatwiej odbywa się przez ładowanie i wykonywanie aplikacji serwera na komputerze klienckim, większość serwerów są self rejestrowania. Jeśli badane Instalatora lokalnie uprzednio tego etapu została już zakończona. Jeśli aplikacja serwera nie jest self rejestrowanie, może zajść potrzeba była to. W przeciwnym razie należy udostępnić plik rejestracji, który można uruchomić użytkownika lokalnego, aby wykonać ten krok. Jeśli żadna z tych czynności użytkownika lub administratora należy dokonać edycji rejestru ręcznie, procedury, która nie jest zalecane dla wszystkich użytkowników najbardziej zaawansowanych.  
  
 Krok 2 wymaga stosowania Menedżer połączeń automatyzacji zdalnej (RAC). Uruchom Menedżera RAC i upewnij się, że karta połączenia serwera jest wyświetlany u góry. Następnie należy znaleźć wpisu dla obiekt serwera w **klasy OLE** okienko i kliknij go. Następnie można przejść do **adres sieciowy** kombi i wpisz nazwę komputera serwera, na którym uruchomiona jest zdalny plik wykonywalny. Na przykład możesz wprowadzić \\\MyServer tutaj. Następnie wybierz odpowiedni protokół sieciowy z listy. Należy skontaktować się z administratorem sieci, aby ustalić, który protokół jest zalecane. W wielu przypadkach będzie TCP/IP. Ponadto można wybrać poziom uwierzytelniania. W większości przypadków będzie to lewej jako (Brak) lub wartość domyślną. Teraz kliknij prawym przyciskiem myszy serwer w **klasy OLE** okienka. Spowoduje to utworzenie menu skrótów, z którego można wybrać operacji lokalnym lub zdalnym. Wybierz zdalnego.  
  
 Krok 3 obejmuje prawidłowo Instalowanie i rejestrowanie aplikacji serwera na komputerze wybranego serwera lub maszyny. Ponownie, gdy aplikacja jest self rejestrowanie, po jej wykonanie Ponadto zarejestruje go.  
  
 Krok 4 wymagane jest skonfigurowanie serwera, aby umożliwić zdalne wykonywanie kodu. Uruchom Menedżera RAC na komputerze z serwerem i upewnij się, że **dostępu klienta** karta ma fokus. Wybierz model aktywacji, który ma (zazwyczaj **Zezwalaj tworzy zdalnego przez klucz**. Jeśli wybierzesz tę opcję, należy również kliknij **Zezwalaj na aktywację zdalną** pole wyboru, aby ustawić wartości wpisu rejestru do "Y"). Jeśli wybierzesz opcję Zezwalaj na zdalny tworzy (ACL), masz również opcję, aby edytować listy ACL przez wypchnięcie **edycję listy ACL** przycisku.  
  
 Aby umożliwić automatyzacji zdalnej do pracy, należy następnie upewnij się, że Menedżer automatyzacji jest zainstalowana i uruchomiona na komputerze serwera lub maszyny. Jeśli nie jest zainstalowany, należy skopiować AUTMGR32. EXE w katalogu systemu Windows. Aby uzyskać informacje, jak to zrobić, zobacz [instalacja automatyzacji zdalnej](../mfc/remote-automation-installation.md). Aby uruchomić automatyzacji zdalnej, należy wykonać Menedżer automatyzacji. Będzie ono okno stanu mała, w którym będzie wyświetlana liczba komunikatów. Po rozpoczęciu, spowoduje to zminimalizowanie samej siebie. Jeśli chcesz kontynuować wyświetlić informacje o stanie, możesz kliknąć **Menedżer automatyzacji** karty na pasku zadań, aby przywrócić okna.  
  
 Ostatnim krokiem jest wykonanie aplikacji klienta na komputerze klienckim. Jeśli powyższe kroki zostały wykonane, powinien połączyć się z obiektem serwera i wykonać dokładnie, jak lokalnie, choć nieco wolniej.  
  
 Zwróć uwagę, że Menedżer RAC umożliwia również przełączać się między automatyzacji zdalnej i rozproszonego modelu COM (DCOM na tych platformach, które obsługują model DCOM) za pomocą jednego kliknięcia przycisku radiowego. Jeśli wybierzesz modelu DCOM, można ustawić różne opcje konfiguracji. W dokumentacji DCOM dalszych szczegółów.  
  
## <a name="see-also"></a>Zobacz też  
 [Automatyzacja zdalna](../mfc/remote-automation.md)   
 [Uruchamianie automatyzacji zdalnej przy użyciu aplikacji AUTOCLIK i AUTODRIV](../mfc/running-remote-automation-using-autoclik-and-autodriv.md)

