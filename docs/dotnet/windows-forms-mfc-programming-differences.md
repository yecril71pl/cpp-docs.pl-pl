---
title: Różnice w programowaniu Windows Forms-MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], compared to MFC
ms.assetid: f3bfcf45-cfd4-45a4-8cde-5f4dbb18ee51
ms.openlocfilehash: 136549bb457cc17293d4c7201c9836d9094eea94
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965551"
---
# <a name="windows-formsmfc-programming-differences"></a>Różnice w programowaniu Windows Forms/MFC

Tematy dotyczące [korzystania z kontrolki użytkownika formularza systemu Windows w MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md) opisują obsługę MFC dla Windows Forms. Jeśli nie masz doświadczenia z programowaniem .NET Framework lub MFC, ten temat zawiera ogólne informacje dotyczące różnic programistycznych między nimi.

Windows Forms służy do tworzenia aplikacji systemu Microsoft Windows na .NET Framework. Ta struktura zawiera nowoczesny, zorientowany obiektowo zestaw klas, które umożliwiają opracowywanie rozbudowanych aplikacji opartych na systemie Windows. Za pomocą Windows Forms można utworzyć rozbudowaną aplikację kliencką, która będzie mogła uzyskiwać dostęp do różnorodnych źródeł danych i zapewniać funkcje do wyświetlania danych i edytowania danych przy użyciu kontrolek Windows Forms.

Jeśli jednak użytkownik jest przyzwyczajony do MFC, może być używany do tworzenia niektórych typów aplikacji, które nie są jeszcze jawnie obsługiwane w Windows Forms. Aplikacje Windows Forms są równoważne z aplikacjami okna dialogowego MFC. Nie zapewniają jednak infrastruktury bezpośredniego obsługi innych typów aplikacji MFC, takich jak serwer dokumentów OLE/kontener, dokumenty ActiveX, Obsługa dokumentu/widoku dla interfejsu pojedynczego dokumentu (SDI), interfejs wielu dokumentów (MDI) i wiele interfejsów najwyższego poziomu (MTI). Można napisać własną logikę, aby utworzyć te aplikacje.

Aby uzyskać więcej informacji na temat aplikacji Windows Forms, zobacz [wprowadzenie do Windows Forms](/dotnet/framework/winforms/windows-forms-overview).

Aby uzyskać przykładową aplikację, która zawiera Windows Forms używane z MFC, zobacz [integrację MFC i Windows Forms](https://www.microsoft.com/download/details.aspx?id=2113).

Następujące funkcje widoku MFC lub dokumentu i poleceń routingu nie mają odpowiedników w Windows Forms:

- Integracja powłoki

   MFC obsługuje polecenia dynamicznej wymiany danych (DDE) i argumenty wiersza polecenia, które są używane przez powłokę po kliknięciu prawym przyciskiem myszy dokumentu i wybranie takich czasowników jako otwartych, edytować lub drukowania. Windows Forms nie ma integracji powłoki i nie odpowiada na czasowniki powłoki.

- Szablony dokumentów

   W MFC, szablony dokumentów kojarzą widok, który znajduje się w oknie ramki (w trybie MDI, SDI lub MTI), przy otwartym dokumencie. Windows Forms nie ma odpowiedników szablonów dokumentów.

- Dokumenty

   MFC rejestruje typy plików dokumentów i przetwarza typ dokumentu podczas otwierania dokumentu z powłoki. Windows Forms nie ma obsługi dokumentów.

- Stany dokumentu

   MFC zachowuje Stany zanieczyszczone dla dokumentu. W związku z tym po zamknięciu aplikacji Zamknij ostatni widok, który zawiera aplikację, lub Zakończ pracę z systemem Windows, MFC wyświetli komunikat z prośbą o zapisanie dokumentu. Windows Forms nie ma równoważnej pomocy technicznej.

- Polecenia

   MFC ma koncepcję poleceń. Pasek menu, pasek narzędzi i menu kontekstowe mogą wywołać to samo polecenie, na przykład Wytnij i Kopiuj. W Windows Forms polecenia są ściśle powiązane zdarzenia z określonego elementu interfejsu użytkownika (np. elementu menu); w związku z tym należy jawnie podłączyć wszystkie zdarzenia poleceń. Można również obsługiwać wiele zdarzeń za pomocą jednego programu obsługi w Windows Forms. Aby uzyskać więcej informacji, zobacz [łączenie wielu zdarzeń z jednym programem obsługi zdarzeń w Windows Forms](/dotnet/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms).

- Routing poleceń

   Routing poleceń MFC umożliwia przetwarzanie poleceń za pomocą aktywnego widoku lub dokumentu. Ponieważ to samo polecenie często ma inne znaczenie dla różnych widoków (na przykład kopiowanie zachowuje się inaczej w widoku edycji tekstu niż w edytorze grafiki), polecenia muszą być obsługiwane przez aktywny widok. Ponieważ Windows Forms menu i paski narzędzi nie są związane z tym widokiem aktywnym, nie można mieć innego programu obsługi dla każdego typu widoku dla elementu **MenuItem. kliknij pozycję** zdarzenia bez pisania dodatkowego kodu wewnętrznego.

- Mechanizm aktualizacji polecenia

   MFC ma mechanizm aktualizacji poleceń. W związku z tym aktywny widok lub dokument jest odpowiedzialny za stan elementów interfejsu użytkownika (na przykład Włączanie lub wyłączanie elementu menu lub przycisku narzędzia, a także opcji zaznaczone). Windows Forms nie jest odpowiednikiem mechanizmu aktualizacji poleceń.

## <a name="see-also"></a>Zobacz także

[Używanie kontrolki użytkownika formularza systemu Windows w MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)
