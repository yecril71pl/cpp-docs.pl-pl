---
title: 'Klienci automatyzacji: Korzystanie z biblioteki typu | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 67fa0f5d164ae325caff576fb41695fc8689fda0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="automation-clients-using-type-libraries"></a>Klienci automatyzacji: korzystanie z bibliotek typów
Klienci automatyzacji musi mieć informacje dotyczące właściwości i metod obiektów serwera, jeżeli klienci są do manipulowania obiektami serwerach programu. Właściwości mają typy danych; metody często zwracać wartości i akceptują parametrów. Klient wymaga informacji o typach danych wszystkich tych statycznie powiązania z typem obiektu serwera.  
  
 Informacje o tym typie może się na kilka sposobów. Zalecaną metodą jest można utworzyć biblioteki typów.  
  
 Aby uzyskać informacje dotyczące [mktyplib —](http://msdn.microsoft.com/library/windows/desktop/aa366797), zobacz zestaw Windows SDK.  
  
 Visual C++ może odczytać pliku biblioteki typów i utworzenia pochodzi od klasy wysyłania [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md). Obiekt tej klasy nie ma właściwości i operacji duplikowania tych obiektu serwera. Aplikacja wymaga właściwości tego obiektu i operacje, i funkcji dziedziczone z `COleDispatchDriver` kieruje te wywołania OLE systemu, który z kolei kieruje je do obiektu serwera.  
  
 Visual C++ również automatycznie obsługuje ten plik biblioteki typów dla Ciebie w przypadku wybrania obejmują automatyzacji, gdy projekt został utworzony. W ramach każdej kompilacji pliku .tlb zostaną skompilowane z mktyplib —.  
  
### <a name="to-create-a-dispatch-class-from-a-type-library-tlb-file"></a>Aby utworzyć klasę wysyłania z pliku biblioteki typów (.tlb)  
  
1.  W widoku klas lub Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i kliknij przycisk **Dodaj** , a następnie kliknij przycisk **Dodaj klasę** menu skrótów.  
  
2.  W **Dodaj klasę** okno dialogowe, wybierz opcję **Visual c + +/ MFC** folderu w okienku po lewej stronie. Wybierz **klasy MFC z biblioteki typów** ikonę w prawym okienku, kliknij **Otwórz**.  
  
3.  W **klasy z Typelib Kreatora dodawania** oknie dialogowym Wybierz bibliotekę typów z **bibliotek typów dostępne** listy rozwijanej. **Interfejsów** w polu są wyświetlane interfejsy dostępne do wybranej biblioteki typów.  
  
    > [!NOTE]
    >  Możesz wybrać interfejsów z więcej niż jednej biblioteki typów.  
  
     Wybierz interfejsy, kliknij je dwukrotnie lub kliknij przycisk **Dodaj** przycisku. Po wykonaniu tej nazwy klas wysyłania będą wyświetlane w **wygenerowane klasy** pole. Można edytować nazwy klas w `Class` pole.  
  
     **Pliku** pliku, w którym będzie można zadeklarować klasy w polu są wyświetlane. (można edytować tej nazwy pliku). Umożliwia także przycisk Przeglądaj i wybierz inne pliki, jeśli wolisz nagłówka i implementacji informacje zapisane w istniejących plików lub w katalogu innym niż katalogu projektu.  
  
    > [!NOTE]
    >  Wszystkie klasy wysyłania wybrane interfejsy zostaną wprowadzone w pliku określonego w tym miejscu. Interfejsy mają zostać zadeklarowane w oddzielnych nagłówków, należy uruchomić tego kreatora dla każdego pliku nagłówka, którą chcesz utworzyć.  
  
    > [!NOTE]
    >  Niektóre informacje o typie biblioteki mogą być przechowywane w plikach z. BIBLIOTEKA DLL. OCX, lub. OLB rozszerzenia pliku.  
  
4.  Kliknij przycisk **Zakończ**.  
  
     Kreator zapisze następnie kod z klasy wysyłania, przy użyciu określonej klasy i nazwy pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Klienci automatyzacji](../mfc/automation-clients.md)

