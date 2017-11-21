---
title: "Testowanie właściwości i zdarzeń za pomocą kontenera testu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- testing, test containers
- tstcon32.exe
- debugging ActiveX controls
- test container
- ActiveX Control Test Container
- ActiveX controls [MFC], testing
- properties [MFC], testing
ms.assetid: 626867cf-fe53-4c30-8973-55bb93ef3917
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 88b1240666c15601f4a003d0d021fd12dc039fe1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="testing-properties-and-events-with-test-container"></a>Testowanie właściwości i zdarzeń za pomocą kontenera testu
Kontener testu aplikacji, w programie Visual C++, jest kontenera formantu ActiveX, testowanie i debugowanie kontrolki ActiveX. Kontener testu umożliwia deweloperowi kontroli przetestować funkcje formantu przez zmianę jego właściwości, wywoływanie metod i wyzwalania jego zdarzenia. Kontener testu można wyświetlać dzienniki powiadomień wiązania z danymi i udostępnia również urządzenia do testowania funkcji trwałości formantu ActiveX: można zapisać właściwości do strumienia lub substorage, Załaduj ponownie je i sprawdzić dane przechowywane strumienia. Tej sekcji opisano sposób użycia podstawowych funkcji kontener testu. Aby uzyskać dodatkowe informacje, wybierz **pomocy** menu podczas wykonywania kontener testu.  
  
### <a name="to-access-the-activex-control-test-container"></a>Aby uzyskać dostęp kontener testu formantu ActiveX  
  
1.  Tworzenie [TSTCON próbki: Kontener testu formantu ActiveX](../visual-cpp-samples.md).  
  
### <a name="to-test-your-activex-control"></a>Aby przetestować formantu ActiveX  
  
1.  Na **Edytuj** kliknij menu Kontener testu **Wstaw nowy formant**.  
  
2.  W **Wstawianie formantu** polu Wybierz żądany sterowania i kliknij **OK**. Formant pojawi się w kontenerze formantu.  
  
    > [!NOTE]
    >  Jeśli formant nie ma na liście **Wstawianie formantu** okna dialogowego upewnij się, został zarejestrowany za pomocą **Zarejestruj formanty** polecenie **pliku** menu Test Kontener.  
  
 W tym momencie można przetestować, właściwości lub zdarzeń formantu.  
  
#### <a name="to-test-properties"></a>Aby przetestować właściwości  
  
1.  Na **kontroli** menu, kliknij przycisk **wywołania metody**.  
  
2.  W **nazwę metody** listy rozwijanej wybierz metodę PropPut dla właściwości mają zostać przetestowane.  
  
3.  Modyfikowanie **wartość parametru** lub **typ parametru** i wybierz polecenie **ustaw wartość** przycisku.  
  
4.  Kliknij przycisk **Invoke** można zastosować nową wartość do obiektu.  
  
     Ta właściwość zawiera teraz nową wartość.  
  
#### <a name="to-test-events-and-specify-the-destination-of-event-information"></a>Aby przetestować zdarzeń i określ miejsce docelowe zdarzeń informacji.  
  
1.  Na **opcje** menu, kliknij przycisk **rejestrowanie**.  
  
2.  Określ miejsce docelowe informacji o zdarzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Porady: debugowanie formantu ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)

