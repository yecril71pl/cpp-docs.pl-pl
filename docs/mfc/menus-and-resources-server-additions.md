---
title: 'Menu i zasoby: dodatki do serwera | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IDP_OLE_INIT_FAILED
dev_langs:
- C++
helpviewer_keywords:
- OLE visual editing servers [MFC]
- accelerator tables [MFC], server applications
- visual editing [MFC], application menus and resources
- server applications [MFC], accelerator table
- string tables [MFC], visual editing applications
- servers [MFC], menu additions
- resources [MFC], server applications
- OLE server applications [MFC], menus and resources
- string editing [MFC], visual editing applications
- IDP_OLE_INIT_FAILED macro [MFC]
- server applications [MFC], OLE menus and resources
- OLE initialization failure [MFC]
ms.assetid: 56ce9e8d-8f41-4db8-8dee-e8b0702d057c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 86b941820b439afc8b914142b412995df30f109c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="menus-and-resources-server-additions"></a>Menu i zasoby: dodatki do serwera
W tym artykule opisano zmiany, które należy wprowadzić do menu i innych zasobów w programie visual edycji aplikacji serwera (składnik). Aplikacja serwera wymaga wielu dodatków do struktury menu i innych zasobów, ponieważ może być uruchamiany w jednym z trzech trybów: autonomiczna samego, lub osadzonych w miejscu. Zgodnie z opisem w [menu i zasoby (OLE)](../mfc/menus-and-resources-ole.md) artykuł, są maksymalnie cztery zestawy menu. Wszystkie cztery są używane dla aplikacji MDI pełny serwer, a tylko trzy służą do miniserver. Kreator aplikacji utworzy niezbędne dla typu serwera, który ma układ menu. Może być konieczne dostosowanie niektórych.  
  
 Jeśli nie używasz Kreatora aplikacji, można przyjrzeć się HIERSVR. RC, skrypt zasobu dla przykładowej aplikacji MFC [HIERSVR](../visual-cpp-samples.md), aby zobaczyć, jak te zmiany są implementowane.  
  
 Omówione w tym artykule tematy obejmują:  
  
-   [Dodatkowe Menu serwera](#_core_server_menu_additions)  
  
-   [Dodatki do tabeli akceleratora](#_core_server_application_accelerator_table_additions)  
  
-   [Dodatki tabeli ciągów](../mfc/menus-and-resources-container-additions.md)  
  
-   [Dodatki miniserver](#_core_mini.2d.server_additions)  
  
##  <a name="_core_server_menu_additions"></a> Dodatkowe Menu serwera  
 Aplikacje serwera (składnik) musi mieć zasoby menu dodane w celu obsługi edycja wizualna OLE. Menu używany, gdy aplikacja jest uruchamiana w trybie autonomicznym, nie ma potrzeby można zmienić, ale przed skompilowaniem aplikacji należy dodać dwa nowe zasoby menu: jeden do obsługi aktywacji w miejscu i jeden do obsługi serwera pełni okna. Oba zasoby menu są używane przez aplikacje pełnego i miniserver.  
  
-   Aby zapewnić obsługę aktywacji w miejscu, należy utworzyć zasobów menu, która jest bardzo podobny do zasobu menu używana podczas uruchamiania w trybie autonomicznym. Różnica w tym menu są elementy pliku i okna (i innych elementów menu, które zajmują się aplikacji, a nie dane) Brak. Aplikacja kontenera poda te elementy menu. Więcej informacji na temat i przykładem, ta metoda scalania menu, zobacz artykuł [menu i zasoby: scalanie Menu](../mfc/menus-and-resources-menu-merging.md).  
  
-   Do obsługi aktywacji całkowicie otwarte, należy utworzyć niemal identyczny jak zasobów menu używane zasobów menu uruchamiania w trybie autonomicznym. Modyfikacja tylko do tego zasobu menu jest niektóre elementy są przeformułować odzwierciedlają fakt, że serwer działa w elemencie osadzonego wewnątrz złożonego dokumentu.  
  
 Oprócz zmian wymienione w tym artykule, musi zawierać AFXOLESV Twojego pliku zasobu. RC, który jest wymagany do wykonania Microsoft Foundation Class Library. Ten plik jest w podkatalogu MFC\Include.  
  
##  <a name="_core_server_application_accelerator_table_additions"></a> Dodatki tabeli akceleratora do serwera aplikacji  
 Dwa nowe zasoby tabeli akceleratora musi zostać dodany do serwera aplikacji; odpowiadają one bezpośrednio nowych zasobów menu opisany wcześniej. W pierwszej tabeli akceleratora jest używany, gdy aplikacja serwera jest aktywny w miejscu. Składa się z wszystkich wpisów w tabeli akceleratora widoku, z wyjątkiem tych, powiązane z pliku i okna menu.  
  
 Druga tabela jest prawie dokładną kopię tabeli akceleratora widoku. Różnice równoległe zmiany wprowadzone w pełni Otwórz menu wspomnianego [dodatki do serwera Menu](#_core_server_menu_additions).  
  
 Na przykład tych zmian w tabeli akceleratora porównania **IDR_HIERSVRTYPE_SRVR_IP** i **IDR_HIERSVRTYPE_SRVR_EMB** akceleratora tabel z **IDR_MAINFRAME** w HIERSVR. W pliku RC w przykładowym MFC OLE [HIERSVR](../visual-cpp-samples.md). Akceleratorów okno i pliku brakuje tabeli w miejscu i dokładne ich kopie w osadzonych tabeli.  
  
##  <a name="_core_string_table_additions_for_server_applications"></a> Ciąg tabeli dodatków dla aplikacji serwera  
 W aplikacji serwera konieczne jest dodanie tabeli tylko jeden ciąg — ciąg na wskazują, że nie można zainicjować OLE. Na przykład w tym miejscu jest generowany przez Kreatora aplikacji ciąg spisu:  
  
|ID|String|  
|--------|------------|  
|**IDP_OLE_INIT_FAILED —**|Nie można zainicjować interfejsu OLE. Upewnij się, że biblioteki OLE są zainstalowane poprawne wersje.|  
  
##  <a name="_core_mini.2d.server_additions"></a> Dodatki miniserver  
 Dotyczą tego samego dodatków miniservers jako wymienione powyżej dla pełnej serwerów. Ponieważ miniserver nie można uruchomić w trybie autonomicznym, jego menu głównego jest znacznie mniejszy. Menu główne tworzone przez Kreatora aplikacji ma tylko menu Plik zawierający tylko elementy zakończenia i o. Menu osadzone i w miejscu i akceleratorów miniservers są takie same jak dla pełnej serwerów.  
  
## <a name="see-also"></a>Zobacz też  
 [Menu i zasoby (OLE)](../mfc/menus-and-resources-ole.md)   
 [Menu i zasoby: scalanie menu](../mfc/menus-and-resources-menu-merging.md)

