---
title: Architektura dokument widok | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CView class [MFC], view architecture
- CDocument class [MFC]
- MFC, views
- views [MFC], MFC document/view model
- document objects [MFC]
- document objects [MFC], MFC document/view model
- MFC, documents
- documents [MFC], MFC document/view model
- document objects [MFC], document/view architecture
ms.assetid: 6127768a-553f-462a-b01b-a5ee6068c81e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9554af9443bbd6a6394789343294630104c96f1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="documentview-architecture"></a>Architektura dokument/widok
Domyślnie Kreator aplikacji MFC tworzy szkielet aplikacji z klasy dokumentów i klasę widoku. MFC oddziela zarządzania danymi w tych dwóch klas. Dokument przechowuje dane i zarządza drukowanie danych i koordynuje aktualizowania wielu widoków danych. Widok przedstawia dane i zarządza interakcji z użytkownikiem z nim, w tym wybór i edytowania.  
  
 W tym modelu obiektu dokumentu MFC odczytuje i zapisuje dane do magazynu trwałego. Dokumentu może również udostępniać interfejs do danych wszędzie tam, gdzie znajduje się on (na przykład w bazie danych). Obiekt osobny widok zarządza wyświetlania danych z renderowania danych w oknie Wybór użytkownika i edytowanie danych. Widok uzyskuje dostęp do wyświetlania danych z dokumentu i komunikuje się w dokumencie wszelkie zmiany danych.  
  
 Chociaż można łatwo zastąpienia lub zignorować separacji dokument/widok, istnieją atrakcyjnych przyczyn, które należy wykonać ten model, w większości przypadków. Jest jednym z najlepszych, gdy potrzebne są różne widoki tego samego dokumentu, takie jak zarówno arkusza kalkulacyjnego i widoku wykresu. Model dokument/widok umożliwia obiektu osobny widok reprezentują każdego widoku danych, podczas wspólnego kodu do wszystkich widoków (np. Aparat obliczania) może znajdować się w dokumencie. Dokument ma również zadania aktualizacji we wszystkich widokach zmianie danych.  
  
 Architektura dokument/widok MFC ułatwia obsługuje wiele widoków, wiele typów dokumentów okna podziału i inne funkcje cenne interfejsu użytkownika.  
  
 Części najbardziej widoczne zarówno dla użytkownika i programisty, struktura MFC są dokument i widoku. Większość pracy w tworzeniu aplikacji z architekturą przechodzi w stan zapisywania dokumentów i widoku klas. Zawiera opis tej rodziny artykułu:  
  
-   Na potrzeby dokumentów i widoków i sposób ich interakcji w ramach.  
  
-   Co należy zrobić, aby ich wdrażania.  
  
 Istotą dokument/widok są cztery klucza klasy:  
  
 [CDocument](../mfc/reference/cdocument-class.md) (lub [COleDocument](../mfc/reference/coledocument-class.md)) klasa obsługuje obiekty używane do przechowywania lub kontrolować danych programu i zapewnia podstawowe funkcje zdefiniowane przez programistę dokumentu klas. Dokument reprezentuje jednostkę danych zwykle użytkownik otwiera przy użyciu polecenia Otwórz w menu Plik i w menu Plik jest zapisywany przy użyciu polecenia Zapisz.  
  
 [CView](../mfc/reference/cview-class.md) (lub jeden z jej klas pochodnych wiele) zapewnia podstawowe funkcje zdefiniowane przez programistę widoku klasy. Widok jest dołączony do dokumentu i działa jako pośrednik między dokumentu i użytkownika: widok renderuje obraz dokumentu na ekranie i interpretuje dane wejściowe użytkownika jako operacje na dokument. Widok również renderuje obraz zarówno drukowania i podglądu wydruku.  
  
 [Cframewnd —](../mfc/reference/cframewnd-class.md) (lub jeden z jego odmiany) obsługuje obiekty, które zawiera ramki wokół co najmniej jeden widok dokumentu.  
  
 [Cdoctemplate —](../mfc/reference/cdoctemplate-class.md) (lub [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) lub [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)) obsługuje obiekt, który koordynuje co najmniej jeden istniejących dokumentów danego typu i zarządza nimi tworzenie poprawny dokument, widoku i ramki okna obiektów dla tego typu.  
  
 Na poniższej ilustracji przedstawiono relację między dokument i jego widoku.  
  
 ![Widok jest częścią dokumentu, który jest wyświetlany](../mfc/media/vc379n1.gif "vc379n1")  
Wyświetl i dokumentów  
  
 Implementacja dokument/widok w bibliotece klas oddziela samych danych z ich wyświetlania i użytkownika operacje na danych. Wszystkie zmiany danych są zarządzane za pośrednictwem klasy dokumentu. Widok wywołuje dostępu i zaktualizować dane w tym interfejsie.  
  
 Dokumenty, ich skojarzone widoków i okna ramowe, które widoki klatek są tworzone przez szablon dokumentu. Szablon dokumentu jest odpowiedzialny za tworzenie i zarządzanie nimi wszystkie dokumenty typu jeden dokument.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Portret architektury dokument/widok](../mfc/a-portrait-of-the-document-view-architecture.md)  
  
-   [Zalety architektury dokument/widok](../mfc/advantages-of-the-document-view-architecture.md)  
  
-   [Klasy dokumentów i widoku tworzone przez Kreatora aplikacji](../mfc/document-and-view-classes-created-by-the-mfc-application-wizard.md)  
  
-   [Alternatywy dla architektury dokument/widok](../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [Dodawanie wielu widoków do pojedynczego dokumentu](../mfc/adding-multiple-views-to-a-single-document.md)  
  
-   [Używanie dokumentów](../mfc/using-documents.md)  
  
-   [Używanie widoków](../mfc/using-views.md)  
  
-   [Wiele typów dokumentów, widoków i okien ramowych](../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [Inicjowanie i oczyszczanie dokumentów i widoków](../mfc/initializing-and-cleaning-up-documents-and-views.md)  
  
-   [Inicjowanie własne ma zostać dodany do dokumentu i widoku klas](../mfc/creating-new-documents-windows-and-views.md)  
  
-   [Używanie klas baz danych z dokumentami i widokami](../data/mfc-using-database-classes-with-documents-and-views.md)  
  
-   [Używanie klas baz danych bez dokumentów i widoków](../data/mfc-using-database-classes-without-documents-and-views.md)  
  
-   [Przykłady](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)   
 [Windows](../mfc/windows.md)   
 [Okna ramowe](../mfc/frame-windows.md)   
 [Szablony dokumentów i proces tworzenia dokumentu/widoku](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Tworzenie dokumentu/widoku](../mfc/document-view-creation.md)   
 [Tworzenie nowych dokumentów, okien i widoków](../mfc/creating-new-documents-windows-and-views.md)

