---
title: Testowanie właściwości i zdarzeń za pomocą kontenera testu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- testing, test containers
- tstcon32.exe
- debugging ActiveX controls
- test container
- ActiveX Control Test Container
- ActiveX controls [MFC], testing
- properties [MFC], testing
ms.assetid: 626867cf-fe53-4c30-8973-55bb93ef3917
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b00eb755ef0fba0037df8c6d1e99bfd25d13b263
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078417"
---
# <a name="testing-properties-and-events-with-test-container"></a>Testowanie właściwości i zdarzeń za pomocą kontenera testu

Aplikacja kontenera testu, w programie Visual C++, jest kontener formantu ActiveX, testowanie i debugowanie kontrolki ActiveX. Kontener testu umożliwia deweloperowi kontroli w celu przetestowania funkcjonalności formantu przez zmianę jej właściwości, wywoływania jego metody i wyzwalanie jego zdarzeń. Kontener testu można wyświetlać dzienniki powiadomień powiązanie danych, a także udostępnia funkcje służące do testowania funkcji trwałości formantu ActiveX: Zapisz właściwości do strumienia lub substorage, ich ładować ponownie i sprawdzanie danych przechowywanych w usłudze stream. W tej sekcji opisano sposób korzystania z podstawowych funkcji kontener testu. Aby uzyskać dodatkowe informacje, wybierz **pomocy** menu podczas uruchamiania kontenera testowego.

### <a name="to-access-the-activex-control-test-container"></a>Aby uzyskać dostęp kontener testu kontrolki ActiveX

1. Tworzenie [TSTCON próbki: Kontener testu kontrolki ActiveX](../visual-cpp-samples.md).

### <a name="to-test-your-activex-control"></a>Aby przetestować formant ActiveX

1. Na **Edytuj** kliknij menu Kontener testu **Wstaw nową kontrolkę**.

1. W **Wstawianie formantu** polu, wybierz odpowiednią kontrolkę i kliknij przycisk **OK**. Formant, pojawi się w kontenerze kontrolek.

    > [!NOTE]
    >  Jeśli formant nie znajduje się w **Wstawianie formantu** okna dialogowego pole, upewnij się, zarejestrowano je przy użyciu **Zarejestruj formanty** polecenia **pliku** menu Test Kontener.

W tym momencie można przetestować kontroli nad właściwości lub zdarzenia.

#### <a name="to-test-properties"></a>Aby przetestować właściwości

1. Na **kontroli** menu, kliknij przycisk **wywołania metody**.

1. W **nazwę metody** listy rozwijanej wybierz metodę PropPut właściwość, którą chcesz przetestować.

1. Modyfikowanie **wartość parametru** lub **typ parametru** i kliknij pozycję **ustaw wartość** przycisku.

1. Kliknij przycisk **Invoke** zastosować nową wartość do obiektu.

   Ta właściwość zawiera teraz nowe wartości.

#### <a name="to-test-events-and-specify-the-destination-of-event-information"></a>Aby przetestować zdarzenia i określ miejsce docelowe informacji o zdarzeniach.

1. Na **opcje** menu, kliknij przycisk **rejestrowania**.

1. Określ miejsce docelowe informacji o zdarzeniach.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Instrukcje: debugowanie kontrolki ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)

