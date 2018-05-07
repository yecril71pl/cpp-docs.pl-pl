---
title: Dodawanie wielu widoków do pojedynczego dokumentu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb40b356b5601e19c33083c7b731a1dc411de3c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="adding-multiple-views-to-a-single-document"></a>Dodawanie wielu widoków do pojedynczego dokumentu
W aplikacji interfejsu pojedynczego dokumentu (SDI) utworzone za pomocą biblioteki Microsoft Foundation Class (MFC) każdego typu dokumentu jest skojarzona z typem jednego widoku. W niektórych przypadkach jest pożądane, aby mieć możliwość zmiany w bieżącym widoku dokumentu nowy widok.  
  
> [!TIP]
>  Dodatkowe procedury dotyczące implementacji wielu widoków do pojedynczego dokumentu, zobacz [CDocument::AddView](../mfc/reference/cdocument-class.md#addview) i [ZBIERANIE](../visual-cpp-samples.md) próbki MFC.  
  
 Można zaimplementować tę funkcję, dodając nową `CView`-pochodzi z klasy i dodatkowego kodu do przełączania widoków dynamicznie do istniejącej aplikacji MFC.  
  
 Dostępne są następujące kroki:  
  
-   [Modyfikowanie istniejącej klasy aplikacji](#vcconmodifyexistingapplicationa1)  
  
-   [Tworzenie i modyfikowanie nowej klasy widoku](#vcconnewviewclassa2)  
  
-   [Utwórz i Dołącz nowy widok](#vcconattachnewviewa3)  
  
-   [Implementowanie funkcji przełączania](#vcconswitchingfunctiona4)  
  
-   [Dodawanie obsługi do przełączania widoku](#vcconswitchingtheviewa5)  
  
 W pozostałej części tego tematu założono następujące czynności:  
  
-   Nazwa `CWinApp`-obiekt pochodnej jest `CMyWinApp`, i `CMyWinApp` został zadeklarowany i zdefiniowanych w MYWINAPP. H i MYWINAPP. CPP.  
  
-   `CNewView` Nazwa nowej `CView`— pochodnych obiektu, i `CNewView` został zadeklarowany i zdefiniowanych w nowy widok. H i nowy widok. CPP.  
  
##  <a name="vcconmodifyexistingapplicationa1"></a> Modyfikowanie istniejącej klasy aplikacji  
 Dla aplikacji w celu przełączania się między widokami należy zmodyfikować klasy aplikacji przez dodanie zmienne Członkowskie do przechowywania widoków i metody, aby przełączyć je.  
  
 Dodaj następujący kod do deklaracji `CMyWinApp` w MYWINAPP. H:  
  
 [!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]  
  
 Nowe zmienne Członkowskie `m_pOldView` i `m_pNewView`, wskaż bieżącego widoku i nowo utworzony jeden. Metoda new (`SwitchView`) przełącza widoki zleconą przez użytkownika. Treść metody została szczegółowo opisana w dalszej części tego tematu w [wdrożenie funkcją przełączania](#vcconswitchingfunctiona4).  
  
 Ostatniej modyfikacji klasy aplikacji wymaga w tym nowy plik nagłówka, który definiuje komunikatów systemu Windows (**WM_INITIALUPDATE**) używany w funkcji przełączania.  
  
 Wstaw następujący wiersz w sekcji Dołącz MYWINAPP. CPP:  
  
 [!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]  
  
 Zapisz zmiany i przejdź do następnego kroku.  
  
##  <a name="vcconnewviewclassa2"></a> Tworzenie i modyfikowanie nowej klasy widoku  
 Tworzenie nowej klasy widok łatwej przy użyciu **nowa klasa** polecenia dostępne w widoku klasy. Jedynym wymaganiem dla tej klasy jest pochodzi od `CView`. Ta nowa klasa należy dodać do aplikacji. Aby uzyskać szczegółowe informacje na temat dodawania nowych klas do projektu, zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md).  
  
 Po dodaniu klasy do projektu, trzeba będzie zmienić dostępność niektóre elementy członkowskie klasy widoku.  
  
 Zmodyfikuj nowy widok. H, zmieniając specyfikator dostępu z `protected` do **publicznego** Konstruktor i destruktor. Dzięki temu klasy tworzone i niszczone dynamicznie, a następnie zmodyfikować wygląd widoku przed udostępnieniem go.  
  
 Zapisz zmiany i przejdź do następnego kroku.  
  
##  <a name="vcconattachnewviewa3"></a> Utwórz i Dołącz nowy widok  
 Aby utworzyć i dołączyć nowy widok, należy zmodyfikować `InitInstance` funkcji klasy aplikacji. Modyfikacja dodaje nowy kod, który tworzy nowy obiekt widoku, a następnie inicjuje zarówno `m_pOldView` i `m_pNewView` z tymi dwoma obiektami istniejącego widoku.  
  
 Ponieważ nowy widok jest tworzony w `InitInstance` funkcji nowych i istniejących widoków utrwalić przez czas ich istnienia aplikacji. Jednak aplikacja może równie łatwo utworzyć nowy widok dynamicznie.  
  
 Wstaw ten kod po wywołaniu `ProcessShellCommand`:  
  
 [!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]  
  
 Zapisz zmiany i przejdź do następnego kroku.  
  
##  <a name="vcconswitchingfunctiona4"></a> Implementowanie funkcji przełączania  
 W poprzednim kroku po dodaniu kod, który utworzone i zainicjowane nowy obiekt widoku. Ostatni element głównych jest implementacja metody przełączania `SwitchView`.  
  
 Na końcu pliku implementacji dla klasy aplikacji (MYWINAPP. CPP), dodaj następującą definicję metody:  
  
 [!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]  
  
 Zapisz zmiany i przejdź do następnego kroku.  
  
##  <a name="vcconswitchingtheviewa5"></a> Dodawanie obsługi do przełączania widoku  
 Ostatni krok polega na dodaniu kod, który wywołuje `SwitchView` metody, gdy aplikacja ma przełączać się między widokami. Można to zrobić na kilka sposobów: przez dodawanie nowego elementu menu dla użytkownika wybrać lub wewnętrznie przełączania widoków, gdy są spełnione następujące warunki.  
  
 Aby uzyskać więcej informacji dotyczących dodawania nowych elementów menu i funkcje programu obsługi poleceń, zobacz [programy obsługi dla poleceń i powiadomień dotyczących formantu karty](../mfc/handlers-for-commands-and-control-notifications.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura dokument/widok](../mfc/document-view-architecture.md)

