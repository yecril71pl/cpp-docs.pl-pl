---
title: Różnice w programie Windows Forms / MFC programowaniu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], compared to MFC
ms.assetid: f3bfcf45-cfd4-45a4-8cde-5f4dbb18ee51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e6bac12d841a065495f7775598c65f39a0aaba67
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394273"
---
# <a name="windows-formsmfc-programming-differences"></a>Różnice w programowaniu Windows Forms/MFC

Tematy w [za pomocą kontrolki użytkownika formularza Windows w MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md) opisują Obsługa MFC dla formularzy Windows Forms. Jeśli nie jesteś zaznajomiony z .NET Framework lub programowania MFC, ten temat zawiera informacje dotyczące programowania różnice między nimi.

Windows Forms służy do tworzenia aplikacji Windows firmy Microsoft dla programu .NET Framework. Ta struktura zawiera nowoczesnych, zorientowany obiektowo i rozszerzalny zestaw klas, które umożliwiają tworzenie rozbudowanych aplikacji z systemem Windows. Za pomocą interfejsu Windows Forms jesteś można tworzyć rozbudowane aplikacje klienckie mogą dostęp do wielu różnych źródeł danych i wyświetlania danych i edytowanie danych z urządzeń, za pomocą kontrolek Windows Forms.

Jednak jeśli użytkownik jest przyzwyczajony do MFC, użytkownik może służyć do tworzenia niektórych typów aplikacji, które nie są jeszcze jawnie obsługiwane w formularzach Windows Forms. Aplikacje Windows Forms są równoważne aplikacji okna dialogowego MFC. Jednak nie zapewniają infrastrukturę do bezpośrednio obsługi innych typów aplikacji MFC, takich jak kontener serwera dokumentów OLE, dokumenty ActiveX, obsługa dokument/widok interfejsu pojedynczego dokumentu (SDI) interfejsu wielu dokumentów (MDI), a wiele interfejs najwyższego poziomu (MTI). Można napisać własną logiką do tworzenia tych aplikacji.

Aby uzyskać więcej informacji o aplikacjach Windows Forms, zobacz [wprowadzenie do formularzy Windows Forms](/dotnet/framework/winforms/windows-forms-overview).

Dla przykładowej aplikacji, który pokazuje formularze Windows używane z biblioteką MFC, zobacz [MFC i integracji formularzy Windows](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).

Następujące widoku MFC lub dokumentu i funkcji routing poleceń ma odpowiedników w formularzach Windows:

- Integracja powłoki

     MFC obsługuje dynamiczne dane programu exchange (DDE) polecenia i argumentów wiersza polecenia, używanych przez powłokę, kliknij prawym przyciskiem myszy dokument i wybierz takie czasowniki jako Otwórz, edytować lub drukować. Formularze Windows ma integracja nie powłoki i nie odpowiada na polecenia powłoki.

- Szablony dokumentów

     W MFC szablonów dokumentów skojarzyć widok, w którym znajduje się w oknie ramowym (w trybie MDI, SDI lub MTI), z dokumentu, które zostało otwarte. Formularze Windows nie ma odpowiedników szablonów dokumentów.

- Dokumenty

     MFC, rejestruje typy plików dokumentów i procesów typu dokumentu, dokument jest otwierany z poziomu powłoki. Formularze Windows ma nie obsługuje dokumentów.

- Stany dokumentu

     MFC obsługuje zanieczyszczone stanów dla dokumentu. W związku z tym Zamknij aplikację, zamknij ostatni widok, który zawiera aplikację lub zakończenia z Windows MFC wyświetli monit o zapisanie dokumentu. Windows Forms zawiera równoważne obsługi.

- Polecenia

     MFC korzysta z koncepcji poleceń. Pasek menu, pasek narzędzi i menu kontekstowego wszystkie można wywołać tego samego polecenia, na przykład wycinanie i kopiowanie. W formularzach Windows Forms polecenia są ściśle powiązane zdarzenia z elementem interfejsu użytkownika (na przykład element menu); w związku z tym należy jawnie dołączyć wszystkie zdarzenia polecenia. Może również obsługiwać wielu zdarzeń z jednym programem obsługi w formularzach Windows Forms. Aby uzyskać więcej informacji, zobacz [łączenie wielu zdarzeń do jednego programu obsługi zdarzeń w formularzach Windows Forms](/dotnet/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms).

- Routing poleceń

     Routing poleceń MFC umożliwia bieżącym widokiem lub dokumentu do przetwarzania poleceń. Ponieważ to samo polecenie często ma różne znaczenie w różnych widokach (na przykład kopiowania zachowuje się inaczej w widoku do edycji tekstu niż w edytorze grafiki), polecenia, które muszą być obsługiwani przez widok aktywny. Ponieważ Windows Forms, menu i paski narzędzi wiedzę na temat nie związane z bieżącym widokiem, nie może mieć różne procedury obsługi dla każdego typu widoku dla Twojego **MenuItem.Click** zdarzeń bez tworzenia dodatkowego kodu wewnętrznego.

- Polecenie mechanizmu aktualizacji

     MFC posiada polecenia mechanizmu aktualizacji. W związku z tym widok aktywny lub dokument jest odpowiedzialny za stan elementów interfejsu użytkownika (na przykład, włączanie lub wyłączanie przycisku lub narzędzia elementu menu i sprawdzane stanów). Formularze Windows nie ma odpowiednika polecenia mechanizmu aktualizacji.

## <a name="see-also"></a>Zobacz też

[Używanie kontrolki użytkownika formularza systemu Windows w MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)
