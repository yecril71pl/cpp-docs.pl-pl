---
title: Dodawanie wielu widoków do pojedynczego dokumentu
ms.date: 11/04/2016
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
ms.openlocfilehash: 4fa39a4d9369c84d2cffdaeff28dc9cb2f966b31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370868"
---
# <a name="adding-multiple-views-to-a-single-document"></a>Dodawanie wielu widoków do pojedynczego dokumentu

W aplikacji interfejsu pojedynczego dokumentu (SDI) utworzonej za pomocą biblioteki Microsoft Foundation Class (MFC) każdy typ dokumentu jest skojarzony z jednym typem widoku. W niektórych przypadkach pożądane jest, aby mieć możliwość przełączania bieżącego widoku dokumentu z nowym widokiem.

> [!TIP]
> Aby uzyskać dodatkowe procedury dotyczące implementowania wielu widoków dla pojedynczego dokumentu, zobacz [CDocument::AddView](../mfc/reference/cdocument-class.md#addview) i [collect](../overview/visual-cpp-samples.md) MFC próbki.

Tę funkcję można zaimplementować, dodając nową `CView`klasę pochodną i dodatkowy kod do dynamicznego przełączania widoków do istniejącej aplikacji MFC.

Kroki tego procesu są następujące:

- [Modyfikowanie istniejącej klasy aplikacji](#vcconmodifyexistingapplicationa1)

- [Tworzenie i modyfikowanie klasy nowego widoku](#vcconnewviewclassa2)

- [Tworzenie i dołączanie nowego widoku](#vcconattachnewviewa3)

- [Zaimplementuj funkcję przełączania](#vcconswitchingfunctiona4)

- [Dodawanie obsługi przełączania widoku](#vcconswitchingtheviewa5)

W dalszej części tego tematu przyjęto następujące kwestie:

- Nazwa obiektu `CWinApp`pochodnego jest `CMyWinApp`, `CMyWinApp` i jest zadeklarowana i zdefiniowana w *MYWINAPP. H* i *MYWINAPP. CPP*.

- `CNewView`jest nazwą nowego `CView`obiektu pochodnego i `CNewView` jest zadeklarowana i zdefiniowana w *NEWVIEW. H* i *NEWVIEW. CPP*.

## <a name="modify-the-existing-application-class"></a><a name="vcconmodifyexistingapplicationa1"></a>Modyfikowanie istniejącej klasy aplikacji

Aby aplikacja przełączała się między widokami, należy zmodyfikować klasę aplikacji, dodając zmienne członkowskie do przechowywania widoków i metodę ich przełączania.

Dodaj poniższy kod do `CMyWinApp` deklaracji w *MYWINAPP. H*:

[!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]

Nowe zmienne członkowskie `m_pOldView` `m_pNewView`i , wskaż bieżący widok i nowo utworzony. Nowa metoda`SwitchView`( ) przełącza widoki na żądanie użytkownika. Treść metody jest omówiona w dalszej części tego tematu w [Implementowanie funkcji przełączania](#vcconswitchingfunctiona4).

Ostatnia modyfikacja klasy aplikacji wymaga łącznie z nowym plikiem nagłówka, który definiuje komunikat systemu Windows (**WM_INITIALUPDATE**), który jest używany w funkcji przełączania.

Wstaw następujący wiersz w sekcji dołączania *aplikacji MYWINAPP. CPP*:

[!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]

Zapisz zmiany i przejdź do następnego kroku.

## <a name="create-and-modify-the-new-view-class"></a><a name="vcconnewviewclassa2"></a>Tworzenie i modyfikowanie klasy nowego widoku

Tworzenie nowej klasy widoku jest łatwe za pomocą **polecenia Nowa klasa** dostępna w widoku klasy. Jedynym wymogiem dla tej klasy jest `CView`to, że pochodzi z . Dodaj tę nową klasę do aplikacji. Aby uzyskać szczegółowe informacje na temat dodawania nowej klasy do projektu, zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md).

Po dodaniu klasy do projektu, należy zmienić dostępność niektórych członków klasy widoku.

Modyfikuj *NEWVIEW. H* przez zmianę specyfikatora dostępu z **chronionego** na **publiczne** dla konstruktora i destruktora. Dzięki temu klasa ma być tworzone i niszczone dynamicznie i zmodyfikować wygląd widoku, zanim będzie widoczny.

Zapisz zmiany i przejdź do następnego kroku.

## <a name="create-and-attach-the-new-view"></a><a name="vcconattachnewviewa3"></a>Tworzenie i dołączanie nowego widoku

Aby utworzyć i dołączyć nowy widok, `InitInstance` należy zmodyfikować funkcję klasy aplikacji. Modyfikacja dodaje nowy kod, który tworzy nowy obiekt `m_pOldView` `m_pNewView` widoku, a następnie inicjuje zarówno i z dwóch istniejących obiektów widoku.

Ponieważ nowy widok jest `InitInstance` tworzony w ramach funkcji, zarówno nowe i istniejące widoki utrzymują się przez cały okres istnienia aplikacji. Jednak aplikacja może równie łatwo utworzyć nowy widok dynamicznie.

Wstaw ten kod `ProcessShellCommand`po wywołaniu:

[!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]

Zapisz zmiany i przejdź do następnego kroku.

## <a name="implement-the-switching-function"></a><a name="vcconswitchingfunctiona4"></a>Zaimplementuj funkcję przełączania

W poprzednim kroku dodano kod, który utworzył i zainicjował nowy obiekt widoku. Ostatnim ważnym elementem jest wdrożenie metody `SwitchView`przełączania, .

Na końcu pliku implementacji dla klasy aplikacji (*MYWINAPP. CPP*), należy dodać następującą definicję metody:

[!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]

Zapisz zmiany i przejdź do następnego kroku.

## <a name="add-support-for-switching-the-view"></a><a name="vcconswitchingtheviewa5"></a>Dodawanie obsługi przełączania widoku

Ostatnim krokiem jest dodanie kodu, który wywołuje `SwitchView` metodę, gdy aplikacja musi przełączać się między widokami. Można to zrobić na kilka sposobów: dodając nowy element menu dla użytkownika, aby wybrać lub przełączanie widoków wewnętrznie, gdy spełnione są określone warunki.

Aby uzyskać więcej informacji na temat dodawania nowych elementów menu i funkcji obsługi poleceń, zobacz [Programy obsługi poleceń i powiadomień sterujących](../mfc/handlers-for-commands-and-control-notifications.md).

## <a name="see-also"></a>Zobacz też

[Architektura dokumentu/widoku](../mfc/document-view-architecture.md)
