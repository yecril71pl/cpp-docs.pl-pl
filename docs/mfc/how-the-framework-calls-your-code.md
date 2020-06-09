---
title: Jak struktura wywołuje kod
ms.date: 11/04/2016
helpviewer_keywords:
- control flow [MFC], MFC framework and your code
- events [MFC], command routing in MFC
- command routing [MFC], framework
- command handling [MFC], calling handlers and code in MFC
- events [MFC], event-driven programming
- MFC, calling code from
- MFC, calling code
- application-specific events [MFC]
- command routing [MFC], MFC
ms.assetid: 39e68189-a580-40d0-9e35-bf5cd24a8ecf
ms.openlocfilehash: 318ca9558d705ca483d41867a1fe2ad46c36666f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622607"
---
# <a name="how-the-framework-calls-your-code"></a>Jak struktura wywołuje kod

Ważne jest zrozumienie relacji między kodem źródłowym i kodem w strukturze MFC. Gdy aplikacja jest uruchomiona, większość przepływu sterowania znajduje się w kodzie struktury. Struktura zarządza pętlą komunikatów, która pobiera komunikaty z systemu Windows, gdy użytkownik wybierze polecenia i edytuje dane w widoku. Zdarzenia, które struktura może obsłużyć samodzielnie, nie polegają na kodzie. Na przykład struktura wie, jak zamknąć okna i jak wyjść z aplikacji w odpowiedzi na polecenia użytkownika. Ponieważ obsługuje te zadania, struktura używa programów obsługi komunikatów i wirtualnych funkcji języka C++, aby zapewnić możliwość reagowania na te zdarzenia. Kod nie jest jednak w kontroli; Struktura to.

Struktura wywołuje kod dla zdarzeń specyficznych dla aplikacji. Na przykład, gdy użytkownik wybierze polecenie menu, struktura kieruje polecenie wzdłuż sekwencji obiektów C++: bieżące okno widok i ramka, dokument skojarzony z widokiem, szablon dokumentu dokumentu i obiekt aplikacji. Jeśli jeden z tych obiektów może obsłużyć polecenie, wywołuje odpowiednią funkcję obsługi komunikatów. W przypadku dowolnego polecenia kod o nazwie może być własny lub być strukturą.

To rozwiązanie jest nieco znane programistom, którzy znają tradycyjne programowanie dla systemu Windows lub programowania opartego na zdarzeniach.

W pokrewnych tematach można przeczytać informacje o tym, co jest inicjowane przez platformę, i uruchomić aplikację, a następnie czyści, gdy aplikacja zakończy działanie. Zapoznaj się również z miejscem, w którym napisano kod.

Aby uzyskać więcej informacji, zobacz [Klasa CWinApp: Klasa aplikacji](cwinapp-the-application-class.md) oraz [Szablony dokumentów i proces tworzenia dokumentu/widoku](document-templates-and-the-document-view-creation-process.md).

## <a name="see-also"></a>Zobacz też

[Opieranie się na strukturze](building-on-the-framework.md)
