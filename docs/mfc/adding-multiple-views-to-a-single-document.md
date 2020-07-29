---
title: Dodawanie wielu widoków do pojedynczego dokumentu
ms.date: 11/04/2016
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
ms.openlocfilehash: 95de3a582c3d45db858e2b4bce0268e1dab63931
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215975"
---
# <a name="adding-multiple-views-to-a-single-document"></a>Dodawanie wielu widoków do pojedynczego dokumentu

W aplikacji interfejsu jednostronicowego (SDI) utworzonej za pomocą biblioteki Microsoft Foundation Class (MFC) każdy typ dokumentu jest skojarzony z pojedynczym typem widoku. W niektórych przypadkach należy mieć możliwość przełączenia bieżącego widoku dokumentu z nowym widokiem.

> [!TIP]
> Aby uzyskać dodatkowe procedury dotyczące implementowania wielu widoków dla pojedynczego dokumentu, zobacz [CDocument:: AddView](reference/cdocument-class.md#addview) i [Collect](../overview/visual-cpp-samples.md) MFC Sample.

Możesz zaimplementować tę funkcję, dodając nową `CView` klasę pochodną i dodatkowy kod służący do dynamicznego przełączania widoków do istniejącej aplikacji MFC.

Kroki tego procesu są następujące:

- [Modyfikowanie istniejącej klasy aplikacji](#vcconmodifyexistingapplicationa1)

- [Tworzenie i modyfikowanie nowej klasy widoku](#vcconnewviewclassa2)

- [Utwórz i Dołącz nowy widok](#vcconattachnewviewa3)

- [Implementowanie funkcji przełączania](#vcconswitchingfunctiona4)

- [Dodawanie obsługi przełączania widoku](#vcconswitchingtheviewa5)

W pozostałej części tego tematu założono następujące kwestie:

- Nazwa `CWinApp` obiektu pochodnego to `CMyWinApp` , i `CMyWinApp` jest zadeklarowana i zdefiniowana w *MyWinApp. H* i *MyWinApp. CPP*.

- `CNewView`jest nazwą nowego `CView` obiektu pochodnego i `CNewView` jest zadeklarowany i zdefiniowany w *NEWVIEW. H* i *NEWVIEW. CPP*.

## <a name="modify-the-existing-application-class"></a><a name="vcconmodifyexistingapplicationa1"></a>Modyfikowanie istniejącej klasy aplikacji

Aby aplikacja mogła przełączać się między widokami, należy zmodyfikować klasę aplikacji, dodając Zmienne Członkowskie do przechowywania widoków i metody w celu ich przełączenia.

Dodaj następujący kod do deklaracji `CMyWinApp` w *MyWinApp. H*:

[!code-cpp[NVC_MFCDocViewSDI#1](codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]

Nowe zmienne składowe `m_pOldView` i `m_pNewView` , wskazują bieżący widok i nowo utworzony. Nowa Metoda ( `SwitchView` ) Przełącza widoki na żądanie użytkownika. Treść metody została omówiona w dalszej części tego tematu w temacie [Implementowanie funkcji przełączania](#vcconswitchingfunctiona4).

Ostatnia modyfikacja klasy aplikacji wymaga uwzględnienia nowego pliku nagłówkowego, który definiuje komunikat systemu Windows (**WM_INITIALUPDATE**), który jest używany w funkcji przełączania.

Wstaw następujący wiersz w sekcji Include elementu *MyWinApp. CPP*:

[!code-cpp[NVC_MFCDocViewSDI#2](codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]

Zapisz zmiany i przejdź do następnego kroku.

## <a name="create-and-modify-the-new-view-class"></a><a name="vcconnewviewclassa2"></a>Tworzenie i modyfikowanie nowej klasy widoku

Tworzenie nowej klasy widoku jest łatwe przy użyciu **nowej klasy** polecenie dostępne w widok klasy. Jedynym wymaganiem dla tej klasy jest, że pochodzi on od `CView` . Dodaj tę nową klasę do aplikacji. Aby uzyskać szczegółowe informacje na temat dodawania nowej klasy do projektu, zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md).

Po dodaniu klasy do projektu należy zmienić dostępność niektórych elementów członkowskich klasy widoku.

Modyfikuj *NEWVIEW. H* przez zmianę specyfikatora dostępu z **`protected`** na **`public`** dla konstruktora i destruktora. Pozwala to na dynamiczne tworzenie i niszczenie klasy oraz modyfikowanie wyglądu widoku, zanim będzie widoczny.

Zapisz zmiany i przejdź do następnego kroku.

## <a name="create-and-attach-the-new-view"></a><a name="vcconattachnewviewa3"></a>Utwórz i Dołącz nowy widok

Aby utworzyć i dołączyć nowy widok, należy zmodyfikować `InitInstance` funkcję klasy aplikacji. Modyfikacja dodaje nowy kod, który tworzy nowy obiekt widoku, a następnie inicjuje oba `m_pOldView` i `m_pNewView` z dwoma istniejącymi obiektami widoku.

Ze względu na to, że nowy widok jest tworzony w ramach `InitInstance` funkcji, zarówno nowe, jak i istniejące widoki utrzymują się w okresie istnienia aplikacji. Aplikacja może jednak po prostu łatwo utworzyć nowy widok.

Wstaw ten kod po wywołaniu `ProcessShellCommand` :

[!code-cpp[NVC_MFCDocViewSDI#3](codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]

Zapisz zmiany i przejdź do następnego kroku.

## <a name="implement-the-switching-function"></a><a name="vcconswitchingfunctiona4"></a>Implementowanie funkcji przełączania

W poprzednim kroku został dodany kod, który utworzył i zainicjował nowy obiekt widoku. Ostatnim elementem głównym jest implementacja metody przełączania `SwitchView` .

Na końcu pliku implementacji dla klasy aplikacji (*MyWinApp. CPP*), Dodaj następującą definicję metody:

[!code-cpp[NVC_MFCDocViewSDI#4](codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]

Zapisz zmiany i przejdź do następnego kroku.

## <a name="add-support-for-switching-the-view"></a><a name="vcconswitchingtheviewa5"></a>Dodawanie obsługi przełączania widoku

Ostatni krok polega na dodaniu kodu, który wywołuje `SwitchView` metodę, gdy aplikacja musi przełączać się między widokami. Można to zrobić na kilka sposobów: dodając nowy element menu dla użytkownika, aby wybrać lub przełączyć widoki wewnętrznie w przypadku spełnienia określonych warunków.

Aby uzyskać więcej informacji na temat dodawania nowych elementów menu i funkcji programu obsługi poleceń, zobacz [programy obsługi dla poleceń i powiadomień o kontrolkach](handlers-for-commands-and-control-notifications.md).

## <a name="see-also"></a>Zobacz także

[Architektura dokumentu/widoku](document-view-architecture.md)
