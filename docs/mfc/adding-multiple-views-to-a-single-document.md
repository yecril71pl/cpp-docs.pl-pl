---
title: Dodawanie wielu widoków do pojedynczego dokumentu
ms.date: 11/04/2016
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
ms.openlocfilehash: 593c59c73b58b4364c9d652ce8eb415c17af496c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394744"
---
# <a name="adding-multiple-views-to-a-single-document"></a>Dodawanie wielu widoków do pojedynczego dokumentu

W aplikacji interfejsu pojedynczego dokumentu (SDI) utworzone za pomocą biblioteki Microsoft Foundation Class (MFC) każdego typu dokumentu jest skojarzony z typem jednego widoku. W niektórych przypadkach jest pożądane, aby mieć możliwość przełączania bieżący widok dokumentu za pomocą nowego widoku.

> [!TIP]
>  Dodatkowe procedury dotyczące implementowania wielu widoków do pojedynczego dokumentu, zobacz [CDocument::AddView](../mfc/reference/cdocument-class.md#addview) i [ZBIERANIE](../overview/visual-cpp-samples.md) próbki MFC.

Możesz zaimplementować tę funkcję, dodając nowe `CView`-pochodne klasy i dodatkowy kod do przełączania widoków dynamicznie do istniejącej aplikacji MFC.

Dostępne są następujące czynności:

- [Modyfikowanie istniejącej klasy aplikacji](#vcconmodifyexistingapplicationa1)

- [Tworzenie i modyfikowanie nowa klasa widoku](#vcconnewviewclassa2)

- [Tworzenie i dołączanie nowego widoku](#vcconattachnewviewa3)

- [Implementowanie przełączania — funkcja](#vcconswitchingfunctiona4)

- [Dodawanie obsługi służącej do przełączania widoku](#vcconswitchingtheviewa5)

W pozostałej części tego tematu założono następujące czynności:

- Nazwa `CWinApp`— obiekt pochodnej jest `CMyWinApp`, i `CMyWinApp` jest deklarowane i definiowane w *MYWINAPP. H* i *MYWINAPP. CPP*.

- `CNewView` jest nazwą nowego `CView`-pochodnych obiektu i `CNewView` jest deklarowane i definiowane w *NEWVIEW. H* i *NEWVIEW. CPP*.

##  <a name="vcconmodifyexistingapplicationa1"></a> Modyfikowanie istniejącej klasy aplikacji

Dla aplikacji przełączać się między widokami musisz zmodyfikować klasy aplikacji przez dodanie elementu członkowskiego zmiennych do przechowywania widoków i metodę, aby przełączać je.

Dodaj następujący kod do deklaracji `CMyWinApp` w *MYWINAPP. H*:

[!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]

Nowe zmienne Członkowskie `m_pOldView` i `m_pNewView`, wskaż bieżący widok i nowo utworzony jeden. Metoda new (`SwitchView`) przełącza widoki zleconą przez użytkownika. Treść metody została omówiona w dalszej części tego tematu w [zaimplementowania funkcji przełączania](#vcconswitchingfunctiona4).

Ostatniej modyfikacji klasy aplikacji wymaga tym nowy plik nagłówkowy, który definiuje komunikat Windows (**WM_INITIALUPDATE**) używany w funkcji przełączania.

Wstaw następujący wiersz do sekcji Dołącz *MYWINAPP. CPP*:

[!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]

Zapisz zmiany i przejdź do następnego kroku.

##  <a name="vcconnewviewclassa2"></a> Tworzenie i modyfikowanie nowa klasa widoku

Tworzenie nowej klasy widoku umożliwiają łatwe za pomocą **nową klasę** polecenia dostępne w widoku klas. Jedynym wymaganiem dla tej klasy jest, że pochodzi od `CView`. Ta nowa klasa należy dodać do aplikacji. Aby uzyskać szczegółowe informacje na temat dodawania nowych klas do projektu, zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md).

Po dodaniu klasy do projektu, musisz zmienić dostępność niektórych członków klasy widoku.

Modyfikowanie *NEWVIEW. H* , zmieniając specyfikator dostępu z **chronione** do **publicznych** Konstruktor i destruktor. Dzięki temu klasy może zostać utworzona i zniszczona dynamicznie, a następnie zmodyfikować wygląd widoku przed udostępnieniem.

Zapisz zmiany i przejdź do następnego kroku.

##  <a name="vcconattachnewviewa3"></a> Tworzenie i dołączanie nowego widoku

Aby utworzyć i dołączyć nowy widok, należy zmodyfikować `InitInstance` funkcji klasy aplikacji. Modyfikacja dodaje nowy kod, który tworzy nowy obiekt widoku, a następnie inicjuje zarówno `m_pOldView` i `m_pNewView` za pomocą dwóch istniejących obiektów widoku.

Ponieważ nowy widok jest tworzony w ramach `InitInstance` funkcji, nowych i istniejących widoków utrzymują się okres istnienia aplikacji. Jednak aplikacja może równie łatwo można utworzyć nowy widok dynamicznie.

Wstaw ten kod po wywołaniu `ProcessShellCommand`:

[!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]

Zapisz zmiany i przejdź do następnego kroku.

##  <a name="vcconswitchingfunctiona4"></a> Implementowanie przełączania — funkcja

W poprzednim kroku dodano kod, który utworzone i zainicjowane nowy obiekt widoku. Ostatni element główne to aby wdrożyć metodę przełączania `SwitchView`.

Na końcu pliku implementacji dla swojej klasy aplikacji (*MYWINAPP. CPP*), dodaj następującą definicję metody:

[!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]

Zapisz zmiany i przejdź do następnego kroku.

##  <a name="vcconswitchingtheviewa5"></a> Dodawanie obsługi służącej do przełączania widoku

Ostatni krok polega na dodawaniu kodu, który wywołuje `SwitchView` metody, gdy aplikację Aby przełączać się między widokami. Można to zrobić na kilka sposobów: przez dodanie nowego elementu menu dla użytkownika o wybranie lub przełączanie widoków wewnętrznie, gdy są spełnione określone warunki.

Aby uzyskać więcej informacji na temat dodawania nowych elementów menu oraz funkcje programu obsługi poleceń, zobacz [programy obsługi dla poleceń i powiadomień dotyczących formantu karty](../mfc/handlers-for-commands-and-control-notifications.md).

## <a name="see-also"></a>Zobacz także

[Architektura dokument/widok](../mfc/document-view-architecture.md)
