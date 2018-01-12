---
title: Kreator konsumenta MFC ODBC | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.class.mfc.consumer.overview
dev_langs: C++
helpviewer_keywords:
- MFC ODBC Consumer Wizard
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ad9e4aeb15d2af04987883b6554d569e3cc16b8d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-odbc-consumer-wizard"></a>Kreator konsumenta MFC ODBC
Tutaj należy wstawić "Wyszukiwanie" podsumowania.  
  
 Ten kreator konfiguruje klasy rekordów ODBC i powiązania danych niezbędnych do uzyskania dostępu z określonego źródła danych.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Źródło danych**  
 **Źródła danych** przycisk umożliwia konfigurowanie określonego źródła danych przy użyciu podanego sterownika ODBC. Aby uzyskać więcej informacji o plikach źródłowych danych (DSN), zobacz [źródeł danych plików](https://msdn.microsoft.com/library/ms715401.aspx) w zestawie SDK ODBC. **Wybierz źródło danych** okno dialogowe ma dwie karty:  
  
-   **Plik źródła danych** kartę: **Szukaj w** pole określa katalog, w którym można wybrać pliki, które mają być używane jako źródła danych. Wartość domyślna to \Program Files\Common Files\ODBC\Data źródeł. Istniejących plików źródeł danych (DSN pliki) są wyświetlane w polu listy głównego. Można albo skonfigurować źródła danych przed przy użyciu czasu **pliku DSN** karcie na [Administrator źródła danych ODBC](https://msdn.microsoft.com/library/ms714024.aspx), lub utworzyć nowe za pomocą tego okna dialogowego.  
  
     Aby utworzyć nowe źródło danych plików z tego okna dialogowego, kliknij przycisk `New` do określenia nazwy DSN; **Utwórz nowe źródło danych** zostanie wyświetlone okno dialogowe. W **Utwórz nowe źródło danych** okna dialogowego, wybierz odpowiedni sterownik a kliknij przycisk `Next`; kliknij przycisk **Przeglądaj**i wybierz nazwę pliku, który ma być używany jako źródło danych (trzeba wybrać "Wszystkie pliki" Widok z systemem innym niż DSN plików, takich jak pliki xls); Kliknij przycisk `Next`, a następnie kliknij przycisk **Zakończ**. (Jeśli wybrano plików z systemem innym niż DSN, zostanie wyświetlona okno dialogowe sterownika, takie jak "ODBC Instalator programu Microsoft Excel," który przekonwertuje pliku DSN).  
  
    > [!NOTE]
    >  Można również utworzyć nowe źródło danych pliku wcześniej przy użyciu Administrator źródła danych ODBC. Z **Start** menu, wybierz opcję **ustawienia**, **Panelu sterowania**, **narzędzia administracyjne**, **źródła danych (ODBC)**, a następnie **Administrator źródła danych ODBC**.  
  
     **Nazwa DSN** pole można określić nazwę pliku źródła danych. Należy się upewnić, że nazwa DSN kończy się odpowiednie rozszerzenie pliku, takie jak xls dla plików programu Excel lub .mdb dostępu do plików.  
  
     Aby uzyskać więcej informacji dotyczących nazw DSN, zobacz [źródeł danych plików](https://msdn.microsoft.com/library/ms715401.aspx) w zestawie SDK ODBC.  
  
-   **Źródło danych komputera** kartę: Ta karta zawiera listę systemu oraz źródeł danych użytkownika. Źródła danych użytkownika są specyficzne dla użytkownika na tym komputerze. System dane mogą zostać użyte przez wszystkich użytkowników na tym komputerze lub w usłudze ogólnosystemowe. Zobacz [źródeł danych komputera](https://msdn.microsoft.com/library/ms710952.aspx) w zestawie SDK ODBC  
  
 Aby uzyskać więcej informacji dotyczących źródła danych ODBC, zobacz [źródeł danych](https://msdn.microsoft.com/library/ms711688.aspx) w zestawie SDK ODBC.  
  
 Kliknij przycisk **OK** aby zakończyć. **Obiektu bazy danych wybierz** zostanie wyświetlone okno dialogowe. To okno dialogowe należy wybrać tabelę lub wyświetlić, które będą używane przez klienta. Pamiętaj, że możesz wybrać wiele widoków i tabel, przytrzymując klawisz control klikając elementy.  
  
 **Klasy**  
 Nazwa klasy konsumentów, domyślnie na podstawie nazwy pliku lub maszyny źródła danych wybrana.  
  
 **w pliku .h**  
 Nazwa pliku nagłówka klasy konsumentów, domyślnie na podstawie nazwy pliku lub maszyny źródła danych wybrana.  
  
 **plik .cpp**  
 Nazwa pliku implementacji klasy konsumentów, domyślnie na podstawie nazwy pliku lub maszyny źródła danych wybrana.  
  
 **Typ**  
 Określa, czy zestaw rekordów jest dynamiczny (ustawienie domyślne) lub migawka.  
  
-   **Zestaw dynamiczny**: Określa, że zestaw rekordów jest dynamiczny. Zestaw dynamiczny jest wynikiem kwerendę, która udostępnia widok indeksowany w danych, którego dotyczy kwerenda bazy danych. Zestaw dynamiczny buforuje tylko integralną indeks do oryginalnych danych i w związku z tym uzyskanie oferty a wydajności za pośrednictwem migawki. Wskazuje indeks bezpośrednio każdego rekordu znaleziono wyniku zapytania i wskazuje, czy rekord jest usuwany. Masz również dostęp do aktualnych informacji w rekordach, którego dotyczy kwerenda. Domyślnie włączone.  
  
-   **Migawki**: Określa, czy zestaw rekordów jest to migawka. Migawka jest wynik zapytania i widoku do bazy danych w jednym punkcie w czasie. Wszystkie rekordy znaleziono wyniku zapytania są buforowane, dlatego nie ma zmiany w oryginalnym rekordów.  
  
 **Powiąż wszystkich kolumn**  
 Określa, czy wszystkie kolumny w tabeli są powiązane. Po zaznaczeniu tego pola (ustawienie domyślne), wszystkie kolumny są powiązane; Jeśli to pole nie jest zaznaczone, Brak kolumn są powiązane i należy powiązać je ręcznie w klasie zestawu rekordów.  
  
## <a name="see-also"></a>Zobacz też  
 [Klient MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [Dodawanie funkcji z kreatorami kodów](../../ide/adding-functionality-with-code-wizards-cpp.md)

