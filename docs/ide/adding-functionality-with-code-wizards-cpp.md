---
title: Dodawanie funkcji za pomocą kreatorów kodu (C++)
ms.date: 05/14/2019
helpviewer_keywords:
- code wizards [C++]
ms.assetid: 6afb7ef9-7056-423d-b244-91bb4236d1d7
ms.openlocfilehash: ab0bf802221bcf3f93469f27f29f86c95877a407
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365331"
---
# <a name="adding-functionality-with-code-wizards-c"></a>Dodawanie funkcji za pomocą kreatorów kodu (C++)

Po utworzeniu projektu, należy zmienić lub dodać do funkcji tego projektu. Takie zadania obejmują tworzenie nowych klas, dodawanie nowych funkcji członkowskich i zmiennych oraz dodawanie metod automatyzacji i właściwości. Kreatory kodu są przeznaczone do umożliwienia wykonywania wszystkich tych rzeczy.

> [!NOTE]
> Następujące rzadko używane kreatory kodu są usuwane w programie Visual Studio 2019. Usunięcie tych kreatorów nie ma wpływu na ogólną obsługę atl i MFC. Przykładowy kod dla tych technologii został zarchiwizowany w witrynie Microsoft Docs i w repozytorium GitHub VCSamples.

- Kreator składników ATL COM+ 1.0
- Kreator składników aktywnych stron serwera ATL
- Kreator dostawcy interfejsu OLE DB ATL
- Kreator strony właściwości ATL
- Kreator konsumenta OLE DB ATL
- MFC ODBC Konsument
- Klasa MFC z formantu ActiveX
- Klasa MFC z typu Lib.

> [!NOTE]
> Można dodawać programy obsługi wiadomości i mapować do nich wiadomości oraz zastępować funkcje wirtualne MFC za pomocą [Kreatora klas MFC](../mfc/reference/mfc-class-wizard.md).

## <a name="accessing-c-code-wizards"></a>Uzyskiwanie dostępu do kreatorów kodu języka C++

Istnieją trzy lokalizacje, w których można uzyskać dostęp do kreatorów kodu języka C++:

- W menu **Projekt** polecenie **Dodaj nowy element** umożliwia `Add New Item` wyświetlenie okna dialogowego, które ułatwia dodawanie nowych plików do projektu. Polecenie **Dodaj klasę** wyświetla okno dialogowe Dodawanie [klasy,](../ide/add-class-dialog-box.md) które z kolei otwiera kreatorów dla każdego z typów klas, które można dodać do projektu. W przypadku klas MFC należy użyć [Kreatora klas MFC](../mfc/reference/mfc-class-wizard.md). Polecenie **Dodaj zasób** wyświetla okno dialogowe [Dodawanie zasobu,](../windows/add-resource-dialog-box.md) z którego można utworzyć lub wybrać zasób do dodania do projektu.

   Jeśli wyróżnisz klasę lub interfejs w projekcie w widoku klasy, w menu **Projekt** zostaną wyświetlone również następujące polecenia:

  - **Implementuj interfejs** (tylko z klasy kontrolnej)

  - **Dodaj funkcję**

  - **Dodaj zmienną**

  - **Dodaj punkt połączenia** (tylko klasa ATL)

  - **Dodaj metodę** (tylko z interfejsu)

  - **Dodaj właściwość** (tylko z interfejsu)

  - **Dodaj zdarzenie** (tylko z klasy kontrolnej)

- W **Eksploratorze rozwiązań**kliknięcie prawym przyciskiem myszy dowolnego folderu i kliknięcie polecenia **Dodaj** z menu skrótów umożliwia dodanie do projektu nowych lub istniejących plików, większej liczby folderów, elementów, klas, zasobów i odniesień do sieci Web.

- W [oknie Widok klasy](/visualstudio/ide/viewing-the-structure-of-code)kliknij prawym przyciskiem myszy odpowiedni węzeł i kliknij polecenie **Dodaj** z menu skrótów umożliwia dodawanie do projektu funkcji, zmiennych, klas, właściwości, metod, zdarzeń, interfejsów, punktów połączenia lub innego kodu.

   > [!NOTE]
   > Visual Studio nie udostępnia kreatora, aby dodać interfejs do projektu. Interfejs można dodać do projektu ATL lub do [obsługi klienta dodawania atl do projektu MFC,](../mfc/reference/adding-atl-support-to-your-mfc-project.md) dodając prosty obiekt za pomocą [Kreatora obiektów prostych obiektów ATL](../atl/reference/atl-simple-object-wizard.md). Alternatywnie otwórz plik .idl projektu i utwórz interfejs, wpisując:

    ```IDL
    interface IMyInterface {
    };
    ```

   Aby uzyskać więcej informacji, zobacz [Implementowanie interfejsu](../ide/implementing-an-interface-visual-cpp.md) i [dodawanie obiektów i formantów do projektu ATL.](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)

   |Kreator kodu dostępu z|Opis|
   |-----------------------------|-----------------|
   |Dodaj nowy element|Kreatorzy dodawania nowego kodu elementu dodają pliki źródłowe do projektu. W razie potrzeby tworzone są dodatkowe katalogi, aby zawierały pliki, w których aparat kompilacji projektu oczekuje ich znalezienia. Kreatory kodu dostępne na ikonie Dodaj element obejmują:<br /><br />- Dodaj pliki źródłowe C++ (.cpp, .h, .idl, .rc, .srf, .def, .rgs).<br />- Dodaj pliki programistyczne w sieci Web (.html, .asp, css, .xml).<br />- Dodaj pliki narzędzi i zasobów (.bmp, .cur, .ico, .rct, .sql, .txt).<br /><br />Te kreatory kodu zazwyczaj nie pytają o żadnych informacji, ale dodać plik do drzewa dewelopera. Można zmienić nazwę pliku w oknie właściwości.|
   |Eksplorator rozwiązań|Kreatory kodu dostępne w Eksploratorze rozwiązań zależą od tego, gdzie znajduje się fokus kursora po kliknięciu elementu prawym przyciskiem myszy. Jeśli opcja **Dodaj** nie jest wyświetlana po kliknięciu prawym przyciskiem myszy elementu, przesuń kursor o jeden poziom w górę o jeden poziom w drzewie rozwoju i spróbuj ponownie. Kreatorzy kodu zawsze umieszczają dodatkowy kod w odpowiednim miejscu w drzewie deweloperów, bez względu na to, gdzie znajduje się kursor. Kreatory kodu dostępne w Eksploratorze rozwiązań obejmują:<br /><br />- Dodaj klasę (otwiera okno dialogowe **Dodaj klasę** zawierające nowe kreatory kodu).<br />- Dodaj zasób (Nowy, Import lub Niestandardowy).<br />- Dodaj odwołanie do sieci Web.|
   |Widok klas|Kreatory kodu dostępne w widoku klasy zależą od tego, gdzie znajduje się fokus kursora po kliknięciu prawym przyciskiem myszy elementu. Jeśli opcja **Dodaj** nie jest wyświetlana po kliknięciu prawym przyciskiem myszy elementu, a następnie przenieś kursor o jeden poziom w górę w drzewie klas i spróbuj ponownie. Kreatorzy kodu zawsze umieszczają dodatkowy kod w odpowiednim miejscu w drzewie deweloperów, bez względu na to, gdzie znajduje się kursor. Kreatorzy kodu dostępni w widoku klasy obejmują:<br /><br />- [Dodaj funkcję elementu członkowskiego](../ide/adding-a-member-function-visual-cpp.md).<br />- [Dodaj zmienną elementu członkowskiego](../ide/adding-a-member-variable-visual-cpp.md).<br />- [Dodaj klasę](../ide/adding-a-class-visual-cpp.md).<br />- [Implementuj interfejs](../ide/implement-interface-wizard.md) (tylko z klasy kontrolnej)<br />- [Dodaj punkt połączenia](../ide/implement-connection-point-wizard.md) (tylko klasa ATL)<br />- [Dodaj metodę](../ide/add-method-wizard.md) (tylko z interfejsu)<br />- [Dodaj właściwość](../ide/names-add-property-wizard.md) (tylko z interfejsu)<br />- [Dodaj zdarzenie](../ide/add-event-wizard.md) (tylko z klasy kontrolnej)<br /><br />Wybór Dodaj klasę otwiera okno dialogowe **Dodawanie klasy,** które daje dostęp do wszystkich nowych kreatorów kodu dodaj klasę.|

## <a name="see-also"></a>Zobacz też

[Zastępowanie funkcji wirtualnej](../ide/overriding-a-virtual-function-visual-cpp.md)<br>
[Poruszanie się po bazie kodu języka C++ w programie Visual Studio](../ide/navigate-code-cpp.md)<br>
[Typy projektów języka C++ w programie Visual Studio](../build/reference/visual-cpp-project-types.md)<br>
[Typy plików utworzone dla projektów programu Visual Studio C++](../build/reference/file-types-created-for-visual-cpp-projects.md)
