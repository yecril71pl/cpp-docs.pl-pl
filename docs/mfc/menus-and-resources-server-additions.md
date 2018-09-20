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
ms.openlocfilehash: 14a7ae414c9cd3015d1f70b779a2c19ea1329ed4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388059"
---
# <a name="menus-and-resources-server-additions"></a>Menu i zasoby: dodatki do serwera

W tym artykule opisano zmiany, które należy podjąć, menu i innych zasobów w ramach visual edycji aplikacji serwera (składnik). Aplikacja serwera wymaga wielu dodatków do struktury menu i innych zasobów, ponieważ może być uruchamiany w jednym z trzech trybów: autonomiczna samodzielnie, embedded, lub w miejscu. Zgodnie z opisem w [menu i zasoby (OLE)](../mfc/menus-and-resources-ole.md) artykułu, są maksymalnie cztery zestawy menu. Wszystkie cztery są używane dla aplikacji MDI pełny serwer, a tylko trzy są używane na potrzeby miniserver. Kreator aplikacji utworzy układ menu niezbędne dla typu serwera, który ma. Dostosowania, może być konieczne.

Jeśli nie używasz Kreatora aplikacji, możesz przyjrzeć się HIERSVR. RC, skrypt zasobu dla przykładowej aplikacji MFC [HIERSVR](../visual-cpp-samples.md), aby zobaczyć, jak te zmiany są zaimplementowane.

Tematy omówione w tym artykule obejmują:

- [Dodatki do serwera Menu](#_core_server_menu_additions)

- [Dodatki do tabeli akceleratora](#_core_server_application_accelerator_table_additions)

- [Dodatki tabeli ciągów](../mfc/menus-and-resources-container-additions.md)

- [Dodatki miniserver](#_core_mini.2d.server_additions)

##  <a name="_core_server_menu_additions"></a> Dodatki do serwera Menu

Aplikacje serwera (składnik) musi mieć zasobów menu dodanych do obsługi edycja wizualna OLE. Menu używany, gdy aplikacja jest uruchamiana w trybie autonomicznym nie trzeba go zmienić, ale należy dodać dwa nowe zasoby menu przed kompilacją aplikacji: jeden do obsługi aktywacji w miejscu i jeden do obsługi serwera są w pełni otwarty. Oba zasoby menu są używane przez aplikacje pełnego i miniserver.

- Aby zapewnić obsługę aktywacji w miejscu, należy utworzyć zasób menu, który jest bardzo podobny do zasobu menu używana podczas uruchamiania w trybie autonomicznym. Różnica w tym menu są elementy pliku i okna (i inne elementy menu, które zajmują się aplikacji, a nie dane) Brak. Aplikacja kontenera będzie dostarczać te elementy menu. Aby uzyskać więcej informacji na temat i przykładem, ta technika scalania menu, zobacz artykuł [menu i zasoby: scalanie Menu](../mfc/menus-and-resources-menu-merging.md).

- Aby zapewnić obsługę aktywacji pełni otwarty, należy utworzyć prawie identyczna zasobu menu używanego zasobu menu uruchamiania w trybie autonomicznym. Modyfikacja tylko do tego zasobu menu jest niektóre elementy są przeformułować odzwierciedlają fakt, że serwer działa element osadzony w dokumencie złożonym.

Oprócz zmian wymienione w tym artykule Twojego pliku zasobu musi zawierać AFXOLESV. RC, który jest wymagany do wykonania w bibliotece klas Microsoft Foundation. Ten plik znajduje się w podkatalogu MFC\Include.

##  <a name="_core_server_application_accelerator_table_additions"></a> Dodawanie tabeli akceleratora aplikacji serwera

Dwa nowe zasoby tabeli akceleratora muszą zostać dodane do serwera aplikacji; odpowiadają one bezpośrednio nowych zasobów menu opisany wcześniej. W pierwszej tabeli akceleratora jest używany, gdy aplikacja serwera jest aktywowany w miejscu. Składa się z wszystkich wpisów w tabeli akceleratora tego widoku, z wyjątkiem tych powiązany plik i okno menu.

Druga tabela jest niemal dokładną kopię tego widoku tabeli klawiszy skrótu. Ewentualne różnice równoległe zmiany wprowadzone w pełni otwarty menu wymienionych w [dodatki do serwera Menu](#_core_server_menu_additions).

Na przykład te zmiany w tabeli akceleratora Porównaj tabel akceleratora IDR_HIERSVRTYPE_SRVR_IP i IDR_HIERSVRTYPE_SRVR_EMB IDR_MAINFRAME w HIERSVR. Plik RC zawarte w przykładzie MFC OLE [HIERSVR](../visual-cpp-samples.md). Akceleratory plików i okna Brak tabeli w miejscu i dokładnie ich kopie znajdują się w tabeli osadzonych.

##  <a name="_core_string_table_additions_for_server_applications"></a> Parametry tabeli dodatki dla aplikacji serwerowych

W aplikacji serwera konieczne jest dodanie tabeli tylko jeden ciąg — ciąg do oznaczają, że Inicjalizacja OLE nie powiodło się. Na przykład Oto wpis tabeli ciągów, który generuje Kreatora aplikacji:

|ID|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|Zainicjowanie OLE nie powiodło się. Upewnij się, że biblioteki OLE są w poprawnej wersji.|

##  <a name="_core_mini.2d.server_additions"></a> Dodatki miniserver

Ten sam dodatki dotyczą miniservers jako wymienione powyżej dla pełnej serwerów. Ponieważ miniserver nie może działać w trybie autonomicznym, głównym menu jest znacznie mniejszy. Menu głównego tworzone przez Kreatora aplikacji ma tylko menu Plik zawierający tylko tych elementów, zakończenia i o. Menu osadzone i w miejscu i akceleratory miniservers są takie same, jak w przypadku pełnej serwerów.

## <a name="see-also"></a>Zobacz też

[Menu i zasoby (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Menu i zasoby: scalanie menu](../mfc/menus-and-resources-menu-merging.md)

