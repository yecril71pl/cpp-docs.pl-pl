---
title: Dodawanie funkcji za pomocą kreatorówC++kodu ()
ms.date: 05/14/2019
helpviewer_keywords:
- code wizards [C++]
ms.assetid: 6afb7ef9-7056-423d-b244-91bb4236d1d7
ms.openlocfilehash: cb77b2ce74f962df0a4c7472b037cb7a73effc2d
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077697"
---
# <a name="adding-functionality-with-code-wizards-c"></a>Dodawanie funkcji za pomocą kreatorówC++kodu ()

Po utworzeniu projektu, należy zmienić lub dodać do funkcji tego projektu. Takie zadania obejmują tworzenie nowych klas, dodawanie nowych funkcji i zmiennych składowych oraz dodawanie metod i właściwości automatyzacji. Kreatory kodu zaprojektowano w celu umożliwienia wykonania wszystkich tych czynności.

> [!NOTE]
> Następujące rzadko używane kreatory kodu są usuwane w programie Visual Studio 2019. Usunięcie tych kreatorów nie ma wpływu na ogólne wsparcie dla ATL i MFC. Przykładowy kod dla tych technologii jest archiwizowany w Microsoft Docs i repozytorium GitHub VCSamples.

- Kreator składników ATL COM+ 1.0
- Kreator składnika stron Active Server ATL
- Kreator dostawcy OLE DB ATL
- Kreator strony właściwości ATL
- Kreator OLE DB klienta ATL
- Odbiorca MFC ODBC
- Klasa MFC z kontrolki ActiveX
- Klasa MFC z typu lib.

> [!NOTE]
>  Można dodać programy obsługi komunikatów oraz zamapować do nich komunikaty i przesłonić funkcje wirtualne MFC przy użyciu [kreatora klas MFC](../mfc/reference/mfc-class-wizard.md).

## <a name="accessing-c-code-wizards"></a>Dostęp C++ do kreatorów kodu

Istnieją trzy lokalizacje, w których można uzyskać C++ dostęp do kreatorów kodu:

- W menu **projekt** polecenie **Dodaj nowy element** umożliwia wyświetlenie okna dialogowego `Add New Item`, które ułatwia dodawanie nowych plików do projektu. Polecenie **Dodaj klasę** wyświetla okno dialogowe [Dodawanie klasy](../ide/add-class-dialog-box.md) , które z kolei umożliwia otwieranie kreatorów dla każdego z typów klas, które można dodać do projektu. W przypadku klas MFC Użyj [kreatora klas MFC](../mfc/reference/mfc-class-wizard.md). Polecenie **Dodaj zasób** wyświetla okno dialogowe [Dodawanie zasobu](../windows/add-resource-dialog-box.md) , w którym można utworzyć lub wybrać zasób do dodania do projektu.

   W przypadku wyróżnienia klasy lub interfejsu w projekcie w Widok klasy, menu **projekt** zostanie również wyświetlone następujące polecenia:

   - **Implementuj interfejs** (tylko z klasy kontrolki)

   - **Dodaj funkcję**

   - **Dodaj zmienną**

   - **Dodaj punkt połączenia** (tylko Klasa ATL)

   - **Dodaj metodę** (tylko z interfejsu)

   - **Dodaj właściwość** (tylko z interfejsu)

   - **Dodaj zdarzenie** (tylko z klasy kontrolki)

- W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy dowolny folder i kliknij polecenie **Dodaj** z menu skrótów, aby dodać nowe lub istniejące pliki, więcej folderów, elementów, klas, zasobów i odwołań sieci Web do projektu.

- W [oknie widok klasy](/visualstudio/ide/viewing-the-structure-of-code)kliknij prawym przyciskiem myszy odpowiedni węzeł, a następnie kliknij polecenie **Dodaj** z menu skrótów umożliwia dodanie funkcji, zmiennych, klas, właściwości, metod, zdarzeń, interfejsów, punktów połączenia lub innego kodu do projektu.

   > [!NOTE]
   > Program Visual Studio nie udostępnia kreatora umożliwiającego dodanie interfejsu do projektu. Można dodać interfejs do projektu ATL lub do [dodawania obsługi ATL do projektu MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) przez dodanie prostego obiektu za pomocą [Kreatora prostych obiektów ATL](../atl/reference/atl-simple-object-wizard.md). Alternatywnie Otwórz plik. idl projektu i Utwórz interfejs, wpisując:

    ```IDL
    interface IMyInterface {
    };
    ```

   Aby uzyskać więcej informacji, zobacz [implementowanie interfejsu](../ide/implementing-an-interface-visual-cpp.md) i [Dodawanie obiektów i kontrolek do projektu ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) .

   |Dostęp do kreatora kodu z|Opis|
   |-----------------------------|-----------------|
   |Dodaj nowy element|Kreator Dodaj nowy kod elementu Dodaj pliki źródłowe do projektu. W razie potrzeby dodatkowe katalogi są tworzone w taki sposób, aby zawierały pliki, których oczekuje aparat kompilacji projektu. Kreatory kodu dostępne z ikony Dodaj element obejmują:<br /><br />-Dodaj C++ pliki źródłowe (. cpp,. h,. idl,. RC,. SRF,. def,. RGS).<br />-Dodaj pliki deweloperskie sieci Web (. html,. ASP,. CSS,. xml).<br />-Dodaj pliki narzędzi i zasobów (. bmp,. CUR,. ico,. rct,. SQL,. txt).<br /><br />Te kreatory kodu zwykle nie pytają o żadne informacje, ale dodają plik do drzewa deweloperskiego. Można zmienić nazwę pliku w oknie właściwości.|
   |Eksplorator rozwiązań|Kreatory kodu dostępne z Eksplorator rozwiązań zależą od tego, gdzie fokus kursora jest po kliknięciu prawym przyciskiem myszy elementu. Jeśli opcja **Dodaj** nie zostanie wyświetlona po kliknięciu prawym przyciskiem myszy elementu, Przenieś kursor w górę o jeden poziom w drzewie deweloperskim i spróbuj ponownie. Kreatory kodu zawsze umieszczają dodatkowy kod w odpowiednim miejscu w drzewie programistycznym, niezależnie od miejsca, w którym znajduje się kursor. Kreatory kodu dostępne z Eksplorator rozwiązań obejmują:<br /><br />-Dodaj klasę (otwiera okno dialogowe **Dodawanie klasy** zawierającej nowych kreatorów kodu).<br />-Dodaj zasób (nowy, importowany lub niestandardowy).<br />-Dodaj odwołanie sieci Web.|
   |Widok klas|Kreatory kodu dostępne z Widok klasy zależą od tego, gdzie fokus kursora jest po kliknięciu prawym przyciskiem myszy elementu. Jeśli opcja **Dodaj** nie jest wyświetlana po kliknięciu prawym przyciskiem myszy elementu, Przenieś kursor w górę o jeden poziom w drzewie klas i spróbuj ponownie. Kreatory kodu zawsze umieszczają dodatkowy kod w odpowiednim miejscu w drzewie programistycznym, niezależnie od miejsca, w którym znajduje się kursor. Kreatory kodu dostępne z Widok klasy obejmują:<br /><br />- [Dodaj funkcję członkowską](../ide/adding-a-member-function-visual-cpp.md).<br />- [dodać zmiennej składowej](../ide/adding-a-member-variable-visual-cpp.md).<br />- [Dodaj klasę](../ide/adding-a-class-visual-cpp.md).<br />- [Implementuj interfejs](../ide/implement-interface-wizard.md) (tylko z klasy kontrolki)<br />- [dodać punktu połączenia](../ide/implement-connection-point-wizard.md) (tylko Klasa ATL)<br />- [Dodaj metodę](../ide/add-method-wizard.md) (tylko z interfejsu)<br />- [Dodaj właściwość](../ide/names-add-property-wizard.md) (tylko z interfejsu)<br />- [dodać zdarzenia](../ide/add-event-wizard.md) (tylko z klasy kontrolki)<br /><br />Dodaj klasę wybór otwiera okno dialogowe **Dodaj klasę** , które zapewnia dostęp do wszystkich kreatorów dodawania kodu klasy.|

## <a name="see-also"></a>Zobacz też

[Zastępowanie funkcji wirtualnej](../ide/overriding-a-virtual-function-visual-cpp.md)<br>
[Nawigowanie C++ po bazie kodu w programie Visual Studio](../ide/navigate-code-cpp.md)<br>
[C++typy projektów w programie Visual Studio](../build/reference/visual-cpp-project-types.md)<br>
[Typy plików utworzone dla projektów programu C++ Visual Studio](../build/reference/file-types-created-for-visual-cpp-projects.md)
