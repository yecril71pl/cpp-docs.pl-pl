---
title: "Różnice w programowaniu Windows Forms MFC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], compared to MFC
ms.assetid: f3bfcf45-cfd4-45a4-8cde-5f4dbb18ee51
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 696e7684eb91abbf41e3f7a2e1df20b6fa7e5c17
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="windows-formsmfc-programming-differences"></a>Różnice w programowaniu Windows Forms/MFC
Tematy w [za pomocą formantu użytkownika formularza systemu Windows w MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md) opisano Obsługa MFC dla formularzy systemu Windows. Jeśli nie masz doświadczenia z .NET Framework lub programowania MFC, ten temat zawiera informacje dotyczące programowania różnice między nimi.  
  
 Formularze systemu Windows jest przy tworzeniu aplikacji Microsoft Windows w programie .NET Framework. Ta struktura zawiera zestaw nowoczesny zorientowany obiektowo, extensible klas, które umożliwiają tworzenie zaawansowanych aplikacji opartych na systemie Windows. W przypadku formularzy systemu Windows jest możliwe do utworzenia aplikacji wzbogaconego klienta, który można uzyskać dostępu do różnych źródeł danych i wyświetlania danych i edytowanie danych urządzeń za pomocą formantów formularzy systemu Windows.  
  
 Jednak jeśli użytkownik jest przyzwyczajony do MFC, możesz mogą być wykorzystane do tworzenia niektórych typów aplikacji, które nie są jeszcze jawnie obsługiwane w formularzach systemu Windows. Aplikacji formularzy systemu Windows są równoważne aplikacji okna dialogowego MFC. Jednak nie zapewniają infrastrukturę do bezpośrednio obsługi różnych typów aplikacji MFC, takich jak kontener serwera dokumentu OLE, dokumenty ActiveX, obsługa dokument/widok dla interfejsu pojedynczego dokumentu (SDI) interfejsu wielu dokumentów (MDI), a wiele interfejs najwyższego poziomu (MTI). Można napisać logiki do tworzenia tych aplikacji.  
  
 Aby uzyskać więcej informacji o aplikacji formularzy systemu Windows, zobacz [wprowadzenie do formularzy systemu Windows](/dotnet/framework/winforms/windows-forms-overview).  
  
 Dla przykładowej aplikacji, która zawiera formularze systemu Windows używana z MFC, zobacz [MFC i integracja z formularzy systemu Windows](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).  
  
 Następujące widoku MFC lub dokument i polecenia funkcje routingu nie mają swoich odpowiedników w formularzach systemu Windows:  
  
-   Integracja powłoki  
  
     MFC obsługuje dane dynamiczne exchange (DDE) polecenia i argumentów wiersza polecenia, których powłoki używa kliknij prawym przyciskiem myszy dokument i wybierz zleceń, takich jak otwieranie, edytować lub drukować. Formularze systemu Windows ma integracja nie powłoki i nie odpowiada na polecenia powłoki.  
  
-   Szablony dokumentów  
  
     W MFC szablonów dokumentów skojarzyć widoku, który znajduje się w oknie ramowym (w trybie MDI, SDI lub MTI), z otwartego dokumentu. Formularze systemu Windows nie ma odpowiednika w szablonach dokumentu.  
  
-   Dokumenty  
  
     MFC rejestruje typy plików dokumentów i procesów typu dokumentu, dokument jest otwierany z poziomu powłoki. Formularze systemu Windows ma Brak obsługi dokumentów.  
  
-   Stany dokumentu  
  
     MFC zachowuje zmiany stanów dla dokumentu. W związku z tym podczas Zamknij aplikację, zamknij ostatni widok, który zawiera aplikację lub wyjść z systemu Windows MFC wyświetli monit o zapisanie dokumentu. Formularze systemu Windows ma równoważne nie są obsługiwane.  
  
-   Polecenia  
  
     MFC korzysta z koncepcji poleceń. Pasek menu, paska narzędzi i menu kontekstowego wszystkie można wywołać tego samego polecenia, na przykład, wycinanie i kopiowanie. W formularzach systemu Windows polecenia są ściśle powiązane zdarzenia z określonego elementu interfejsu użytkownika (na przykład element menu); w związku z tym należy jawnie podpinanie zdarzeń polecenia. Można również obsługa wielu zdarzeń z jednym programem obsługi w formularzach systemu Windows. Aby uzyskać więcej informacji, zobacz [łączenie wielu zdarzeń pojedynczego obsługi zdarzeń w formularzach systemu Windows](/dotnet/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms).  
  
-   Routing poleceń  
  
     Routing poleceń MFC umożliwia aktywnego widoku lub dokument do przetwarzania poleceń. Ponieważ tego samego polecenia często ma inną funkcję dla różnych widoków (na przykład kopii zachowuje się inaczej w widoku edycji tekstu niż w edytorze grafiki), polecenia muszą być obsługiwani przez aktywnego widoku. Ponieważ formularzy systemu Windows menu i pasków narzędzi nie nie związanego z używaniem opis widoku aktywnego, nie może mieć inny program obsługi dla każdego typu widoku dla Twojego **MenuItem.Click** zdarzenia bez pisania dodatkowy kod wewnętrzny.  
  
-   Polecenie mechanizmu aktualizacji  
  
     MFC zawiera polecenie mechanizm aktualizacji. W związku z tym aktywnego widoku lub dokument jest odpowiedzialny za stan elementy interfejsu użytkownika (na przykład włączenie lub wyłączenie przycisku menu element lub narzędzia i sprawdzane stanów). Formularze systemu Windows nie ma odpowiednika mechanizmu aktualizacji polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie formantu użytkownika formularza systemu Windows w MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [Wskazówki dotyczące formularzy systemu Windows](http://msdn.microsoft.com/en-us/fd44d13d-4733-416f-aefc-32592e59e5d9)