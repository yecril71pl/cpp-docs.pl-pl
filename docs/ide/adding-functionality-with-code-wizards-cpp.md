---
title: Dodawanie funkcji za pomocą kreatorów kodu (C++) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 13d163ad8de9ef3ee6c8c1375c234a412c70de7d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213139"
---
# <a name="adding-functionality-with-code-wizards-c"></a>Dodawanie funkcji za pomocą kreatorów kodu (C++)
Po utworzeniu projektu można zmienić lub dodać do funkcji tego projektu. Takie zadania obejmują tworzenie nowych klas, dodając nowe funkcje Członkowskie i zmienne i Dodawanie metody automatyzacji i właściwości. Kreatorzy kodu są przeznaczone do pozwalają korzystać z tych możliwości.  
  
> [!NOTE]
>  Teraz możesz dodać procedury obsługi komunikatów i mapowanie komunikatów do nich i zastępują funkcje wirtualne MFC przy użyciu [okno właściwości](/visualstudio/ide/reference/properties-window).  
  
## <a name="accessing-visual-c-code-wizards"></a>Uzyskiwanie dostępu do kreatorów kodu Visual C++  
 Istnieją trzy lokalizacje, gdzie uzyskujesz dostęp kreatorów kodu Visual C++:  
  
-   Na **projektu** menu **Dodaj nowy element** polecenie umożliwia wyświetlenie `Add New Item` okno dialogowe, które ułatwia dodawanie nowych plików do projektu. **Dodaj klasę** polecenie wyświetla [Dodaj klasę](../ide/add-class-dialog-box.md) okno dialogowe, które z kolei Otwórz kreatorów, dla każdej klasy typów, możesz dodać do projektu. **Dodaj zasób** polecenie wyświetla [Dodaj zasób](../windows/add-resource-dialog-box.md) okno dialogowe, w którym można utworzyć lub wybrać zasób, aby dodać do projektu.  
  
     Jeśli zaznacz klasę lub interfejs, w projekcie w widoku klas **projektu** menu zawiera również następujące polecenia:  
  
    -   **Implementuj interfejs** (sterowania tylko z klasy)  
  
    -   **Dodaj funkcję**  
  
    -   **Dodaj zmienną**  
  
    -   **Dodaj punkt połączenia z** (tylko w przypadku klasy ATL)  
  
    -   **Dodaj metodę** (z interfejsu tylko)  
  
    -   **Dodaj właściwość** (z interfejsu tylko)  
  
    -   **Dodaj zdarzenie** (sterowania tylko z klasy)  
  
-   W **Eksploratora rozwiązań**, klikając prawym przyciskiem myszy dowolny folder i klikając pozycję **Dodaj** za pomocą skrótu menu pozwala na dodawanie nowych lub istniejących plików, folderów, elementy, klasy, zasoby i odwołania do sieci Web Projekt.  
  
-   Z [okna widoku klasy](https://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925), klikając prawym przyciskiem myszy odpowiedni węzeł i klikając pozycję **Dodaj** za pomocą skrótu menu pozwala na dodawanie funkcje, zmienne, klas, właściwości, metody, zdarzenia, interfejsy punkty połączenia lub innego kodu do projektu.  
  
    > [!NOTE]
    >  Program Visual Studio nie udostępnia kreatora, aby dodać interfejs do projektu. Można dodać interfejs do projektu ATL lub do [Dodawanie obsługi ATL do projektu MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) przez dodanie przy użyciu prostego obiektu [proste Kreator obiektu ATL](../atl/reference/atl-simple-object-wizard.md). Alternatywnie Otwórz pliku .idl projektu i Utwórz interfejs, wpisując:  
  
    ```  
    interface IMyInterface {  
    };  
  
    ```  
  
     Zobacz [implementującej interfejs](../ide/implementing-an-interface-visual-cpp.md) i [Dodawanie obiektów i kontrolek do projektu ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) Aby uzyskać więcej informacji.  
  
    |Kod dostępu do Kreatora|Opis|  
    |-----------------------------|-----------------|  
    |Dodaj nowy element|Dodaj nowy element kreatorów kodu Dodaj pliki źródłowe do projektu. Jeśli to konieczne, dodatkowe katalogi są tworzone ma zawierać pliki, w którym aparat kompilacji projektu spodziewa się je znaleźć. Dostępne z ikony elementu Dodawanie kreatorów kodu, obejmują:<br /><br /> -Dodaj pliki źródłowe C++ (.cpp, .h, .idl, .rc, .srf, .def, .rgs).<br />-Dodaj pliki programowanie sieci Web (HTML, .asp, CSS, .xml).<br />— Dodawanie plików narzędzi i zasobów (.bmp, .cur, .ico, .rct, .sql, txt).<br /><br /> Tych kreatorów kodu zwykle nie monit o podanie informacji, ale Dodaj plik do drzewa Twojego rozwoju. Może zmienić nazwy pliku w oknie właściwości.|  
    |Eksplorator rozwiązań|Dostępne z Eksploratora rozwiązań, kreatorów kodu, zależą od tego, gdzie fokus kursora jest po kliknięciu prawym przyciskiem myszy element. Jeśli **Dodaj** opcja nie jest wyświetlana po kliknięciu prawym przyciskiem myszy element, przesuń kursor góry o jeden poziom w drzewie programowania, a następnie spróbuj ponownie. Kreatorów kodu będzie zawsze umieszczaj dodatkowy kod w odpowiednim miejscu w drzewie programowania niezależnie od tego przypadku kursor. Kreatorzy kodu jest dostępny w Eksploratorze rozwiązań, obejmują:<br /><br /> -Dodaj klasę (otwiera **Dodaj klasę** okno dialogowe zawierające nowe kreatorów kodu).<br />— Dodawanie zasobów (nowa, Import lub niestandardowe).<br />-Dodaj odwołanie sieci Web.|  
    |Widok klas|Dostępne w widoku klas kreatorów kodu, zależą od tego, gdzie fokus kursora jest kliknięcie prawym przyciskiem myszy element. Jeśli **Dodaj** opcja nie jest wyświetlana po kliknięciu prawym przyciskiem myszy element, przesuń kursor góry o jeden poziom w drzewie klasy, a następnie spróbuj ponownie. Kreatorów kodu będzie zawsze umieszczaj dodatkowy kod w odpowiednim miejscu w drzewie programowania niezależnie od tego przypadku kursor. Kreatorzy kodu jest dostępny w widoku klas obejmują:<br /><br /> -   [Dodaj funkcję członkowską](../ide/adding-a-member-function-visual-cpp.md).<br />-   [Dodaj zmienną składową](../ide/adding-a-member-variable-visual-cpp.md).<br />-   [Dodaj klasę](../ide/adding-a-class-visual-cpp.md).<br />-   [Implementuj interfejs](../ide/implement-interface-wizard.md) (sterowania tylko z klasy)<br />-   [Dodaj punkt połączenia z](../ide/implement-connection-point-wizard.md) (tylko w przypadku klasy ATL)<br />-   [Dodaj metodę](../ide/add-method-wizard.md) (z interfejsu tylko)<br />-   [Dodaj właściwość](../ide/names-add-property-wizard.md) (z interfejsu tylko)<br />-   [Dodaj zdarzenie](../ide/add-event-wizard.md) (sterowania tylko z klasy)<br /><br /> Wybór Dodaj klasę spowoduje otwarcie **Dodaj klasę** okno dialogowe, które umożliwia dostęp do wszystkich nowych kreatorów kodu Dodaj klasę.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zastępowanie funkcji wirtualnych](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Nawigacja w strukturze klas](../ide/navigating-the-class-structure-visual-cpp.md)   
 [Tworzenie projektów pulpitu za pomocą kreatorów aplikacji](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Typy projektów Visual C++](../ide/visual-cpp-project-types.md)   
 [Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)