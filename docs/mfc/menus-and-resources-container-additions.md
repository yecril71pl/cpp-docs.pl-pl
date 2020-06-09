---
title: 'Menu i zasoby: dodatki do kontenera'
ms.date: 11/04/2016
f1_keywords:
- IDP_OLE_INIT_FAILED
- IDP_FAILED_TO_CREATE
- VK_ESCAPE
helpviewer_keywords:
- application accelerator table [MFC]
- VK_ESCAPE key [MFC]
- IDP_FAILED_TO_CREATE macro [MFC]
- visual editing, application menus and resources
- OLE containers [MFC], menus and resources
- accelerator tables [MFC], container applications
- IDP_OLE_INIT_FAILED macro [MFC]
- CONTAIN tutorial [MFC]
- Links menu item [MFC]
ms.assetid: 425448be-8ca0-412e-909a-a3a9ce845288
ms.openlocfilehash: a082a75ef0292e190e597f29be0cdc0bd0b497ef
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626239"
---
# <a name="menus-and-resources-container-additions"></a>Menu i zasoby: dodatki do kontenera

W tym artykule wyjaśniono zmiany, które należy wykonać w menu i innych zasobach w aplikacji kontenera edycji wizualnej.

W aplikacjach kontenera należy wprowadzić dwa typy zmian: modyfikacje istniejących zasobów w celu obsługi edycji wizualizacji OLE i dodania nowych zasobów używanych do aktywacji w miejscu. W przypadku utworzenia aplikacji kontenera za pomocą Kreatora aplikacji te kroki zostaną wykonane dla Ciebie, ale mogą wymagać pewnych dostosowań.

Jeśli nie używasz Kreatora aplikacji, możesz chcieć przyjrzeć się OCLIENT. RC, skrypt zasobów dla przykładowej aplikacji OCLIENT, aby zobaczyć, jak te zmiany zostały zaimplementowane. Zobacz przykład OLE MFC [OCLIENT](../overview/visual-cpp-samples.md).

Tematy omówione w tym artykule obejmują:

- [Dodatki menu kontenerów](#_core_container_menu_additions)

- [Dodatki do tabeli akceleratora](#_core_container_application_accelerator_table_additions)

- [Dodatki do tabeli ciągów](#_core_string_table_additions_for_container_applications)

## <a name="container-menu-additions"></a><a name="_core_container_menu_additions"></a>Dodatki menu kontenerów

Do menu Edycja należy dodać następujące elementy:

|Element|Przeznaczenie|
|----------|-------------|
|**Wstaw nowy obiekt**|Otwiera okno dialogowe OLE Wstaw obiekt, w którym można wstawić połączony lub osadzony element do dokumentu.|
|**Wklej link**|Wkleja link do elementu w schowku do dokumentu.|
|**Zlecenie OLE**|Wywołuje podstawowe zlecenie wybranego elementu. Tekst tego elementu menu zmieni się, aby odzwierciedlić podstawowe zlecenie wybranego elementu.|
|**Linki**|Otwiera okno dialogowe Edytowanie linków OLE, aby zmienić istniejące elementy połączone.|

Poza zmianami wymienionymi w tym artykule, plik źródłowy musi zawierać AFXOLECL. RC, który jest wymagany dla implementacji biblioteka MFC. Wstaw nowy obiekt jest jedynym wymaganym dodatkiem menu. Można dodać inne elementy, ale te wymienione tutaj są najczęściej używane.

Należy utworzyć nowe menu dla aplikacji kontenera, jeśli chcesz obsługiwać aktywację w miejscu zawartych elementów. To menu składa się z tego samego menu plik i okna podręcznego, które są używane podczas otwierania plików, ale ma dwa separatory między nimi. Te separatory są używane do wskazywania miejsca, w którym element serwera (składnik) powinien umieścić swoje menu po aktywowaniu. Aby uzyskać więcej informacji na temat tej techniki łączenia menu, zobacz menu [i zasoby: scalanie menu](menus-and-resources-menu-merging.md).

## <a name="container-application-accelerator-table-additions"></a><a name="_core_container_application_accelerator_table_additions"></a>Dodatki tabel akceleratora aplikacji kontenera

Niewielkie zmiany zasobów tabeli akceleratorów aplikacji kontenera są niezbędne, Jeśli obsługujesz aktywację w miejscu. Pierwsza zmiana umożliwia użytkownikowi naciśnięcie klawisza ucieczki (ESC) w celu anulowania trybu edycji w miejscu. Dodaj następujący wpis do tabeli głównego akceleratora:

|ID|Klucz|Typ|
|--------|---------|----------|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**STANDARDOWYM VIRTKEY**|

Druga zmiana polega na utworzeniu nowej tabeli akceleratora, która odnosi się do nowego zasobu menu utworzonego dla aktywacji w miejscu. Ta tabela zawiera wpisy do menu plików i okien, a także wpis VK_ESCAPE powyżej. Poniższy przykład to tabela akceleratorów utworzona dla aktywacji w miejscu w [kontenerze](../overview/visual-cpp-samples.md)przykładowym MFC:

|ID|Klucz|Typ|
|--------|---------|----------|
|ID_FILE_NEW|CTRL+N|**STANDARDOWYM VIRTKEY**|
|ID_FILE_OPEN|CTRL+O|**STANDARDOWYM VIRTKEY**|
|ID_FILE_SAVE|CTRL+S|**STANDARDOWYM VIRTKEY**|
|ID_FILE_PRINT|CTRL + P|**STANDARDOWYM VIRTKEY**|
|ID_NEXT_PANE|VK_F6|**STANDARDOWYM VIRTKEY**|
|ID_PREV_PANE|SHIFT + VK_F6|**STANDARDOWYM VIRTKEY**|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**STANDARDOWYM VIRTKEY**|

## <a name="string-table-additions-for-container-applications"></a><a name="_core_string_table_additions_for_container_applications"></a>Dodatki do tabeli ciągów dla aplikacji kontenera

Większość zmian w tabelach ciągów dla aplikacji kontenera odpowiada dodatkowym elementom menu wymienionym w [dodatkach menu kontenerów](#_core_container_menu_additions). Dostarczają tekst wyświetlany na pasku stanu po wyświetleniu każdego elementu menu. Poniżej przedstawiono przykładowe wpisy w tabeli ciągów generowane przez Kreatora aplikacji:

|ID|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|Inicjowanie OLE nie powiodło się. Upewnij się, że biblioteki OLE są w poprawnej wersji.|
|IDP_FAILED_TO_CREATE|Nie można utworzyć obiektu. Upewnij się, że obiekt został wprowadzony w rejestrze systemu.|

## <a name="see-also"></a>Zobacz też

[Menu i zasoby (OLE)](menus-and-resources-ole.md)<br/>
[Menu i zasoby: dodatki do serwera](menus-and-resources-server-additions.md)
