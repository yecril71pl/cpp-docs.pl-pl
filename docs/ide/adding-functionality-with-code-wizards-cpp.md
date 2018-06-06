---
title: Dodawanie funkcji z użyciem kreatorów kodu (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.classes
dev_langs:
- C++
helpviewer_keywords:
- code wizards [C++]
- wizards [C++], code
- Visual C++ projects, adding functionality
- projects [C++], adding functionality
- class wizards [C++]
ms.assetid: 6afb7ef9-7056-423d-b244-91bb4236d1d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 55a2bb282d19a48cfd510056e327e7abca4de4ad
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33337044"
---
# <a name="adding-functionality-with-code-wizards-c"></a>Dodawanie funkcji z użyciem kreatorów kodu (C++)
Po utworzeniu projektu, można zmienić lub dodać do funkcji tego projektu. Takie zadania obejmują tworzenie nowych klas, dodawanie nowych funkcji Członkowskich i zmiennych i dodanie automatyzacji metody i właściwości. Kreatorzy kodów mają pozwalają na wykonywanie tych czynności.  
  
> [!NOTE]
>  Można teraz dodać programy obsługi wiadomości i mapowanie komunikatów do nich i przesłonić funkcje wirtualne MFC przy użyciu [okna właściwości](/visualstudio/ide/reference/properties-window).  
  
## <a name="accessing-visual-c-code-wizards"></a>Uzyskiwanie dostępu do kreatorów kodu języka Visual C++  
 Istnieją trzy miejsca, w której można uzyskać dostęp kreatorów kodu Visual C++:  
  
-   Na **projektu** menu **Dodaj nowy element** polecenie pozwala wyświetlić `Add New Item` okno dialogowe, które ułatwia dodawanie nowych plików do projektu. **Dodaj klasę** polecenie wyświetla [Dodaj klasę](../ide/add-class-dialog-box.md) okno dialogowe, które z kolei Otwórz kreatorów dla każdej klasy typów można dodać do projektu. **Dodawania zasobów** polecenie wyświetla [dodawania zasobów](../windows/add-resource-dialog-box.md) okno dialogowe, w którym można utworzyć lub wybrać zasobów do dodania do projektu.  
  
     Jeśli zaznaczysz klasę lub interfejs w projekcie w widoku klas **projektu** menu zawiera również następujące polecenia:  
  
    -   **Zaimplementuj interfejs** (z formantu klasy tylko)  
  
    -   **Add — funkcja**  
  
    -   **Dodaj zmienną**  
  
    -   **Dodawanie punktu połączenia** (tylko w przypadku klasy ATL)  
  
    -   **Dodaj metodę** (z interfejsu tylko)  
  
    -   **Dodaj właściwość** (z interfejsu tylko)  
  
    -   **Dodawanie zdarzeń** (z formantu klasy tylko)  
  
-   W **Eksploratora rozwiązań**, klikając prawym przyciskiem myszy w dowolnym folderze i klikając pozycję **Dodaj** ze skrótu menu umożliwia dodawanie nowych lub istniejących plików, folderów, elementy, klasy, zasobów i odwołania do sieci Web Projekt.  
  
-   Z [okno widoku klasy](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), klikając prawym przyciskiem myszy odpowiedni węzeł i klikając pozycję **Dodaj** ze skrótu menu pozwala dodać funkcje, zmienne, klas, właściwości, metody, zdarzenia, interfejsów, punkty połączenia, lub inny kod projektu.  
  
    > [!NOTE]
    >  Program Visual Studio nie udostępnia kreatora, aby dodać interfejs do projektu. Można dodać interfejs do Projekt ATL lub do [Dodawanie obsługi ATL do projektu MFC Your](../mfc/reference/adding-atl-support-to-your-mfc-project.md) przez dodawanie przy użyciu prostego obiektu [Kreator prostych obiektów ATL](../atl/reference/atl-simple-object-wizard.md). Alternatywnie Otwórz pliku .idl projektu i utworzyć interfejsu, wpisz:  
  
    ```  
    interface IMyInterface {  
    };  
  
    ```  
  
     Zobacz [implementującej interfejs](../ide/implementing-an-interface-visual-cpp.md) i [Dodawanie obiektów i kontroli w celu Projekt ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) Aby uzyskać więcej informacji.  
  
    |Kreator kodu dostępu z|Opis|  
    |-----------------------------|-----------------|  
    |Dodaj nowy element|Dodaj nowy element kodu kreatorów dodać pliki źródłowe do projektu. Jeśli to konieczne, dodatkowe katalogi są tworzone pliki, których aparatu kompilacji projektu oczekuje je znaleźć. Dostępne z ikony Dodaj element kreatorów kodu obejmują:<br /><br /> -Dodaj pliki źródłowe C++ (.cpp, .h, .idl, .rc, braku, .def, .rgs).<br />-Dodaj pliki Projektowanie sieci Web (HTML, .asp, CSS, .xml).<br />-Dodaj pliki narzędzi i zasobów (bmp, .cur, .ico, .rct —, SQL, txt).<br /><br /> Tych kreatorów kodu zazwyczaj nie monit o podanie informacji, ale Dodaj plik do Twojej rozwój drzewa. Może zmienić nazwy pliku w oknie właściwości.|  
    |Eksplorator rozwiązań|Dostępne w Eksploratorze rozwiązań kreatorów kodu zależą od tego, gdzie zespół kursora jest po kliknięciu prawym przyciskiem myszy element. Jeśli **Dodaj** opcja nie jest wyświetlana po kliknięciu prawym przyciskiem myszy element, następnie przenieś kursor w górę o jeden poziom w drzewie programowania i spróbuj ponownie. Kreatorzy kodów zawsze umieści dodatkowy kod w odpowiednim miejscu w drzewie programowania niezależnie gdzie kursor jest. Kreatorzy kodów dostępne w Eksploratorze rozwiązań obejmują:<br /><br /> -Dodaj klasę (otwiera **Dodaj klasę** okno dialogowe zawierające nowych kreatorów kodu).<br />-Dodaj zasób (nowe, importowanie lub niestandardowy).<br />-Dodaj odwołanie sieci Web.|  
    |Widok klas|Dostępne w widoku klasy kreatorów kodu zależą od tego, gdzie zespół kursora jest kliknięcie prawym przyciskiem myszy element. Jeśli **Dodaj** opcja nie jest wyświetlana po kliknięciu prawym przyciskiem myszy element, następnie przenieś kursor w górę o jeden poziom w drzewie klasy i spróbuj ponownie. Kreatorzy kodów zawsze umieści dodatkowy kod w odpowiednim miejscu w drzewie programowania niezależnie gdzie kursor jest. Kreatorzy kodów dostępne w widoku klas obejmują:<br /><br /> -   [Dodanie funkcji składowej](../ide/adding-a-member-function-visual-cpp.md).<br />-   [Dodawanie zmiennej członkowskiej](../ide/adding-a-member-variable-visual-cpp.md).<br />-   [Dodaj klasę](../ide/adding-a-class-visual-cpp.md).<br />-   [Zaimplementuj interfejs](../ide/implement-interface-wizard.md) (z formantu klasy tylko)<br />-   [Dodawanie punktu połączenia](../ide/implement-connection-point-wizard.md) (tylko w przypadku klasy ATL)<br />-   [Dodaj metodę](../ide/add-method-wizard.md) (z interfejsu tylko)<br />-   [Dodaj właściwość](../ide/names-add-property-wizard.md) (z interfejsu tylko)<br />-   [Dodawanie zdarzeń](../ide/add-event-wizard.md) (z formantu klasy tylko)<br /><br /> Otwiera wyboru Dodaj klasę **Dodaj klasę** okno dialogowe, które umożliwia dostęp do wszystkich nowych kreatorów kodu Dodaj klasę.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zastępowanie funkcji wirtualnych](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Nawigacja w strukturze klas](../ide/navigating-the-class-structure-visual-cpp.md)   
 [Tworzenie projektów pulpitu za pomocą kreatorów aplikacji](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Typy projektów Visual C++](../ide/visual-cpp-project-types.md)   
 [Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)