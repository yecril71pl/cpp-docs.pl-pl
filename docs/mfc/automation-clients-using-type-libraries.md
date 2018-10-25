---
title: 'Klienci automatyzacji: Korzystanie z bibliotek typów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MkTypLib
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 001dfb29a5ac0f6d93b0715bd2b86ccd60e91259
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054608"
---
# <a name="automation-clients-using-type-libraries"></a>Klienci automatyzacji: korzystanie z bibliotek typów

Klienci automatyzacji muszą mieć informacji na temat właściwości i metod obiektów serwera, jeśli klienci znajdują się do manipulowania obiektami serwerów. Właściwości mają typy danych; metody często zwracać wartości i akceptuje parametrów. Klient wymaga informacji o typach danych wszystkich tych statycznie wiążącej typu obiektu serwera.

Informacje o tym typie może przedstawili na kilka sposobów. Zalecaną metodą jest, aby utworzyć bibliotekę typów.

Instrukcje dotyczące [z MkTypLib](/windows/desktop/Midl/differences-between-midl-and-mktyplib), zobacz dokumentację Windows SDK.

Visual C++ można odczytać pliku biblioteki typów oraz tworzyć wysyłania klasy pochodzącej od [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md). Obiekt tej klasy nie ma właściwości i operacje duplikowania udostępnianych przez obiekt serwera. Twoja aplikacja wywołuje właściwości tego obiektu i operacje i funkcje są dziedziczone z `COleDispatchDriver` kieruje te wywołania na system OLE, który z kolei kieruje je do obiektu serwera.

Jeśli wybrano automatyzacji podczas tworzenia projektu Visual C++ automatycznie przechowuje ten plik biblioteki typów dla Ciebie. W ramach każdej kompilacji zostanie utworzona pliku .tlb z mktyplib —.

### <a name="to-create-a-dispatch-class-from-a-type-library-tlb-file"></a>Aby utworzyć klasę wysyłania z pliku biblioteki typów (.tlb)

1. W widoku klas lub Eksploratora rozwiązań kliknij prawym przyciskiem myszy projekt, a następnie kliknij pozycję **Dodaj** a następnie kliknij przycisk **Dodaj klasę** w menu skrótów.

1. W **Dodaj klasę** okno dialogowe, wybierz opcję **Visual c + +/ MFC** folderu w okienku po lewej stronie. Wybierz **klasy MFC z biblioteki typów** ikonę w okienku po prawej stronie, a następnie kliknij **Otwórz**.

1. W **klasy z Typelib Kreatora dodawania** okna dialogowego Wybierz bibliotekę typów z **bibliotek typów dostępnych** listy rozwijanej. **Interfejsów** wyświetlone interfejsy, które są dostępne dla wybranej biblioteki typów.

    > [!NOTE]
    >  Możesz wybrać interfejsy z więcej niż jednej biblioteki typów.

   Wybierz interfejsy, kliknij je dwukrotnie lub kliknij przycisk **Dodaj** przycisku. Jeśli tak zrobisz, nazwy klas wysyłania pojawi się w **wygenerowane klasy** pole. Można edytować nazwy klasy w `Class` pole.

   **Pliku** wyświetlone pliku, w którym będzie można zadeklarować klasy. (można edytować tej nazwy pliku). Umożliwia także przycisk przeglądania i wybierz inne pliki, jeśli chcesz mieć nagłówkowy i implementacji informacje zapisane w istniejących plików lub w katalogu innym niż katalog projektu.

    > [!NOTE]
    >  Wszystkie klasy wysyłania dla wybranych interfejsów, będą umieszczone w pliku określonego w tym miejscu. Chcąc interfejsów deklaruje się w oddzielnych nagłówków, należy uruchomić tego kreatora dla każdego pliku nagłówka, który chcesz utworzyć.

    > [!NOTE]
    >  Niektóre informacje o typie biblioteki mogą być przechowywane w plikach za pomocą. BIBLIOTEKA DLL. OCX, lub. Rozszerzenia pliku OLB.

1. Kliknij przycisk **Zakończ**.

   Kreator zostanie następnie pisanie kodu dla swojej klasy wysyłania, przy użyciu określonej klasy i nazwy plików.

## <a name="see-also"></a>Zobacz też

[Klienci automatyzacji](../mfc/automation-clients.md)

