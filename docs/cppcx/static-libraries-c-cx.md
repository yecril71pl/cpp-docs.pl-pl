---
title: Biblioteki statyczne (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 02/03/2017
ms.prod: windows-client-threshold
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a68475447ed520298b0eab7949386c2e8d078ac6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="static-libraries-ccx"></a>Biblioteki statyczne (C + +/ CX)
Biblioteka statyczna, który jest używany w aplikacji platformy uniwersalnej systemu Windows może zawierać kod ISO standard C++, w tym typy STL i wywołania funkcji Win32 API, które nie są wykluczone z platformy aplikacji platformy uniwersalnej systemu Windows. Biblioteka statyczna zużywa składników środowiska wykonawczego systemu Windows i może utworzyć składników środowiska wykonawczego systemu Windows z pewnymi ograniczeniami.  
  
## <a name="creating-static-libraries"></a>Tworzenie biblioteki statyczne  
  
#### <a name="to-create-a-static-library-for-use-in-a-universal-windows-platform-app"></a>Do tworzenia biblioteki statycznej do użycia w aplikacji platformy uniwersalnej systemu Windows  
  
1.  Na pasku menu wybierz **pliku** > **nowy** > **projektu** > **puste biblioteki statycznej** dla uniwersalnych systemu Windows platformy aplikacji.  
  
2.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz pozycję **właściwości**. W **właściwości** na okna dialogowego **właściwości konfiguracji** > **ogólne** Ustaw obsługę aplikacji platformy uniwersalnej systemu Windows  **Tak**.  
  
3.  Na **właściwości konfiguracji** > **C/C++** ustaw **Consume** środowiska wykonawczego systemu Windows **rozszerzenia** do **Tak (/ZW)**.  
  
 Podczas kompilowania nowej biblioteki statyczne, jeśli wywołanie interfejsu API Win32, które jest wyłączone dla aplikacji platformy uniwersalnej systemu Windows, kompilator zgłosi błąd C3861, "Nie odnaleziono identyfikatora". Aby wyszukać alternatywną metodą jest obsługiwana w przypadku środowiska uruchomieniowego systemu Windows, temacie [alternatywy dla interfejsów API systemu Windows w aplikacjach w Sklepie Windows](http://msdn.microsoft.com/en-us/75568012-61e0-41cc-a4df-c698f54f21ec).  
  
 Jeśli dodasz projektu biblioteki statycznej C++ do rozwiązania aplikacji platformy uniwersalnej systemu Windows, może być konieczne zaktualizowanie ustawień właściwości projektu biblioteki, tak aby właściwość pomocy technicznej platformy uniwersalnej systemu Windows jest ustawiona na **tak**. Bez tego ustawienia kompilacji kodu i linki, ale wystąpił błąd występuje, gdy użytkownik podejmie próbę Sprawdź aplikacji dla [!INCLUDE[win8_appstore_long](../cppcx/includes/win8-appstore-long-md.md)]. Statycznej lib powinna być skompilowana z tymi samymi ustawieniami kompilatora jako projekt, który wykorzystuje go.  
  
 Jeśli korzystać bibliotekę statyczną, która tworzy publiczny `ref` klasy, klasy interfejs publiczny lub klasy wartość publicznego konsolidator zgłasza to ostrzeżenie:  
  
> **Ostrzeżenie LNK4264:** archiwizowanie pliku obiektu skompilowanego z parametrem /ZW do biblioteki statycznej; należy pamiętać, że podczas tworzenia typów środowiska wykonawczego systemu Windows nie zaleca się połączyć z biblioteką statyczną zawierającą metadane środowiska wykonawczego systemu Windows.  
  
 Można bezpiecznie zignorować to ostrzeżenie, tylko wtedy, gdy biblioteka statyczna nie wytwarza składników środowiska wykonawczego systemu Windows, które są używane poza samej biblioteki. Jeśli biblioteka nie korzystać składnik, który definiuje, następnie konsolidator zoptymalizować optymalizacji wdrożenia nawet publicznego metadane zawierają informacje o typie. Oznacza to, że składniki publicznego w bibliotece statycznej zostanie skompilowany, ale nie będą aktywowane w czasie wykonywania. Z tego powodu jakikolwiek składnik środowiska wykonawczego systemu Windows jest przeznaczony do użytku przez inne składniki lub aplikacji musi być implementowana w biblioteki dołączanej (dynamicznie DLL).  
  
## <a name="see-also"></a>Zobacz też  
 [Wątkowość i organizowanie](../cppcx/threading-and-marshaling-c-cx.md)