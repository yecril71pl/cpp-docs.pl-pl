---
title: 'Klienci automatyzacji: korzystanie z bibliotek typów'
ms.date: 11/04/2016
f1_keywords:
- MkTypLib
helpviewer_keywords:
- clients, Automation
- dispatch class [MFC]
- Automation clients, type libraries
- type libraries, Automation clients
- ODL (Object Description Language)
- ODL files
- classes [MFC], dispatch
- MkTypLib tool
- .odl files
ms.assetid: d405bc47-118d-4786-b371-920d035b2047
ms.openlocfilehash: e5f9ffcebc3725851c599e7b21369f45d0029d81
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626089"
---
# <a name="automation-clients-using-type-libraries"></a>Klienci automatyzacji: korzystanie z bibliotek typów

Klienci usługi Automation muszą mieć informacje o właściwościach obiektów serwera i metodach, jeśli klienci są do manipulowania obiektami serwerów. Właściwości mają typy danych; Metody często zwracają wartości i akceptują parametry. Klient wymaga informacji o typach danych wszystkich tych elementów, aby można było statycznie powiązać z typem obiektu serwera.

Informacje tego typu mogą być określane na kilka sposobów. Zalecanym sposobem jest utworzenie biblioteki typów.

Aby uzyskać informacje na temat [MkTypLib](/windows/win32/Midl/differences-between-midl-and-mktyplib), zobacz Windows SDK.

Visual C++ może odczytać plik biblioteki typów i utworzyć klasę wysyłania pochodną z [COleDispatchDriver](reference/coledispatchdriver-class.md). Obiekt tej klasy ma właściwości i operacje duplikowania tych obiektów serwera. Aplikacja wywołuje właściwości i operacje tego obiektu, a funkcje Odziedziczone po `COleDispatchDriver` kierowaniu tych wywołań do systemu OLE, które z kolei kierują do obiektu serwer.

Visual C++ automatycznie utrzymuje ten plik biblioteki typów, jeśli wybrano opcję dołączenia automatyzacji podczas tworzenia projektu. W ramach każdej kompilacji plik. tlb zostanie skompilowany przy użyciu MkTypLib.

### <a name="to-create-a-dispatch-class-from-a-type-library-tlb-file"></a>Aby utworzyć klasę wysyłania z pliku biblioteki typów (. tlb)

1. W Widok klasy lub Eksplorator rozwiązań, kliknij prawym przyciskiem myszy projekt, a następnie kliknij polecenie **Dodaj** , a następnie kliknij polecenie **Dodaj klasę** w menu skrótów.

1. W oknie dialogowym **Dodaj klasę** wybierz folder **Visual C++/MFC** w lewym okienku. W prawym okienku wybierz **klasę MFC z ikony TypeLib** , a następnie kliknij przycisk **Otwórz**.

1. W oknie dialogowym **Kreator dodawania klasy z biblioteki typów** wybierz bibliotekę typów z listy rozwijanej **dostępne biblioteki typów** . W polu **interfejsy** są wyświetlane interfejsy dostępne dla wybranej biblioteki typów.

    > [!NOTE]
    >  Można wybrać interfejsy z więcej niż jednej biblioteki typów.

   Aby wybrać interfejsy, kliknij je dwukrotnie lub kliknij przycisk **Dodaj** . W takim przypadku nazwy klas wysyłania będą wyświetlane w polu **wygenerowane klasy** . W polu można edytować nazwy klas `Class` .

   W polu **plik** zostanie wyświetlony plik, w którym zostanie zadeklarowana Klasa. (można edytować również tę nazwę pliku). Możesz również użyć przycisku Przeglądaj, aby wybrać inne pliki, jeśli wolisz, aby informacje o nagłówku i implementacji były zapisywane w istniejących plikach lub w katalogu innym niż katalog projektu.

    > [!NOTE]
    >  Wszystkie klasy wysyłania dla wybranych interfejsów zostaną umieszczone w pliku określonym w tym miejscu. Jeśli chcesz, aby interfejsy zostały zadeklarowane w oddzielnych nagłówkach, należy uruchomić tego kreatora dla każdego pliku nagłówkowego, który ma zostać utworzony.

    > [!NOTE]
    >  Niektóre informacje o bibliotece typów mogą być przechowywane w plikach z. DLL,. OCX lub. Rozszerzenia plików OLB.

1. Kliknij przycisk **Zakończ**.

   Następnie Kreator zapisze kod dla klas wysyłania przy użyciu określonych nazw klas i plików.

## <a name="see-also"></a>Zobacz też

[Klienci automatyzacji](automation-clients.md)
